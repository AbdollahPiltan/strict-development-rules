# Start a Project

Start from an empty directory or adopt the policy in an existing project without rewriting engineering rules for every task.

## Reuse once, then resume with a short prompt

1. Copy [AGENTS.md](AGENTS.md) into the target project root. Merge with existing instructions instead of overwriting them.
2. Copy [templates/PROJECT.md](templates/PROJECT.md) to the target root as `PROJECT.md` and fill in the known project requirements once.
3. Use the prompt below. Consult this guide during initial setup or when a setup step is incomplete; it does not need to be loaded for every implementation task.

> Read AGENTS.md and the relevant parts of PROJECT.md. Start or resume the next incomplete milestone using the existing specifications and acceptance criteria. Complete and verify that milestone, review its diff, and commit and push it on a dedicated feature branch with a meaningful message. Record progress and checkpoint references without repeating unchanged requirements. Continue through the authorized milestones, respect pull-request requirements, and report status, checks, commits, branches, and blockers concisely. Ask only about material unresolved requirements or permissions.

`AGENTS.md` owns engineering policy. `PROJECT.md` owns product requirements, setup decisions, milestone status, and recovery notes. Link to existing specifications rather than duplicating them. A filled project brief becomes durable context; an empty template is not a requirement to invent a product or technology stack.

## 1. Define the project boundary

Record the intended outcome, users, minimum scope, exclusions, acceptance criteria, stack, repository owner/name, visibility, and deployment intent in `PROJECT.md`.

Reuse documented decisions. Make routine reversible choices within the task's scope and record material assumptions. If a missing product requirement or permission changes what should be built or published, resolve it before dependent work. Do not add a database, authentication system, gateway service, cloud account, or paid dependency merely because a generic template mentions it.

## 2. Check Git and GitHub access

The command examples use Git and GitHub CLI in a POSIX-style terminal. They are documentation examples, not an installer. Replace uppercase placeholders with the chosen values; do not paste them unchanged.

Check installed tools and the intended account:

```sh
git --version
gh --version
gh auth status --hostname github.com
gh api user --jq .login
```

If authentication is missing, the human completes the browser sign-in:

```sh
gh auth login --hostname github.com --git-protocol https --web
```

