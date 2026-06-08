# WASSL Platform — BAFO Response
## Architecture & Product Governance Addendum v1.1
### Vendor Technical Response — WOLFx Digital

---

| Field | Detail |
|---|---|
| Document Type | BAFO — Best and Final Offer Response |
| Prepared By | WOLFx Digital |
| Prepared For | WASSL — Broker Intelligence & Deal Matchmaking Network |
| Version | v1.0 |
| Date | June 2026 |
| Classification | Confidential — For Evaluation Purposes Only |

---

## SECTION 1 — Product Strategy & Architecture Vision

### 1.1 Architecture in Support of the WASSL Vision

WOLFx Digital proposes a domain-isolated microservice architecture as the foundational engineering pattern for the WASSL platform. This design philosophy directly mirrors WASSL's stated value model — structuring broker communication, capturing deal flow, enabling intelligent matchmaking, and building a proprietary market intelligence layer.

Each platform capability is treated as a discrete, independently deployable service module rather than a tightly coupled monolith. Inter-service communication is handled via gRPC for synchronous, low-latency operations (user auth, listing queries, match resolution) and an event-driven messaging layer powered by Apache Kafka for asynchronous workflows (broker activity events, deal state changes, notification pipelines).

**Core Service Domains:**

- **Identity & Verification Service** — Broker onboarding, KYC, agency verification, admin approval workflows
- **Listings & Requirements Service** — Property listing CRUD, buyer requirement capture, advanced filtering
- **Matchmaking & Intelligence Service** — AI-driven opportunity scoring, ELO-based broker ranking, recommendation engine
- **Communication & Collaboration Service** — Async messaging, deal rooms, document management, digital agreements
- **Ingestion & Extraction Service** — WhatsApp Business API capture, OCR, voice note parsing, AI extraction pipeline
- **Market Intelligence Service** — Area analytics, heatmaps, distress marketplace, DLD data processing
- **Notification Service** — Multi-channel delivery (push, email, WhatsApp) via Kafka consumers

> **Deployment Model:** Each service runs in an isolated Docker container. All containers are orchestrated on a single application server for Phase 1, with Terraform-defined autoscaling playbooks ready to horizontally distribute workloads at defined traffic thresholds. The database layer remains unified (PostgreSQL) during Years 1–2 to eliminate cross-service query latency, transitioning to read-replica horizontal scaling post Year 2.

---

### 1.2 Differentiation from a Traditional Property Portal

A traditional listing portal is a passive directory — it stores and displays inventory. WASSL is an active intelligence network. The architectural differentiation is structural:

| Traditional Portal | WASSL via WOLFx Architecture |
|---|---|
| Static listings directory | Live deal flow capture with AI-structured ingestion |
| Manual broker search | Automated opportunity matching with ELO-based scoring |
| No collaboration layer | Deal Rooms with task management, document trails, e-signatures |
| No data extraction | WhatsApp-native capture — PDFs, images, voice notes |
| No broker analytics | Bespoke Business Rule Engine with AI-driven broker performance scoring |
| Generic user accounts | Verified broker profiles with reputation tracking and network graphs |

---

### 1.3 Long-Term Defensibility & Network Effects

The WASSL platform's defensibility is a function of data accumulation, not feature parity. The architecture is designed to create compounding value through:

- **Proprietary Transaction Graph** — Every deal, interaction, and match contributes to a growing transaction dataset that competitors cannot replicate without equivalent broker density.
- **AI Model Improvement Loops** — Matchmaking precision and broker performance scoring improve continuously as training data volume increases. The ELO-based opportunity allocation system becomes more accurate over time.
- **Communication Dependency Lock-in** — Brokers who communicate, collaborate, and close deals within the platform ecosystem have structural incentives to remain. The messaging and deal room layer creates habitual dependency.
- **Verified Network Moat** — Broker verification and agency credentials create a trusted, closed ecosystem that cannot be replicated by open listing portals.
- **Follow Mechanism & Social Graph** — A broker follow system creates personalised deal feeds and collaborative referral flows, building an internal social layer that amplifies network stickiness.

> **Advisory Note:** WOLFx strongly recommends a Retainer Engagement Model for this platform. WASSL's AI layer — matchmaking models, broker scoring, market intelligence — requires continuous retraining, parameter tuning, and architectural iteration. A fixed-scope contract applied to an evolving intelligence platform will result in scope creep, budget overruns, and delivery friction. A phased retainer aligned to product milestones is the commercially sound approach.

