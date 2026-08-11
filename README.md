# AI Scribe – AI-Powered Medical Documentation Platform 🏥

<div align="center"> 
  <img src="https://shields.io" alt="FHIR R4"> 
  <img src="https://shields.io" alt="HL7 Compliant">
  <img src="https://shields.io" alt="Next.js"> 
  <img src="https://shields.io" alt="FastAPI"> 
  <img src="https://shields.io" alt="Supabase"> 
</div>

> **Note on Repository Access:** The complete source code, asynchronous background worker configurations, and proprietary FHIR interoperability pipelines for this application are hosted in a private repository to protect healthcare data structures and regulatory system architecture. Full code access can be securely granted to recruiters, hiring managers, or interviewers upon request. Please contact me at info@edgehit.ca or via linkedin.com/in/femiag
---

## 💡 Project Overview
AI Scribe is a comprehensive, production-grade medical documentation and virtual appointment platform engineered for healthcare providers. The application utilizes advanced artificial intelligence to securely transcribe real-time patient-practitioner conversations and automatically structure them into clinically accurate, specialized documentation. 

Designed natively around enterprise healthcare ecosystems, the platform features multi-location clinic topology, granular patient data consent management, and full **FHIR R4 (HL7)** compliance for seamless interoperability with legacy EMR/EHR systems (such as OSCAR, TELUS, and Meditech).

---

## 📱 Previews & Media
<img width="1508" height="1202" alt="Screenshot 2026-08-10 at 6 49 49 PM" src="https://github.com/user-attachments/assets/4a46ffbd-dc75-423e-be75-80e7465edabf" />
<img width="1345" height="998" alt="Screenshot 2026-08-10 at 7 35 57 PM" src="https://github.com/user-attachments/assets/22a9e890-e21c-4f70-ab4c-b5f55bd80c71" />
<img width="1344" height="1183" alt="Screenshot 2026-08-10 at 7 39 52 PM" src="https://github.com/user-attachments/assets/ec9f7573-903d-4c52-95c5-5b4b65f48c87" />


---

## 🛠️ Distributed Tech Stack & Architecture
The system is built on a decoupled, production-scale microservices architecture designed to prevent main-thread blocking during intense processing tasks:

### Client Interface (Frontend)
* **Framework:** Next.js 14 (App Router) – Powering stateful multi-clinic views, real-time audio visualization components (via Wavesurfer.js), and dynamic analytical charts (via Recharts).
* **Media Pipelines:** MediaRecorder Web APIs paired with WebRTC layers (via Daily.co SDK) to drive interactive virtual appointments and waiting rooms.

### Core Server & Distributed Queues (Backend)
* **Framework:** FastAPI – An asynchronous, high-throughput Python gateway managing authenticated REST endpoints and stateful WebSocket routers.
* **Background Workers:** Celery & Redis – Independent distributed task queues processing heavy, long-running data synthesis pipelines asynchronously to ensure high server availability.

### Secure Data & Storage Layer
* **Database & Auth:** Supabase (PostgreSQL) – Implements rigorous Row Level Security (RLS) policies and cryptographically verified JSON Web Token (JWT) session routing.
* **Compliance Schema:** Programmatic data mapping layers fully compliant with the global **FHIR R4** standard (HL7 specification).

---

## 🏆 Key Features & Engineering Challenges Solved

### 1. Healthcare Interoperability & FHIR R4 REST API Compliance
Engineered an enterprise-ready compliance abstraction layer transforming incoming data models into standardized JSON structures. The API fully implements and validates standard FHIR R4 resources including:
* **Core Resources:** `Patient`, `Practitioner`, `Organization`, `Location`
* **Clinical Context:** `Appointment`, `Encounter`, `Observation`, `Condition`
* **Directives & Storage:** `MedicationRequest`, `DocumentReference`

### 2. Low-Latency WebSocket Transcription & Clinical Note Synthesis
Developed stateful **FastAPI WebSockets** to ingest continuous data from the frontend MediaRecorder API. The backend orchestrates multi-model AI streams (via Deepgram Nova-2 and Groq Llama architectures) to convert raw voice streams into specialized, structured notes—such as **SOAP, APSO, or Narrative formats**—customized to medical sub-specialties (Cardiology, Family Medicine, Psychiatry) in real-time.

### 3. Asynchronous Task Architecture (Celery & Redis)
To avoid degradation of the user experience during long data processing intervals, intensive workloads (such as generating end-of-day multi-location reports, auditing trails, and exporting complex DOCX/CSV medical files) are decoupled from the main HTTP loop. FastAPI hands these workloads off to a **Redis** message broker, where independent **Celery worker daemons** process them safely in the background.

### 4. Advanced Security, Auditing & Consent Controls
Architected a secure framework to respect Patient Health Information (PHI) constraints. The database layer leverages strict Row Level Security (RLS) to enforce organization-network boundaries and location isolation. Added custom middleware to write absolute, unalterable administrative audit logs tracking data access alongside flexible, patient-controlled data sharing permissions.

---

## 🗺️ Long-Term Development Roadmap
1. **Biometric Voice Fingerprinting:** Integrating speaker-diarization models to automatically distinguish between the practitioner's voice and the patient's voice in multi-person environments.
2. **Automated ICD-10 Code Extraction:** Training downstream NLP models to parse finished SOAP documentation and automatically suggest standard medical billing codes.
3. **Offline-First Synchronization Nodes:** Developing an offline-first buffer queue inside the client app to gracefully cache audio fragments during localized clinic internet dropouts.
