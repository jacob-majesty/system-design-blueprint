# AI-Driven Development: Prompt Guide for Architects

## Core Philosophy
You are the **Solution Architect & AI Conductor**. Your value is in system design, client communication, and defining *what* to build. AI handles implementation details.

## Daily Workflow Prompts

### 🏗️ SYSTEM DESIGN & ARCHITECTURE

**High-Level System Design**
```
Act as a senior software architect. We're building [system description]. 
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
- Function signature
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

First, define the data models/interfaces (ABCs). Critique for SOLID principles and data integrity.
```

**Follow-up Implementation**
```
Based on the [Interface Name], I need the concrete implementation using [specific technology].

Chain of Thought:
1. What [query/algorithm] is required?
2. How will you handle [edge case]?
3. How will you log/monitor this?
4. Write implementation. Explain design choices in one paragraph after code.
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

Requirement: Use mocks for [dependencies]. Isolate the [component] logic.
```

**Code Review & Security Scan**
```
Perform a code review on this code block. Analyze for:
1. Security issues (SQL injection, data exposure)
2. Performance bottlenecks  
3. Code quality (readability, SRP)
4. Error handling adequacy
5. Potential bugs

Provide specific, actionable suggestions.

[Paste code here]
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

Focus on: performance, scalability, maintenance, and ecosystem.
```

## Pro Tips

### 🎯 Prompt Engineering
- **Be Specific**: Include frameworks, versions, and constraints
- **Chain Thoughts**: Break complex tasks into step-by-step reasoning
- **Iterate**: Treat first output as draft; refine with follow-ups
- **Set Context Once**: Start sessions with project standards

### 🔄 Workflow Optimization
1. **Design First**: Create clear interfaces and data models
2. **Generate Implementation**: Use multi-stage prompts for quality code  
3. **Test Immediately**: Generate comprehensive tests alongside code
4. **Review Critically**: Focus on tests and integration points
5. **Integrate**: Use AI for glue code between components

### 📐 Focus Areas for Architects
- **Data Models & Type Systems**: Your primary coding focus
- **Component Interfaces**: The "seams" between system parts  
- **Test Strategy**: Review test coverage, not implementation details
- **Client Communication**: Use AI to draft reports and clarify requirements

## Example Session Flow
```
1. SYSTEM_DESIGN → "Outline e-commerce auth system components"
2. COMPONENT_SPEC → "Break down UserService functions"  
3. IMPLEMENT → "Implement UserRepository with SQLAlchemy"
4. TEST → "Generate pytest for UserRepository"
5. INTEGRATE → "Create FastAPI routes connecting services"
6. REVIEW → "Security review of authentication flow"
```

**Remember**: You own the vision and quality. AI owns the syntax and implementation. Your superpower is asking the right questions and connecting business needs to technical solutions.
