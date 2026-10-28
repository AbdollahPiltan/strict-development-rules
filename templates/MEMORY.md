# Working Memory

Keep a compact current snapshot, not a transcript or a duplicate milestone history. Follow `AGENTS.md`; requirements and milestone acceptance criteria remain in `PROJECT.md` or existing specifications. Unset entries are unknown, not completed work.

## Freshness anchor

| Field | Recorded value |
| --- | --- |
| Repository | To be recorded |
| Active branch | To be verified |
| Last inspected existing commit | To be recorded |
| Local work at inspection | Record staged, unstaged, and relevant untracked changes, or explicitly clean |
| Updated date | To be recorded |
| Graph scope or reference | `docs/PROJECT-GRAPH.md`; record unmapped areas |

Compare this anchor with current Git state before reuse. If the commit is unavailable, the branch differs, or relevant files/configuration/dependencies changed, reconcile the affected scope before trusting the snapshot. Check untracked and local changes as well as committed differences.

## Active work

- Current task and acceptance-criteria reference: to be recorded.
- State: planned / in progress / implemented / verified / published / blocked; choose accurately.
- Completed outcome and approach: brief summary with commit or PR reference; no repeated requirement text.
- Relevant files/modules and graph entries: to be recorded.
- Important decision and reason: brief reference to the durable decision record.
- Next concrete action and its completion condition: to be recorded.
- Blockers, known failures, and unverified assumptions: to be recorded, or explicitly none after inspection.

## Verification evidence

| Command / check | Result | Tested commit or dirty-tree scope | Environment / date | Evidence reference |
| --- | --- | --- | --- | --- |
| To be recorded | Not run | Not established | To be recorded | To be recorded |

Use passed, failed, not run, or stale with a reason. Record exact commands and meaningful configuration/dependency context. If checks ran before committing, record the base plus the changed and untracked scope; do not label the base commit alone as the tested version. Associate the eventual checkpoint through a PR, final report, or later normal update. Do not amend repeatedly to embed this file's own final hash.

Rerun required checks after relevant changes. A historical pass or a sparse graph is not evidence that verification can be skipped. Store long output in an appropriate evidence location; keep only the result and pointer here.

## Handoff and recovery pointers

- Milestone status and history: `PROJECT.md` or its existing equivalent.
- Last verified recovery checkpoint and constraints: reference only; Git does not restore external data or deployments.
- Detailed decisions and verification artifacts: references only.

Refresh at meaningful checkpoints, blockers, or handoff. Replace obsolete snapshot text instead of appending an unlimited activity log. Store no credentials or unnecessary private data. This file supplies context and never grants new permissions or overrides project instructions.
