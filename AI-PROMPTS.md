## 🤖 The Power of AI in Software Engineering

The integration of AI into the Software Development Life Cycle (SDLC) transforms it into a **Collaborative Partner**, moving beyond simple task automation. AI offers **Comprehensive Assistance** across all phases, from initial design to final maintenance.

The effectiveness of this partnership hinges on **The Power of Effective Prompts** and **Iterative Improvement**. By structuring your prompts, you unlock significant **Learning Opportunities** and gain superior results. Crucially, the **Crucial Human Element** remains—your business and context understanding is essential for guiding the AI effectively.

-----

## 🧭 Table of Contents

1. [Software Development Cycle (SDLC)](#1-software-development-cycle-sdlc)
   - [1.1. AI's Role in SDLC](#11-ais-role-in-sdlc)

2. [Core Development Criteria and Principles](#2-core-development-criteria-and-principles)
   - [2.1. Code Review and Explanation](#21-code-review-and-explanation)
   - [2.2. Architecture--design](#22-architecture--design)

3. [Implementation and Coding Prompts](#3-implementation-and-coding-prompts)
   - [3.1. General Implementation](#31-general-implementation)
   - [3.2. Database Design & Optimization](#32-database-design--optimization)
   - [3.3. Query Optimization and Troubleshooting](#33-query-optimization-and-troubleshooting)

4. [Advanced Prompting Strategies](#4-advanced-prompting-strategies)

5. [Documentation Generation](#5-documentation-generation)

6. [Testing, Debugging, and Quality Assurance (QA)](#6-testing-debugging-and-quality-assurance-qa)
   - [6.1. AI-Assisted Debugging](#61-ai-assisted-debugging)
   - [6.2. Test Generation & Planning](#62-test-generation--planning)

7. [Security and Performance Optimization](#7-security-and-performance-optimization)
   - [7.1. Code Security Enhancement](#71-code-security-enhancement)
   - [7.2. Performance Optimization](#72-performance-optimization)

8. [Version Control and Collaboration](#8-version-control-and-collaboration)

-----

## 1\. Software Development Cycle (SDLC)

### 1.1. AI's Role in SDLC

| Phase | Focus Areas |
| :--- | :--- |
| **Part 1: Laying the Foundations** | Project Planning, Design, and Architecture |
| **Part 2: Building with AI** | Code Generation, Database Design, and Documentation |
| **Part 3: Polishing and Maintaining** | Testing, Optimization, and Version Control |

-----

## 2\. Core Development Criteria and Principles

These criteria ensure AI-generated content adheres to high standards of software engineering.

### 2.1. Code Review and Explanation

  * **CRITERIAS**
      * **Communication:** Simplicity, should read like a story.
      * **Software Engineering Principles:** SOLID, KISS, YAGNI, DRY, TDA, and MVC.
      * **Requirements:** Error handling, Edge cases, Performance optimization, Best practices for `[language/framework]`, Coding style, and constraints.
  * **Code Review Prompt Example**
    ```
    Please review the following code:
    [paste your code]
    Consider: 1. Code quality and adherence to best practices, 2. Potential bugs or edge cases, 3. Performance optimizations, 4. Readability and maintainability, 5. Any security concerns.
    Suggest improvements and explain your reasoning for each suggestion.
    ```
  * **Code Explanation Prompt Example**
    ```
    Can you explain the following part of the code in detail:
    [paste code section]
    Specifically: 1. What is the purpose of this section?, 2. How does it work step-by-step?, 3. Are there any potential issues or limitations with this approach?
    ```

### 2.2. Architecture & Design

  * **Focus:** Communication and simplicity.
  * **Key Deliverables:** Tradeoffs and decisions (both positive and negative), Architecture Decision Record (ADR), and Design patterns.
  * **Visual Diagram:** Request a UML, Flowchart, Class, Sequence, or Entity-Relationship Diagram.
  * **Other Elements:** TEST: UNIT TEST, CODE REVIEW, DOCUMENTATION: Resume of MR & Technical detail of implementation with explanation.

-----

## 3\. Implementation and Coding Prompts

### 3.1. General Implementation

| Task | Prompt Requirements |
| :--- | :--- |
| **Implementing an Algorithm** | 1. Main function with clear parameter/return types. 2. Helper functions (if necessary). 3. **Time and space complexity analysis**. 4. Example usage. |
| **Creating a Class/Module** | 1. Constructor/initialization. 2. Main methods with clear docstrings. 3. Necessary private helper methods. 4. Proper encapsulation and adherence to OOP principles. |
| **Optimizing Existing Code** | Suggest optimizations. For each suggestion, explain the expected improvement and any trade-offs. |
| **Writing Unit Tests** | Include tests for: 1. Normal expected inputs. 2. Edge cases. 3. Invalid inputs. Use `[preferred testing framework]` syntax. |

### 3.2. Database Design & Optimization

#### Designing Database Schemas

The request requires: Tables and columns (with data types), Primary/Foreign key relationships, Necessary junction tables, Suggested indexes for performance, Considerations for scalability, and Rationale behind design choices.

#### Analyzing Existing Schemas

  * **Analysis Points:** Normalization (suggest improvements if needed), Denormalization (where it might improve performance), Indexing strategy, Scalability (handling growth and potential bottlenecks), and Data integrity (constraints/triggers).
  * **Requirement:** For each suggestion, explain the pros and cons.

### 3.3. Query Optimization and Troubleshooting

| Task | Requirements |
| :--- | :--- |
| **Optimizing Slow Queries** | 1. Analyze for performance issues. 2. Suggest optimizations (rewriting, indexes, schema changes). 3. Explain the reasoning. 4. **Estimate performance improvement**. |
| **Index Optimization** | Consider: 1. Which columns to index. 2. Single-column vs. multi-column indexes. 3. Covering indexes. 4. Effect on write performance. |
| **Troubleshooting Poor Performance** | 1. Identify sub-optimal parts (query/execution plan). 2. Suggest alternative query writes. 3. Identify missing indexes. 4. Denormalization potential. |
| **Data Migration Planning** | 1. Identify transformation steps. 2. Suggest intermediate tables/views. 3. Consider data integrity and conflict handling. 4. Propose a verification strategy. |
| **Database Performance Tuning** | Comprehensive tuning plan including: Configuration parameters, Indexing strategy review, Query optimization techniques, Potential schema optimizations, and Caching strategies. |

-----

## 4\. Advanced Prompting Strategies

Use these strategies to get more tailored and actionable results from the AI.

| Strategy | Goal | Example (Template) |
| :--- | :--- | :--- |
| **Q\&A Strategy** | Ensures the AI understands specific needs and constraints before providing a solution. | *"I need to build a user authentication system... Before providing a solution, please ask me relevant questions about my specific requirements and constraints..."* |
| **Pros and Cons Strategy** | Helps weigh factors for specific use cases against generic recommendations. | *"Please analyze the pros and cons of using MongoDB, PostgreSQL, and Firebase for this application. Consider factors like scalability, query capabilities, ease of development, and maintenance requirements."* |
| **Stepwise Chain of Thought** | Allows you to maintain control and guide a process (e.g., refactoring) one stage at a time. | *Step 1: "Help me refactor the code... Go one step at a time. Do not move to the next step until I give the keyword ‘next’."* |
| **Role Prompt Strategy** | Specifies a professional context, ensuring feedback prioritizes professional considerations (e.g., security). | *"Act as a senior security engineer... Review the following authentication code for my React application and identify any security vulnerabilities..."* |
| **Combined Strategies** | Merge strategies for highly complex tasks (e.g., [Role + Q\&A], [Stepwise + Pros/Cons], [Role + Stepwise], [Q\&A + Pros/Cons + Stepwise]). | *"Act as a senior database architect... Walk me through the optimization process step by step..."* |

-----

## 5\. Documentation Generation

| Task | Key Requirements |
| :--- | :--- |
| **General Documentation Blueprint** | Overview, Installation, Configuration, API reference, Usage examples, Troubleshooting, and FAQ. Consider target audience, prerequisites, pitfalls, and best practices. |
| **Refining Specific Sections** | Review for: Clarity, Completeness, Appropriate level of detail, and Consistency. |
| **API Documentation** | Endpoint URL/method, Request parameters/body, Response format/status codes, Example request/response, Authentication, and Rate limiting. |
| **README.md File** | Project title/description, Installation, Usage examples, Contributing guidelines, License, and Badges. **Use proper Markdown and a Table of Contents**. |
| **User Guides** | Introduction, Getting started, Main features, Advanced tips, and Troubleshooting. Use simple language and step-by-step instructions. |
| **Code Comments and Docstrings** | Follow `[language-specific]` conventions. Include: Brief description, Parameters/types, Return value/type, Exceptions, and Usage examples. |
| **Living Documentation Update** | Update relevant sections based on code changes. **Highlight breaking changes or new features**. |
| **Periodic Review** | Suggest sections to add/expand, identify outdated/irrelevant parts, and recommend improvements for clarity. |

### Details:
### Blueprint Prompt

I need to create documentation for `[project/component name]`. Please generate:

1.  An overview of the `[project/component]`
2.  Installation instructions
3.  Configuration options
4.  API reference (if applicable)
5.  Usage examples
6.  Troubleshooting guide
7.  FAQ section

For each section, consider:
* The target audience (e.g., developers, end-users)
* Any prerequisites or dependencies
* Common pitfalls or misconceptions
* Best practices

Please use clear, concise language and include relevant code snippets where appropriate.

### Refining Specific Sections Prompt

```markdown
Please review and improve the following documentation section:
[Paste section here]

Consider:
1. Clarity of explanation
2. Completeness of information
3. Appropriate level of detail for the target audience
4. Consistency with best practices in technical writing

Suggest improvements and explain your reasoning.
````

### For API Documentation

  * **Prompt Template:**
    ```markdown
    Generate API documentation for the following endpoint:
    [Paste endpoint details]
    Include:
    1. Endpoint URL and method
    2. Request parameters and their types
    3. Request body format (if applicable)
    4. Response format and possible status codes
    5. Example request and response
    6. Any authentication requirements
    7. Rate limiting information (if applicable)
    ```

### For a README File

  * **Prompt Template:**
    ```markdown
    Create a README.md file for my GitHub repository. The project is [brief description]. Include:
    1. Project title and description
    2. Installation instructions
    3. Usage examples
    4. Contributing guidelines
    5. License information
    6. Badges (e.g., build status, version, etc.)

    Use proper Markdown formatting and consider adding a table of contents for easier navigation.
    ```

### For User Guides

  * **Prompt Template:**
    ```markdown
    Generate a user guide for [product/feature name]. The target audience is [describe audience]. Include:
    1. Introduction and purpose of the product/feature
    2. Getting started guide
    3. Main features and how to use them
    4. Advanced usage tips
    5. Troubleshooting common issues

    Use simple language and consider including step-by-step instructions with hypothetical screenshots placeholders.
    ```

### For Code Comments and Docstrings

  * **Prompt Template:**
    ```markdown
    Generate appropriate comments and docstrings for the following code:
    [Paste code here]
    Follow [language-specific] conventions for docstrings. Include:
    1. Brief description of the function/class
    2. Parameters and their types
    3. Return value and type
    4. Any exceptions that might be raised
    5. Usage examples if the function/class usage is not immediately obvious
    ```

### Leveraging AI for Living Documentation (Update Based on Changes)

  * **Prompt Template:**
    ```markdown
    I've made the following changes to my code:
    [Summarize changes]
    Please update the relevant sections of the documentation to reflect these changes. 
    Highlight any breaking changes or new features that users should be aware of.
    ```

### Periodic Review

  * **Prompt Template:**
    ```markdown
    Please review the following documentation:
    [Paste current docs]
    Considering the latest best practices and common user pain points in similar projects:
    1. Suggest any sections that should be added or expanded
    2. Identify any parts that might be outdated or no longer relevant
    3. Recommend improvements for clarity and user-friendliness
    ```

-----

## 6\. Testing, Debugging, and Quality Assurance (QA)

### 6.1. AI-Assisted Debugging

  * **Debugging Prompt:** Describe the bug/error, paste relevant code.
  * **AI Output Request:** 1. Analyze code and suggest potential causes. 2. Provide step-by-step debugging strategies. 3. Suggest tools/techniques. 4. Propose fixes and explain reasoning. 5. Mention best practices/common pitfalls.
  * **Code Review (Continuous Improvement):** Review for: Code style, Potential bugs/edge cases, Performance, Security, and Readability/Maintainability.

### 6.2. Test Generation & Planning

| Type of Test | Coverage Requirements |
| :--- | :--- |
| **Unit Tests** | Happy path scenarios, Edge cases, Error conditions, and Boundary value analysis. Include: Description of check, Actual test code (using `[framework]`), and necessary mock objects or fixtures. |
| **Integration Tests** | Main interaction scenarios, Proper error handling and edge cases, and necessary setup/teardown procedures. |
| **Performance Test Plan** | Key performance indicators, Test scenarios, Tools/frameworks, Strategies for bottleneck identification, and Interpretation best practices. |
| **Security Testing** | Review for common issues (Injection flaws, Broken authentication, Sensitive data exposure, XSS, etc.). For each vulnerability, explain the risk and suggest secure coding practices. |
| **Test Data Generation** | Appropriate value ranges, SQL/Script to generate diverse data (Normal, Edge, Invalid), **Ensure referential integrity**, and cover crucial scenarios. |

### Details:
### Unit Tests

* **Prompt Template:**
    ```markdown
    I need unit tests for the following function:
    [Paste your function here]

    Please generate a comprehensive set of unit tests that cover:
    1. Happy path scenarios
    2. Edge cases
    3. Error conditions
    4. Boundary value analysis

    For each test case, please:
    1. Provide a brief description of what the test is checking
    2. Write the actual test code using [preferred testing framework, e.g., pytest]
    3. Explain any mock objects or fixtures that might be needed

    Also, suggest any additional tests that might be relevant based on common pitfalls or best practices for this type of function.
    ```

### AI-Assisted Debugging Techniques

* **Prompt Template:**
    ```markdown
    I'm encountering the following bug:
    [Describe the bug, including any error messages and the steps to reproduce]

    Here's the relevant code:
    [Paste the code related to the bug]

    Please help me debug this issue:
    1. Analyze the code and suggest potential causes of the bug
    2. Provide step-by-step debugging strategies I can follow
    3. Suggest any tools or techniques that might be helpful in diagnosing the issue
    4. If possible, propose potential fixes and explain their reasoning

    Additionally, are there any best practices or common pitfalls related to this type of issue that I should be aware of for future reference?
    ```

### Continuous Improvement through AI Code Reviews

* **Prompt Template:**
    ```markdown
    Please review the following code for quality and potential issues:
    [Paste your code here]

    In your review, please consider:
    1. Code style and adherence to best practices
    2. Potential bugs or edge cases not handled
    3. Performance optimizations
    4. Security vulnerabilities
    5. Readability and maintainability

    For each issue found, please:
    1. Explain the problem
    2. Suggest a fix
    3. Provide a brief rationale for the suggested change

    Additionally, are there any overall improvements or refactoring suggestions you would make for this code?
    ```

### For Generating Integration Tests

* **Prompt Template:**
    ```markdown
    I need to create integration tests for the following components:
    [List components and their interactions]

    Please suggest a set of integration tests that:
    1. Cover the main interaction scenarios between these components
    2. Test for proper error handling and edge cases
    3. Include any necessary setup and teardown procedures

    Provide the test scenarios in a clear, step-by-step format, and include any necessary mock objects or test data.
    ```

### For Performance Testing

* **Prompt Template:**
    ```markdown
    I need to create a performance test plan for my application. The key areas of concern are:
    [List main functionalities or components to be tested]

    Please help me create a performance test plan that includes:
    1. Key performance indicators to measure
    2. Test scenarios to simulate various load conditions
    3. Suggestions for tools or frameworks to use
    4. Strategies for identifying performance bottlenecks
    5. Best practices for interpreting and acting on the results
    ```

-----

## 7\. Security and Performance Optimization

### 7.1. Code Security Enhancement

  * **Security Audit Focus:** Identify potential security vulnerabilities including: Injection flaws, Broken authentication/access control, Sensitive data exposure, XSS, Security misconfigurations, Insecure deserialization, Known vulnerable components, and Insufficient logging.
  * **Audit Output:** 1. Explain potential impact. 2. Suggest fix/mitigation strategy. 3. Provide code snippet for the fix. 4. Recommend security-related libraries/tools.
  * **SQL Injection Prompt:** Explain how it could be exploited, provide a secure alternative, and suggest relevant security libraries.
  * **Front-End Security Prompt:** Review for XSS prevention, secure handling of sensitive data, CSRF protection, and secure API communication.

### 7.2. Performance Optimization

  * **Optimization Analysis Focus:** Identify bottlenecks/inefficiencies. Suggest improvements considering: Time complexity, Memory usage, Reduction of unnecessary operations, Parallelization/Asynchronous ops, and Caching strategies.
  * **Optimization Output:** 1. Explain expected impact. 2. Provide code snippet. 3. Discuss trade-offs (e.g., readability). 4. Recommend language-specific practices/libraries. 5. Suggest profiling tools.
  * **Resource-Intensive Operations Prompt:** Suggest optimization focusing on: Time complexity, Memory usage, Caching/Memoization, and Parallel processing.
  * **Staying Updated:** Request an update on the latest best practices for `[language/framework]` focusing on: Security enhancements, Performance optimization, New language features, and Deprecated practices.

### Details:
### For Security Testing

* **Prompt Template:**
    ```markdown
    Please review the following code for potential security vulnerabilities:
    [Paste your code]

    Consider common security issues such as:
    1. Injection flaws
    2. Broken authentication
    3. Sensitive data exposure
    4. XML external entities (XXE)
    5. Broken access control
    6. Security misconfigurations
    7. Cross-site scripting (XSS)

    For each vulnerability found, explain the risk and suggest secure coding practices to mitigate it.
    ```

### Using AI for Test Data Generation

* **Prompt Template:**
    ```markdown
    I need to generate test data for the following database schema:
    [Paste your schema here]

    Please help me create a test data generation plan:
    1. Suggest appropriate ranges or types of values for each field
    2. Provide SQL or script to generate a diverse set of test data, including:
        - Normal cases
        - Edge cases
        - Invalid data to test error handling
    3. Ensure referential integrity is maintained for related tables
    4. Include any specific scenarios or data patterns crucial for thorough testing

    The test data should be comprehensive enough to cover various testing scenarios while remaining manageable in size.
    ```

### Security Best Practices and Code Optimization with AI

### Enhance Code Security
* **Prompt Template:**
    ```markdown
    Please perform a security audit on the following code:
    [Paste your code here]

    In your audit, please:
    1. Identify any potential security vulnerabilities, including but not limited to:
        - Injection flaws (SQL, NoSQL, OS command injection, etc.)
        - Broken authentication
        - Sensitive data exposure
        - XML External Entities (XXE)
        - Broken access control
        - Security misconfigurations
        - Cross-Site Scripting (XSS)
        - Insecure deserialization
        - Using components with known vulnerabilities
        - Insufficient logging & monitoring
    2. For each vulnerability found:
        - Explain the potential impact
        - Suggest a fix or mitigation strategy
        - Provide a code snippet demonstrating the fix, if applicable
    3. Suggest any general security improvements or best practices that could be applied to this code.
    4. Recommend any security-related libraries or tools that could help improve the overall security posture of the application.

    This comprehensive prompt usually gives me a solid starting point for hardening my application’s security.
    ```

#### Optimizing Performance with AI Suggestions

* **Prompt Template:**
    ```markdown
    Please analyze the following code for performance optimization opportunities:
    [Paste your code here]

    In your analysis, please:
    1. Identify any performance bottlenecks or inefficient operations
    2. Suggest optimizations, considering:
        - Time complexity improvements
        - Memory usage optimization
        - Reduction of unnecessary operations or function calls
        - Potential for parallelization or asynchronous operations
        - Caching strategies
    3. For each suggestion:
        - Explain the expected performance impact
        - Provide a code snippet demonstrating the optimization
        - Discuss any potential trade-offs (e.g., readability, maintainability)
    4. Recommend any language-specific performance best practices or libraries that could be beneficial
    5. Suggest any profiling tools or techniques that could help further analyze the performance in a real-world scenario
    ```

#### Staying Updated on Best Practices

* **Prompt Template:**
    ```markdown
    Please provide an update on the latest best practices for [your language/framework] as of [current date], focusing on:
    1. Security enhancements and newly discovered vulnerabilities
    2. Performance optimization techniques
    3. New language features or libraries that could improve security or performance
    4. Any deprecated practices that should be avoided

    For each point, please explain:
    - What the practice or vulnerability is
    - Why it's important
    - How to implement or mitigate it in practical terms
    ```

### Prompt Ideas for Security and Optimization Tasks

#### For analyzing potential SQL injection vulnerabilities

* **Prompt Template:**
    ```markdown
    Please review the following database interaction code for potential SQL injection vulnerabilities:
    [Paste your database interaction code]

    For each vulnerability found:
    1. Explain how it could be exploited
    2. Provide a secure alternative implementation
    3. Suggest any relevant security libraries or techniques specific to our database system
    ```

#### For optimizing resource-intensive operations

* **Prompt Template:**
    ```markdown
    The following function is causing performance issues in our application:
    [Paste your function]

    Please suggest ways to optimize this function, considering:
    1. Time complexity improvements
    2. Memory usage optimization
    3. Potential for caching or memoization
    4. Opportunities for parallel processing, if applicable

    For each suggestion, provide a brief explanation of the expected performance gain and any potential trade-offs.
    ```

#### For improving front-end security

* **Prompt Template:**
    ```markdown
    Please review the following front-end code for security best practices:
    [Paste your front-end code]

    Consider aspects such as:
    1. Cross-Site Scripting (XSS) prevention
    2. Secure handling of sensitive data
    3. Protection against Cross-Site Request Forgery (CSRF)
    4. Secure communication with back-end APIs

    Provide specific recommendations for improving the security of this code, including any relevant libraries or techniques for our front-end framework.
    ```
-----

## 8\. Version Control and Collaboration

| Task | Key Requirements |
| :--- | :--- |
| **Commit Messages** | 1. Concise subject line (50 chars or less). 2. Detailed body (wrap at 72 chars). 3. Follow best practices. 4. Include relevant issue numbers. 5.The commit message should be informative enough that team members can understand the changes without having to look at the code. |
| **Resolving Merge Conflicts** | AI should: 1. Analyze both versions. 2. Suggest the best combination method. 3. Provide the resolved code. 4. Explain the reasoning. 5. Advise on side effects. |
| **Enhancing Pull Request Reviews** | Identify issues/improvements, Check coding standards, Suggest needed tests, Point out documentation gaps, and Highlight security/performance concerns. |
| **Creating a .gitignore** | Exclude common system/IDE files, ignore language-specific artifacts/dependencies, and **ensure no sensitive info is committed**. |
| **Writing Release Notes** | Summarize key new features, list breaking changes/migration steps, mention bug fixes/performance improvements, and thank contributors. Tone should be professional but friendly. |
| **Improving Branch Naming** | Suggest a strategy that clearly indicates work type (feature, bugfix, etc.), includes ticket numbers, and is concise/descriptive. |

### Details:
### Commit Messages

* **Criteria for Informative Commit Messages:**
    1.  Concise subject line (50 chars or less).
    2.  Detailed body (wrap at 72 chars).
    3.  Follow best practices (e.g., use imperative mood).
    4.  Include relevant issue numbers (e.g., `[#123]`).
    5.  The commit message should be informative enough that team members can understand the changes without having to look at the code.

### Resolving Merge Conflicts with AI Assistance

* **Prompt Template:**
    ```
    I'm facing the following merge conflict:
    [Paste the conflicting code sections]

    The feature I'm trying to merge aims to: [Briefly describe the feature's purpose]

    Please help me resolve this conflict by:
    1. Analyzing both versions of the code
    2. Suggesting the best way to combine the changes
    3. Providing a resolved version of the code
    4. Explaining the reasoning behind the suggested resolution

    Also, please advise if there are any potential issues or side effects I should be aware of after this merge.
    ```

### Enhancing Pull Request Reviews

* **Prompt Template:**
    ```
    Please review the following pull request:
    [Paste the PR diff or provide a summary of changes]

    In your review, please:
    1. Identify any potential issues or improvements in the code
    2. Check for adherence to our project's coding standards and best practices
    3. Suggest any tests that might be needed
    4. Point out any parts of the code that might need more documentation
    5. Highlight any security or performance concerns

    For each point, provide a brief explanation and, if applicable, suggest how it could be addressed.
    ```

### Prompt Ideas for Version Control and Collaboration Tasks

#### For creating a `.gitignore` file:
* **Prompt Template:**
    ```
    I'm starting a new [language/framework] project. Please help me create a comprehensive .gitignore file that:
    1. Excludes common system and IDE files
    2. Ignores language-specific build artifacts and dependencies
    3. Ensures no sensitive information (like API keys) is accidentally committed

    Please provide explanations for any non-obvious entries.
    ```

#### For writing release notes:
* **Prompt Template:**
    ```
    We're preparing to release version [X.Y.Z] of our software. Based on the following commit history since our last release:
    [Paste relevant commit history]

    Please help me draft release notes that:
    1. Summarize key new features
    2. List any breaking changes and migration steps
    3. Mention bug fixes and performance improvements
    4. Thank contributors (if applicable)

    The tone should be professional but friendly, suitable for both technical and non-technical readers.
    ```

#### For improving branch naming conventions:
* **Prompt Template:**
    ```
    Our team needs a consistent branch naming convention. Please suggest a branch naming strategy that:
    1. Clearly indicates the type of work (e.g., feature, bugfix, hotfix)
    2. Includes relevant ticket or issue numbers
    3. Is concise but descriptive

    Provide examples for different scenarios and explain the rationale behind the suggested convention.
    ```

-----

## 9. Sources

* **4 Must-Know AI Prompt Strategies for Developers**
  [Link to Article](https://reykario.medium.com/4-must-know-ai-prompt-strategies-for-developers-0572e85a0730)
* **AI-Assisted Software Development: A Comprehensive Guide with Practical Prompts (Part 1-3)**
  [Link to Article](https://aalapdavjekar.medium.com/ai-assisted-software-development-a-comprehensive-guide-with-practical-prompts-part-1-3-989a529908e0)
  
