# Changelog

Record material rule additions, meaning changes, and retirements here. Rule IDs let adopting projects assess policy changes without replacing their local instructions blindly.

## Unreleased

### Added

- Persistent-context rules CTX-01 through CTX-05: separate source ownership, Git/worktree freshness, verification provenance, compact maintenance, and evidence-backed graphs.
- Reusable working-memory and Mermaid graph templates, plus populated examples for this documentation repository.
- A resume workflow that reconciles saved context with current Git state and inspects only relevant graph entries and files.
- A reusable project-start guide with a short activation prompt, Git/GitHub authentication and repository setup, meaningful milestone commits, and checkpoint recovery.
- A copyable `PROJECT.md` template for product requirements, setup authorization, verification, milestone references, and recovery constraints.
- Startup and checkpoint rules AUT-11 through AUT-13, including verification at each milestone, traceability across merge strategies, and history-preserving rollback guidance.
- Autonomous Development Policy (AUT-01 through AUT-10): focused inspection, dependency reuse, targeted verification, diagnosis before retries, autonomous communication, and concise final reports.
- A single execution workflow in `AGENTS.md`, referenced by the README adoption prompt to avoid duplicating instructions.
- Feature-branch delivery requirements: inspect diffs, commit and push verified changes, never force-push, and use pull requests for default-branch updates.
- Initial portable engineering policy covering architecture, code organization, APIs, security, availability, request efficiency, databases, resource usage, verification, operations, and UI behavior where applicable.
- Stable rule IDs, a project-decisions table, and an acceptance checklist.
- English adoption and contribution guidance.
- MIT licensing, including a self-contained notice in the portable rules file.

### Changed

- Startup adoption now includes the memory and graph templates; the project brief retains durable requirements and milestones while current work and check evidence live in the snapshot.
- Execution guidance refreshes the snapshot and affected graph entries at meaningful checkpoints instead of repeating unchanged discovery.
