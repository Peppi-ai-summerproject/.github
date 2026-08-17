# Academic Copilot

Academic Copilot is an AI-powered academic support system designed to help tutor teachers understand student progress, identify academic risks, retrieve relevant academic information, and receive actionable recommendations through natural-language conversations.

The system combines multi-agent orchestration, Retrieval-Augmented Generation (RAG), academic data services, persistent conversation memory, and Telegram integration into a unified conversational workflow.

The project was developed as a university summer software engineering project with a focus on AI agents, backend architecture, intelligent workflow orchestration, academic analytics, testing, and system integration.

## Overview

Academic Copilot allows tutor teachers to interact with academic services using natural language instead of manually navigating multiple systems or knowing which internal service should handle a request.

For example:

```text
Tutor:
"How is student 123 progressing?"

Academic Copilot:
Intent Detection
    ↓
Agent Selection
    ↓
Progress Analysis Agent
    ↓
Academic Data
    ↓
Analysis
    ↓
Tutor-friendly Response
```

More complex requests can automatically trigger multiple specialized agents.

```text
"Give me a complete overview of student 123
and tell me what I should do next."

            ↓
    Intent Detection
            ↓
     Agent Selection
            ↓
 Dependency Resolution
            ↓
     Progress Agent
            ↓
   Study Rights Agent
            ↓
       Risk Agent
            ↓
 Recommendation Agent
            ↓
    Reporting Agent
            ↓
 Communication Agent
            ↓
     Final Response
```

## Key Features

- Natural-language academic requests
- Automatic intent detection
- Automatic agent selection
- Multi-agent dependency resolution
- LangGraph-based workflow orchestration
- Student progress analysis
- Academic risk detection
- Study-right analysis
- Explainable recommendations
- Academic reporting
- Calendar and event processing
- Retrieval-Augmented Generation
- MCP-based academic tools
- Persistent conversation memory
- Telegram integration
- Safe fallback handling
- Unit, integration, agent, RAG, MCP, and end-to-end testing

## Multi-Agent System

Academic Copilot uses specialized agents with clearly separated responsibilities.

### Progress Analysis Agent

Analyzes student study progress and academic performance using available academic data.

### Study Rights Agent

Evaluates study-right information and relevant academic status.

### Risk Detection Agent

Identifies academic risks using structured evidence from available academic information.

### Recommendation Agent

Generates actionable recommendations based on verified academic information, detected risks, and relevant policy context.

### Reporting Agent

Aggregates results from multiple academic agents into structured tutor reports.

### Calendar Agent

Handles academic calendar and event-related requests.

### Communication Agent

Transforms structured workflow results into safe and concise tutor-facing responses.

## Intelligent Request Routing

Tutors do not need to specify which agent should process a request.

The system automatically determines the appropriate workflow.

```text
Natural Language Request
        ↓
Intent Detection
        ↓
Agent Selection
        ↓
Dependency Resolution
        ↓
Execution Plan
        ↓
LangGraph Workflow
```

Supported routing categories include:

- Progress
- Study rights
- Risk
- Recommendation
- Reporting
- Calendar
- Communication
- General conversation
- Unknown or unsupported requests

Ambiguous and unsupported requests are handled without unnecessarily executing academic workflows.

## Multi-Agent Dependency Resolution

Some requests require results from multiple agents.

For example, a recommendation requires an existing risk assessment:

```text
Risk
  ↓
Recommendation
```

A comprehensive student report can require:

```text
Progress
    ↓
Study Rights
    ↓
Risk
    ↓
Recommendation
    ↓
Reporting
```

The routing layer expands required dependencies and produces a deterministic execution plan while preventing duplicate or invalid agent execution.

## LangGraph Workflow Orchestration

Agent execution is orchestrated using LangGraph.

The workflow is responsible for:

- Agent execution order
- Shared workflow state
- Dependency-safe execution
- Agent result accumulation
- Partial-result handling
- Failure handling
- Maximum execution steps
- Unknown agent handling
- Workflow finalization

A simplified workflow is:

```text
START
  ↓
Prepare
  ↓
Execute Agent
  ↓
Update AgentState
  ↓
More Agents?
  ├── Yes → Execute Next Agent
  │
  └── No
       ↓
    Finalize
       ↓
      END
```

Workflows can produce completed, partial, or failed results, allowing verified information to be preserved even when individual components are unavailable.

## System Architecture

```text
┌──────────────────────────────┐
│           Telegram           │
│          Tutor User          │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       Telegram Adapter       │
│        BackendClient         │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│        FastAPI Backend       │
│           Chat API           │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│         ChatService          │
│                              │
│ Conversation Management      │
│ Workflow Integration         │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       Intent Detection       │
│              ↓               │
│        Agent Selection       │
│              ↓               │
│     Dependency Resolution    │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│      LangGraph Workflow      │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       Academic Agents        │
│                              │
│ Progress                     │
│ Study Rights                 │
│ Risk Detection               │
│ Recommendation               │
│ Reporting                    │
│ Calendar                     │
│ Communication                │
└──────────────┬───────────────┘
               │
        ┌──────┴──────┐
        ▼             ▼
┌──────────────┐ ┌──────────────┐
│ MCP /        │ │ RAG Pipeline │
│ Academic     │ │              │
│ Services     │ │ Qdrant       │
└──────────────┘ └──────────────┘
        │             │
        └──────┬──────┘
               ▼
┌──────────────────────────────┐
│       Agent Results          │
│              ↓               │
│     Communication Agent      │
│              ↓               │
│        Final Response        │
└──────────────┬───────────────┘
               │
               ▼
           Telegram
```

