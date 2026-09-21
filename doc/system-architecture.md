# System Architecture

## Math Intellect – AI-Assisted Mathematics Learning Platform
 
**Project Lead:** Ngwe Htoon (Howard)  
**Document status:** Current MVP architecture with planned infrastructure clearly separated; not evidence of production deployment, completed security controls, or compliance certification.

## Architectural Objective

The Math Intellect functional MVP integrates a familiar messaging interface, API-based event delivery, local workflow automation, AI vision/language processing, explicit review stages, and controlled response formatting. Its primary purpose is to deliver a structured mathematics explanation in LINE after a student submits a question image.

## Current MVP Architecture

```text
Student / teacher
    |
    v
LINE Official Account (image message)
    |
    v
LINE Messaging API (webhook event)
    |
    v
n8n webhook — locally hosted development instance
    |
    v
Image retrieval → OpenAI API vision-based interpretation
    |
    v
Question Analyzer → Solver → Examiner → Moderator → Quality Checker
    |
    v
JavaScript Formatter (structured text assembly)
    |
    v
LINE Messaging API → LINE text response
```

**Deployment boundary:** ngrok provides externally reachable development webhook access to the locally hosted n8n instance. ngrok is not described as production hosting. The OpenAI API and LINE Messaging API are external services; the orchestration and custom processing logic run in the development workflow.

The flow is a high-level design derived from the working prototype and project-report diagrams, not a claim that public repository files contain a complete executable deployment.

## Component Responsibilities

| Component | Current role | Status |
|---|---|---|
| LINE Official Account | Familiar interface for image submission and text response. | Implemented |
| LINE Messaging API | Delivers inbound events and outbound responses. | Implemented |
| n8n webhook and workflow | Receives event, retrieves image, and coordinates processing stages. | Implemented; locally hosted |
| OpenAI API | Vision/language processing for question interpretation and mathematical tasks. | Implemented |
| Question Analyzer through Quality Checker | Structured analysis, solving, assessment, moderation, and quality review. | Implemented workflow stages |
| JavaScript Formatter | Structures reviewed information into LINE-facing output. | Implemented |
| ngrok | Exposes the local webhook in development. | Development only |
| Docker / PostgreSQL | Containerized deployment and persistent storage options. | Planned |
| Cloud hosting / teacher dashboard / learner database | Scalable service and educator-facing functionality. | Planned |

## Information and Control Flow

1. A user submits an image to the LINE Official Account.
2. LINE delivers a messaging event to the registered n8n webhook; the workflow retrieves the associated image.
3. Vision-based processing extracts mathematical information, and the Question Analyzer constructs the question interpretation.
4. The Solver generates working and answers; the Examiner adds assessment-oriented guidance.
5. The Moderator and Quality Checker review intermediate results. Their checks can identify problems but cannot guarantee correctness.
6. JavaScript formatting consolidates reviewed content into the Header–Body–Tail LINE response; the messaging integration delivers the reply.

## Output Contract: Header, Body and Tail

| Section | Purpose |
|---|---|
| Header | Question analysis and assessment context. |
| Body | Step-by-step solution and final answer. |
| Tail | Examiner-inspired assessment guidance. |

A formatted PDF sent by email is a future delivery extension, **not** a currently demonstrated output channel.

## Trust, Security, and Data Boundaries

LINE events and user-submitted images cross external service boundaries, and AI processing sends relevant content to an API. A public repository must omit actual channel secrets, access tokens, API keys, webhook identifiers where sensitive, personal data, and student-submitted material without appropriate permissions. Screenshots and exported workflows should be sanitized before publication. The current documents do not establish completed production security controls, formal compliance certification, or consent-ready school operations.

## Limitations and Planned Architecture

The MVP lacks persistent learner records, cloud deployment, teacher dashboards, institutional administration, and production monitoring. Image/diagram interpretation is an identified technical limitation. Future architecture may add Docker, PostgreSQL, managed hosting, access control, stable logging, PDF delivery, and learning analytics, subject to further testing and design.

## Evidence and Related Documents

- [Root README and architecture image](../README.md)
- [AI workflow](ai-workflow.md)
- [Quality assurance](quality-assurance.md)
- [Validation methodology](validation-methodology.md)

When publishing repository assets, ensure the README's `screenshots/architecture.png` and other referenced images actually exist. An illustrative diagram is design evidence; it is not by itself proof of successful execution.
