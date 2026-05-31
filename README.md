# Krishna Singh

**Systems & Backend Engineer** building production-grade distributed architectures, high-throughput AI pipelines, and event-driven automation engines.

 **Primary GitHub:** [@krishnasingh020](https://github.com/krishnasingh020)  
 **Projects GitHub:** [@Rarebuffalo](https://github.com/Rarebuffalo)  
 **LinkedIn:** [krishna-singh-8a06461b8](https://www.linkedin.com/in/krishna-singh-8a06461b8/)  
 **Email:** [workforkrishnasingh@gmail.com](mailto:workforkrishnasingh@gmail.com)

---

## Core Philosophy & Design Pillars
I focus on building reliable systems that operate in real conditions, prioritizing telemetry, failure isolation, and performance:

*   **Designing for Failures:** Implementing structured task retries, backoffs, database locks, and fallback behaviors at the architecture layer.
*   **Decoupled Concurrency:** Moving heavy calculations, scanning workloads, and LLM orchestration out of the web request thread into asynchronous worker pools.
*   **Deterministic Workflows:** Structuring RAG pipelines, schema validations (Pydantic), and database transactions to avoid run-time execution drift.

---

## Technical Competencies

| Layer | Technologies & Frameworks |
| :--- | :--- |
| **Languages** | Python, Java, TypeScript, JavaScript, C, SQL |
| **Backend & Distributed Systems** | FastAPI, Django, Express.js, Bun/ElysiaJS, Celery, BullMQ |
| **Databases & Cache** | PostgreSQL, MongoDB, SQLite, Redis |
| **AI / Machine Learning** | Gemini 2.0/1.5, OpenAI API, LangGraph, FAISS, NetworkX, LightGBM, YOLOv8 |
| **Infrastructure & Tools** | Docker, Linux, Git, REST APIs, Webhooks, SSE/WebSockets |

---

## Selected Engineering Systems (Priority Index)

### 1. SecureLens System — AI AppSec Scanner & Prober
*An automated repository security scanner using concurrency constraints and LLM-driven vulnerability classification.*
*   **Architecture:** Built with **FastAPI** and **Gemini 2.0 Flash**. Orchestrates file-system triage using `asyncio.gather` throttled by a Semaphore of `5` to prevent gateway timeouts.
*   **Impact:** Reduced scan latencies on large codebases from **12 minutes to under 45 seconds**. Runs 30+ checks across 5 transport layers.
*   **Stack:** Python, FastAPI, Gemini API, Pydantic v2, PostgreSQL, SQLAlchemy.
*   **Links:** [GitHub Repository](https://github.com/Rarebuffalo/securelens-backend) | [Demo Video](https://www.loom.com/share/eb484ed3765443fb963f8f5634c4f7a2)

### 2. Sentinel System — Event-Driven Uptime Monitor
*A multi-tenant uptime monitoring engine handling automated polling schedules and alerting channels.*
*   **Architecture:** Implemented an async **FastAPI** backend with **Celery** workers executing endpoint checks. A companion **Node.js** alert worker listens to the state transitions on **Redis** to dispatch webhook payloads.
*   **Impact:** Delivers downtime notifications (Slack, Discord, Email) within **150ms** of state failure detection.
*   **Stack:** Python, FastAPI, Celery, Redis, Node.js, PostgreSQL.
*   **Links:** [GitHub Repository](https://github.com/Rarebuffalo/Sentinel)

### 3. ScaleShorts System — AI Content Automation Pipeline
*A Python-based multi-agent orchestration pipeline for automated short-form video generation.*
*   **Architecture:** Gemini 1.5 generates scripts, Edge TTS produces neural voice narration, and the Pexels API downloads matching vertical stock footage. Programmatic cropping, mix downs, and caption renders are executed via `moviepy` in an async downloader queue using `aiohttp`.
*   **Impact:** Completely automates end-to-end vertical reel creation and asset rendering via a single CLI invocation.
*   **Stack:** Python, google-genai, Edge-TTS, moviepy, aiohttp, SQLite.
*   **Links:** [GitHub Repository](https://github.com/Rarebuffalo/ScaleShorts) | [Demo Video](https://www.loom.com/share/db3357f8901940e6bdfd666d999c4f69)

### 4. BreatheESG Ingestion System — ESG Normalization & Audit Pipeline
*An enterprise ESG metrics normalizer calculating carbon emissions (Scope 1/2/3) with model-level audit locks.*
*   **Architecture:** Fuel logs, utility bills, and travel records are parsed and mapped to emissions coefficients. Implements model-level validation hooks in **Django** and double-entry timeline ledger logs to guarantee source data immutability.
*   **Impact:** Normalizes mismatched units (GAL/kWh/IATA codes) to emissions with 100% data audit compliance. Optimized SQL queries by 73% using materialized views.
*   **Stack:** Django, React, PostgreSQL, SQLite.
*   **Links:** [GitHub Repository](https://github.com/Rarebuffalo/ESGReviewDashboard) | [Demo Video](https://drive.google.com/file/d/17-5A0sO-ZlqkExN_mhye9ZVzH1diAazC/view?usp=sharing)

### 5. VedaAI Assessment Creator — AI Generation Workflow Platform
*A high-throughput exam compilation layout generator designed to shield external models from rate-limiting locks.*
*   **Architecture:** Separates UI operations from heavy PDF token workloads. Inbound compilation tasks are enqueued into a **BullMQ + Redis** task queue running background retries with exponential backoffs. Deploys Puppeteer headless Chromium instances to compile A4-paginated PDF templates.
*   **Impact:** Prevents rate-limit issues on concurrent textbook-scale PDF uploads (up to 15 pages safely on free API tiers).
*   **Stack:** Next.js, Express.js, Redis, BullMQ, Puppeteer, Gemini 2.5.
*   **Links:** [GitHub Repository](https://github.com/Rarebuffalo/AssessmentCreator) | [Demo Video](https://drive.google.com/file/d/1xFIWhmc9o_x2-HTJUiS-onwGLo8X471Q/view?usp=sharing)

### 6. Vanco AI Suite — Computer Vision & Forecasting Engine
*A multi-modal ML suite combining tabular forecasting, real-time hand-sign recognition, and custom hybrid QA RAG.*
*   **Architecture:** Integrates LightGBM for sales forecasting, YOLOv8 Nano for 30 FPS CPU hand gesture tracking, and an academic physics RAG parsing context graphs through NetworkX.
*   **Impact:** Achieved a validation RMSLE of `0.40718` (outperforming standard public benchmarks) by eliminating chronological time leakage in data splitting.
*   **Stack:** LightGBM, YOLOv8, FAISS, NetworkX, FastAPI, OpenCV, Gemini API.
*   **Links:** [GitHub Repository](https://github.com/Rarebuffalo/vanco-ai-solution-architect)

### 7. SpacedCode System — Developer Workflow Platform
*A developer ecosystem combining an interactive dashboard with a terminal-based system interface.*
*   **Architecture:** Integrates developer activity metrics (LeetCode, WakaTime, GitHub) using automated data aggregation pipelines. Utilizes **Redis** for state persistence and fallback caches.
*   **Impact:** Implemented a command-driven interface with persistent Socket.io connections for real-time telemetry streaming.
*   **Stack:** Next.js, Express.js, Redis, Socket.io, Zustand.
*   **Links:** [Deployed Platform](https://spacedcode.vercel.app/)

### 8. OpenLLM Gateway — High-Throughput LLM Proxy
*An open-source self-hostable LLM routing layer managing API keys, costs, budget bounds, and failover routing.*
*   **Architecture:** High-throughput gateway server built with Bun and ElysiaJS. Implements database key isolation, encrypting all external provider API keys at rest using AES-256-GCM.
*   **Impact:** Serves a single unified completions endpoint for OpenAI, Anthropic, and Gemini while monitoring rate boundaries.
*   **Stack:** Bun, ElysiaJS, Prisma ORM, PostgreSQL, React.
*   **Links:** [GitHub Repository](https://github.com/Rarebuffalo/OpenLLM-Gateway)

### 9. DriveSeek System — Conversational Google Drive Search Agent
*A natural language file discovery agent translating conversational prompts into structured Google Drive queries.*
*   **Architecture:** Powered by a **LangGraph** react-agent loop. Translates colloquial requests into nested parameters (containment comparisons instead of exact match) to search file structures securely.
*   **Impact:** Resolves spelling errors and folder complexity, locating deep directory files conversational-first.
*   **Stack:** Python, FastAPI, Streamlit, LangGraph, LangChain, Google Drive API.
*   **Links:** [GitHub Repository](https://github.com/Rarebuffalo/DriveSeek)

---

## What I'm Looking For
*   **Roles:** Fullstack AI Engineer ,Backend Engineer, or Systems Engineer.
*   **Focus Areas:** Asynchronous architectures, data pipeline normalization, LLM-based autonomous workflows, and performance optimization.
*   **Teams:** Engineering-led startups, infrastructure engineering, and remote-first teams that value ownership and clean code.
