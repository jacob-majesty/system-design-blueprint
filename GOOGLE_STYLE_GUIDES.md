# Software Engineering Principles and Practices at Google

## Reference Links

* Google style guides: https://google.github.io/styleguide
* Refactoring | Design Patterns: https://refactoring.guru/
* Code review: https://google.github.io/eng-practices

## 🔑 Key Principles

The entire philosophy is structured around three fundamental principles that software organizations must consider:

1. **Time and Change:** Software must be resilient and adaptable to inevitable changes over time (new features, security fixes, deprecation, etc.). Delaying change often increases the cost of change later.
2. **Scale and Growth:** Practices and processes must be viable as the codebase and the engineering organization itself grow. What works for a small team may break at Google's scale (e.g., build times, complexity).
3. **Trade-Offs and Costs:** Engineering decisions must be made by consciously evaluating trade-offs, considering various costs (financial, personnel, opportunity, societal), and being evidence-driven.

---

## 🏛️ Three Main Aspects

The book is divided into three major sections that cover the landscape of Google's software engineering:

### 1. Culture

* **Team-Centric Development:** Emphasizes that software development is a collaborative team effort, not the work of a "lone genius."
* **Humility, Respect, and Trust (HRT):** These are presented as the essential pillars for healthy social interaction and team dynamics.
* **Psychological Safety:** The importance of creating a safe environment for asking questions, learning, and admitting mistakes.
* **Blameless Postmortems:** A process for analyzing failures to learn from them without blaming individuals.
* **Leadership:** Discusses the roles of Engineering Managers and Tech Leads and advocates for **Servant Leadership**, focusing on empowering the team and removing roadblocks.

### 2. Processes

* **Code Review:** Detailed practices for effective code review, stressing its benefits for correctness, consistency, knowledge sharing, and code comprehension.
* **Style Guides:** The necessity of codified style guides and rules to enforce consistency across a massive, shared codebase.
* **Documentation and Knowledge Sharing:** Strategies for scaling knowledge within the organization, including mentorship, internal platforms, and writing effective documentation.
* **Measuring Productivity:** Using frameworks like **Goals-Signals-Metrics (GSM)** to guide the creation of meaningful productivity metrics (often categorized by **QUANTS**: Quality, Attention, INtellectual complexity, Tempo & Velocity, Satisfaction).

### 3. Tools

* **Testing:** Stresses the critical role of a strong testing culture, test design , and strategies for testing at Google's scale.
  * **Test Doubles:** Guidance on when to use Fakes, Stubs, and Mocks, often advocating for the use of real implementations over test doubles when possible to ensure realism.
* **Build Systems and Version Control:** Insights into Google's monolithic version control system and the use of artifact-based, distributed build systems like Bazel.
* **Continuous Delivery:** Practices like small, frequent changes, feature flagging, and release trains to ensure velocity and quality.

---

## Key Pillars & Foundational Concepts

### Software Engineering vs. Programming

* **Programming** is about writing new code.
* **Software Engineering** is about the entire lifecycle: maintenance, debugging, updating, and ensuring that code remains functional and healthy as requirements, teams, and technology change.

### The Three Pillars of Google's Software Engineering

The entire culture and process are built upon these three principles:

1. **Culture:** Creating an environment of psychological safety, collaboration, and blamelessness.
2. **Processes:** Establishing clear, scalable workflows for code, knowledge, and decision-making.
3. **Tools:** Building and using tools that enforce and enable the desired culture and processes at scale.

---

## Major Practices and Lessons (Organized by Theme)

### Code & Collaboration

* **Code Review (Critiquing):** Code review is mandatory for every change. It's not just for finding bugs; its primary goals are:
  * **Code Understanding:** Ensuring at least one other person understands the change.
  * **Knowledge Transfer:** Spreading knowledge across the team.
  * **Maintainability:** Enforcing style guides and long-term code health.

* **Code Style Guides:** Strict, language-specific style guides are enforced by automated tools. This eliminates pointless debates and creates a consistent, readable codebase where any engineer can work on any project.

* **Documentation:** Emphasizes "Documentation as Code," stored in the monorepo and reviewed alongside code. They distinguish between:
  * **Tutorials** (Learning-oriented)
  * **How-To Guides** (Problem-oriented)
  * **Reference** (Information-oriented)
  * **Design Docs** (Decision-oriented)

### Testing & Reliability

* **The Test Sizes:** A clear taxonomy for tests:
  * **Small:** A single function or class; fast and hermetic.
  * **Medium:** Multiple classes; may involve a test database or other services.
  * **Large:** End-to-end tests; slow and can be flaky.
  * **Guideline:** Prefer small tests. Relying too heavily on large tests creates a slow, brittle feedback loop.

* **Site Reliability Engineering (SRE):** Introduces the core concepts of SRE, where the goal is not to eliminate failures but to manage them. Key ideas include:
  * **Error Budgets:** A service's reliability target is not 100%. The difference between 100% and the target is the "error budget" that allows for innovation and releases.
  * **Eliminating Toil:** Automating repetitive operational tasks.

### Tools & Automation

* **The "Paved Road" (Boring Infrastructure):** Google provides a set of highly supported, standard tools and frameworks. Using the "paved road" is the easiest path to success, reducing cognitive load and ensuring reliability, security, and maintainability.

* **Continuous Integration (CI) / Continuous Delivery (CD):** Practices for maintaining velocity and quality through automated processes.

### Project Management & Leadership

* **Engineering Productivity Teams:** Dedicated teams whose job is to improve the productivity of *other* engineers by building tools, optimizing processes, and researching better practices.

* **The Role of Staff Engineers:** Focuses on the importance of technical leadership—engineers who guide architecture, set technical direction, and mentor others without becoming people managers.

* **Design Docs & OKRs:** Highlights the importance of written design documents for making major technical decisions and Objectives and Key Results (OKRs) for setting and measuring team goals.

---