---

## SECTION 2 — MVP Sequencing & Delivery Timeline

### 2.1 Phase Delivery Overview

| Phase | Timeline | Scope |
|---|---|---|
| Phase 1 — Foundation | 80 Working Days | Authentication, User Profiles, Broker & Agency Verification, Core Data Model, Design System |
| Phase 2 — Core Loop | 90 Working Days | Listings, Buyer Requirements, Search, AI Matchmaking, AI Copilot |
| Phase 3 — Capture & Collaborate | 70 Working Days | WhatsApp Forward-to-Capture, OCR, Voice Extraction, Deal Rooms, Digital Agreements |
| Phase 4 — Intelligence | TBD — Post Consultation | Distress Marketplace, Heatmaps, Area Analytics, Broker Reputation Engine, Market Intelligence |

---

### 2.2 Phase 1 — Foundation

The Phase 1 delivery encompasses the full identity and onboarding infrastructure. The broker onboarding UX will be engineered to complete the full registration flow, including all required validation fields, within 3 minutes for a prepared user. This is achieved through progressive form disclosure, inline field validation, and a streamlined document upload flow — not by reducing mandatory compliance steps.

- Broker and Agency verification workflows will be fully operational with admin approval panels.
- Admin approval pipelines will include status tracking, rejection with reason, and re-submission flows.
- Core data model and design system will serve as the foundational layer for all subsequent phases.

---

### 2.3 Phase 2 — Core Loop

The Core Loop phase delivers the primary value exchange on the platform. Listing search performance is architecturally dependent on two variables: algorithmic complexity and server infrastructure specifications. WOLFx commits to sub-2-second search response times under the following conditions:

- Elasticsearch cluster provisioned to specification (AWS-hosted, adequately sized nodes).
- Automatic keyword generation triggered on listing creation — keywords stored as indexed columns for compound search processing.
- Semantic vector search via pgvector for similarity-based requirements matching.

AI Matchmaking will generate match scores automatically using cosine distance similarity across listing attributes and buyer requirements vectors. AI Copilot will return contextual, platform-aware responses via the Claude API.

---

### 2.4 Phase 3 — Capture & Collaborate

WOLFx has directly relevant prior experience in document ingestion, voice processing, and digital agreement management through a delivered project for the Indian judicial system — involving PDF ingestion, voice note extraction, and legally compliant audit trails. This institutional knowledge will be applied directly to the WASSL capture and collaboration layer.

- WhatsApp Forward-to-Capture will be implemented via the WhatsApp Business API. WOLFx will conduct technical due diligence on the forward-to-capture workflow specification prior to implementation.
- OCR and voice note extraction pipelines will be built on FastAPI with proven extraction libraries.
- Deal Rooms will support task assignment, document management, activity timelines, and participant management.
- Digital Agreements will include commission split structuring, e-signature workflows, and immutable audit trails.

---

### 2.5 Phase 4 — Intelligence

Phase 4 is a post-consultation deliverable. Timeline and scope will be defined following Phase 3 delivery and a dedicated architecture consultation session. WOLFx will deliver:

- Heatmaps and area analytics powered by aggregated transaction data.
- Distress marketplace with configurable listing criteria.
- Bespoke Business Rule Engine for broker performance measurement — incorporating ELO-based tracking and AI-defined performance criteria.
- Market intelligence dashboards with DLD analytics, developer rankings, and area rankings.

> **Important Clarification:** Phase 4 scope cannot be accurately estimated without a formal consultation session. Delivering intelligence infrastructure without alignment on data sources, regulatory constraints, DLD API access, and broker-facing analytics requirements will result in rework. WOLFx will not commit to a fixed price on Phase 4 prior to this consultation.

---

## SECTION 3 — WhatsApp Strategy

### 3.1 Approved Approach Confirmation

WOLFx confirms full alignment with the approved WhatsApp strategy: WhatsApp Business API, Forward-to-Capture workflow, and AI extraction. No private group scraping, no policy-violating automation.

---

### 3.2 End-to-End Workflow Architecture

**Capture Workflow:**

