# Poverview

**Never lose your place.**

Poverview is a local-first project companion for developers who work on multiple software projects and want to quickly remember where they left off.

It connects existing workflows rather than replacing them: local Git repositories, optional GitHub activity, a project overview, an activity timeline, and an editable **Resume Point** for each project.

The long-term product is a Linux desktop application paired with an Android companion. Desktop is the primary device and has access to the selected project workspace; Android keeps a local offline copy of synchronized project context and can edit supported notes and Resume Points.

> Poverview is in its planning and foundation phase. This repository documents product direction and architecture; it does not yet contain a working application.

## Core principles

- **Resume first:** make it easy to understand where work stopped and how to continue.
- **Local-first:** no Poverview-hosted backend, mandatory cloud, or required account.
- **Direct sync:** desktop and Android communicate directly over a trusted LAN or a user-managed VPN such as Tailscale.
- **Offline-capable:** Android retains the last synchronized data while disconnected.
- **Desktop-primary, multi-device editing:** desktop owns the local project workspace, while both devices can edit supported project context without silently losing changes.
- **Source-code boundary:** project source code stays on desktop; only project metadata and context are synchronized.
- **Automation with transparency:** prefer deterministic collection and clearly distinguish observed facts from inference; core features do not depend on AI/LLMs.
- **User control:** the user controls project lifecycle and can edit or replace the automatically maintained Resume Point.
- **Existing workflow:** Poverview complements IDEs, terminals, Git, and GitHub instead of replacing them.

## Planned applications

| Application | Role | Initial platform |
| --- | --- | --- |
| Poverview Desktop | Primary workspace, project discovery, local collectors, integrations, pairing, and sync host | Linux |
| Poverview Android | Offline-capable companion with synchronized project context and editing of supported metadata | Android |

## Documentation

Start with the [documentation index](docs/README.md).

Key documents:

- [Product philosophy](docs/PRODUCT_PHILOSOPHY.md)
- [Product vision](docs/VISION.md)
- [Requirements](docs/REQUIREMENTS.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Roadmap](docs/ROADMAP.md)
- [Initial technology direction (ADR 0001)](docs/decisions/0001-initial-technology-direction.md)
- [Release process](docs/RELEASING.md)
- [Contributing](CONTRIBUTING.md)
- [Security policy](SECURITY.md)

## Development status

The first milestone is the project foundation: documenting scope, requirements, architecture, and development principles before implementation begins.

No application functionality or release date is promised yet.

## Contributing

The project is currently in its planning and foundation phase. Read [CONTRIBUTING.md](CONTRIBUTING.md) before proposing changes.

## License

A license has not been selected yet. Until one is added, all rights are reserved by default; do not assume the repository is open for reuse merely because it is public.
