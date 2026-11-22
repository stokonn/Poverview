# Product philosophy

**Status:** Confirmed product direction, captured during product-discovery discussions on 2026-11-23.

This document records the product decisions that have been explicitly agreed so far. It is the current reference for product intent. Older planning documents may still contain assumptions that predate these decisions; they must be reconciled before implementation and must not silently override this direction.

## 1. The problem Poverview solves

A developer may have several projects in progress and regularly switch between them. When returning to a project after hours or days, they have to reconstruct where they left off, what changed, what remains unfinished, and what they intended to do next.

Poverview exists to reduce that lost-context cost.

Its central promise is:

> **Never lose your place.**

Poverview is not another place where a developer is required to do their actual work. It connects the tools and workspaces they already use, keeps project context available, and makes it easy to resume.

## 2. Product scope

### Initial focus

The first product scope is **software development projects**.

Poverview should work with local Git repositories whether or not they have a GitHub remote. GitHub integration is optional, not a prerequisite.

### Long-term direction

The broader vision may include other technical projects, such as electronics, ESP32 and Raspberry Pi projects, homelabs, and 3D-printing/CAD work.

This is a future direction, not a requirement for the first version. The initial design should avoid needlessly blocking that expansion, but should not build a universal project-management system prematurely.

## 3. Core experience

Poverview brings three complementary views together:

- **Project overview:** see all tracked projects and their current known state.
- **Activity timeline:** understand what has happened across projects and when.
- **Project workspace/context:** quickly understand an individual project's current situation and how to continue.

These are parts of one coherent experience, not three separate products or dashboards.

Poverview should be a hybrid companion: quiet and unobtrusive during normal work, useful when opened, and able to offer notifications only when they are genuinely helpful. It must not become a nagging task manager.

## 4. Resume Point is the heart of Poverview

Every project should have a clear **Resume Point**: the best available answer to "Where did I leave off, and what should I do when I return?"

A Resume Point may combine:

- Facts collected automatically from local Git activity and enabled integrations.
- User-written notes and context.
- The last known work session.
- A next step explicitly written by the user or cautiously suggested from available information.

The Resume Point should update automatically when useful new facts are collected, while remaining editable at any time. The user can correct or replace it.

User-authored context takes precedence over automated inference. Poverview must distinguish observed facts from guesses and must never present an inference as certainty. A recent commit alone does not prove what the developer intended or what the next task should be.

The aim is to combine automatic collection with as little manual input as possible, not to force the user to maintain project records by hand.

## 5. Work with existing tools

Poverview does not replace an IDE, terminal, Git client, GitHub, or the developer's existing workflow.

A user should be able to keep working in their normal tools. Poverview observes permitted project metadata and connects the context around that work. It should not require the user to move their development process into Poverview.

## 6. Project discovery and workspace root

The user chooses one root directory for their projects.

Poverview continuously monitors that workspace, with reasonable resource usage, and discovers candidate project directories beneath it. Git repositories are recognized as projects automatically. The product should also allow a user to add a non-Git project manually and to explicitly ignore folders that should not be tracked.

Discovery must avoid duplicate projects when repositories are nested. Poverview must not move, rename, rewrite, or otherwise modify the user's project files as a side effect of discovery.

The user remains in control of which discovered folders are actually tracked.

## 7. Local-first, direct synchronization, and offline use

Poverview is local-first and does not depend on a Poverview-operated cloud service, hosted backend, or mandatory account.

The intended device model is:

- **Desktop is the primary device.** It owns access to the selected project workspace, performs local collection, and holds the canonical view of project files and local repository state.
- **Android is a full companion, not a read-only viewer.** It keeps a local copy of synchronized project information and can edit supported metadata, notes, and Resume Points.
- **Both devices can make changes.** Desktop has primary status, but this must not mean that desktop changes silently overwrite edits made on Android.

Devices communicate directly when reachable, initially over a trusted LAN and potentially through a user-managed VPN such as Tailscale when away from the local network. No public port forwarding or Poverview-hosted relay is assumed.

Android retains its last synchronized data when disconnected and remains useful offline. It shows that data may be stale and resumes synchronization when the desktop becomes reachable again.

Local storage is expected and is not the same thing as a hosted backend. A local database such as SQLite may be used to persist application data.

Synchronization must be authenticated and encrypted. It must support interrupted connections, incremental updates, and explicit conflict handling. Conflicting edits must not be silently discarded. The exact conflict-resolution model remains an open technical design question.

## 8. Data boundaries and privacy

Project source code stays on the desktop and is not copied to Android by the synchronization system.

The companion synchronizes project metadata and context, such as:

- Project identity and status.
- Git activity and selected repository metadata.
- Activity history and timeline records.
- Resume Points and user notes.
- Other explicitly supported project metadata.

GitHub data may be collected only through an optional, user-authorized integration. Credentials must be protected and must not be copied to Android unnecessarily.

Poverview should be transparent about what it collects, where each fact came from, and when it was last updated.

## 9. Automation without AI dependency

The product should not require an LLM, a hosted AI service, or a custom trained model to deliver its core value.

Prefer understandable, deterministic mechanisms where possible: Git metadata, filesystem events, GitHub API data, timestamps, user notes, and explicit rules.

Any future AI assistance must be optional and must not become a dependency for basic project tracking, synchronization, or Resume Point functionality.

## 10. User control over project lifecycle

Poverview may show inactivity, highlight stale information, or suggest that a project be paused or archived.

The user chooses what happens to a project. Poverview must not automatically pause, archive, complete, or delete projects based only on inactivity or inferred status.

## 11. Confirmed non-goals and guardrails

- Do not replace the user's IDE, terminal, Git workflow, or hosting platform.
- Do not require a Poverview cloud account or hosted backend.
- Do not require AI/LLM functionality.
- Do not sync project source code to Android.
- Do not make Android read-only for supported project context.
- Do not silently overwrite changes made on another device.
- Do not execute arbitrary project commands without explicit user configuration and consent.
- Do not automatically change project lifecycle state.
- Do not burden the user with constant notifications or mandatory manual status reports.

## 12. Decisions still open

The following have deliberately **not** been decided yet:

- Detailed visual design, navigation, and interaction model.
- Exact desktop and Android technology choices.
- Exact local database schema and synchronization protocol.
- Pairing UX, device authorization, and certificate/trust model.
- Conflict-resolution UX and merge semantics for simultaneous edits.
- Exact filesystem monitoring and polling strategy.
- Exact GitHub permissions and authentication flow.
- Notification rules and Android background behavior.
- The detailed definition of a work session and how one is ended.
- The point at which a discovered folder becomes a tracked project by default.

These questions should be explored later. They must not be treated as settled merely because an implementation proposal exists elsewhere in the repository.
