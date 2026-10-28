# Contributing

Help make the rules specific, usable, and verifiable across real projects.

## Scope

This is a documentation-only repository. Contributions should improve the rules, adoption guidance, or maintenance documentation. Application source, installers, executable workflows, and framework scaffolds are outside its current scope.

## Propose a change

Open an issue or pull request describing:

1. The existing rule ID, or the gap a new rule would address.
2. A concrete situation where the current guidance is missing, ambiguous, incorrect, or unnecessarily expensive.
3. The proposed wording and its applicability.
4. How a reviewer could verify compliance.
5. Relevant tradeoffs, exceptions, and primary references.

Small, focused proposals are easier to assess. Be respectful, explain disagreements with examples, and avoid including credentials or private project data.

## Rule quality

A rule should:

- Describe an observable behavior or decision.
- Distinguish a requirement from a recommendation.
- State relevant conditions instead of forcing one architecture on every project.
- Preserve correctness, security, and maintainability when discussing optimization.
- Be useful without an arbitrary universal line count, latency target, coverage percentage, or infrastructure choice.
- Prefer official documentation or established primary references for technical claims.

Update existing wording before adding an overlapping rule. Keep the portable policy in `AGENTS.md`; summarize its purpose in the README without duplicating the full rule set.

## Rule IDs and compatibility

- Preserve existing IDs when clarifying wording without changing its intent.
- Assign a new ID for a genuinely new requirement. Do not renumber unrelated rules.
- Record material meaning changes and removals in `CHANGELOG.md` so adopting projects can evaluate them.
- A removed ID must not be reused for a different meaning. Record it as retired in the changelog.
- Explain adoption consequences for changes that add obligations or change accepted behavior.

## Before submitting

- Check that local document links and referenced rule IDs resolve.
- Confirm that wording is English and Markdown renders clearly.
- Review claims against applicable primary sources.
- Keep application-specific commands and performance budgets in the adopting project's copy.
- Keep the embedded license in `AGENTS.md` consistent with `LICENSE`.
- Update the changelog for material policy changes.

There is no application to build or run here. Documentation checks and careful review are the appropriate validation for this repository.

## License

By submitting original contributions, you agree to license them under this repository's [MIT license](LICENSE). Do not copy third-party text unless its license permits the contribution and required notices are preserved.
