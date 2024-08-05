First priority:

Why cloud?

Scale to meet digital demand.

Optimize costs.

Increase operational efficiencies.

Improve application and data security.

Ship new features faster.

Aggrege on Event Driven Microservices Architecture and implementation

DDD

SQRS

Event Sourcing?

When got new requirements (partner, internal, any product requirement)

architecture team sync should be scheduled

POs and PM must enforce Engineering Leads sync with Architects

Guidance for devs on Sync vs Async (not .Net)

Partner business flow

partner intent is pub and wait for webhook => must go Async (pub/sub) pattern

hide transient errors from partner

notify or provide result with webhook/etc.

partner intent is request/response => 

implement real-time request/response

consider preprocessing and caching data for fast querying (request/response)

Inter-microservices communication

Consider requirements:

SLA including different SLAs for different partners

partner’s intent/requirements

if has hard time to decide => contact Principal or Architect for suggestions or setup the meeting with Arch or Principal team

TODO: create Arch & Principal architecture teams channel

Incorrect: start coding, found questions, go to arch team, redo the development

MQ based red flags:

adding latency

complexity (must be covered by good examples)

REST cons:

cannot handle TPS spikes well

reduces availability of the service

 

external calls =>

try do async

Tenants handling

 

Definition of a microservice

Size of microservices

Security and Auth

….

 

 

07/08/2024
Principals do not think deeply about tech problems (scalability, failures, etc.)

they need to push things to be done for business, not to implement rock solid systems

devs are too much into business and have no vision/seniority to implement stable, robust system

devs sometime act as POs

we need a different mindset

some Principals are integrators (take whatever exist and put together) and fast-tracking for business and harm the system because do not think about

team does not follow templates

why? 

do we have enough vision of teams needs?

do we have a vision why they can’t adapt the template?

is the template so restrictive?

do teams have understanding of the practices inbuilt in the template

team need trainings, not just KT

we need to enforce education

how to enforce properly?

time to review what's everyone goal is

what do people think their role are

need reevaluate roles

how can we identify the most critical problems to proceed with?

how can we make sure we are informed enough to decide?

should we engage others who are not in the meeting

if they are too busy => this is a question for executives

feedback from the team does not come

how much time members can dedicate for strategic topics, improvements and enforcement?

 

 

Fundamental aspects:
Principal Engineers must have time for strategic aspects, need to free up calendar

 

 

Roadmap for Synchronization of Architectural Standards and Patterns
Phase 1: Ideation & Agreement
Kickoff Meeting:

Align on objectives and expectations.

Identify key stakeholders and their roles.

Define the End Goal:

Create a vision statement for aligned standards, tools, and approaches.

Set measurable goals for faster decision-making and clarity on standards compliance.

Brainstorming Sessions:

Gather input on current challenges, existing practices, and potential solutions.

Categorize use cases (transaction processing, communication patterns, scaling, etc.).

Agreement on Principles:

Consensus on what constitutes a microservice.

Define the scope of standards and patterns (e.g., Microservices, Data Strategy, Event-Driven Services).

Phase 2: Standards Formalization
Documentation of Standards:

Develop documents for microservice definitions, communication patterns, and architectural principles.

Include detailed definitions, templates, and examples.

Selection of Tools and Frameworks:

Evaluate and select tools for messaging (e.g., RMQ vs. Kafka), logging, testing, and infrastructure.

Decide on function implementations (Functions vs. MassTransit).

Templates Creation:

Develop templates for different scenarios (e.g., Basic Sync API, Publishing Events, Consuming Events).

Ensure templates include necessary boilerplate, common libraries, and configurations.

Code Review and Architecture Review Process:

Establish a standardized code review process.

Define architecture review gates and criteria for new services.

Phase 3: Template Creation
Proof of Concepts (POCs):

Develop POCs for key scenarios to validate templates and standards.

Ensure POCs address security, stability, and performance.

Create Production-Ready Templates:

Finalize templates based on feedback from POCs.

Include support for common patterns (Transactional Outbox, CQRS).

Documentation and Guides:

Develop comprehensive documentation and guides for each template.

Create a centralized repository for easy access.

Internal Workshops and Training:

Conduct workshops to educate teams on new standards and templates.

Develop training materials and sessions for continuous learning.

Phase 4: Implementation in Production Projects
Pilot Projects:

Select a few pilot projects to implement the new standards and templates.

Monitor and gather feedback from pilot implementations.

Continuous Improvement:

Refine standards and templates based on pilot feedback.

Address any gaps or challenges identified during pilot projects.

Broad Rollout:

Implement standards and templates across all new projects.

Develop a migration plan for existing services to align with new standards.

Mechanisms for Sharing and Publicizing:

Create a knowledge-sharing platform (e.g., internal wiki, Confluence).

Regularly update and share best practices, case studies, and success stories.

Ongoing Education and Support:

Schedule regular share-out sessions and code review meetings.

Provide continuous support through office hours or a dedicated Slack channel.

General Architecture Direction
Microservices:

Clear definition and scope.

Strategies for versioning and ownership.

Data Strategy:

Approach for data storage, retrieval, and consistency.

Use of event sourcing and CQRS patterns.

Event-Driven Services:

Establish event publication and consumption patterns.

Resiliency and performance considerations for event processing.

Key Topics for Sync
Transactional Outbox Patterns:

Handling failures in database and messaging queue transactions.

Ensure atomicity and consistency.

Caching Strategies:

Define strategies for cache management, refresh, and invalidation.

Select appropriate caching tools.

State Management and Orchestration:

Implement SAGA, Routing Slip patterns.

Workflow management and orchestration strategies.

Testing and Observability:

Promote test-first design.

Implement comprehensive observability (logging, metrics, tracing).

Addressing Challenges and Concerns
Test Coverage and Integration:

Shift-left testing approach.

Strategies for testing third-party integrations.

Style vs. Structure:

Balance individual coding styles with adherence to standards.

Foster a culture of meaningful code reviews and architectural discussions.

Knowledge Transfer and Education:

Develop continuous learning paths.

Encourage participation in internal and external tech communities.