1. Broker forwards a message, PDF, image, or voice note to the WASSL designated WhatsApp Business number.
2. WhatsApp Business API receives the inbound payload and triggers a webhook event to the Ingestion Service.
3. The Ingestion Service classifies the payload type (text, document, image, audio) and routes to the appropriate extraction pipeline.
4. A confirmation acknowledgement is sent back to the broker via the WhatsApp API.

**AI Extraction Workflow:**

1. Text messages are passed directly to the Claude API with a structured extraction prompt to identify property attributes, deal terms, and broker intent.
2. PDFs are processed via an OCR pipeline (FastAPI + extraction libraries) to extract structured text, then passed through the AI extraction layer.
3. Images are processed via OCR for text-bearing images (floor plans, listing sheets); computer vision classification handles property photos.
4. Voice notes are transcribed via a speech-to-text model, and the transcription is processed through the same Claude API extraction pipeline as text messages.
5. Extracted data is structured into a standardised JSON payload mapped to the WASSL data model schema.

**Data Storage Workflow:**

1. Structured extracted payloads are written to PostgreSQL via the Listings or Requirements service, depending on content classification.
2. Original media files (PDFs, images, audio) are stored in AWS S3 with broker-scoped access controls and encrypted at rest.
3. Extraction metadata, confidence scores, and processing status are logged in the audit table for admin review.
4. Broker is notified via WhatsApp and in-app notification confirming successful capture and data entry.

> **Compliance Note:** All workflows operate strictly within WhatsApp Business API terms of service. No private group access, no automated scraping, and no bulk messaging outside approved messaging templates. Full compliance with Meta's Business Messaging Policy will be maintained throughout.

---

## SECTION 4 — Mandatory Technical Architecture

### 4.1 Mobile — React Native (Expo)

WOLFx recommends React Native via Expo over Flutter for the following commercially and technically justified reasons:

- **Stack Consolidation** — Both mobile and web codebases operate in TypeScript/JavaScript, eliminating the need for two separate talent pipelines (Dart/Flutter vs TS). This reduces long-term maintenance cost and enables full-stack engineers to contribute across layers.
- **Unified Codebase** — Shared business logic, API integration layers, and utility functions between the Next.js web platform and the mobile app reduce duplication and synchronisation overhead.
- **Ecosystem Maturity** — Expo's managed workflow provides production-grade OTA updates, push notifications, and native module access without requiring native toolchain expertise.

WOLFx confirms that Flutter capability exists within the team and can be deployed if the client mandates it. However, React Native is the recommended approach on technical and commercial grounds.

---

### 4.2 Web — Next.js

The web platform will be built in Next.js with a deliberate split-rendering architecture:

- **Marketing Site & SEO Layer** — Server-Side Rendered (SSR). Full SEO control, meta tag management, and content delivery via static generation where applicable. Optimised for Google indexation of WASSL's marketplace and market intelligence content.
- **Authenticated Dashboard & Broker Portal** — Client-Side Rendered (CSR). High-interactivity broker workspace, deal rooms, matchmaking interface, and analytics dashboards. Decoupled from SSR to prevent unnecessary server load on authenticated sessions.

---

### 4.3 Backend — NestJS / Django Recommendation

WOLFx is fully capable of delivering on NestJS as specified. However, we wish to formally propose Django (Python) as an alternative backend framework for the WASSL core services, based on the following security-first rationale:

- **Native Security Middleware** — Django ships with production-hardened protection against XSS, CSRF, SQL Injection, Clickjacking, and Host Header injection — out of the box, without additional configuration.
- **Rapid API Scaffolding** — WOLFx has developed an internal framework layer called API-Helpers (available for both Node and Python stacks) that enables accelerated data model scaffolding, service bootstrapping, and standardised endpoint generation. This significantly compresses Phase 1 and Phase 2 delivery timelines.
- **Python AI Ecosystem Alignment** — With AI Services running on FastAPI (Python), a Django backend eliminates cross-language data contract friction. Shared Pydantic schemas and internal libraries can be used across both layers.

The final backend framework selection is subject to client preference. WOLFx will deliver on either NestJS or Django without timeline impact.

---

### 4.4 AI Services — FastAPI

AI services will be exposed via FastAPI microservices, responsible for the following capabilities:

