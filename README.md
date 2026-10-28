# Strict Development Rules

Practical engineering rules for secure, maintainable, resource-efficient software.

A documentation-only repository for developers, reviewers, and AI coding assistants. Adopt one file, adapt it to your project, and turn applicable rules into checks your team can verify.

**[Read and adopt the rules →](AGENTS.md)**

## What the rules cover

| Area | Focus |
| --- | --- |
| Architecture | SOLID, clear responsibilities, module boundaries, and appropriate complexity |
| Code organization | Meaningful names, cohesive files, and predictable folders |
| APIs | Controlled entry points, contracts, authorization, and bounded requests |
| Security | Injection prevention, secrets, access control, and safe input handling |
| Availability | DoS defenses, rate limits, timeouts, and backpressure |
| Efficiency | Fewer duplicate requests, safe caching, bounded retries, and useful payloads |
| Data | Avoiding N+1 queries, appropriate indexes, transactions, and safe migrations |
| Resources | Bounded concurrency, memory limits, cancellation, and measured performance |
| Delivery | Meaningful tests, automated checks, observability, and recovery |

## Use in a project

1. Open [AGENTS.md](AGENTS.md), select its raw view, and save it as `AGENTS.md` in your project root.
2. If your project already has an instructions file, merge the relevant rules into it. Preserve existing project-specific requirements.
3. Complete the **Project decisions** table in your copy. Agree on constraints before treating a performance budget or deployment choice as established.
4. Use the acceptance checklist during implementation and review. Configure the checks your stack supports in your own CI.

The rules file includes its MIT license notice so it can be copied as one self-contained document. Keep that notice when redistributing it.

For an AI assistant, use this instruction:

> Read AGENTS.md and follow all applicable rules throughout this task. Before editing, identify the relevant project conventions. Verify the change with proportionate checks, and report any unresolved issue or justified exception using its rule ID.

Codex supports project instructions in `AGENTS.md`; see the [official guide](https://learn.chatgpt.com/docs/agent-configuration/agents-md). For other tools, use their documented project-instruction mechanism or explicitly attach the file. Recognition of this filename is tool-specific.

## What “strict” means

Applicable rules are acceptance criteria. An exception needs a recorded reason, impact, and mitigation. Rules outside a project's scope can be marked not applicable with a reason; a static site does not need a database connection pool.

Strictness does not require a separate API gateway, microservices, a cache, or a queue in every project. Select infrastructure when the need and operating cost justify it. A Markdown policy must be supported by implementation, review, and relevant automated checks.

The rules are engineering guidance. They do not certify security, guarantee protection against every attack, or replace requirements specific to a product or deployment environment.

## Keep adoption predictable

- Record the upstream commit or release used when you adopt the file.
- Review later changes before merging them into a project; do not silently replace local instructions from a moving upstream branch.
- Keep customizations explicit. If a rule changes meaning, record the change in your local copy.
- Refer to rule IDs in reviews, such as **SEC-02** or **EFF-06**.

## Repository contents

| File | Purpose |
| --- | --- |
| [AGENTS.md](AGENTS.md) | Portable rules, project decisions, and acceptance checklist |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to propose, evaluate, and revise rules |
| [CHANGELOG.md](CHANGELOG.md) | Meaningful policy changes |
| [LICENSE](LICENSE) | MIT license |

This repository contains no application source, package dependencies, installer, or executable automation. Projects adopting the rules provide their own enforcement tools.

## Contribute

Read [CONTRIBUTING.md](CONTRIBUTING.md). Useful contributions clarify ambiguous rules, identify counterexamples, improve verifiability, or add a missing control with a primary reference.

## References

- [Microsoft REST API Guidelines](https://github.com/microsoft/api-guidelines)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
- [Node.js Best Practices](https://github.com/goldbergyoni/nodebestpractices), when using Node.js
- [System Design Primer](https://github.com/donnemartin/system-design-primer)

These are references for further study. This project is independent of their maintainers and does not reproduce their complete rule sets.

## License

[MIT](LICENSE). The repository's license covers its original content; linked third-party materials retain their own licenses.
