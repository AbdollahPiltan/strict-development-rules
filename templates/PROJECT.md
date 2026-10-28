# Project Brief and Milestones

Fill this file once, then update decisions and milestones as the project evolves. Engineering rules belong in `AGENTS.md`; reference them instead of copying them here. Replace unset values with decisions, links to existing specifications, or explicit reasons for non-applicability.

Keep the active task, current branch/worktree anchor, immediate next action, and detailed check results in `MEMORY.md`; use `docs/PROJECT-GRAPH.md` for component/check navigation. This file owns the durable requirements, milestone ledger, and recovery constraints. Reference current evidence instead of copying it between files.

## Product

| Field | Value |
| --- | --- |
| Project name | To be defined |
| Intended outcome and users | To be defined |
| Minimum useful scope | To be defined |
| Explicit exclusions | To be defined |
| Product specifications and acceptance criteria | To be defined or linked |
| Current work and next-action snapshot | `MEMORY.md` or an existing equivalent |

## Setup and authorization

| Field | Value |
| --- | --- |
| Languages, frameworks, and supported versions | To be defined from actual requirements |
| Architecture and data-model references | Link when relevant |
| Local workspace | To be defined |
| GitHub owner/repository | To be defined |
| Repository visibility | Private until a public decision is documented |
| Remote name and URL | To be verified |
| Default branch | To be verified; do not assume `main` |
| Branch convention | Dedicated feature branches; current branch recorded in the snapshot |
| Commit identity | Verified name and email/noreply; no credentials |
| Authorized repository, cloud, and publication actions | To be defined; unresolved actions are not authorized by this template |
| PR, review, and merge requirements | To be verified |

## Verification and operation

| Field | Value |
| --- | --- |
| Installation and local run instructions | To be defined |
| Relevant test, lint, type, and documentation checks | To be defined |
| CI and required review/checks | To be defined |
| Security, sensitive data, and tenant boundaries | To be defined where applicable |
| Workload and performance budgets | To be measured and agreed |
| Deployment target and authorization | To be defined, or not applicable |
| Recovery constraints and backup/restore procedure | To be defined where applicable |

## Milestones and checkpoints

Adapt milestones to the product. Each completed phase must have a coherent, verified commit and a remote checkpoint when pushing is authorized. Status values: planned, in progress, verified, published, blocked, or not applicable with a reason.

| Milestone | Acceptance criteria / specification | Status | Verification evidence reference | Commit / branch / PR |
| --- | --- | --- | --- | --- |
| Project definition | Define outcome, scope, and acceptance criteria | Planned | Pending | Pending |
| Repository bootstrap | Verify policy, identity, remote, and ignore rules | Planned | Pending | Pending |
| Minimal foundation | Define the smallest required working scaffold | Planned | Pending | Pending |
| First useful capability | Replace with the actual end-to-end workflow | Planned | Pending | Pending |
| Risk-based hardening | Define relevant security, error, and resource cases | Planned | Pending | Pending |
| Handoff | Verify run instructions and recovery notes | Planned | Pending | Pending |

Record a milestone's own commit hash in the PR/final report or the next normal update. Do not create self-referential hash updates or empty milestone commits. If a merge changes commit IDs, record integrated references where required.

## Decisions, exceptions, and blockers

| Item | Decision / evidence | Impact or next action |
| --- | --- | --- |
| No recorded items yet | Replace when a material decision or blocker exists | Keep concise |

## Recovery notes

- Last verified checkpoint and its evidence: reference the snapshot or PR; do not duplicate the run log.
- Relevant dependencies between milestone commits: to be recorded.
- Changes outside tracked files, including data or deployment state: to be recorded where applicable.
- Rollback approach and checks that establish recovery: to be recorded.

Keep credentials and private authentication material out of this file.
