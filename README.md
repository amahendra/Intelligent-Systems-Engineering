# Intelligent Systems Engineering

**MT25C02 — Rekayasa Sistem Cerdas**  
**Master of Information Technology (Magister Teknologi Informasi)**  
**Faculty of Engineering and Design, Universitas Bunda Mulia (UBM)**  
**Credits:** 3 SKS · **Semester:** 2

This repository provides lecture materials, Google Colab notebooks, sample datasets, and practical exercises for **Intelligent Systems Engineering**. The course focuses on the design, evaluation, integration, and operationalization of **enterprise-scale intelligent systems**, particularly applications built with foundation models and generative AI.

The emphasis is on engineering a **complete, reliable, scalable, secure, and measurable system**—not merely training or prompting an AI model.

> **Repository status:** Course materials are added progressively. A session listed in the syllabus does not necessarily have a published notebook yet. The directory tree below is the recommended organization for this repository.

## Learning outcomes

According to the official course syllabus (RPS), students are expected to:

1. **CPMK 1 — Explain enterprise intelligent systems.** Describe reference architectures and the roles of data/AI pipelines, model serving, observability, security, and scalability.
2. **CPMK 2 — Design from requirements.** Analyze business needs and translate them into reliable and measurable architectures using foundation models or generative AI.
3. **CPMK 3 — Evaluate operational readiness.** Assess an intelligent system against service-level objectives, reliability, governance, security, cost, and operational considerations.
4. **CPMK 4 — Present an end-to-end design.** Communicate and justify a coherent, measurable intelligent-system architecture for an enterprise or smart-city use case.

The course contributes to the program outcomes **CPL-03**, **CPL-06**, and **CPL-07**, covering intelligent-system engineering, applied AI system development, and data-driven decision support.

## Course syllabus

The topics and sequence below follow the RPS. Practical exercises complement the syllabus; they do not replace its specified learning outcomes or assessments.

| Session | Topic | Key concepts / expected work |
|:--:|---|---|
| 1 | **Introduction to Enterprise Intelligent Systems** | Intelligent systems vs. AI prototypes and AI products; enterprise use cases; reference architectures; system boundaries. |
| 2 | **AI Engineering Stack** | Data, model, serving, and observability layers; training-serving skew; online/offline inference; system architecture diagrams. |
| 3 | **Requirements Engineering** | Business objectives and KPIs; SLA/SLO/SLI; latency, throughput, and availability; cost-performance trade-offs; requirements sheet. |
| 4 | **Foundation Model Application Design Patterns** | Prompting; retrieval augmentation (RAG); tool use; multi-step orchestration; architecture selection and justification. |
| 5 | **Enterprise System Integration** | Data ingestion and transformation; API orchestration; event-driven pipelines; integration with enterprise systems. |
| 6 | **Evaluation and Operations** | Offline/online evaluation; monitoring for drift and quality; guardrails and policy checks; incident handling. |
| 7 | **Governance and Security** | Access control; prompt injection and model risks; privacy and compliance; responsible AI governance. |
| — | **Midterm Examination (UTS)** | Written examination on concepts, architecture selection, and technical justification. |
| 8 | **Knowledge-Intensive Intelligent Systems** | Internal copilots; enterprise search; knowledge workflows; human-in-the-loop design. |
| 9 | **Agentic System Design** | Planning loops; tool calling; state and memory; workflow guardrails and autonomy boundaries. |
| 10 | **Deployment Strategy** | Cloud/on-premises/edge options; inference economics; scalability; release and rollback. |
| 11 | **Observability and Post-Deployment Governance** | Logging and tracing; model behavior analytics; review and escalation; continuous improvement. |
| 12 | **End-to-End System Design Documentation** | Architecture narrative; component diagrams; risk/control matrix; rollout plan. |
| 13 | **Design Review and Technical Justification** | Review system designs and defend technical trade-offs, risks, and assumptions. |
| 14 | **Integrative Review** | Consolidate course concepts and prepare the final architecture presentation. |
| — | **Final Examination (UAS)** | Group presentation of an enterprise/smart-city intelligent system covering requirements, architecture, security, evaluation, and deployment. |

## Repository layout

A suggested layout that separates teaching materials, executable code, input data, and generated results:

