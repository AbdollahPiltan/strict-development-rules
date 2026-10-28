# Strict Development Rules

Reusable engineering policy for secure, maintainable, resource-efficient software.

## Scope and interpretation

Apply these rules throughout design, implementation, review, and delivery of software that adopts this policy. Within this documentation-only repository, only rules relevant to documentation and maintenance apply; do not create application infrastructure to satisfy irrelevant rules.

**MUST** defines an acceptance requirement when a rule applies. **SHOULD** defines a default that may be changed for a recorded reason. **MAY** describes an option. Follow higher-priority instructions and explicit project requirements. Record material exceptions with the rule ID, reason, impact, and mitigation. Do not interpret this document as permission to deploy, publish, disclose secrets, or change unrelated systems.

“Strict” describes adherence to applicable engineering rules; it is independent of any language's strict-mode setting. Prefer the smallest sound implementation. Do not introduce an architecture, dependency, test suite, or service solely to satisfy a rule that does not apply.

## Autonomous Development Policy

### Goal

Complete each assigned task end-to-end with minimal unnecessary model, context, and tool usage. Efficiency MUST NOT reduce correctness, security, error handling, or required verification.

### Context

- **AUT-01 — Documented requirements:** Use existing project specifications, architecture, and acceptance criteria as the source of truth, subject to instruction priority. Do not ask questions already answered there; clarify only material gaps or conflicts that cannot be resolved from the available context.
- **AUT-02 — Focused inspection:** Inspect task-relevant files first and expand only when dependencies or findings require it. Read architecture and database documents when relevant. Avoid repeated full-repository exploration and re-reading unchanged files; refresh context when files change, previous context is unavailable, or a finding needs confirmation.

### Development

- **AUT-03 — Complete, scoped work:** Follow existing architecture and conventions, reuse suitable components, and implement all acceptance criteria. Avoid unrelated refactoring and speculative abstractions. Apply the relevant engineering and security rules below throughout implementation.

### Dependencies

- **AUT-04 — Reuse before adding:** Check installed packages before adding dependencies. Prefer existing compatible libraries and do not add packages solely for trivial utilities.

### Verification

- **AUT-05 — Proportionate checks:** Run relevant tests or documentation checks first. Run broader checks when the change, repository requirements, failures, or remaining risks warrant them. Prefer concise diagnostic output and avoid repeated full builds without new justification. Never skip required verification to save tokens or time.
- **AUT-06 — Diagnose before retrying:** Fix failures introduced by the task. Investigate repeated failures before another attempt; do not retry unchanged actions without new diagnostics or a changed condition. Distinguish existing failures from task regressions. If a blocker remains unresolved, stop dependent work and report the issue instead of making speculative changes; finish independent authorized work where possible.

### Git

- **AUT-07 — Feature branches:** Work on a dedicated feature branch. Never force-push or push directly to `main` or the repository's default branch. Deliver default-branch changes through the repository's pull-request process.
- **AUT-08 — Verified commits:** Inspect the final diff before committing. Commit only intended, verified changes; never include secrets, generated junk, or unrelated user changes. Commit and push to the feature branch when task authorization and repository permissions allow it. If verification, commit, or push is blocked, report the exact incomplete step.

### Communication

- **AUT-09 — Autonomous execution:** Proceed autonomously on documented tasks within the authorized scope. Avoid unnecessary progress messages, lengthy routine explanations, and excessive terminal output. Keep required updates and material findings, blockers, or decisions clear and concise.
- **AUT-10 — Final report:** State task status, changed files, verification passed/failed/not run, commit hash and branch, and remaining blockers, if any. Do not claim completion when required work remains.

### Project startup and checkpoints

