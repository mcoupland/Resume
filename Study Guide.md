<span style="color:#8ab4f8;font-weight:600;">**Study Guide (Expanded Notes)**</span><br/>

<span style="color:#8ab4f8;font-weight:600;">**Philosophy**</span><br/>

I optimize for maintainable systems where behavior is consistent, failures are obvious, and problems are diagnosable.
When something goes wrong, I assume the system failed before the person did and look for leverage in design, tooling, and feedback loops rather than heroics.

---

<span style="color:#8ab4f8;font-weight:600;">**Leadership & Mentorship**</span><br/>

<span style="color:#8ab4f8;font-weight:600;">**Mentorship**</span><br/>
I mentor by reducing ambiguity. Clear expectations, consistent standards, and fast feedback build confidence and independence. When developers understand the system and trust it, they make better decisions without constant oversight.

<span style="color:#8ab4f8;font-weight:600;">**How**</span><br/>
- Code standards remove subjective debate.
- Automated style enforcement catches mechanical issues early.
- Version control makes change auditable and reversible.
- Build and test pipelines surface problems early and consistently.

<span style="color:#8ab4f8;font-weight:600;">**Result**</span><br/>
When this works, developers don’t feel watched. Quality comes from the system, not judgment. Work progresses predictably, and quality holds over time.

<span style="color:#8ab4f8;font-weight:600;">**Dealing with Problems**</span><br/>
When code quality is poor, I look for system gaps first. If slowness or defects depend on inputs, conventions, or context, it’s usually a design or tooling issue. Only after expectations are clear and enforced do performance conversations become necessary — and then they’re objective.

---

<span style="color:#8ab4f8;font-weight:600;">**Database**</span><br/>

<span style="color:#8ab4f8;font-weight:600;">**Performance Tuning Mindset**</span><br/>
I diagnose performance issues by pattern recognition rather than guesswork.

<span style="color:#8ab4f8;font-weight:600;">**Covering Indexes**</span><br/>
If users say “this one search is slow,” I suspect the query shape isn’t supported by an index. A covering index often resolves this without changing application code.

<span style="color:#8ab4f8;font-weight:600;">**Bad SQL Code**</span><br/>
Slowness that varies by input usually points to the query, not the database engine. Parameter sensitivity and query shape matter.

<span style="color:#8ab4f8;font-weight:600;">**Views**</span><br/>
If multiple screens or reports complain about the same slow data, I suspect duplicated query logic that belongs in a view.

<span style="color:#8ab4f8;font-weight:600;">**Missing Keys**</span><br/>
When customers say “anything that combines this data is slow,” I suspect missing or incorrect keys. Without clear relationships, the database has to work harder than it should.

<span style="color:#8ab4f8;font-weight:600;">**SQL Constructs**</span><br/>

<span style="color:#8ab4f8;font-weight:600;">**Stored Procedures**</span><br/>
Encapsulate data logic, improve reuse, and give the database optimizer stable execution boundaries.

<span style="color:#8ab4f8;font-weight:600;">**Temp Tables**</span><br/>
Useful for breaking complex queries into readable, optimizable steps when intermediate results matter.

<span style="color:#8ab4f8;font-weight:600;">**Table Variables**</span><br/>
Best for small, predictable datasets where scope and simplicity matter more than optimization.

<span style="color:#8ab4f8;font-weight:600;">**Joins**</span><br/>
Performance depends on keys, cardinality, and intent. Most “slow joins” are really unclear relationships.

<span style="color:#8ab4f8;font-weight:600;">**SSIS**</span><br/>
SSIS handles repeatable data movement, such as scheduled imports and exports, so data flows reliably without manual scripts or babysitting.

---

<span style="color:#8ab4f8;font-weight:600;">**UI Architecture**</span><br/>

<span style="color:#8ab4f8;font-weight:600;">**MVC**</span><br/>
MVC routes user actions through controllers, keeps rules in models, and limits views to rendering. Application flow is explicit and step-by-step.

<span style="color:#8ab4f8;font-weight:600;">**MVVM**</span><br/>
MVVM separates UI from logic by binding views to view models. The UI reacts automatically when data changes, reducing imperative UI code.

<span style="color:#8ab4f8;font-weight:600;">**Key Difference**</span><br/>
MVC tells the application what to do.
MVVM lets the UI respond to state.