- **OCR & Document Parsing** — Structured extraction from PDF and image payloads.
- **Voice Transcription & Parsing** — Speech-to-text pipeline feeding the AI extraction layer.
- **Semantic Search** — Embedding-based cosine distance search via pgvector (Phase 2) and Pinecone (Phase 3+) for similarity-driven listing and requirement matching.
- **Matchmaking Engine** — LangGraph-orchestrated multi-step matching pipeline. Claude API for contextual reasoning, Pinecone for vector similarity retrieval.
- **AI Copilot** — Claude API-powered conversational assistant with WASSL platform context. Token usage restrictions enforced at the application layer to control cost.
- **Keyword Auto-Generation** — On listing creation, an AI pipeline generates and stores searchable keyword clusters in indexed PostgreSQL columns for Elasticsearch compound processing.

---

### 4.5 Technology Stack Summary

| Layer | Technology Decision |
|---|---|
| Mobile | React Native (Expo) — TypeScript |
| Web Frontend | Next.js — SSR for marketing, CSR for broker portal |
| Core Backend | NestJS (default) / Django (recommended) — see Section 4.3 |
| AI Services | FastAPI (Python) |
| AI Models | Claude API (Anthropic) — primary reasoning and copilot |
| Agentic Layer | LangChain + LangGraph — orchestration and agent workflows |
| Database | PostgreSQL — unified primary store |
| Search | Elasticsearch — full-text and compound keyword search |
| Vector Database | Pinecone (primary) + pgvector (Phase 1/2 caching layer) |
| Message Queue | Apache Kafka — async events and notification pipeline |
| Cloud Infrastructure | AWS |
| Containerisation | Docker per service |
| IaC & Scaling | Terraform + Ansible playbooks |
| CI/CD | GitHub Enterprise Edition |

> **Diagrams Note:** Architecture, infrastructure, data flow, and deployment diagrams are deliverables of the formal consultation engagement. Reference diagrams from prior correspondence provide high-level topology context. Full production-grade diagrams will be produced and submitted as part of the post-consultation technical package.

---

## SECTION 5 — Scalability Requirements

### 5.1 Horizontal & Vertical Scaling Strategy

- **Phase 1 (0–2,000 brokers)** — All service containers deployed on a single AWS application server. Vertical scaling (instance size upgrades) applied to services showing elevated CPU/memory consumption under load.
- **Phase 2 (2,000–10,000 brokers)** — High-load services (Matchmaking, Ingestion, Search) isolated into dedicated deployment clusters with independent autoscaling groups. Low-load services (Notifications, Billing) remain on shared infrastructure to control cost.
- **Phase 3 (10,000–20,000+ users)** — Full horizontal distribution across an AWS load-balanced server network. Each service domain managed by its own autoscaling policy with traffic-threshold triggers.
- Infrastructure scaling is codified in Terraform playbooks — scaling events are reproducible, auditable, and deployable without manual intervention.

---

### 5.2 Database Scaling Strategy

- **Years 1–2** — Unified PostgreSQL monolith. This is the correct architectural choice at this stage. Premature database decomposition at MVP introduces operational complexity, cross-service transaction management overhead, and latency without commensurate benefit at sub-10,000 user volumes.
- **Post Year 2** — Read replica horizontal scaling. A master write node with multiple read replicas distributes query load. High-read services (search, analytics, broker profiles) are routed to read replicas via connection pooling (PgBouncer).
- **Long-term** — Specialised service-scoped database clusters introduced where independently justified by load profiling.

---

### 5.3 Search Scaling Strategy

- **Index Partitioning** — Separate indices for listings, requirements, brokers, and market data. Independent scaling per index based on query volume.
- **Shard Distribution** — Horizontal shard expansion as broker and listing volume grows.
- **Keyword Pre-computation** — AI-generated keyword clusters stored at listing creation reduce real-time query complexity.
- **Vector Search Layer** — pgvector handles semantic similarity at Phase 1/2 volumes. Pinecone absorbs vector search load at Phase 3+ scale.

---

### 5.4 AI Scaling & Cost Control Strategy

- **Token Budget Enforcement** — Maximum token limits enforced per request type at application-layer code. Copilot, extraction, and matchmaking prompts are independently budget-controlled.
- **Claude API Usage Dashboard** — Monitored via Anthropic's control panel with alert thresholds on daily and monthly spend.
- **Prompt Caching** — Frequently repeated context windows (platform instructions, schema definitions) leverage Claude's prompt caching capability to reduce billable tokens.
- **Model Tiering** — Lightweight classification tasks use smaller, faster model configurations. Complex reasoning tasks (matchmaking, copilot) use full model capacity.