- **AUT-11 — Reusable startup:** For a new project or incomplete setup, use the project-start guide to establish specifications, Git identity, the intended remote, and authorized repository settings. Keep product decisions and progress in the project's `PROJECT.md` or existing equivalent; do not duplicate policy or reload startup guidance for every routine task.
- **AUT-12 — Milestone commits:** Create one or more coherent, verified commits for each completed milestone, with meaningful messages describing the scope and outcome. Follow existing commit conventions, or use `<type>(<scope>): <outcome>`. Push authorized checkpoints to the feature branch and record their references and checks; avoid empty commits and self-referential commit-hash updates.
- **AUT-13 — Recoverable history:** Preserve checkpoint traceability through the chosen PR merge strategy. Prefer new revert commits for undoing published changes, inspect dependencies and merge parents, and never force-push shared rollback history. Git checkpoints do not restore databases, external effects, or deployed state; document compatible recovery steps where relevant.

### Persistent context and project graph

- **CTX-01 — Context ownership:** Use `MEMORY.md` or an existing equivalent for a compact working snapshot, `PROJECT.md` or existing specifications for requirements and milestone history, and `docs/PROJECT-GRAPH.md` or an equivalent map for navigation. Reference these sources instead of duplicating their contents; load only the relevant sections after the applicable instructions.
- **CTX-02 — Freshness before reuse:** Compare the snapshot's recorded repository, branch, and inspected commit with current Git state, including staged, unstaged, and untracked work. A missing anchor, changed branch, or relevant code/configuration/dependency change requires scoped reconciliation. Do not silently trust stale memory or restart full-repository exploration when a focused refresh is sufficient.
- **CTX-03 — Verification provenance:** Record check commands, outcomes including failed/not run, the actual tested commit or explicit dirty-tree scope, relevant environment, and evidence references. Do not describe a baseline commit as tested when checks included uncommitted edits. Earlier passing results do not establish correctness after relevant changes; run required checks and record what remains unverified.
- **CTX-04 — Bounded maintenance:** Update the snapshot at meaningful checkpoints, blockers, and handoffs; update affected graph entries only when structure, paths, dependencies, or check mappings change. Keep summaries small and point to commits, PRs, or detailed evidence. Do not store transcripts, full logs, secrets, or copied untrusted instructions, and do not create commit loops to record a snapshot's own hash.
- **CTX-05 — Evidence-backed graph:** Map verified modules, entry points, important paths, dependencies, and relevant checks. Label planned or unknown relationships explicitly; templates are not facts about the project. Use the graph to guide inspection, not as proof that no other files or tests are affected. No graph database, vector store, or additional service is required by this policy.

### Execution workflow

Use this sequence for the assigned task, or the next documented task when instructed to continue:

1. Identify scope, applicable specifications, and acceptance criteria.
2. Reconcile the working snapshot with Git, consult relevant graph entries, and inspect the necessary files; expand context only as needed.
3. Implement the complete change under existing conventions and applicable rules.
4. Confirm existing dependencies meet the need before adding any package.
5. Run targeted verification and any required broader checks.
6. Diagnose and fix task-related failures; report unresolved blockers.
7. Review the final diff against scope, security, and acceptance criteria.
8. Refresh the working snapshot and any affected graph entries, commit and push verified changes under AUT-07 and AUT-08, and provide the concise final report with checkpoint references.

## Project decisions

Complete this table in an adopting project. An unset value is an open decision, not an established requirement. Review repository conventions before filling it in; do not invent performance targets or deployment facts.

| Decision | Project value |
| --- | --- |
| Product scope and critical workflows | To be defined |
| Languages, frameworks, and supported versions | To be defined |
| Naming, formatting, and module conventions | To be defined |
| Deployment model and controlled API entry point | To be defined, or not applicable with reason |
| Data sensitivity, roles, and tenant boundaries | To be defined |
| API contracts and compatibility policy | To be defined, or not applicable with reason |
| Expected traffic, concurrency, and dataset sizes | To be defined |
| Latency, error-rate, memory, CPU, and query budgets | To be measured and agreed |
| Timeouts, request limits, retry limits, and queue capacity | To be defined where applicable |
| Cache scope, freshness, and invalidation requirements | To be defined, or not applicable with reason |
| Required verification and CI commands | To be defined |
| Recovery objectives, backups, and rollback method | To be defined where applicable |

