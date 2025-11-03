# AI-Driven Development: Prompt Guide for Architects

## Core Philosophy

You are the **Solution Architect & AI Conductor**. Your value is in system design, client communication, and defining *what* to build. AI handles implementation details. Your superpower is asking the right questions and connecting business needs to technical solutions.

## Daily Workflow Prompts

### 📈 BUSINESS & REQUIREMENTS ANALYSIS

**Feature Elaboration & User Story Generation**

```
Act as a senior product manager. Our business goal is [Business Goal, e.g., "reduce user churn during onboarding"]. The stakeholders have suggested [Vague Feature, e.g., "a new user dashboard"].

Break this down into:
1. Key user personas and their primary needs.
2. A list of specific user stories in the format "As a [Persona], I want [Action], so that [Value]".
3. Potential edge cases and non-functional requirements (NFRs) like performance, accessibility, and security.
```

**Identifying Non-Functional Requirements (NFRs)**

```
Analyze this system proposal: [System Description, e.g., "a global, high-traffic e-commerce review platform"].
What are the most critical non-functional requirements we must define?
For each NFR (e.g., latency, scalability, data residency, security compliance), provide:
1. A clear, measurable definition (e.g., "P99 latency for read-APIs must be < 150ms").
2. Key architectural decisions that will be influenced by this NFR.
```

### 🏗️ SYSTEM DESIGN & ARCHITECTURE

**High-Level System Design**

```
Act as a senior software architect. We're building [system description, informed by requirements analysis]. 
Outline the key components, data models, and external dependencies for these core features:
1. [Feature A]
2. [Feature B] 
3. [Feature C]
List components in logical implementation order.
```

**Component Specification**

```
We're focusing on the [Component Name] from our architecture. 
Break it down into core functions. For each function, list:
- Function signature (or API endpoint: GET /users/{id})
- One-line description  
- Key business logic/validation rules
- Potential errors
```

### 🔧 IMPLEMENTATION PROMPTS

**Multi-Stage Implementation**

```
Role: Expert [Technology] Senior Engineer
Task: Develop [Component/Function Name]
Context: [Language/Framework, Design Principles, Constraints]
Goal: [Specific deliverable]

First, define the data models/interfaces (e.g., Abstract Base Classes, TypeScript interfaces). Critique them for SOLID principles and data integrity.
```

**Follow-up Implementation**

```
Based on the [Interface Name] definition, I need the concrete implementation using [specific technology, e.g., SQLAlchemy, TypeORM].

Chain of Thought:
1. What [query/algorithm] is required?
2. How will you handle [edge case, e.g., 'user not found']?
3. How will you log/monitor this function's execution?
4. Write the implementation. Explain key design choices in one paragraph after the code.
```

### 🧪 TESTING & QUALITY

**Comprehensive Test Generation**

```
Generate unit tests for the [Component/Function] implementation.

Testing Framework: [pytest/Jest/etc.]
Tests to Include:
1. [Happy path scenario]
2. [Edge case: non-existent resource] 
3. [Error condition: database failure]

Requirement: Use mocks for all external dependencies like [dependency names]. Isolate the [component] logic.
```

**Code Review & Security Scan**

```
Perform a code review on this code block. Analyze for:
1. Security issues (SQL injection, data exposure, insecure defaults)
2. Performance bottlenecks (N+1 queries, inefficient loops)  
3. Code quality (readability, Single Responsibility Principle)
4. Error handling adequacy (are errors caught and handled gracefully?)
5. Potential bugs

Provide specific, actionable suggestions.

[Paste code here]
```

### 📚 DOCUMENTATION & COMMUNICATION

**Generating Architectural Decision Records (ADRs)**

```
Generate an Architectural Decision Record (ADR) for our choice to use [Technology A].

Context: [Provide the problem, constraints, and technologies compared, e.g., from your "Technology Comparison" prompt output].
Format:
- Title: [e.g., "ADR-001: Choice of [Technology A] for [Component]"]
- Status: [Proposed/Accepted/Deprecated]
- Context: [The problem we are solving]
- Decision: [The decision that was made]
- Consequences: [Positive and negative consequences of this decision, including trade-offs]
```