---

## SECTION 6 — Security Architecture

### 6.1 Security Stack

| Control | Implementation |
|---|---|
| Authentication | JWT with short-lived access tokens + refresh token rotation |
| Authorisation | Role-Based Access Control (RBAC) — Broker, Agency Admin, Platform Admin, Read-Only |
| Audit Logging | Immutable audit log table — all state-changing events recorded with timestamp, actor, IP, and payload hash |
| Encryption at Rest | AWS RDS encryption (AES-256) for PostgreSQL; S3 SSE-S3 for media files |
| Encryption in Transit | TLS 1.3 enforced across all service-to-service and client-to-server communication |
| Secrets Management | AWS Secrets Manager — no credentials in environment files or version control |
| SSH Access | IP-whitelisted SSH — only authorised developer IPs permitted |
| RPC Communication | gRPC inter-service calls restricted to internal VPC network; IP whitelist enforced at firewall level |
| Firewall | AWS Security Groups + Network ACLs — strict ingress/egress rules per service tier |
| Web Application Security | Django native XSS, CSRF, SQL injection, clickjacking protection (if Django backend adopted); equivalent middleware for NestJS |
| Vulnerability Scanning | Automated dependency scanning via GitHub Enterprise Edition security advisories |

---

### 6.2 Backup Policy

- **PostgreSQL** — AWS RDS automated daily snapshots with 30-day retention. Point-in-time recovery enabled.
- **Media Files (S3)** — S3 Versioning enabled on all production buckets. Cross-region replication configured for disaster recovery.
- **Application State** — Configuration files and Terraform state backed up to S3 with versioning.
- Manual snapshot triggers available pre-deployment for all major release cycles.

---

### 6.3 Disaster Recovery Strategy

- **AWS Health Monitoring Service** — Continuous monitoring of EC2, RDS, and S3 health. Automated alerting on service degradation or failure events.
- **Auto-Scaling Recovery** — Terraform playbooks define auto-recovery behaviour for failed application server instances. New containers spin up automatically on instance replacement.
- **RDS Multi-AZ** — Enabled for production PostgreSQL. Automatic failover to standby replica in the event of primary node failure.
- **Recovery Time Objective (RTO)** — Target 2 hours for full application stack recovery.
- **Recovery Point Objective (RPO)** — Maximum 24 hours data loss tolerance (daily snapshot baseline); real-time replication for critical transaction data.

> **DR Implementation Note:** Full DR automation via Terraform and Ansible playbooks is a post-deployment operational undertaking. Phase 1 will include manual DR runbooks. Automated DR orchestration will be introduced as a Phase 2 operational deliverable under the recommended retainer model.

---

### 6.4 CI/CD Pipeline

- **GitHub Enterprise Edition** — All source code managed in private repositories with branch protection rules, required review approvals, and signed commits.
- **Pipeline Stages** — Lint → Unit Tests → Integration Tests → Docker Build → Staging Deploy → Manual Approval Gate → Production Deploy.
- **Container Registry** — AWS ECR for Docker image storage and versioning.
- **Zero-Downtime Deployments** — Rolling update strategy for production container replacements.

---

### 6.5 Compliance Approach

- **Data Residency** — Primary infrastructure provisioned on AWS Middle East (UAE) region to satisfy data localisation requirements.
- **PDPL Alignment** — Platform data handling practices will be aligned with UAE Personal Data Protection Law principles — consent capture, data minimisation, and subject access provisions.
- **WhatsApp Compliance** — Strict adherence to Meta Business Messaging Policy. No group scraping, no bulk unsolicited messaging.
- **Audit Trail Completeness** — All broker transactions, agreement signings, and admin actions are logged with non-repudiation guarantees.

---

## SECTION 7 — Specific Feature Clarifications

### 7.1 Conveyancing

- **SPA Tracking** — Sale and Purchase Agreement status tracked through a defined workflow state machine: Draft → Submitted → Under Review → Executed → Registered.
- **Transfer Tracking** — Title transfer milestones logged against deal room timeline with document attachment support.
- **Payment Tracking** — Milestone-based payment schedule tracking with status flags and notification triggers.
- **Closing Tracking** — Closing checklist management with configurable completion criteria per jurisdiction.