Use an existing working SSH or credential-helper configuration when available. GitHub API access through an assistant integration does not by itself authenticate local Git pushes. If using GitHub CLI as the HTTPS credential helper, follow its [setup-git guidance](https://cli.github.com/manual/gh_auth_setup-git); do not replace another working configuration unnecessarily.

Never request a token in chat or put it in a remote URL, project file, command example, or commit. An authentication or network failure needs diagnosis before retrying; do not assume a restricted execution environment proves the account credentials are invalid.

## 3. Create or connect the repository

Use exactly one of the paths below. Repository creation and visibility must match the user's authorized target; default to private when no public-publication decision has been made.

### A. A new project and a new repository

From a parent folder outside any unrelated Git working tree, create a repository with an initial README and clone it into a new directory:

```sh
gh repo create OWNER/PROJECT --private --add-readme --clone
cd PROJECT
gh repo view --json nameWithOwner,defaultBranchRef,url
git remote -v
git switch -c chore/project-bootstrap
```

Use `--public` instead of `--private` only when public creation is intended. GitHub creates the initial default-branch seed; subsequent project changes go through feature branches and pull requests. Do not assume the configured default branch is named `main`.

Cloning initializes local Git and connects `origin`; a second `git init` is unnecessary. Copy the policy and project brief into this clone and adapt its README to the actual product. Do not publish this rules repository's marketing README as the product description.

### B. An existing GitHub repository

Clone the chosen repository if it is not already local. In the existing working tree, inspect its status and remotes, identify its default branch, fetch updates, and create the feature branch from the appropriate current base:

```sh
git status --short --branch
git remote -v
gh repo view OWNER/PROJECT --json nameWithOwner,defaultBranchRef,url
git fetch origin
git switch -c chore/project-bootstrap origin/DEFAULT_BRANCH
```

The example assumes a remote named `origin`; substitute the actual remote when different. Preserve unrelated local changes and stop if they would be overwritten. Reuse an existing suitable task branch instead of creating branches repeatedly. Do not replace a configured remote without understanding its purpose.

### C. Local files that are not yet versioned

Check whether the directory is already inside a Git working tree before creating another repository. Preserve the original files, follow path A in a new sibling directory, then copy only intended project files into that clone. Exclude `.git`, credentials, build output, and unrelated files. Resolve filename collisions deliberately.

If local Git history already exists without a GitHub remote, preserve it: create the authorized remote, add or verify the intended remote URL, and plan how the existing history joins its default branch. Do not overwrite that history or use a force-push to make a generic bootstrap recipe fit. This case needs a history-aware plan rather than path C's file-copy approach.

### Local identity and first checkpoint

Check the effective commit identity inside the target repository. If missing or incorrect, set the agreed identity locally, not globally:

```sh
git config user.name
git config user.email
git config --local user.name "YOUR_NAME"
git config --local user.email "YOUR_VERIFIED_OR_NOREPLY_EMAIL"
```

Only run the two setters when needed. A GitHub noreply address can preserve email privacy. Add a stack-appropriate `.gitignore` and a safe example configuration before staging application files. Include reproducibility files such as a required lockfile; do not treat every generated file as junk.

Verify access and the policy/brief contents, review the diff, commit the bootstrap milestone on its feature branch, and push it. Remote creation alone is not proof that Git pushes work.

## 4. Plan independently verifiable milestones

Adapt this default sequence to the product. Skip inapplicable phases with a reason; do not create empty commits to satisfy a table.

| Milestone | Result and checkpoint gate | Example commit message |
| --- | --- | --- |
| Project definition | Scope, acceptance criteria, and material decisions recorded | `docs(project): define scope and acceptance criteria` |
| Repository bootstrap | Policy, project brief, ignore rules, identity, and remote verified | `chore(repo): establish project policies and git workflow` |
| Minimal foundation | Required scaffold, configuration, and relevant checks work | `chore(scaffold): add minimal application foundation` |
| First useful capability | One complete product workflow meets its acceptance criteria | `feat(catalog): add paginated product search` |
| Risk-based hardening | Applicable error, authorization, concurrency, and resource cases verified | `fix(catalog): prevent duplicate search requests` |
| Handoff | Run instructions, recovery notes, checks, and PR evidence complete | `docs(project): document operation and recovery` |

These messages are examples, not instructions to build a catalog. Use actual scopes and outcomes. Related definition and bootstrap work MAY share a coherent commit. Larger milestones MAY need multiple independently understandable commits. Commit real verified outcomes rather than every tool call, file save, or arbitrary time interval.

At each milestone:

1. Read its acceptance criteria and the relevant files.
2. Implement the complete scoped change using installed dependencies where suitable.
3. Run required targeted checks; broaden only when justified.
4. Review changed and staged files for correctness, secrets, scope, and documentation.
5. Commit with a meaningful message and push the feature branch.
6. Record the result, checks, and checkpoint reference in `PROJECT.md` or the pull request. Continue only when the next milestone's prerequisites are satisfied.

Use `<type>(<scope>): <outcome>` when the project has no established commit convention. Common types include `docs`, `chore`, `feat`, `fix`, `test`, and `refactor`. Avoid messages such as `update`, `changes`, and `final` without a concrete outcome. See [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) for the optional standard.

A commit cannot contain its own final hash. Record that hash in the PR or final report, or in the next normal progress update; do not create a commit/amend loop just to fill the ledger.

## 5. Preserve checkpoints when integrating

Open a pull request with the completed milestones, verification evidence, and recovery considerations. Satisfy required checks and reviews; do not bypass repository protections.

When retaining each milestone's original commit on the default branch matters, use a regular merge commit if repository policy allows it. Squash merging collapses the milestone commits; rebase merging preserves their sequence but changes their SHAs on GitHub. Under those policies, use smaller milestone PRs or record the resulting integrated SHAs as appropriate. Do not claim branch checkpoint hashes remain unchanged after every merge method. See [GitHub's merge-method documentation](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/about-merge-methods-on-github).

If useful, create agreed annotated milestone tags after verification. Do not overwrite shared tags. Report a push or merge blocker accurately instead of calling an unpublished checkpoint complete.

## 6. Inspect or roll back a checkpoint

Start with a clean working tree or preserve unrelated work explicitly. Identify the exact target and inspect its effect before changing history or files.

### Inspect an earlier snapshot

```sh
git log --oneline --decorate -n 20
git show --stat CHECKPOINT_SHA
git switch -c inspect/checkpoint CHECKPOINT_SHA
```

This creates a new inspection branch at an existing commit. It does not change the default branch or undo a deployment. Use a unique branch name if the example name already exists. See [git-switch](https://git-scm.com/docs/git-switch).

### Undo a published ordinary commit

Create a rollback branch from the current remote default branch, then create a revert commit:

```sh
git fetch origin
git switch -c fix/revert-regression origin/DEFAULT_BRANCH
git show --stat BAD_COMMIT_SHA
git revert --no-edit BAD_COMMIT_SHA
```

Verify the resulting behavior and diff, push the rollback branch, and open a pull request. A revert records a new inverse change without deleting published history. Resolve conflicts deliberately, or use `git revert --abort` to cancel an in-progress conflicting revert. See [git-revert](https://git-scm.com/docs/git-revert).

For a milestone spanning multiple commits, inspect dependencies and plan the appropriate reverse order. A merge commit requires selecting its mainline parent; do not guess or apply the ordinary-commit recipe blindly. Avoid destructive resets and never force-push a shared rollback.

Git reverses tracked file changes. Database migrations, deleted data, infrastructure changes, queued jobs, external side effects, and running deployments need their own compatible recovery procedure. Record those constraints before treating a checkpoint as recoverable.

## Completion report

Report the completed milestone, changed files, checks and results, checkpoint commit/branch, remote or PR link, next milestone, and any blocker. Keep routine explanations short and reuse recorded requirements.