```text
intelligent-systems-engineering/
├── README.md
├── lectures/
│   ├── session_01/
│   ├── session_02/
│   ├── session_03/
│   ├── session_04/
│   ├── session_05/
│   └── ...
├── notebooks/
│   ├── session_02_foundation_models_simple.ipynb
│   ├── ISE_Sesi4_Design_Patterns_Colab_Free.ipynb
│   └── session_05_enterprise_system_integration.ipynb
├── datasets/
│   └── railway_maintenance/
│       ├── SOP-PS-001_Pemeriksaan_Awal_Bearing.txt
│       ├── SOP-PS-002_Pemantauan_Suhu_dan_Getaran.txt
│       ├── SOP-PS-003_Pelaporan_dan_Persetujuan_Tindak_Lanjut.txt
│       └── sensor_readings.csv
└── results/
    └── .gitkeep
```

**Notes:**

- The filenames above correspond to practical materials prepared for this course; include them when publishing the repository.
- The `lectures/` folders can contain editable slide decks or lecture PDFs. They are optional until the materials are published.
- Notebook-generated results should normally stay out of version control. The `results/` directory is optional.
- The Session 4 notebook expects the SOP text files to be available in its Colab `sample_data/` directory (or uploaded as its companion ZIP). Session 5 can create its sample data automatically if they are absent.

## Practical project: Railway Maintenance Assistant

Several sessions use a **single continuing case study**: an AI assistant that helps maintenance personnel inspect a simulated railway asset, `TR-001`.

The case study allows students to incrementally connect:

- **Asset and sensor data:** identifiers, temperatures, vibration readings, timestamps, and measurement units.
- **Maintenance documentation:** versioned Standard Operating Procedures (SOPs) retrieved as supporting evidence.
- **Foundation models:** instruction-following models that summarize available evidence and prepare recommendations.
- **Enterprise services:** REST APIs, workflow orchestration, event processing, and maintenance requests.
- **Human control:** supervisor review before any operational work order is approved.

### Data flow

```text
Maintenance question / asset ID
             |
             v
      Input validation
             |
             v
   Sensor data / REST API -------> Sensor readings + timestamp
             |
             v
      SOP retrieval -------------> Relevant, valid SOP excerpt
             |
             v
   Context preparation
             |
             v
    Foundation model
             |
             v
  Output / evidence validation
             |
             v
 Draft maintenance recommendation
             |
             v
    Supervisor approval
             |
             v
       Audit record
```

**Important:** The railway asset readings, documents, and any example operating thresholds are **educational simulations**. They must not be treated as certified railway maintenance or safety procedures. The system must not invent safety limits or execute safety-critical actions without appropriate authorization.

## Google Colab notebooks

| Session | Notebook | Main exercises | Runtime |
|---|---|---|---|
| 2 | [`session_02_foundation_models_simple.ipynb`](notebooks/session_02_foundation_models_simple.ipynb) | Compare small text-to-text foundation models using a railway-maintenance task. | Colab Free; CPU-oriented version. |
| 4 | [`ISE_Sesi4_Design_Patterns_Colab_Free.ipynb`](notebooks/ISE_Sesi4_Design_Patterns_Colab_Free.ipynb) | Compare prompt-only, structured prompting, contextual prompting, retrieval, and tool/workflow patterns; export evaluations. | Colab Free; Ollama + Qwen2.5 0.5B Instruct. |
| 5 | [`session_05_enterprise_system_integration.ipynb`](notebooks/session_05_enterprise_system_integration.ipynb) | Data ingestion and validation; local REST API testing; API orchestration; event-driven processing; approval and audit logging. | Colab Free; Python, FastAPI TestClient, optional Ollama model inference. |

Additional exercises and notebooks may be added as the course progresses.

### Run a notebook