---

### 7.2 Deal Rooms

- **Tasks** — Assignable task items with due dates, priority levels, and completion tracking per deal.
- **Documents** — Secure document upload, version management, and access-controlled sharing within deal participants.
- **Timeline** — Chronological deal event log with milestone markers and automated event capture.
- **Activity Feed** — Real-time activity stream for all deal room participants showing all actions, comments, and document changes.

---

### 7.3 Digital Agreements

- **Commission Splits** — Configurable commission distribution between participating brokers and agencies with approval workflows.
- **E-Signature** — Integrated e-signature capability for binding digital agreement execution.
- **Audit Trail** — Immutable, timestamped record of all agreement views, signature events, and modifications — legally defensible audit log.

---

### 7.4 Market Intelligence

- **DLD Analytics** — Dubai Land Department transaction data integration (subject to API access provision by WASSL).
- **Area Rankings** — Computed area performance rankings based on transaction velocity, price per sqft trends, and demand signals.
- **Heatmaps** — Geographic transaction density and price visualisation layers rendered on the broker-facing map interface.
- **Developer Rankings** — Developer performance scoring based on delivery timelines, transaction volume, and broker sentiment signals.

---

## SECTION 8 — Final Architecture Questions

### 8.1 Why this Architecture?

Microservice architecture was selected because WASSL's value model is not monolithic — it is a composition of specialised capabilities (ingestion, matchmaking, intelligence, collaboration) that have fundamentally different scaling profiles, technology requirements, and evolution timelines. A monolith would create deployment coupling, scaling inefficiency, and technology lock-in across unrelated domains. Microservices allow each capability to evolve, scale, and be maintained independently.

---

### 8.2 Why this AI Stack?

Claude API (Anthropic) was selected for its leading performance on structured extraction, contextual reasoning, and instruction-following tasks — the exact requirements for the WASSL copilot, matchmaking, and ingestion extraction pipelines. LangChain and LangGraph provide production-grade orchestration for multi-step agentic workflows without requiring custom agent framework development. Pinecone provides a managed, high-performance vector store for semantic similarity at scale. pgvector handles vector operations at Phase 1/2 volumes within the existing PostgreSQL infrastructure, deferring Pinecone infrastructure cost until justified by volume.

---

### 8.3 Why PostgreSQL?

PostgreSQL is the only database that combines relational integrity (critical for agreement and financial records), native JSON support (for flexible AI-extracted data structures), pgvector extension (eliminating a separate vector store at early scale), and enterprise-grade reliability. It is the correct and defensible choice for WASSL's primary data store.

---

### 8.4 Why Pinecone + pgvector?

pgvector handles vector operations within the existing PostgreSQL instance at Phase 1/2 volumes — zero additional infrastructure cost and operational overhead. Pinecone is introduced at Phase 3+ when vector query volumes and similarity search complexity exceed what pgvector can serve at required latency. This dual-layer approach is cost-optimised and performance-appropriate at each growth stage.

---

### 8.5 How Will the System Scale?

Scaling occurs in two phases: (1) Vertical scaling of individual high-load service containers with isolation from low-load services on shared infrastructure. (2) Horizontal distribution across load-balanced server networks with Terraform-managed autoscaling groups. Infrastructure playbooks are written and version-controlled pre-deployment, enabling scaling events to be executed without architectural rework.

---

### 8.6 How Will AI Costs Be Controlled?

Token budget limits enforced at application-layer code per request type. Claude API spend monitored via Anthropic's usage dashboard with daily and monthly threshold alerts. Prompt caching applied to repeated high-frequency context. Model tiering used to route lightweight tasks to faster, lower-cost model configurations.

---

### 8.7 How Will Search Performance Be Maintained?

AI-generated keyword clusters stored as indexed PostgreSQL columns at listing creation reduce real-time search computation. Elasticsearch compound search operates on pre-built indices. Automatic index refresh scheduling ensures listing data is available for search within acceptable latency. pgvector cosine distance search handles semantic similarity for requirements matching. Performance SLAs will be defined, instrumented, and monitored via application performance tooling.

---

### 8.8 How Will Data Security Be Ensured?

AWS Secrets Manager for all credentials. IP-whitelisted SSH. Internal VPC for all gRPC inter-service communication with firewall-enforced network ACLs. TLS 1.3 in transit. AES-256 at rest. RBAC at application layer. Immutable audit logs. GitHub Enterprise Edition with signed commits and branch protection.