## Retrieval-Augmented Generation

The project includes a RAG pipeline for retrieving relevant academic and policy information.

```text
Academic Documents
       ↓
Document Processing
       ↓
Chunking
       ↓
Embeddings
       ↓
Qdrant
       ↓
Semantic Retrieval
       ↓
Relevant Context
       ↓
Academic Workflow
```

Retrieved context can support components such as the Recommendation Agent with relevant academic policy information.

The system is designed to avoid presenting unsupported information as authoritative university policy.

## Model Context Protocol

The project includes an MCP-based academic tool layer for structured access to academic information and services.

Agents interact with academic capabilities through gateway abstractions rather than directly depending on infrastructure implementations.

This separation improves:

- Testability
- Dependency isolation
- Architecture boundaries
- Deterministic testing
- Replaceability of external integrations

## Conversation Memory

Academic Copilot supports persistent conversation memory for authenticated Telegram interactions.

The memory system includes:

- PostgreSQL-backed conversation storage
- Telegram user/chat mapping
- Conversation ownership isolation
- Student-specific isolation
- Transactional message storage
- Bounded message retention
- Concurrent-write protection
- Separation between conversation memory and workflow state

Internal workflow data and sensitive infrastructure information are kept separate from stored conversation history.

## Academic Risk Analysis

The system includes structured academic risk analysis based on available academic evidence.

Risk evaluation can use signals such as:

- Study progress
- ECTS completion
- Study-right status
- Academic deadlines
- Tutor-meeting information
- Available academic indicators

The system supports structured risk levels and handles missing data explicitly rather than treating unavailable information as evidence of no risk.

## Recommendations

Recommendations are generated from verified academic information.

```text
Progress Analysis
       +
Study Rights
       +
Risk Assessment
       +
Relevant Policy Context
       ↓
Actionable Recommendation
```

Recommendations remain advisory and are intended to support tutor decision-making rather than automatically perform academic actions.

## Telegram Integration

Telegram provides the primary conversational interface.

```text
Telegram
   ↓
Webhook
   ↓
Telegram Handler
   ↓
BackendClient
   ↓
Chat API
   ↓
ChatService
   ↓
Intent Detection
   ↓
Agent Routing
   ↓
Academic Workflow
   ↓
Final Response
   ↓
Telegram Reply
```

The system supports both natural-language academic requests and academic commands.

## Testing

Testing is a major part of the project.

The repository includes coverage for:

- Unit tests
- Agent tests
- Workflow tests
- RAG tests
- MCP tests
- Integration tests
- Request-routing tests
- Chat-to-agent integration tests
- Telegram integration tests
- End-to-end conversation-flow tests
- Failure and fallback scenarios

External services can be replaced with deterministic test doubles so production workflow logic can be tested without requiring live infrastructure.

## Reliability and Safety

The system is designed to handle incomplete and unavailable information safely.

Important behaviors include:

- Missing academic data produces qualified results
- Failed agents do not automatically discard verified results from other agents
- Unsupported requests do not execute unrelated academic workflows
- Internal exceptions are not exposed to users
- Infrastructure details are kept out of tutor-facing responses
- Missing information is not interpreted as evidence of no risk
- Recommendations remain advisory

## Tech Stack

### Backend

- Python
- FastAPI
- Pydantic
- PostgreSQL

### AI and Orchestration

- LangGraph
- Multi-Agent Architecture
- Retrieval-Augmented Generation
- Model Context Protocol
- Embeddings
- Vector Search

### Vector Database

- Qdrant

### Interface

- Telegram Bot

### Infrastructure

- Docker
- Docker Compose
- Linux
- Nginx

### Testing

- Pytest
- Unit Testing
- Integration Testing
- End-to-End Testing
- Deterministic Test Doubles

### Development

- Git
- GitHub
- GitHub Issues
- Pull Requests
- Feature Branch Workflow

## Repository Structure

```text
academic-copilot/
│
├── backend/
│   ├── app/
│   │   ├── agents/
│   │   ├── api/
│   │   ├── services/
│   │   ├── telegram/
│   │   └── ...
│   ├── tests/
│   └── db/
│
├── rag/
├── database/
├── docs/
├── research/
├── diagrams/
├── presentations/
├── docker-compose.yml
├── pytest.ini
├── README.md
└── TEAM.md
```

## Team

Academic Copilot was developed collaboratively as a university summer software engineering project.

The project involved work across AI agents, backend development, RAG, MCP, academic analytics, testing, infrastructure, and system integration.

For individual team members and their contributions, see:

[TEAM.md](./TEAM.md)

## Project Context

Academic Copilot was developed as a university summer software engineering project exploring how AI-powered multi-agent systems can support academic guidance and tutor workflows.

The project combines concepts from:

- Software Engineering
- Backend Development
- Artificial Intelligence
- Multi-Agent Systems
- Retrieval-Augmented Generation
- Academic Analytics
- Conversational Interfaces
- Automated Testing
- DevOps

## Project Status

Academic Copilot is an academic software engineering project and is not a production university service.

Some integrations may use development environments, test data, mocks, or deterministic external-boundary implementations depending on the execution environment.

## License

See the repository license for licensing information.
