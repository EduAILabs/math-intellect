# Commercialization Plan

## Math Intellect – AI-Assisted Mathematics Learning Platform

**Project Lead:** Ngwe Htoon (Howard)  
**Document status:** Proposed commercialization strategy; not evidence of existing sales or institutional deployment.

## Vision and Commercial Objective

Math Intellect is a self-initiated EdTech project that combines mathematics education, AI-assisted processing, workflow automation, and LINE-based delivery. The current functional MVP provides image-based mathematics question intake, structured solutions, examiner-inspired assessment guidance, and multi-stage quality review. Its initial curriculum reference is Cambridge IGCSE Mathematics 0580 and Additional Mathematics 0606.

The commercial objective is to develop this prototype into a sustainable digital learning service for students, teachers, tutors, learning centres, and schools. Future features and commercial arrangements described in this document are plans rather than implemented capabilities or confirmed customer relationships. Math Intellect is an independent project and is not affiliated with or endorsed by Cambridge University Press & Assessment.

## Strategic Positioning

Math Intellect brings together three areas of experience and design:

- **Mathematics education:** structured reasoning, curriculum-aware explanation, and assessment-oriented feedback.
- **Software and AI workflow design:** n8n orchestration, OpenAI API processing, JavaScript formatting, and LINE Messaging API integration.
- **Educational product development:** an MVP that can be tested with learners before expanding to teacher-facing and institutional workflows.

The project is not positioned as a replacement for teachers or as an officially certified examination-marking service. Its intended role is to complement instruction by making structured learning support more accessible and, in later phases, by assisting educators with repetitive preparation and assessment tasks.

## Target Users and Proposed Value

| Segment | Educational need | Current MVP or planned offering | Indicative commercial approach |
|---|---|---|---|
| Students and independent learners | Support with mathematics questions outside lesson hours | Current: image submission through LINE and structured responses; broader curriculum support is planned | Future individual subscription |
| Teachers and private tutors | Preparation, feedback, and assessment workload | Current: demonstration of structured mathematics and assessment guidance; worksheet generation and teacher tools are planned | Future professional subscription or tool access |
| Learning centres and schools | Consistent learning support and institution-level administration | Current: no institutional dashboard or deployed school administration system; pilots, analytics, and administration features are planned | Future institutional licensing or partnership |

These segments describe intended users and potential customers. They are not presented as an established customer base, paid subscriptions, or signed partnerships.

## Current MVP and Commercial Readiness

The current locally hosted prototype uses n8n, the LINE Official Account/Messaging API, the OpenAI API, JavaScript, and ngrok for development webhook access. The implemented workflow covers image intake, question analysis, mathematical reasoning, examiner-inspired assessment review, moderation, quality checking, formatting, and LINE response delivery.

A prototype validation record covers **51 test cases**. It provides baseline measurements and identifies visual/diagram interpretation as a substantial limitation. These technical test results should not be treated as evidence of educational learning gains, commercial demand, product-market fit, or readiness for unsupervised institutional deployment. Detailed metric definitions, denominators, and supporting test records are maintained in the project's validation materials.

Before wider pilots or commercialization, development priorities include improving diagram interpretation, extending controlled validation, strengthening privacy and data-handling procedures, and preparing stable hosting and operational support. The current prototype does not include persistent learner records, a teacher dashboard, subscription infrastructure, or production cloud deployment.

## Go-to-Market Strategy

The proposed route to market is staged so that product and educational claims can be evaluated before expanding access.

| Stage | Proposed activity | Evidence needed before progressing |
|---|---|---|
| 1. MVP validation | Extend the existing test set, investigate failure cases, and improve question interpretation, particularly diagrams | Reproducible technical results, documented limitations, and improved reliability |
| 2. Controlled learner and teacher pilot | Invite a limited number of consenting participants to test usability, usefulness, and feedback quality | Structured feedback, observed usage, consent/privacy safeguards, and issue resolution |
| 3. Learning-centre or school pilot | Explore a supervised pilot with an interested institution after appropriate permissions and operational safeguards | Agreed pilot scope, educator review, institutional feedback, and documented outcomes |
| 4. Institutional deployment | Consider paid service arrangements after technical reliability, support processes, privacy controls, and product features are established | Verified service readiness, agreed terms, and evidence of customer demand |

