# Architecture

## Status

This is the initial proposed architecture. Validate it with small technical spikes before implementation decisions become difficult to reverse.

## System overview

Poverview has two native applications:
- **Desktop host:** Linux application, local data owner, integration manager, and synchronization host.
- **Android companion:** read-only client with a local cache.

A Poverview-operated cloud backend is not required.

## Proposed technology direction

| Area | Proposed technology | Rationale |
| --- | --- | --- |
| Linux UI | Qt 6 + QML / Qt Quick | Flexible native desktop interface |
| Desktop implementation | C++ | Direct Qt integration |
| Android UI | Kotlin + Jetpack Compose | Native Android development |
| Desktop storage | SQLite | Local relational storage |
| Android cache | Room | Android SQLite abstraction |
| Git collection | Git CLI initially | Reuse installed Git behavior |
| GitHub integration | GitHub REST API | Optional hosted metadata |
| Desktop/mobile API | HTTPS REST + WebSocket | Pairing, snapshots, and updates |
| LAN discovery | mDNS / DNS-SD | Discover desktop host locally |
| Shared contract | Versioned JSON | Language-neutral protocol |

These are proposals, not irreversible commitments.

## Responsibilities

The desktop owns project configuration, collection scheduling, source integrations, canonical local data, SQLite migrations, pairing, device authorization, and the sync API.

Collectors should normalize source-specific data into domain records rather than letting integration-specific structures leak into UI code.

Android receives a limited projection of project metadata and context, stores it in Room, and can edit supported records such as Resume Points and notes. It should not need a live connection for every screen. It must not receive credentials that allow it to act as the desktop user on GitHub or execute local commands.

## Data flow

1. The user adds a repository or enables an integration on desktop.
2. A collector reads permitted metadata.
3. The adapter normalizes the result into domain records.
4. The desktop persists records and provenance in SQLite.
5. The sync layer publishes versioned changes to paired devices.
6. Android validates and stores changes in Room; supported user edits are recorded as outbound changes.
7. When connected, both devices exchange changes and resolve or surface conflicts without silently discarding either side.
8. The UI reads the local cache and displays freshness.

## Initial domain concepts

Workspace, Project, Repository, Branch, Commit, ActivityEvent, BuildRun, TestRun, Release, IssueReference, PullRequestReference, Device, SyncCursor, and IntegrationAccount.

Records should include stable identifiers, timestamps, and provenance such as source type, source identifier, and last-collected time.

## Synchronization protocol

The protocol must be language-neutral and versioned from its first release.

Each event should have a stable identifier, protocol version, event type, source identifier, occurrence and collection timestamps where applicable, and a documented payload.

Support an initial snapshot followed by incremental updates using cursors. Both desktop and Android may produce supported metadata changes. Changes need stable identifiers, ordering/version information, and conflict handling so an offline edit is not silently overwritten. Clients must detect incompatible protocol versions and request a fresh snapshot when needed.

REST should support pairing, snapshots, cursor-based bidirectional synchronization, and health checks. WebSocket may deliver updates while the desktop host is available.

## Pairing and network security

The intended flow uses a QR code containing host information and a short-lived one-time pairing secret. The desktop authorizes the device and issues a distinct revocable device credential.

- Use HTTPS for application data.
- Bind the host only to trusted interfaces and make exposure explicit.
- Do not require router port forwarding.
- Do not reuse one permanent secret across all devices.
- Provide device revocation.
- Treat LAN discovery as locating a host, never as authentication.

Outside the local network, synchronization requires a user-managed secure network such as a VPN. The product must not imply that LAN sync works from anywhere.

## Availability limits

The desktop host must be running and reachable for synchronization with the primary workspace. Android remains usable from its local cache while disconnected. Android background execution is constrained by the operating system; show last-sync time and do not promise immediate updates while the app is suspended.

## Credentials and execution safety

Do not store GitHub credentials or device secrets as plaintext in the general database. Use platform credential storage where available. Redact tokens and pairing secrets from logs.

Build and test collection must use explicitly configured commands and working directories. Require opt-in, bound output, and provide cancellation and status reporting. Never infer and execute a build command merely from repository contents.

## Suggested module boundaries

Desktop: domain, storage, collectors, sync, and UI.

Android: data, domain, and UI.

## Open questions

- HTTPS server implementation and certificate trust model.
- Qt networking and Android certificate strategy.
- GitHub authentication approach.
- Repository discovery and polling strategy.
- Fedora and Arch packaging.
- Minimum supported Android version.
