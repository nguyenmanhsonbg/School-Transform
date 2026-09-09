# Product Glossary

Status: DRAFT

## Purpose

Provide a shared vocabulary for product, domain, architecture and later module specifications.

## Terms

| Term | Definition |
|---|---|
| School Digital Platform | The product that provides school foundation, academic, operational, digital and later AI capabilities |
| School Core | The reusable core capabilities required for a school to run its essential academic cycle |
| Tenant | The logical customer boundary representing one school in the initial model |
| Foundation | Shared platform capabilities used by multiple phases and modules |
| Phase | A business milestone in the product roadmap |
| Module | A bounded business capability and the primary unit of specification and development |
| Capability | A reusable platform or domain function; it may be shared across modules |
| Feature | A user-visible or operational slice of a module or capability |
| Specification | The controlled description of purpose, scope, actors, use cases, rules, flows, data, permissions and acceptance |
| Actor | A person, role or external system that interacts with a capability |
| Scope | The boundary within which an actor's permission applies |
| Configuration | Tenant or module settings that change behavior without changing the core code |
| Integration | A controlled connection to an external system or channel |
| Customization | A customer-specific extension isolated from the School Core where possible |
| Academic Year | A configured period representing one school year |
| Term | A configured subdivision of an academic year |
| Organization | The school structure, including school, department, grade, class and room concepts |
| Class | A student grouping used for school organization and learning activities |
| Subject | A teachable academic subject, optionally configured by grade |
| Teaching Assignment | The association of teacher, subject, class, academic year and term |
| Timetable | The planned schedule of teaching sessions |
| Attendance | Recording a student's presence, absence, permitted absence, lateness or early leave |
| Grading | The configured process of recording and calculating student assessment results |
| Grade | A recorded assessment result or, depending on context, an academic level; specifications must state which meaning applies |
| Workflow | A configurable sequence of request, review, approval or rejection steps |
| Audit | A trace of a significant action, its actor, time, tenant and affected data |
| Permission | An authorization to perform an action on a resource within a scope |

## Open Questions

- The business concept for a student grouping is currently Class. The folder name classroom in the source structure may conflict with the physical Room concept and must be resolved before Phase 1 files are created.
- The business capability is currently called Grading; the source documentation tree uses grades. The canonical module and folder name must be confirmed before Phase 1 files are created.
- School is the business organization and Tenant is the isolation/customer boundary. Whether these are always one-to-one must be confirmed for future multi-school management.