No pilot, partnership, subscription, or revenue is claimed as completed unless separately documented.

## Proposed Revenue Model

| Product tier | Intended users | Indicative model | Status |
|---|---|---|---|
| Starter | Individual students and self-learners | Individual subscription | Planned |
| Professional | Teachers and private tutors | Subscription for productivity and assessment-support tools | Planned |
| Institutional | Learning centres and schools | Institutional licensing or negotiated partnership | Planned |

Pricing, subscription limits, service-level terms, and licensing conditions have **not** been finalized. They would depend on pilot findings, operating costs, user needs, safeguarding obligations, and the scope of delivered features. Potential custom deployments or assessment services are longer-term possibilities, not current products.

## Commercial and Operational Considerations

A sustainable service would require more than a functional workflow. Key considerations include OpenAI API usage costs, n8n/cloud hosting, LINE messaging costs and platform limits, system monitoring, customer support, maintenance, privacy and security controls, and educator-led review of assessment-sensitive outputs.

The pricing and operating model should be tested against actual usage and costs before public commercial commitments are made. Where student work or personal information is processed, appropriate consent, access control, retention practices, and applicable legal obligations need to be addressed before expanded deployment.

## Development Roadmap

The commercial plan follows the same milestone structure used in the Math Intellect portfolio and README. Dates are planning targets, not delivery guarantees.

### 2026 – Functional MVP
**Phase 1: Intelligent Mathematics Assistant**

- Maintain the implemented LINE-based mathematics support workflow.
- Extend structured technical validation and address visual/diagram interpretation failures.
- Publish sanitized technical documentation and validation evidence.
- Prepare a controlled pilot design and evaluate privacy requirements.

### 2027 – Teacher Dashboard & Cloud SaaS Platform
**Phase 2: Teacher Productivity Platform**

- Develop worksheet generation and assessment-support tools.
- Build and test teacher-facing dashboard functions.
- Plan and validate cloud deployment, persistent services, and SaaS operations.
- Test a proposed professional subscription model with pilot feedback.

### 2028 – School Partnerships & Institutional Licensing
**Phase 3: School-Level Deployment**

- Explore supervised learning-centre and school pilots.
- Develop institutional tools and learning analytics subject to privacy safeguards.
- Evaluate institutional licensing requirements and support arrangements.

### 2029+ – Regional Expansion & AI Learning Analysis
**Phase 4: Regional Expansion**

- Evaluate demand for additional international mathematics curricula and languages.
- Consider regional partnerships based on demonstrated product readiness and local requirements.
- Extend AI-assisted learning analytics only after sufficient validation and appropriate data governance.

## Educational and Commercial Success Measures

Future evaluation should distinguish technical performance, educational outcomes, and commercial viability rather than treating them as interchangeable:

- **Technical:** question interpretation, mathematical accuracy, solution completeness, assessment alignment, and end-to-end response reliability.
- **Educational:** learner and teacher feedback, usefulness of explanations, and learning outcomes where a properly designed pilot permits measurement.
- **Operational:** latency, support workload, service availability, API/hosting costs, and incident handling.
- **Commercial:** pilot interest, conversion to paid use, retention, and unit economics, measured only after actual deployment.

The current validation record provides technical prototype evidence; it does not yet establish educational impact or commercial performance.

## Long-Term Direction

Math Intellect aims to evolve from an AI-assisted mathematics learning MVP into a broader AI-enabled STEM education platform. Its commercial development will prioritize measured reliability, explainable mathematics support, educator oversight, and practical adoption before pursuing wider institutional or regional expansion.

The objective is to complement teachers—not replace them—while building a digital service whose educational value and operating model can be demonstrated through successive, evidence-based development stages.
