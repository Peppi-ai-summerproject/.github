# Academic Copilot — Team and Contributions

Academic Copilot was developed collaboratively as a university summer software engineering project.

This document describes the main contributors and their areas of work based on the repository's Git history, merged changes, issues, and implemented components.

The project was developed collaboratively, and several components were integrated across team members. The descriptions below therefore focus on verified areas of contribution rather than claiming exclusive ownership of shared systems.

## Project Team

### Minou Vahedinezhad

GitHub: [@Minoovn](https://github.com/Minoovn)

Role: AI / Backend Software Engineering Contributor

Minou contributed extensively to the AI orchestration, backend integration, academic analytics, agent architecture, conversation workflows, and testing layers of Academic Copilot.

#### Multi-Agent Architecture

Contributions included:

- LangGraph-based academic workflow orchestration
- Multi-agent execution and shared workflow state
- Natural-language intent detection
- Automatic agent selection and routing
- Multi-agent dependency resolution
- Deterministic execution planning
- Safe handling of unsupported and ambiguous requests

#### Academic Agents

Contributed to the implementation and integration of:

- Risk Detection Agent
- Recommendation Agent
- Communication Agent
- Reporting Agent

This work included connecting specialized agents to the shared academic workflow and maintaining structured communication between agents.

#### Backend and Chat Integration

Contributions included:

- Connecting academic workflows to ChatService
- Integrating automatic routing into the chat pipeline
- Connecting Telegram academic commands to backend workflows
- General-conversation and fallback handling
- Final workflow response handling
- Chat-to-agent integration

#### RAG Integration

Contributions included:

- Integrating the RAG pipeline with backend services
- Connecting retrieved academic policy context with recommendation workflows
- Maintaining architecture boundaries between retrieval and agent logic
- Integration testing around RAG-backed workflows

#### Conversation Memory

Contributions included:

- PostgreSQL-backed conversation memory
- Telegram user/chat-to-conversation mapping
- Conversation ownership isolation
- Student-context isolation
- Bounded conversation retention
- Concurrency-safe persistence
- Separation between durable conversation history and agent workflow state

#### Academic Analytics

Contributions included work related to:

- ECTS progress analysis
- Expected academic progress
- Delay detection
- Study-right risk analysis
- Academic risk scoring
- Academic health scoring
- Progress dashboard integration
- Tutor-meeting risk indicators
- Weekly academic analytics

#### Testing and Reliability

Contributed extensively to:

- Agent tests
- Workflow tests
- Multi-agent collaboration tests
- Chat-to-agent integration tests
- Request-routing tests
- Academic workflow integration tests
- Conversation-memory tests
- Failure and fallback scenarios
- End-to-end system validation

---

### Pooja

GitHub: [@poojapanchal300798](https://github.com/poojapanchal300798)

Role: AI / Backend / RAG Contributor

Pooja contributed across the project's AI, backend, retrieval, workflow, and testing areas.

GitHub records 43 contributions to the Academic Copilot repository.

#### RAG and Retrieval

Contributions included work on the Retrieval-Augmented Generation system and its validation, including:

- RAG retrieval testing
- Retrieval benchmark evaluation
- Validation of retrieval quality
- Testing of the RAG pipeline
- Integration of retrieval-related work with the broader system

A notable contribution included evaluation of the project's canonical retrieval benchmark.

#### Backend and System Development

Contributed to backend development and integration work required to connect academic services and AI functionality.

This work was performed as part of the shared project architecture and integrated with other backend, agent, and academic-service components.

#### Testing

Contributed to the project's testing and quality-assurance effort, including work around:

- RAG testing
- System integration
- Backend validation
- Academic workflow behavior
- Regression prevention

#### Project Integration

Participated in integrating independently developed branches and components into the shared Academic Copilot codebase.

---

### Achini

GitHub: [@Achini-gf](https://github.com/Achini-gf)

Role: Software Testing / QA / Integration Contributor

Achini contributed primarily to software quality, system validation, integration testing, security testing, and end-to-end verification of Academic Copilot.

GitHub records 24 contributions to the Academic Copilot repository.

#### End-to-End Testing

Contributed to end-to-end validation of the complete Academic Copilot workflow.

This included testing interactions across system boundaries and verifying that individual components function correctly when combined into complete user-facing workflows.

#### Security Testing

Contributed to security-focused QA coverage, including validation of security-sensitive system behavior and failure scenarios.

#### Integration Testing

Contributed to testing interactions between major system components, including:

- Backend services
- Academic agents
- Workflow orchestration
- Telegram integration
- Academic data boundaries
- Failure handling

#### Quality Assurance

Contributed to the broader QA effort through:

- End-to-end test scenarios
- Integration testing
- Security testing
- Failure and edge-case validation
- Regression testing
- Verification of complete user flows

This work helped validate that independently developed components could operate together as a complete Academic Copilot system.

---

## Contribution Summary

| Contributor | Main Areas |
| --- | --- |
| Minou Vahedinezhad | Multi-Agent AI, LangGraph, Agents, Backend Integration, RAG Integration, Conversation Memory, Academic Analytics, Testing |
| Pooja (@poojapanchal300798) | RAG, Retrieval Evaluation, Backend/AI Integration, Testing |
| Achini (@Achini-gf) | QA, Security Testing, Integration Testing, End-to-End Testing |

## Collaboration Model

Academic Copilot was developed collaboratively using a Git-based software engineering workflow.

The team worked across several interconnected technical areas:

- Backend development
- AI agent development
- Multi-agent orchestration
- Retrieval-Augmented Generation
- MCP integration
- Academic analytics
- Database integration
- Telegram integration
- Automated testing
- System integration

Development was coordinated through:

- GitHub Issues
- Feature branches
- Pull Requests
- Code integration
- Automated testing
- Technical documentation

Because many components interact across system boundaries, some areas of the project represent shared work rather than isolated individual ownership.

## Contribution Verification

The contribution descriptions in this document are based on repository evidence including:

- Git commit history
- GitHub contributor history
- Merged changes
- Issues
- Implemented modules
- Testing history

The purpose of this document is to present team contributions transparently without attributing shared work exclusively to one contributor.
