# Market Analysis

## Math Intellect – AI-Assisted Mathematics Learning Platform

**Project Lead:** Ngwe Htoon (Howard)  
**Document status:** Exploratory market analysis and proposed market-entry plan; not evidence of measured demand, existing customers, or institutional partnerships.

## Market Scope and Product Positioning

Math Intellect is a self-initiated EdTech project addressing a defined mathematics-learning problem: students may need structured help with questions outside scheduled lessons, while teachers and learning providers must balance explanation, assessment preparation, and individual feedback. Its current functional MVP enables image-based mathematics question submission through LINE and returns structured solutions and examiner-inspired assessment guidance through a multi-stage AI workflow.

The current curriculum references are Cambridge IGCSE Mathematics 0580 and Cambridge IGCSE Additional Mathematics 0606. The product is independently developed and is not affiliated with or endorsed by Cambridge University Press & Assessment. Broader curriculum coverage, teacher productivity tools, institutional services, and commercial delivery remain planned rather than implemented.

This document identifies potential users, their needs, a proposed route to market, and assumptions that require validation. It is not a quantified market-size study or a claim that customer demand has already been established.

## Primary User Segments and Needs

| Segment | Potential users | Need or use case | Current MVP relevance | Planned development |
|---|---|---|---|---|
| Students and independent learners | Cambridge IGCSE Mathematics learners; examination-preparation and supplementary-learning users | Support with interpreting questions, following intermediate steps, and reviewing assessment-oriented explanations outside lesson hours | LINE image submission, question analysis, structured mathematical response, and assessment guidance | Broader curriculum and language support; learner records and more adaptive support |
| Teachers and private tutors | International-school mathematics teachers, tutors, examination-preparation educators, and curriculum coordinators | Clear worked solutions and assistance with repetitive feedback or preparation tasks | Demonstration of structured solutions and assessment-oriented responses; no dedicated teacher dashboard | Worksheet and question generation, assessment-support tools, and teacher-facing workflows |
| Schools and learning centres | International schools offering relevant mathematics programmes; mathematics learning centres and examination-preparation providers | Supervised learner support, consistent educational workflows, and tools that may help educators manage support at scale | A locally hosted student-facing prototype; no production institutional deployment or administration system | Controlled pilots, teacher dashboards, learning analytics, institutional administration, and licensing |

These are **prospective user segments**, not verified customers. The student-facing mathematics assistant is the current entry product; professional and institutional features form the proposed expansion pathway.

## Educational Pain Points to Investigate

The following are problem hypotheses informed by the project’s teaching perspective and motivation. Their prevalence and commercial importance must be evaluated with actual users rather than assumed for every school or learner.

### Students

- Mathematics questions can arise when a teacher or tutor is unavailable.
- AI-generated answers may omit steps, misinterpret an image, or lack the level of explanation the learner needs.
- Learners may find it difficult to relate a final answer to the reasoning and assessment expectations behind it.
- Usability, language preferences, and trust in AI-generated guidance may influence adoption.

### Teachers and tutors

- Preparing suitable explanations, practice materials, and individualized feedback can consume teaching time.
- AI-assisted outputs need mathematical review, curriculum fit, and appropriate assessment guidance before classroom use.
- Educators need clear boundaries between tools that exist now and features being proposed for future preparation workflows.

### Schools and learning centres

- Institutions may need a consistent approach to supplementary mathematics support without replacing educator oversight.
- Any school-facing product must account for safeguarding, data privacy, permissions, support processes, and reliable operation.
- Institutional interest in dashboards, learner analytics, or licensing remains to be tested through supervised pilots.

## Current Product Offering Versus Planned Solutions

| Area | Implemented in the current MVP | Planned or subject to further validation |
|---|---|---|
| Mathematics question intake | Image submission through LINE; webhook and image retrieval | More robust handling of unclear images and diagrams |
| Learning response | Question analysis, step-by-step solution, examiner-inspired guidance, and formatted LINE response | Broader curriculum coverage, additional languages, and richer response formats |
| Processing and review | Question Analyzer → Solver → Examiner → Moderator → Quality Checker → Formatter | Continued accuracy testing and more reliable handling of visual questions |
| Teacher productivity | Existing structured-output workflow can be demonstrated to educators | Worksheet and question generation, assessment-support tools, and teacher dashboard |
| Institutional delivery | No production school deployment | Supervised school/learning-centre pilots, administration features, learning analytics, and licensing |
| Infrastructure | Locally hosted n8n prototype; ngrok for development webhook access | Cloud deployment, persistent learner records, and scalable SaaS operation |

