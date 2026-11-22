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
- [ ] Add and persist local Git repositories.
- [ ] Collect branch, working-tree, and recent-commit information.
- [ ] Implement project overview and detail screens.
- [ ] Handle missing and inaccessible repositories.
- [ ] Add automated tests and Linux development documentation.

**Exit criteria:** monitor several local repositories without GitHub.

## 2. GitHub integration

- [ ] Implement optional GitHub authentication.
- [ ] Link local projects to GitHub repositories.
- [ ] Display issues, pull requests, releases, and Actions activity.
- [ ] Handle API limits, permissions, and stale results.

**Exit criteria:** local and hosted activity appears in a unified view.

## 3. Activity and insights

- [ ] Build a normalized activity timeline.
- [ ] Add explicit, user-configured build/test collection.
- [ ] Add project statistics and filters.
- [ ] Define transparent project-health indicators.

**Exit criteria:** desktop provides meaningful current project status.

## 4. Local synchronization

- [ ] Implement the versioned protocol.
- [ ] Add authenticated QR pairing and device revocation.
- [ ] Implement HTTPS snapshots and incremental sync.
- [ ] Add LAN discovery.
- [ ] Test reconnects, duplicate delivery, cursor recovery, and version compatibility.

**Exit criteria:** a paired device receives a consistent read-only view over the LAN.

## 5. Android companion

- [ ] Create the Kotlin/Compose application.
- [ ] Implement pairing and connection status.
- [ ] Add Room-backed offline overview.
- [ ] Add project detail and activity timeline.
- [ ] Display freshness and synchronization errors.

**Exit criteria:** Android displays synchronized data reliably and remains useful offline.

## 6. Stabilization and first public release

- [ ] Add packaging and installation guidance for supported Linux distributions.
- [ ] Add Android release builds and update guidance.
- [ ] Complete privacy, security, and migration reviews.
- [ ] Publish user documentation and known limitations.
- [ ] Tag a stable release only when release criteria are met.

## Later possibilities

User-managed VPN support, additional hosting providers, optional team workflows on a user-controlled host, more build-system adapters, and advanced analytics.

Remote multi-user collaboration and hosted synchronization are not part of the initial MVP.