**Drafting Diagrams (Mermaid/PlantUML)**

```
Based on our system design [paste a simple description or components list], generate the Mermaid.js (or PlantUML) code for a C4-style component diagram. Show the key components, their interactions, and the system boundaries.
```

**Executive Summary for Stakeholders**

```
Translate the following technical update into a concise, one-paragraph executive summary for non-technical stakeholders. Focus on business value and project status, avoiding technical jargon.

[Paste technical status update, e.g., "We finished implementing the UserRepository with SQLAlchemy and refactored the auth service to use JWT..."]
```

### ☁️ INFRASTRUCTURE & DEPLOYMENT (DevOps)

**Generating Infrastructure as Code (IaC)**

```
Act as a principal DevOps engineer.
Based on our system [System Description, e.g., "a Python FastAPI service with a PostgreSQL database"], generate a [Terraform/Pulumi/CloudFormation] configuration to deploy this on [Cloud Provider, e.g., AWS].

Include:
1. A [e.g., ECS/EKS] service for the application.
2. An [e.g., RDS] instance for the database.
3. Basic networking (VPC, subnets).
4. Essential IAM roles with least-privilege permissions.
```

**CI/CD Pipeline Configuration**

```
Generate the `.gitlab-ci.yml` (or GitHub Actions workflow) file for our [Language/Framework] project.
The pipeline must include these stages:
1. Lint: [e.g., ruff, eslint]
2. Test: [e.g., pytest, jest]
3. Build: [e.g., build Docker image]
4. Deploy: [Stub for deploying to staging]
```

### 🔍 CONTEXT & UNDERSTANDING

**Legacy Code Analysis**

```
Analyze this codebase for understanding:
[Paste code/file structure]

Explain:
1. Primary responsibility and architecture
2. Key data flows and dependencies
3. Potential technical debt or improvement areas
4. How to extend for [new requirement]
```

**Technology Comparison**

```
Compare [Technology A] vs [Technology B] for a system with:
- [Requirement 1: e.g., high read throughput]
- [Requirement 2: e.g., complex aggregations]
- [Constraint: e.g., team's existing expertise]

Focus on: performance, scalability, maintenance, and ecosystem. Provide a final recommendation.
```

## Pro Tips

### 🎯 Prompt Engineering

  - **Be Specific**: Include frameworks, versions, and constraints.
  - **Chain Thoughts**: Break complex tasks into step-by-step reasoning.
  - **Iterate**: Treat first output as a draft; refine with follow-ups.
  - **Set Context Once**: Start sessions with project standards (e.g., "We are using Python 3.11 with FastAPI and pydantic").

### 🔄 Workflow Optimization

1.  **Analyze First**: Use AI to refine requirements and NFRs.
2.  **Design Interfaces**: Create clear data models and component interfaces. This is your primary coding focus.
3.  **Generate Implementation**: Use multi-stage prompts for quality code.
4.  **Test Immediately**: Generate comprehensive tests alongside code.
5.  **Review Critically**: Focus on integration points and business logic, not syntax.
6.  **Document & Deploy**: Use AI to generate ADRs, diagrams, and IaC scripts.

### 📐 Focus Areas for Architects

  - **Data Models & Type Systems**: The blueprint of your system.
  - **Component Interfaces**: The "seams" and contracts between system parts.
  - **Test Strategy**: Review test coverage and scenarios, not implementation details.
  - **Communication**: Use AI to draft reports, ADRs, and clarify requirements for all audiences.

## Example Session Flow

```
1. REQUIREMENTS → "Elaborate user stories for an e-commerce auth system"
2. SYSTEM_DESIGN → "Outline the auth system components based on these stories"  
3. COMPONENT_SPEC → "Break down the UserService functions"  
4. IMPLEMENT → "Implement the UserRepository interface with SQLAlchemy"
5. TEST → "Generate pytest for UserRepository, mocking the DB connection"
6. DOCUMENT → "Generate an ADR for our choice of JWT over session cookies"
7. INFRA → "Generate a Terraform module for the RDS PostgreSQL instance"
8. REVIEW → "Security review of the authentication flow logic"
```

**Remember**: You own the vision and quality. AI owns the syntax and implementation.
