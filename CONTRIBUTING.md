# Contributing

Poverview is currently in its planning and foundation phase. Contributions should help establish a clear, secure, and maintainable foundation without presenting planned functionality as implemented.

## Before opening a pull request

1. Read the [product vision](docs/VISION.md), [requirements](docs/REQUIREMENTS.md), [architecture](docs/ARCHITECTURE.md), and [roadmap](docs/ROADMAP.md).
2. For a substantial product, architecture, or scope change, open an issue first and discuss the direction.
3. Keep changes focused, reviewable, and consistent with the project's documented principles.
4. Update relevant documentation when behavior, scope, or decisions change.
5. Report exactly what you validated. Do not claim tests or builds were run if they were not.

## Project principles

- Keep the product local-first and useful without GitHub.
- Do not introduce mandatory cloud services.
- Keep Android read-only.
- Never run arbitrary build or test commands without explicit user configuration and consent.
- Never commit credentials, access tokens, private repository data, or personal information.
- Prefer small, reviewable changes with tests and clear documentation.
- Distinguish implemented behavior from proposals and future plans.

## Branch and commit conventions

Use short, descriptive branch names with a type prefix where practical:

- `docs/` for documentation
- `feat/` for product functionality
- `fix/` for bug fixes
- `refactor/` for internal restructuring
- `test/` for tests
- `chore/` for maintenance

Use [Conventional Commits](https://www.conventionalcommits.org/) for commit messages. Common types include `feat`, `fix`, `docs`, `refactor`, `test`, and `chore`. Keep the subject imperative, concise, and specific. Add a scope when it improves clarity.

Examples:

- `docs: add documentation index`
- `feat(desktop): add local repository registration`
- `fix(sync): reject expired pairing tokens`

## Issues

Use GitHub Issues for actionable bugs, feature proposals, and scoped documentation or maintenance work.

- Search existing issues before opening a duplicate.
- Use the repository's bug report or feature request template.
- Give each issue a concise, specific title.
- For bugs, include the affected area, reproduction steps, expected behavior, actual behavior, and sanitized logs where useful.
- For proposals, explain the problem, intended outcome, and relevant constraints.
- Do not include credentials, private repository contents, personal data, or unredacted logs.
- Keep one independently reviewable problem or proposal per issue.

Questions and broad design discussions should explain the decision that needs to be made rather than acting as an unbounded task list.

## Pull requests

Pull requests should:

- Explain the problem and motivation.
- Summarize the implementation or documentation changes.
- Link related issues where applicable.
- List validation performed and any validation not performed.
- Identify compatibility, privacy, and security implications.
- Include screenshots for meaningful UI changes when available.
- Update documentation and tests when relevant.

Keep pull requests focused. Do not bundle unrelated cleanup with a feature or bug fix.

## Releases

Release versioning, tags, prereleases, and the release checklist are defined in [docs/RELEASING.md](docs/RELEASING.md). Do not create a release or stable version merely because a roadmap milestone is marked complete.

## Security

Never report vulnerabilities in public issues. Follow the private reporting guidance in [SECURITY.md](SECURITY.md).

## License

A license has not been selected yet. Until one is added, all rights are reserved by default. By submitting a contribution, do not assume that the public repository grants permission to reuse your work under an open-source license; clarify licensing before making contributions intended for redistribution.
