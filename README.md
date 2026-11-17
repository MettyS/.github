# .github

Default files for every repository owned by MettyS. GitHub shows them in any repository that doesn't have its own file of the same kind, private repositories included.

| File | What it is |
|---|---|
| `CONTRIBUTING.md` | The contribution standards: pull requests, naming, versions, testing |
| `.github/pull_request_template.md` | The description a new pull request starts with |

GitHub only reads default files from a public repository, so this one is public. Keep anything private out of it.

- **Goal:** one short set of standards that every small MettyS project follows.
- **Done when:** each active project follows them and Claude Code picks them up on every computer.
- **Where it stands:** the standards and template are in place (November 2026). The local clone lives at `~/Developer/projects/github-defaults`.

## Changing the standards

Changes go through a pull request like anywhere else. A project that needs something different overrides it in its own CONTRIBUTING.md or CLAUDE.md instead of changing this file.