## Architecture and responsibilities

- **ARC-01 — Cohesion:** Each function MUST perform one coherent task, each class MUST have a clear responsibility, and each file MUST cover a coherent topic. Related helpers MAY share a file; arbitrary file or line limits are not a substitute for cohesion.
- **ARC-02 — SOLID:** Apply single responsibility, open/closed design, substitutability, interface segregation, and dependency inversion where they improve real boundaries. Do not create an interface for every implementation by default.
- **ARC-03 — Boundaries:** Business rules MUST be separable from transport, persistence, UI, and external-service details. Request handlers SHOULD coordinate work rather than contain unrelated business and storage logic.
- **ARC-04 — Dependencies:** Avoid dependency cycles, hidden dependencies, and mutable global state. Make significant dependencies and side effects explicit.
- **ARC-05 — Simplicity:** Prefer KISS, YAGNI, and clear code. Reuse repeated knowledge; do not merge unrelated concepts simply because their current code looks similar.
- **ARC-06 — Infrastructure:** A new service, gateway, queue, distributed cache, or abstraction MUST have a concrete need and a considered operating cost. A modular monolith is a valid architecture.

## Names, files, and folders

- **ORG-01 — Names:** Names MUST communicate purpose. Use meaningful verbs for actions and meaningful nouns for types; make boolean meaning clear. Follow the language's established naming conventions consistently.
- **ORG-02 — Files:** File names MUST match their main responsibility. Remove dead code, unused imports, and abandoned commented-out implementations.
- **ORG-03 — Structure:** Group related capabilities together and keep module ownership clear. Avoid unrelated contents in generic `utils`, `common`, or manager modules and avoid needless nesting.
- **ORG-04 — Reading order:** Follow established repository conventions. Otherwise, organize imports, related declarations, the public entry point, and private details in a predictable reading order, keeping helpers near their use.
- **ORG-05 — Explanation:** Comments SHOULD explain reasons, constraints, or surprising behavior. Public contracts and material side effects MUST be understandable without guessing.

## API design and entry points

- **API-01 — Controlled ingress:** Public APIs MUST have a controlled entry point appropriate to the deployment. A platform ingress or reverse proxy MAY satisfy this need; a separate gateway service is not always necessary.
- **API-02 — Responsibility:** Keep domain logic out of the gateway. Authentication MAY be centralized, but protected operations MUST enforce authorization at the service or resource boundary.
- **API-03 — Contracts:** Document inputs, outputs, errors, pagination, and compatibility behavior. Use an appropriate schema or contract format when the project benefits from one.
- **API-04 — Semantics:** Use protocol methods and status codes correctly. Read operations MUST NOT mutate business state; failures MUST NOT be disguised as success.
- **API-05 — Bounds:** Bound request bodies, collection sizes, page sizes, execution time, and concurrent work. Long-running operations MUST have a defined completion or status mechanism.
- **API-06 — Compatibility:** Breaking changes MUST have an explicit migration strategy. Do not create oversized, incoherent endpoints merely to reduce request counts.

## Security

- **SEC-01 — Validation:** Validate untrusted inputs at server-side boundaries for type, shape, length, and range. Client-side validation does not replace this control.
- **SEC-02 — SQL injection:** Bind data values through parameterized queries. Select dynamic identifiers and ordering tokens from application-owned allowlists. Neither ORM use nor manual escaping guarantees safety.
- **SEC-03 — Authorization:** Check access to the operation and the specific resource, including ownership and tenant boundaries. A client-supplied identifier is not proof of permission.
- **SEC-04 — Least privilege:** Default protected access to denial. Give users, services, and database identities only necessary permissions; do not expose privileged credentials to clients.
- **SEC-05 — Contextual defenses:** Where relevant, implement output encoding against XSS, CSRF protection for cookie-authenticated actions, SSRF controls for outbound URLs, and defenses against path traversal and command injection.
- **SEC-06 — Secrets:** Keep secrets out of repositories, client bundles, logs, and error output. Use managed configuration or secret storage appropriate to the environment.
- **SEC-07 — Credentials:** Use established libraries for password hashing and cryptography. Configure sessions, cookies, tokens, HTTPS, and CORS appropriately; CORS is not authorization.
- **SEC-08 — Disclosure:** Public errors MUST avoid internal details and sensitive data. Logs MUST avoid credentials and unnecessary personal data while retaining useful diagnostic context.
- **SEC-09 — Files:** Where uploads exist, validate size and expected content, generate safe storage names, and use an appropriate storage and access policy.

