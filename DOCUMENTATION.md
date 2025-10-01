Standardized templates are crucial for team efficiency, quality control, and reducing cognitive load, which is exactly what a pragmatic Principal Engineer should champion.

Here are the templates, designed to be concise yet comprehensive for high-velocity software development.

---

## 1. Merge Request (MR) / Pull Request (PR) Documentation Template

This template ensures every MR provides reviewers with the necessary context, testing instructions, and technical details to approve the change quickly and confidently.

| Section | Title | Description / Content |
| :--- | :--- | :--- |
| **I.** | **Summary & Motivation** | A concise, one-sentence description of *what* this MR does. State *why* the change is needed (e.g., fixes a critical bug, implements a key feature, addresses technical debt). |
| **II.** | **Related Issues** | List all associated Jira tickets, Epics, or other related MRs. **Example:** `JIRA: PROJECT-123, PROJECT-456` |
| **III.** | **Technical Changes** | Briefly summarize the key technical changes. **Focus on:** architectural impact, new dependencies, database schema changes, or any non-obvious implementation details. *Keep this to 3-5 bullet points max.* |
| **IV.** | **Testing / Review Notes** | **The most critical section for reviewers.** Detail the exact steps a reviewer should take to verify the changes work as intended. |
| | **Test Steps:** | 1. **Setup:** (e.g., pull new branch, run `npm install`) |
| | | 2. **Execution:** (e.g., Navigate to `/settings`, click 'Save') |
| | | 3. **Expected Result:** (e.g., A success banner appears and the value updates in the DB.) |
| **V.** | **Screenshots / Videos** | (Optional but highly recommended for UI changes) Include screenshots or a short Loom video demonstrating the new feature or the bug fix. |
| **VI.** | **Risk Assessment** | What is the potential impact of this change? (e.g., Low, Medium, High). Mention any areas of the codebase that might be indirectly affected. |

---

## 2. Jira Documentation Template (Bug Fix)

This template is for a **Bug Fix** ticket, ensuring comprehensive data capture for triage, reproduction, and post-mortem analysis.

| Section | Title | Description / Content |
| :--- | :--- | :--- |
| **I.** | **Summary** | (Jira Title) **[Area] Short description of the unexpected behavior.** (e.g., [Checkout] Payment fails when item quantity is zero.) |
| **II.** | **Environment & Details** | **App Version:** (e.g., v3.4.1) |
| | | **OS / Browser:** (e.g., Chrome 120 on macOS) |
| | | **User / Account Type:** (e.g., Standard User, Admin) |
| | | **Severity:** (e.g., Blocker, Critical, Major, Minor, Trivial) |
| **III.** | **Steps to Reproduce** | **Clear, numbered list of actions leading to the bug.** This must be repeatable. |
| | | 1. Go to [https://unemployment.oregon.gov/](https://unemployment.oregon.gov/). |
| | | 2. Perform [Action 1]. |
| | | 3. Perform [Action 2]. |
| | | 4. (The error occurs here.) |
| **IV.** | **Expected Behavior** | Describe what *should* happen when the steps are followed. |
| **V.** | **Actual Behavior** | Describe what *actually* happens (the bug). Include any specific error messages, screenshots, or screen recordings. |
| **VI.** | **Technical Context (Dev Only)** | (To be filled in by the dev who triages/fixes it) |
| | | **Root Cause:** (e.g., Missing null check in `WidgetFactory.java:50`) |
| | | **Logs/Trace:** (Paste relevant log snippets or stack traces here.) |

---

## 3. Jira Documentation Template (New Feature / Story)

This template focuses on user value, acceptance criteria, and technical feasibility for a new feature or substantial enhancement.

| Section | Title | Description / Content |
| :--- | :--- | :--- |
| **I.** | **User Story** | **As a** [Type of User], **I want to** [Goal/Action], **so that** [Benefit/Value]. |
| **II.** | **Goals & Business Value** | What is the primary objective? (e.g., Increase conversion rate by 5%, reduce customer support tickets.) |
| **III.** | **Acceptance Criteria (AC)** | **The "Definition of Done."** Clear, verifiable conditions that must be met for the story to be considered complete and shippable. *Use the "GIVEN, WHEN, THEN" format where possible.* |
| | | **Example AC 1:** GIVEN the user is logged in, WHEN they navigate to the new Settings tab, THEN they shall see fields for Name and Email pre-populated with their current data. |
| **IV.** | **Design / Mockups** | Link to the specific Figma/Sketch/InVision file for the feature. |
| **V.** | **Technical Notes** | High-level technical considerations or constraints (e.g., Requires a new index in Postgres, API endpoint `POST /api/widgets/new` must be created, requires integration with AWS SQS). |
| **VI.** | **Dependencies** | List any external teams, services, or other Jira tickets that must be completed *before* work on this ticket can start. |
