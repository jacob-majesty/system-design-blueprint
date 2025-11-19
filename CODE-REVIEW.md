# ⚙️ Senior Software Engineer Code Review Checklist

This checklist is organized by key focus areas to ensure comprehensive review coverage, balancing correctness, design, and efficiency.

---

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