## Availability and abuse resistance

- **AVL-01 — Rate limits:** Apply limits appropriate to identity, endpoint cost, and deployment. Give expensive and authentication-related operations additional protection where needed.
- **AVL-02 — Capacity:** Bound connections, concurrency, queues, and execution time. Define backpressure or overload responses instead of accepting unlimited work.
- **AVL-03 — Expensive inputs:** Bound work caused by regexes, nested payloads, decompression, complex queries, and other attacker-controlled inputs before performing expensive processing.
- **AVL-04 — DDoS layers:** Address volumetric DDoS at the network or provider layer when the exposure requires it. Application rate limiting alone cannot prevent upstream bandwidth saturation.
- **AVL-05 — Trusted proxies:** Trust forwarded client-identity headers only from configured trusted proxies. Prevent header spoofing from bypassing limits or security decisions.
- **AVL-06 — Failure behavior:** Define how relevant dependencies fail, how excess load is rejected, and how metered-service usage is bounded. Use circuit breakers where justified by the failure model.

## Requests, responses, and repeated work

- **EFF-01 — Useful work:** Eliminate unnecessary repeated requests, responses, computations, and writes while preserving correctness, required freshness, and authorization.
- **EFF-02 — Duplicate reads:** Coalesce identical in-flight reads where safe. Keys MUST include the relevant parameters and access scope; sharing results MUST NOT cross authorization boundaries.
- **EFF-03 — UI requests:** Prevent render/effect loops and duplicate event submissions. Debounce appropriate interactive searches and cancel obsolete work where useful.
- **EFF-04 — Cancellation:** Propagate cancellation to downstream work when supported. A client disconnect or aborted browser request does not automatically stop server or database work.
- **EFF-05 — Caching:** Define cache keys, authorization scope, TTL, capacity, and invalidation. Protect against cache stampedes where relevant. Use HTTP caching or conditional requests for suitable content.
- **EFF-06 — Retries:** Retry only eligible failures and operations safe to repeat, with bounded attempts, backoff, and jitter. Respect retry guidance such as `Retry-After`; avoid multiplicative retries across layers.
- **EFF-07 — Idempotency:** Protect sensitive repeatable operations against duplicate effects with appropriate idempotency and atomic persistence. Do not assume a network provides exactly-once delivery.
- **EFF-08 — Freshness:** Choose polling frequency or push delivery based on freshness requirements and total cost. Fast fixed polling, WebSockets, and queues are not universal defaults.
- **EFF-09 — Payloads:** Return necessary fields and bounded collections. Use batching when it improves the workload, with explicit size limits and partial-failure behavior.

## Database and CRUD

- **DB-01 — Necessary operations:** Remove redundant reads and writes without sacrificing integrity, authorization, or required transactional behavior.
- **DB-02 — Query shape:** Identify N+1 queries and per-item database calls over growing datasets. Use suitable joins, loading strategies, or bounded batches.
- **DB-03 — Retrieval:** Select necessary fields and paginate growing collections with stable ordering. Consider cursor pagination when the access pattern supports it.
- **DB-04 — Indexes:** Choose indexes using real query patterns and execution plans. Account for write and storage costs; indexing every column is not a general solution.
- **DB-05 — Writes:** Bound bulk work and avoid unnecessary no-op updates. Use atomic operations, constraints, and appropriate concurrency control to prevent races.
- **DB-06 — Transactions:** Keep transactions short and correctly scoped. Avoid long network calls inside them; handle external side effects with an explicit consistency strategy.
- **DB-07 — Connections:** Configure connection pools and query timeouts for the total deployment capacity. Do not create a new independent pool for every request.
- **DB-08 — Migration:** Make migrations reviewable and compatible with the deployment sequence. Provide recovery and backup/restore verification proportionate to data risk.