---

### 8.9 What Happens at 10x User Growth?

Nothing unexpected — because the infrastructure playbooks exist before the growth event occurs. Terraform autoscaling groups trigger on defined CPU/memory/request-rate thresholds. High-load service containers are isolated and independently scaled. Read replicas absorb database query load. Elasticsearch shard distribution expands horizontally. Pinecone scales managed infrastructure without operational intervention. The architecture is designed for this scenario, not adapted to it retrospectively.

---

### 8.10 What Are the Biggest Technical Risks?

WOLFx will not provide false assurances. The honest technical risk register for WASSL is:

- **Scope Expansion Without Consultation** — WASSL's Phase 4 intelligence layer and AI training requirements will evolve with usage data. Attempting to define these as fixed-scope deliverables before the platform generates real transaction data is a governance risk, not an engineering risk.
- **DLD Data Access** — Market intelligence features are contingent on access to Dubai Land Department data via API. If this access is unavailable or restricted, alternative data sourcing will be required.
- **WhatsApp Forward-to-Capture Specification** — This feature's implementation depends on the specific workflow documentation. WOLFx will conduct technical due diligence before committing to an implementation timeline for this specific capability.
- **AI Training Continuity** — Broker performance scoring and matchmaking models require ongoing retraining as transaction volume grows. This is an operational commitment, not a one-time delivery — and is the primary rationale for the recommended retainer model.

---

## SECTION 9 — Final Deliverables & Commercial Terms

### 9.1 Proposed Team Structure

| Role | Profile |
|---|---|
| Senior UI/UX Designer | 4 years experience — Design system, UX flows, broker onboarding, mobile and web interfaces |
| Junior UI/UX Designer | 2 years experience — Component production, design iterations, asset management |
| Senior Frontend Engineer | 5 years experience — Next.js, TypeScript, SSR/CSR architecture, performance optimisation |
| Junior Frontend Engineer | 1 year experience — Component development, feature implementation under senior guidance |
| Senior Backend Engineer (Active Development) | 5 years experience — Service development, API design, database architecture, integration |
| Principal Backend Architect | 10 years experience — System architecture, technical governance, scalability planning, code review |
| Project Manager (POC) | 1 dedicated PM — Client communication, sprint management, delivery accountability, BAFO coordination |

---

### 9.2 Warranty Terms

- **System Warranty** — 30 calendar days post-production deployment covering critical bug fixes and regression resolution at no additional cost.
- **Post-Warranty Support** — Annual Maintenance Contract (AMC) required for continued support, SLA coverage, and platform maintenance. AMC terms, response SLAs, and pricing to be defined in the maintenance agreement.
- **Source Code Ownership** — Full source code ownership transfers to WASSL upon project completion and final payment. WOLFx retains no licensing rights, usage rights, or ongoing IP claims on delivered code.

---

### 9.3 Support Model

- SLA Lifecycle managed under AMC — Priority 1 (Critical) response within 4 hours; Priority 2 (High) within 24 hours; Priority 3 (Medium) within 72 hours.
- Dedicated support channel with WOLFx technical team.
- Quarterly platform health reviews included under AMC.

---

### 9.4 Deliverables Submission Status

| Required Deliverable | Status |
|---|---|
| Revised Proposal | This Document |
| Architecture Diagram | Post-Consultation Deliverable - But initial level architecture is attached for your consideration |
| Database Diagram | Post-Consultation Deliverable |
| AI Architecture Diagram | Post-Consultation Deliverable |
| Security Architecture | Addressed in Section 6 |
| DevOps Architecture | Addressed in Section 6.4 - But initial level architecture is attached for your consideration |
| Team Structure | Section 9.1 |
| Warranty Terms | Section 9.2 |
| Support Model | Section 9.3 |
| Source Code Ownership | Full transfer to client on project completion |
| Revised Fixed Price | $150,000 (Pending Consultation Session — we can come to a clear cost breakdown after a short pilot consultation.) |
| Revised Timeline | Phase 1: 80 days \| Phase 2: 90 days \| Phase 3: 70 days \| Phase 4: TBD |

---

*© 2026 WOLFx Digital. All Rights Reserved.*
*Mumbai, India | wolfx.io*
