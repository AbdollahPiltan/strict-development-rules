# Working Memory

## Freshness anchor

- Repository: `AbdollahPiltan/strict-development-rules`.
- Active branch: `docs/project-memory-graph`.
- Last inspected and verified implementation checkpoint: `67dbaa2dbff9d3808542c2c46cf3301759f6696c`.
- Local scope at this update: snapshot-only follow-up to that checkpoint; compare current Git status and subsequent commits before reuse.
- Updated: 2026-10-28.
- Navigation: [repository graph](docs/PROJECT-GRAPH.md).

## Active work

- Task: add the approved file-based memory and graph workflow so adopting projects can resume from a small, evidence-backed snapshot.
- State: core implementation verified and pushed at the checkpoint above. Check [PR 3](https://github.com/AbdollahPiltan/strict-development-rules/pull/3) for current publication state and follow-up verification; do not treat this snapshot as a live GitHub status cache.
- Approach: keep policy in `AGENTS.md`, durable product/milestone information in `PROJECT.md` or existing specifications, current work and check evidence in `MEMORY.md`, and navigation in `docs/PROJECT-GRAPH.md`.
- This repository's product scope is documented in [README.md](README.md); it does not require an application scaffold or a separate product-brief copy.
- Recent completed work: autonomous policy ([PR 1](https://github.com/AbdollahPiltan/strict-development-rules/pull/1)) and project startup/checkpoint guide ([PR 2](https://github.com/AbdollahPiltan/strict-development-rules/pull/2)). Use those records for history instead of copying it here.
- Next action at handoff: reconcile the current branch/commit and PR state, then follow the next assigned task. The known remaining verification gap is rendered Mermaid layout; the content changes themselves have no known blocker.

## Verification evidence

| Command / check | Result | Tested version / scope | Environment / date |
| --- | --- | --- | --- |
| `python3 work/validate_memory_graph.py` from the authoring workspace | Passed: links/anchors, 80 rule IDs/references, English text, fences, whitespace, preserved rules, license; seven shell examples and two graph structures checked | Content committed as `67dbaa2`; Git was clean immediately after committing the checked content | Python 3 and Bash; workspace-only scratch validator, not a shipped repository command / 2026-10-28 |
| `git show --format= --check 67dbaa2` | Passed | Exact committed checkpoint `67dbaa2` | Git / 2026-10-28 |
| Mermaid rendered layout | Not run: renderer unavailable | Both diagrams at `67dbaa2`; structural checks passed only | No Mermaid package installed in the authoring environment / 2026-10-28 |

The validator's scope and results are summarized in PR 3. No application runtime tests are defined for this documentation-only repository. This follow-up snapshot is not the tested implementation commit itself: its verification is associated through the PR/final report, avoiding a self-referential hash. Relevant later changes still require their own checks.

## Handoff

- No known implementation blocker. Consult PR 3 for integration status and the rendered-layout limitation above for verification scope.
- Preserve the existing policy rules and keep all repository content English.
- The reusable graph is explicitly illustrative. Its example modules do not exist in this repository.
- Use the feature-branch commits and PR as evidence references; do not create a commit loop to record this file's own final SHA.