## CPU, memory, loops, and background jobs

- **RES-01 — Bounded execution:** Loops and recursion MUST have an appropriate termination or cancellation condition. Long-lived workers MUST wait appropriately, support shutdown, and limit retries.
- **RES-02 — Concurrency:** Bound spawned tasks, promises, worker counts, and queue depth. Async execution alone does not limit resource consumption.
- **RES-03 — Memory:** Stream or chunk large inputs where suitable. Bound caches and buffers; release connections, files, timers, and listeners appropriately.
- **RES-04 — Heavy work:** Assess CPU-heavy work in request paths or event loops. Move it to bounded workers or jobs when justified, with defined failure and completion behavior.
- **RES-05 — Total cost:** Moving work to a queue does not eliminate its cost. Measure processing, duplicate jobs, backlog, and downstream load together.
- **RES-06 — Evidence:** Agree on relevant latency percentiles, error rates, throughput, query counts, CPU, and memory budgets for a representative workload. Support optimization claims with comparable before/after measurements.

## Verification and operations

- **VER-01 — Automated checks:** Use applicable formatting, linting, type/compiler checks, dependency review, and secret scanning. Keep dependencies necessary, maintained, and reproducible through the ecosystem's appropriate versioning and lock mechanisms.
- **VER-02 — Meaningful tests:** Test important behavior, errors, access boundaries, retries, and concurrency according to risk. Do not add tests that merely mirror implementation or target an arbitrary coverage percentage.
- **VER-03 — Scope of verification:** Use integration tests for relevant API/data boundaries and authorized load tests for meaningful performance risks. Documentation-only edits do not require a new application test suite.
- **VER-04 — Honest reporting:** Run required relevant checks and report their actual results. Clearly identify checks that could not run, remaining failures, and unverified assumptions.
- **OPS-01 — Observability:** Provide useful structured logs, request correlation, metrics, and alerts appropriate to the service. Bound log volume and metric-label cardinality; avoid sensitive data.
- **OPS-02 — Lifecycle:** Define appropriate readiness, health checks, graceful shutdown, environment configuration, recovery, and rollback behavior for deployed services.
- **UX-01 — User states:** Where a UI exists, handle loading, empty, error, repeated-submit, and slow-network states. Verify applicable accessibility and responsive behavior.

## Acceptance checklist

Use the rule IDs above as the detailed reference. Before completing a change, verify that:

- [ ] The requested behavior is complete and responsibilities, names, and module boundaries are clear.
- [ ] Applicable input, authorization, data disclosure, and abuse controls have been considered.
- [ ] The change does not introduce unbounded work, duplicate effects, or unnecessary requests and queries.
- [ ] Relevant checks ran, and performance claims have measurements where applicable.
- [ ] Contracts, configuration, and documentation reflect the resulting behavior.
- [ ] Material exceptions have a rule ID, reason, impact, and mitigation.
- [ ] The delivery report states the outcome, verification, and material remaining limitations.

## Primary security references

- [OWASP SQL Injection Prevention](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)
- [OWASP Denial of Service](https://cheatsheetseries.owasp.org/cheatsheets/Denial_of_Service_Cheat_Sheet.html)
- [OWASP REST Security](https://cheatsheetseries.owasp.org/cheatsheets/REST_Security_Cheat_Sheet.html)
- [Microsoft REST API Guidelines](https://github.com/microsoft/api-guidelines)

## License notice — retain when copying this file

MIT License

Copyright (c) 2026 Strict Development Rules contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