Math Intellect offers **assessment-oriented guidance informed by curriculum and marking principles**. It does not claim to reproduce official Cambridge mark schemes or to provide an officially certified marking service.

## Initial Geographic Considerations

Taiwan is the proposed base for future product development and initial market exploration, consistent with the project’s broader development vision. Other Asian markets may be investigated later where relevant mathematics curricula, potential education partners, language requirements, and suitable communication channels make a pilot feasible.

| Geography | Proposed exploration focus | Validation needed |
|---|---|---|
| Taiwan | Potential student, tutor, learning-centre, and international-school use cases; suitability of LINE-based interaction | Interviews, curriculum fit, language needs, privacy requirements, and pilot partners |
| Thailand and other selected Asian markets | Possible expansion through relevant mathematics-education communities and learning providers | Local curriculum needs, platform preference, willingness to participate, and operating constraints |
| Wider regional expansion | Additional examination curricula and institutional partnerships | Evidence of demand, localization costs, partner readiness, and product reliability |

This is a **geographic exploration plan**, not a ranking of country-level market opportunities. No market-size estimates, growth rates, adoption figures, or confirmed partnerships are asserted here.

## Market Validation and Go-to-Market Plan

Commercial assumptions will be tested in stages, rather than treating a technically working prototype as proof of demand.

| Stage | Proposed activity | Evidence to collect |
|---|---|---|
| 1. Technical MVP refinement | Extend the existing technical tests and investigate failure cases, especially visual/diagram interpretation | Reproducible technical metrics, error categories, and documented improvements |
| 2. Controlled learner and teacher pilot | Obtain appropriate consent and conduct supervised trials of explanations, usability, and educator review | User feedback, observed use, explanation usefulness, and pilot issues |
| 3. Learning-centre or school pilot | Explore a limited institutional pilot after obtaining permissions and establishing operational safeguards | Institutional feedback, defined educational measures, support workload, and privacy review |
| 4. Commercial evaluation | Assess whether a stable product and support model justify a paid offering | Willingness to pay, usage costs, adoption/retention evidence, and viable service terms |

Technical prototype validation has been performed using **51 mathematics test cases**. The results identify visual/diagram interpretation as a substantial limitation. These tests do **not** by themselves establish learner improvement, teacher time savings, product-market fit, sales, or institutional readiness. Educational impact evaluation and market testing are separate future activities.

## Proposed Commercial Segments

| Offering | Intended segment | Indicative approach | Status |
|---|---|---|---|
| Starter | Individual learners | Subscription for mathematics learning support | Planned |
| Professional | Teachers and private tutors | Subscription for future productivity and assessment-support tools | Planned |
| Institutional | Learning centres and schools | Licensing or negotiated partnership following supervised pilots | Planned |

Prices, subscriptions, customer agreements, and revenues have not been finalized or demonstrated. The detailed staged business model is maintained in [Commercialization Plan](commercialization-plan.md).

## Key Market and Delivery Risks

- **Technical reliability:** Diagram interpretation and broader mathematical accuracy require continued improvement and validation.
- **Educational suitability:** Learners’ understanding and teachers’ confidence in the outputs have not yet been established through controlled impact studies.
- **Adoption and differentiation:** Prospective users must confirm that the structured workflow solves a meaningful problem compared with their existing resources and tools.
- **Privacy and safeguarding:** Student submissions and future learner data require suitable consent, access controls, retention practices, and educator oversight.
- **Operational viability:** OpenAI API, LINE messaging, hosting, monitoring, and support costs must be assessed against real usage before pricing commitments.
- **Localization:** Curriculum coverage, language, platform preferences, and institutional requirements may vary by target market.

## Market Analysis Status and Next Steps

**Current status:** Exploratory analysis based on a functional, technically tested MVP and a proposed product-development strategy. Customer research, controlled learner/teacher pilots, institutional demand assessment, and commercial validation are planned; no completed sales or partnerships are claimed.

Next-stage decisions should depend on observed user needs, measurable educational usefulness, improvements in technical reliability, appropriate privacy safeguards, and evidence that proposed subscriptions or institutional licensing can support a viable service.

For the current implementation and validation summary, see the repository [README](../README.md). For the proposed educational evaluation, see [Educational Impact](educational-impact.md). For the proposed commercial pathway, see [Commercialization Plan](commercialization-plan.md).

Math Intellect’s longer-term direction is to evolve from an AI-assisted mathematics learning MVP into an AI-enabled STEM education platform while preserving the central role of teachers.
