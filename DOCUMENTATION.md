As a Senior Software Engineer, you know that detailed Jira documentation isn't just about ticking boxes; it's a critical tool for **code review**, **knowledge transfer** (onboarding), and **future reference** (production debugging).

The secret is to use a clear, concise structure that focuses on the *problem*, the *solution*, and the *impact*.

Below is a structured documentation template you can copy, paste, and fill in.

***

## 📄 Detailed JIRA Documentation Template

Use the standard Jira fields (like Title, Description, Comments) to organize your information. The main **Description** section should follow this template:

### Title (JIRA Summary)
**Example:** `[Backend/Feature] Implement 15-minute cache for the GET /api/v1/users/ route`

---
## 1. Problem / Context (The *Why*)

This section quickly explains the reason for the story or bug ticket. Use bold text for the primary impact.

* **Objective:** Clarify the main goal of the task.
    * *Example:* Reduce the p95 latency of the user lookup endpoint by $50\%$ and decrease the load on the database.
* **Initial Problem/Bug Report:** Describe the previous state (what was slow, what was breaking).
    * *Example:* The `/users/` route was hitting the database on every call, resulting in p95 latencies of $800$ms.

---
## 2. Implemented Solution (The *What* and *How*)

This is the core of your documentation. Be specific about the technical changes.

### 2.1. Change Overview
* Describe the solution in a high-level overview, mentioning the **design pattern** or **technology** used.
    * *Example:* Implemented a **cache-aside pattern** using **Redis** within the `User-Service`.

### 2.2. Technical Details (Where the Work Was Done)
Use a list or table to indicate exactly where the code was changed.

| File/Module | Change Type | Brief Description |
| :--- | :--- | :--- |
| `src/routes/user.ts` | **Code Change** | Added cache lookup logic before the DB call. |
| `config/redis.yml` | **Configuration** | Added a new cache key and a TTL (Time-To-Live) of $15$ minutes. |
| `infra/k8s/deployment.yml` | **Infrastructure** | Increased `CPU limit` to accommodate the new serialization library. |

### 2.3. Architectural Decisions (Why *Not* other options)
For complex tasks, justify your choices, as a Senior Engineer would.

* *Decision:* We chose cache-aside over cache-through.
* *Justification:* To keep the **service decoupled** from write-cache management and focus purely on read optimization.

---
## 3. Testing and Validation

Show that you thought about both use cases and **edge cases**.

### 3.1. Manual/Functional Validation
* **Scenario 1 (Success):** Called the API, got a `200 OK`, and the payload was correct.
* **Scenario 2 (Cache Miss/First Call):** Initial call took $800$ms (empty cache).
* **Scenario 3 (Cache Hit/Second Call):** Immediate second call took $50$ms (cache hit).

### 3.2. Automated Testing and Coverage
* **Unit Tests:** $100\%$ coverage on `src/cache-manager.ts`.
* **Integration Tests:** Added a new test that simulates **cache eviction**.
* **Edge Cases Addressed:** Verified behavior when Redis is down (implemented fallback to the database).

---
## 4. Next Steps and Follow-ups

Help the team understand what comes next.

* **Related PR:** [Link to the Pull Request on GitHub/GitLab]
* **Monitoring:** New metric **`redis_cache_hit_rate`** configured in Grafana to track effectiveness.
* **Technical Debt/Follow-up:** Implementation of **event-based cache invalidation** will be addressed in ticket `TICKET-1234`.

---
## 💡 Best Practice Tip: Use Comments for a Log

* Use Jira **comments** to record a **work log** of your efforts:
    * *Example Comment 1:* "Initially tried using library `XYZ` but it didn't support dynamic TTL. Switched to library `ABC`."
    * *Example Comment 2:* "Deploy to *staging* environment failed due to a missing environment variable. Fixed in the `fix/env-var` branch."

This structure, besides being detailed, demonstrates a **senior-level thought process** that considers not only implementation but also architecture, testing, monitoring, and the feature's long-term lifecycle.
