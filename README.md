# Poverview

**Your projects. One overview.**

Poverview is an independent project-monitoring workspace for keeping software projects and their development activity visible in one place.

The long-term product is a native Linux desktop application paired with a read-only Android companion. The desktop application is the primary workspace; Android provides a convenient view of project status while away from the computer.

> Poverview is in its early planning stage. The repository currently contains product direction and architecture planning, not a working application.

## What Poverview is

Poverview aims to bring together information that is otherwise scattered across local repositories, GitHub, and development tools:

- Local Git repositories, including projects that are not hosted on GitHub
- GitHub activity such as issues, pull requests, releases, and Actions
- Build and test results collected with the user's explicit permission
- Project activity timelines, statistics, and health indicators
- A local connection between the Linux desktop and Android companion

## Product principles

- **Local-first:** project data stays under the user's control; a cloud account is not required.
- **Useful without GitHub:** local repositories are first-class projects.
- **Read-only Android:** the companion monitors and displays; project management remains on desktop.
- **Explicit execution:** Poverview never runs arbitrary build or test commands without user configuration and consent.
- **Transparent data:** show where information came from and when it was last updated.
- **Secure by default:** pairing and sync must be authenticated; no public port forwarding is required.

## Planned applications

| Application | Role | Initial platform |
| --- | --- | --- |
| Poverview Desktop | Main workspace, project discovery, integrations, configuration | Linux |
| Poverview Android | Read-only project monitoring and offline viewing | Android |

## Documentation

Start with the [documentation index](docs/README.md) for an overview of the project's product, technical, and contributor documentation.

Key documents:

- [Product vision](docs/VISION.md)
- [Requirements](docs/REQUIREMENTS.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Roadmap](docs/ROADMAP.md)
- [Architecture decision records](docs/decisions/)
- [Release process](docs/RELEASING.md)

## Development status

The first milestone is the project foundation: documenting scope, requirements, architecture, and development principles before implementation begins.

No application functionality or release date is promised yet.

## Contributing

The project is currently in its planning and foundation phase. Read [CONTRIBUTING.md](CONTRIBUTING.md) before proposing changes.

## License

A license has not been selected yet. Until one is added, all rights are reserved by default; do not assume the repository is open for reuse merely because it is public.
