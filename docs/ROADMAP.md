# Roadmap

Milestones are goals, not date commitments. Scope may change as technical risks are tested. A checked item means the corresponding repository or product work is actually complete; it does not imply that future application functionality exists.

## 0. Foundation

- [x] Create the public repository and initial project documentation.
- [ ] Select and document the project license.
- [ ] Finalize initial architecture decisions after reviewing the proposed ADR and relevant technical risks.
- [x] Define contribution conventions in `CONTRIBUTING.md`.
- [x] Define issue conventions and provide GitHub issue templates.
- [x] Define release and versioning conventions in `docs/RELEASING.md`.
- [ ] Set up baseline CI and repository quality checks appropriate to the implementation languages.

**Exit criteria:** product scope, project policies, architecture direction, and remaining open decisions are documented; the license and repository quality baseline are settled before implementation begins.

## 1. Desktop MVP

- [ ] Create the Qt 6 desktop application skeleton.
- [ ] Let the user select a project workspace root.
- [ ] Discover local Git repositories beneath the workspace root without duplicate entries.
- [ ] Allow the user to ignore discovered folders and report inaccessible paths.
- [ ] Collect branch, working-tree, and recent-commit information.
- [ ] Implement project overview, project detail, activity timeline, and editable Resume Point.
- [ ] Handle missing and inaccessible repositories.
- [ ] Add automated tests and Linux development documentation.

**Exit criteria:** monitor several local repositories from one selected workspace without requiring GitHub.

## 2. GitHub integration

- [ ] Implement optional GitHub authentication.
- [ ] Link local projects to GitHub repositories.
- [ ] Display issues, pull requests, releases, and Actions activity.
- [ ] Handle API limits, permissions, and stale results.

**Exit criteria:** local and hosted activity appears in a unified view.

## 3. Activity and insights

- [ ] Build a normalized activity timeline.
- [ ] Define how work sessions and Resume Point updates are derived from observed facts and user input.
- [ ] Add explicit, user-configured build/test collection.
- [ ] Add project statistics and filters.
- [ ] Define transparent project-health indicators.

**Exit criteria:** desktop provides meaningful current project context and a reliable way to resume work.

## 4. Direct synchronization foundation

- [ ] Define the versioned, language-neutral synchronization protocol.
- [ ] Add authenticated device pairing and device revocation.
- [ ] Implement encrypted snapshots and bidirectional incremental sync.
- [ ] Preserve supported edits from both devices, including offline edits.
- [ ] Detect conflicts and provide a safe resolution or review path.
- [ ] Add LAN discovery.
- [ ] Test reconnects, duplicate delivery, cursor recovery, conflict handling, and version compatibility.

**Exit criteria:** a paired Android device receives project context and can safely return supported edits over a direct LAN connection; neither side silently loses changes.

## 5. Android companion

- [ ] Create the Kotlin/Compose application.
- [ ] Implement pairing and connection status.
- [ ] Add Room-backed offline project overview.
- [ ] Add project detail, activity timeline, and Resume Point editing.
- [ ] Queue supported offline edits and synchronize them on reconnect.
- [ ] Display data freshness and synchronization errors.

**Exit criteria:** Android remains useful offline and safely exchanges supported project-context edits with the desktop.

## 6. Stabilization and first public release

- [ ] Add packaging and installation guidance for supported Linux distributions.
- [ ] Add Android release builds and update guidance.
- [ ] Complete privacy, security, and migration reviews.
- [ ] Publish user documentation and known limitations.
- [ ] Tag a stable release only when release criteria are met.

## Later possibilities

User-managed VPN support, additional hosting providers, optional team workflows on a user-controlled host, more build-system adapters, and advanced analytics.

Remote multi-user collaboration and hosted synchronization are not part of the initial MVP.
