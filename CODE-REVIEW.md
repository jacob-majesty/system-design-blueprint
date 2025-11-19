# ⚙️ Senior Software Engineer Code Review Checklist

##  Key Senior Review Focus Areas
---
# Senior Code Review Summary: High-Leverage Focus

This section outlines the most important aspects of a senior code review, emphasizing systems-level thinking and mentorship.

---

## 1. 🔑 P1 & P2: The Mandatory Review Focus

The primary goal is to act as a **gatekeeper** against issues that automated tools miss. Prioritize your time on these critical areas:

* **Architectural Drift:** Ensure the change aligns with the system's long-term design. **Avoid** introducing new, unnecessary patterns or tight coupling.
* **Security Integrity:** **Absolutely block** any merge request that introduces potential security vulnerabilities (e.g., injection, insecure defaults).
* **Non-Obvious Correctness:** Verify complex logic, concurrency handling, and that all **edge cases** and failure scenarios are properly accounted for.
* **Performance Regression:** Quickly identify high-impact performance flaws, especially inefficient database access (N+1 queries) or $O(n^2)$ complexity.
* **Test Quality:** Check that tests are not only present but are **high-quality, deterministic,** and cover the intended *behavior* of the change.

---

## 2. 🗣️ Communication & Mentorship

As a senior engineer, your role is to teach, not just criticize.

* **Explain the *Why***: For every mandatory change, clearly explain the **principle, risk, or technical debt** that necessitates the fix.
* **Be Constructive:** Maintain a positive, objective tone. Frame feedback as suggestions for improvement rather than personal criticism.
* **Actionability:** Clearly label comments as **[Blocking]** (P1/P2 must-fix) or **[Suggestion]** (P3 nice-to-have/nit) to guide the author.
* **Be Efficient:** For complex or lengthy debates, move the discussion offline immediately (e.g., "Let's schedule a 5-minute sync") rather than engaging in long comment threads.

---

## 3. 🧠 Mastery Requires Practice

Exceling at code review is a skill requiring continuous development:

* **Practice Predictive Thinking:** Consistently ask: "What breaks if this is merged?" and "How does this scale?"
* **Practice Prioritization:** Develop the ability to quickly triage issues to ensure the team's development pipeline moves quickly and is not blocked over minor stylistic concerns.
---

As a senior engineer, your review should prioritize issues that **automated tools cannot find** or that have a **disproportionately large impact** on the system's long-term health and stability. These areas are **mandatory** checks before merging.

| Focus Area | Description | Priority | Checklist Reference |
| :--- | :--- | :--- | :--- |
| **Architectural Drift** | Does this change introduce a new, non-standard pattern, or violate the system's core design principles? Does it unnecessarily couple components? | P1/P2 | Section 3 |
| **Security Integrity** | Is the code vulnerable to common attacks (e.g., injection, cross-site scripting, insecure handling of sensitive data)? Is user input trusted? | **P1 (Critical)** | Section 1 |
| **Performance Regression**| Could this change lead to significant slowdowns, resource exhaustion, or increased infrastructure cost (e.g., N+1 queries, high-complexity loops, memory leaks)? | P1/P2 | Section 4 |
| **Non-Obvious Correctness**| Are **all** edge cases, concurrency issues, and complex failure scenarios handled properly? Does the code work under load or in distributed environments? | **P1 (Critical)** | Section 1 |
| **Test Quality & Intent** | Do the tests cover the *intent* of the feature? Are the tests brittle, slow, or testing implementation details rather than behavior? (Not just *if* tests exist, but *how well* they exist). | P2 | Section 2 |
| **Technical Debt Burden** | Is the solution the simplest one? Does it introduce temporary fixes that will become permanent maintenance headaches later? | P2 | Section 3, 5 |

---
This checklist is organized by key focus areas to ensure comprehensive review coverage, balancing correctness, design, and efficiency.

## 1. 🎯 Functional Correctness & Integrity

| Check | Description | Pass/Fail |
| :--- | :--- | :--- |
| **Logic** | Does the code accurately solve the reported problem/user story? | |
| **Edge Cases** | Are nulls, zero inputs, empty arrays, timeouts, and boundary conditions handled? | |
| **Error Handling** | Are appropriate exceptions caught/thrown? Are error messages clear and helpful? | |
| **Input Validation** | Is all external/user input properly sanitized and validated before use? | |
| **Security** | Does the code introduce common vulnerabilities (XSS, SQL Injection, CSRF, insecure defaults)? | |

## 2. 🧪 Testing and Reliability

| Check | Description | Pass/Fail |
| :--- | :--- | :--- |
| **Coverage** | Are new/changed features adequately covered by unit and integration tests? | |
| **Test Quality** | Are tests deterministic, fast, and testing the *behavior* (not the implementation details)? | |
| **Mocks/Stubs** | Are external dependencies properly mocked/stubbed to isolate the unit under test? | |
| **Negative Tests** | Are tests included to ensure error paths and invalid inputs fail as expected? | |

## 3. 🏛️ Architectural & Design Quality

| Check | Description | Pass/Fail |
| :--- | :--- | :--- |
| **Separation of Concerns** | Is the code responsible for only one thing (e.g., UI logic separate from business logic)? | |
| **Dependency Management**| Are new dependencies necessary? Are they correctly installed and managed? | |
| **Abstraction** | Are appropriate interfaces/abstractions used? Are classes too tightly coupled? | |
| **API Design** | If exposing an API endpoint, is the interface intuitive, versioned, and RESTful/GraphQL-compliant? | |
| **Technical Debt** | Is the change introducing unnecessary complexity or making future changes harder? | |

## 4. ⚡ Performance & Efficiency

| Check | Description | Pass/Fail |
| :--- | :--- | :--- |
| **Database Queries** | Are database interactions efficient (e.g., correct indexing, avoiding N+1 queries, correct transactions)? | |
| **Loops/Complexity** | Are algorithms unnecessarily slow (e.g., nested loops leading to $O(n^2)$ complexity)? | |
| **Resource Leaks** | Are resources (connections, file handles, memory) properly closed/released? | |
| **Caching** | Is necessary data cached, and is the cache invalidation strategy sound? | |

## 5. 📖 Readability and Maintainability

| Check | Description | Pass/Fail |
| :--- | :--- | :--- |
| **Naming** | Are variable, function, and class names clear, descriptive, and accurately reflecting their purpose? | |
| **Comments** | Are comments used only where necessary (to explain *why* or complex logic), not *what* the code does? | |
| **Documentation** | Are public methods/APIs documented (e.g., JSDoc, JavaDoc) if required? | |
| **Style Guide** | Does the code adhere to the project's established style guide (handled mostly by linting/formatting)? | |
| **PR Scope** | Is the Pull Request small, focused, and dedicated to a single logical change? (Ideal: $<250$ lines of code changed) | |

## 6. 💬 Mentoring and Feedback Tone (Reviewer's Focus)

| Check | Description | Action |
| :--- | :--- | :--- |
| **Constructive Tone** | Is the feedback polite, objective, and focused on the code, not the developer? | **Avoid:** "You did this wrong." **Use:** "This approach can lead to X problem." |
| **Explain *Why*** | Does every critical comment include an explanation of *why* the suggested change is better? | Offer external resources or links to internal docs for context. |
| **Actionability** | Are comments clear about whether a fix is **Mandatory** or merely a **Suggestion/Nit**? | Use clear labels like **[Blocking]** or **[Suggestion]** for categorization. |
| **Efficiency** | Was the review completed within the team's agreed-upon timeframe (e.g., 24 hours)? | If a discussion is too long, move it to an offline call. |
