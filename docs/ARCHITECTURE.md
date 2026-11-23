# Architecture

## Status

This document describes the current architectural direction derived from the confirmed product philosophy. Specific technologies and protocol details remain proposals until validated with focused technical spikes.

## System overview

Poverview has two native applications:

- **Desktop host:** primary application, selected-workspace monitor, local collector, integration manager, and synchronization host.
- **Android companion:** offline-capable application with a local copy of synchronized project context and the ability to edit supported metadata.

A Poverview-operated cloud backend is not required. Devices communicate directly when reachable.

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

The desktop owns the selected project workspace, project discovery, local collection, source integrations, canonical local repository state, SQLite migrations, pairing, device authorization, and the sync host.

The user selects one workspace root. The desktop monitors it and discovers candidate project directories beneath it. Git repositories are recognized automatically. Non-Git projects may be added manually, and folders can be explicitly excluded. Discovery must avoid duplicate projects for nested repositories and must never modify project files.

Collectors normalize source-specific information into domain records rather than allowing integration-specific structures to leak into UI code.

Android stores a local projection of synchronized project metadata and context. It remains useful without a live connection and can edit supported records, including Resume Points, notes, and explicitly supported project metadata. It does not receive project source code, GitHub credentials, or permission to execute desktop commands.

Desktop is the primary device because it owns access to the selected workspace. Primary status does not authorize it to silently overwrite edits made on Android. Both devices can produce supported changes, and synchronization must preserve or explicitly surface conflicts.

## Data flow

1. The user selects a workspace root on desktop.
2. The desktop discovers candidate repositories and records the user's tracking or ignore choices.
3. Local collectors read permitted Git metadata; optional integrations collect explicitly authorized external metadata.
4. Adapters normalize collected information into domain records with provenance.
5. The desktop persists its local project state and publishes versioned changes to paired devices.
6. Android validates and stores synchronized information locally; supported user edits are recorded as outbound changes.
7. When connected, both devices exchange incremental changes and resolve or surface conflicts without silently discarding either side.
8. Each UI reads local storage and displays data freshness and connection state.

## Initial domain concepts

Workspace, Project, Repository, Branch, Commit, ActivityEvent, WorkSession, ResumePoint, Note, BuildRun, TestRun, Release, IssueReference, PullRequestReference, Device, SyncCursor, and IntegrationAccount.

Records should include stable identifiers, timestamps, and provenance such as source type, source identifier, and last-collected time. User-authored context must remain distinguishable from automatically collected facts and inferred suggestions.

## Synchronization protocol

The protocol must be language-neutral and versioned from its first release.

Each event should have a stable identifier, protocol version, event type, source identifier, occurrence and collection timestamps where applicable, and a documented payload.

Support an initial snapshot followed by incremental updates using cursors. Both desktop and Android may produce supported metadata changes. Changes need stable identifiers and version or ordering information. Offline edits must survive reconnection; conflicts must never be silently discarded. The exact conflict-resolution model remains an open technical design question.

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

The desktop host must be running and reachable for synchronization with the primary workspace. Android remains usable from its local cache while disconnected. It must show when cached data may be stale and the time of the last successful sync.

Android background execution is constrained by the operating system; do not promise immediate updates while the app is suspended.

## Credentials and execution safety

Do not store GitHub credentials or device secrets as plaintext in the general database. Use platform credential storage where available. Redact tokens and pairing secrets from logs.

Build and test collection must use explicitly configured commands and working directories. Require opt-in, bound output, and provide cancellation and status reporting. Never infer and execute a build command merely from repository contents.

## Suggested module boundaries

Desktop: domain, storage, workspace discovery, collectors, integrations, sync, and UI.

Android: data, local storage, sync client, domain, and UI.

## Open questions

- HTTPS server implementation and certificate trust model.
- Qt networking and Android certificate strategy.
- GitHub authentication approach.
- Exact repository discovery rules, including nested repositories and symlinks.
- Conflict-resolution UX and merge semantics for simultaneous edits.
- Pairing UX and device authorization lifecycle.
- Filesystem monitoring and polling strategy.
- Fedora and Arch packaging.
- Minimum supported Android version.
