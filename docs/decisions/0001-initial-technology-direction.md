# ADR 0001: Initial technology direction

- **Status:** Proposed
- **Date:** 2026-11-21

## Context

Poverview is a solo-developed, local-first application with a Linux desktop host and a read-only Android companion. The clients need a stable shared data contract, but do not need to share a UI implementation.

The initial technology surface should remain manageable and avoid unnecessary cross-language FFI.

## Decision

Propose the following starting direction:

- Linux desktop: C++ with Qt 6 and QML / Qt Quick.
- Android: Kotlin with Jetpack Compose.
- Desktop persistence: SQLite.
- Android persistence: Room.
- Inter-client protocol: versioned JSON over HTTPS REST and WebSocket.
- Initial Git integration: Git CLI.
- Optional hosted integration: GitHub REST API.
- Local host discovery: mDNS / DNS-SD.

## Consequences

Benefits include native applications on both platforms, a flexible desktop UI, standard Android tooling, a language-neutral network contract, and less initial build complexity than introducing Rust and FFI.

Trade-offs include duplicated domain/protocol validation, separate packaging workflows, the need for explicit protocol compatibility rules, and careful handling of Git CLI errors and unusual repository states.

## Revisit when

A technical spike reveals a blocking limitation, platform scope changes, or duplicated protocol logic becomes a measurable maintenance problem.