---

<span style="color:#8ab4f8;font-weight:600;">**WPF & Client Architecture**</span><br/>

<span style="color:#8ab4f8;font-weight:600;">**WPF Styles**</span><br/>
Use ResourceDictionaries, scoping, and reuse to keep UI consistent and maintainable. Styling decisions live centrally so changes are predictable.

<span style="color:#8ab4f8;font-weight:600;">**Dependency Injection**</span><br/>
Supply dependencies externally so components remain decoupled and testable. Construction is handled by the framework, not scattered through code.

<span style="color:#8ab4f8;font-weight:600;">**Binding Modes**</span><br/>
Choose the narrowest binding mode that fits the scenario. One-way is the default; two-way bindings are used deliberately.

<span style="color:#8ab4f8;font-weight:600;">**Async vs Task.Run**</span><br/>
Async is for non-blocking I/O. Task.Run is for offloading CPU-bound work. Mixing the two without intent usually causes responsiveness issues.

<span style="color:#8ab4f8;font-weight:600;">**Threading in WPF**</span><br/>
Keep the UI thread free. Do background work off-thread and marshal back only to update UI state.

---

<span style="color:#8ab4f8;font-weight:600;">**Engineering Practices**</span><br/>

<span style="color:#8ab4f8;font-weight:600;">**Testing Philosophy**</span><br/>
Focus testing on confidence and risk reduction, not coverage metrics or ritual. Tests exist to make change safer.

<span style="color:#8ab4f8;font-weight:600;">**Regression Tests**</span><br/>
Treat automated tests as guardrails added in response to real failures. Each regression test captures a lesson learned.

---

<span style="color:#8ab4f8;font-weight:600;">**ASP.NET & Web Architecture**</span><br/>

<span style="color:#8ab4f8;font-weight:600;">**ASP.NET Core Model**</span><br/>
- HTTP request in, response out.
- Stateless by default.
- Behavior is largely configured, not hard-coded.

Important behaviors live in middleware and configuration, allowing changes without rewriting business logic.

<span style="color:#8ab4f8;font-weight:600;">**Layering**</span><br/>
- Controllers handle HTTP concerns.
- Services contain business logic.
- Repositories handle data access.

If business logic depends on HTTP concepts, it’s in the wrong place.

---

<span style="color:#8ab4f8;font-weight:600;">**WCF & Web API**</span><br/>

<span style="color:#8ab4f8;font-weight:600;">**WCF**</span><br/>
WCF allows different systems to communicate safely and consistently across machines or networks. Clients call service endpoints but share only a contract; WCF handles transport, security, and serialization.

<span style="color:#8ab4f8;font-weight:600;">**Web API**</span><br/>
Web APIs expose data and actions over HTTP using standard verbs and formats so other systems can integrate easily.

---

<span style="color:#8ab4f8;font-weight:600;">**Cloud**</span><br/>

<span style="color:#8ab4f8;font-weight:600;">**Diagnosing Cloud Issues**</span><br/>
If something breaks without a deploy and later recovers on its own, the issue is often environmental rather than code-related.

<span style="color:#8ab4f8;font-weight:600;">**Core Cloud Principles**</span><br/>

<span style="color:#8ab4f8;font-weight:600;">**Identity Over Secrets**</span><br/>
Use managed identities and roles instead of storing credentials in code or configuration.

<span style="color:#8ab4f8;font-weight:600;">**Design for Failure**</span><br/>
Assume dependencies will be slow or unavailable. Use timeouts, retries, and graceful degradation.

<span style="color:#8ab4f8;font-weight:600;">**Observability First**</span><br/>
Log and measure what matters so failures are obvious and diagnosable.

<span style="color:#8ab4f8;font-weight:600;">**Elasticity on Demand**</span><br/>
Scale up or down quickly without provisioning or maintaining hardware.

<span style="color:#8ab4f8;font-weight:600;">**Managed Reliability**</span><br/>
Leverage built-in availability, backups, and monitoring instead of running infrastructure yourself.

<span style="color:#8ab4f8;font-weight:600;">**AI**</span><br/>
It can be a very good collaborator. I’ve experimented with AI personally to understand its strengths and limits, but I haven’t used it professionally yet. My takeaway is that it’s only effective when a seasoned developer already understands the system and intent — otherwise it just generates plausible-looking code without judgment.