1. Open [Google Colab](https://colab.research.google.com/).
2. Choose **File → Open notebook → GitHub**, paste the repository URL, and select the desired notebook. Alternatively, upload an `.ipynb` file.
3. Use a **CPU runtime** unless a particular notebook explicitly requests a GPU.
4. Read the notebook's setup cell and provide the referenced SOP files if required.
5. Run cells **in order**. Review the outputs and complete the questions provided in the notebook.
6. Download the generated CSV files for further evaluation in Excel or another analysis tool.

Some notebooks install Python packages or download model weights during setup. This requires internet access at least once per fresh Colab runtime. **Using Ollama does not require a Hugging Face login or a paid model API key**, but model downloads and execution depend on Colab runtime resources.

## Session 4: Foundation model application design

Session 4 compares several approaches on the **same questions and documents**, making differences observable rather than purely theoretical:

1. **Prompt-only:** Answer without external evidence.
2. **Structured prompt:** Apply explicit output instructions while keeping the task unchanged.
3. **Prompt + context:** Add selected, relevant SOP evidence.
4. **Retrieval + generation:** Find supporting documents before generating a response.
5. **Retrieval + tools + workflow:** Combine evidence, operational data, validation, and controlled execution.

Students compare **correctness**, **groundedness**, **input/output tokens**, **latency**, and **implementation complexity**. The notebook exports experiment results to CSV for analysis.

## Session 5: Enterprise system integration

Session 5 extends the same case study beyond a standalone language-model application.

**Experiment 1 — Data ingestion and REST APIs**  
Load local sensor readings; validate the record schema and timestamps; expose or test a local API; inspect expected HTTP status codes and errors.

**Experiment 2 — API orchestration**  
Retrieve an asset reading, select relevant SOP evidence, prepare model context, construct a recommendation, and validate outputs and error states.

**Experiment 3 — Event-driven processing**  
Simulate an event producer, queue, and consumer; handle duplicate events; prepare a draft maintenance action; require supervisor approval and retain an audit trail.

The notebook uses a **local API test client and simulated events** so students can learn integration concepts without deploying cloud services, exposing a public server, or provisioning a message broker.

## Datasets and reproducibility

The shared railway-maintenance dataset comprises three text SOPs and simulated sensor measurements. Keep the **same source files and asset identifiers** between sessions when comparing implementation approaches.

| File | Purpose |
|---|---|
| `SOP-PS-001_Pemeriksaan_Awal_Bearing.txt` | Initial bearing examination procedure. |
| `SOP-PS-002_Pemantauan_Suhu_dan_Getaran.txt` | Temperature and vibration monitoring guidance. |
| `SOP-PS-003_Pelaporan_dan_Persetujuan_Tindak_Lanjut.txt` | Reporting, escalation, and supervisor approval. |
| `sensor_readings.csv` | Simulated operational readings for the integration exercises. |

For reproducible practical submissions, record the model name/version, notebook version, dataset version, runtime configuration, experiment parameters, and evaluation criteria. Do not compare latencies across different Colab hardware as though they were controlled measurements.

**Data privacy:** Do not commit credentials, tokens, confidential enterprise documents, personal data, or real infrastructure endpoints to this public repository.

## Assessment

The RPS specifies the following overall assessment weights:

| Component | Weight |
|---|---:|
| Independent assignments (*Tugas Mandiri*) | 20% |
| Midterm examination (*UTS*) | 30% |
| Final examination / project presentation (*UAS*) | 50% |
| **Total** | **100%** |

Individual assignment instructions, rubrics, and deadlines should be taken from the lecturer's official course announcements and the university learning platform.

## Core textbooks

The two **primary references listed in the RPS** are:

1. **Chip Huyen.** *AI Engineering: Building Applications with Foundation Models*. O'Reilly Media, 2025. Covers model selection, evaluation, prompting, RAG, agents, dataset engineering, inference, and deployment.
2. **Miroslaw Staron.** *Engineering Generative AI-Based Software*. Covers software requirements, architecture, testing, APIs, deployment, and software quality in generative AI systems.

**Supplementary reference used for integration and data-engineering topics:**

3. **Vasundra Srinivasan.** *Data Engineering for Multimodal AI: Architecting Scalable Systems for Next-Generation AI Applications*. O'Reilly Media, 2026. Useful for data contracts, ingestion, entity resolution, multimodal data alignment, provenance, and resilient data pipelines.

The supplementary textbook expands the teaching materials but **does not change the official RPS learning outcomes**.

## Expected course deliverable

By the end of the course, students should be able to present and defend an **end-to-end intelligent-system design** for an enterprise or smart-city problem. A complete design should address:

- Problem definition, users, business objectives, and measurable KPIs.
- Functional and non-functional requirements, including service levels.
- Data sources, system boundaries, component architecture, and integration interfaces.
- Model/application design choices and evidence-based evaluation.
- Security, privacy, governance, reliability, and human oversight.
- Deployment topology, cost/performance trade-offs, monitoring, risks, and rollout planning.

The final emphasis is on **defensible engineering decisions supported by requirements, evidence, and evaluation**.

## Usage

This repository is intended for teaching, learning, and reproducible experimentation within the course. Check the applicable university policies and the licenses or usage terms of any third-party models, packages, and datasets before redistribution. No open-source license is implied unless a `LICENSE` file is explicitly added.
