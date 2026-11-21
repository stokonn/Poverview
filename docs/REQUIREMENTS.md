# Product requirements

These are planning targets, not claims of implemented functionality.

Scope labels: **MVP** means required for the first useful release; **Later** means not required to prove the core product; **Out of scope** means excluded from the initial product.

## Linux desktop

### Projects and repositories
- **MVP** Add a local Git repository by selecting its directory.
- **MVP** Support repositories without a GitHub remote.
- **MVP** Show repository name, path, current branch, working-tree state, and latest commit.
- **MVP** Group or favorite projects.
- **MVP** Clearly report missing, moved, or inaccessible paths.
- **Later** Discover repositories in user-selected directories.

### Git and GitHub
- **MVP** Collect branches, recent commits, and working-tree status.
- **MVP** Identify the source and collection time of each record.
- **MVP** Make GitHub integration optional and user-authorized.
- **MVP** Display linked issues, pull requests, releases, and Actions activity where API access permits.
- **MVP** Handle API errors, rate limits, permissions, and stale data visibly.
- **Later** Add other hosting providers and organization-level views.

### Builds, tests, and overview
- **MVP** Display results imported from supported sources or explicitly configured commands.
- **MVP** Require configuration and consent before running any local command.
- **MVP** Record command, working directory, time, exit status, and useful summary.
- **MVP** Provide all-project overview, project detail, and recent activity timeline.
- **Later** Add charts, trends, filters, and configurable health indicators.
- **MVP** Distinguish unknown data from healthy or successful status.

## Android companion

- **MVP** Pair with a desktop instance using an authenticated flow.
- **MVP** Display synchronized projects, details, and recent activity.
- **MVP** Cache received data for offline reading.
- **MVP** Display last successful sync and connection state.
- **MVP** Remain read-only: no repository edits, command execution, or remote control.
- **Later** Add notification summaries within Android background-execution limits.

## Synchronization and networking

- **MVP** Synchronize over a trusted local network while the desktop host is running.
- **MVP** Authenticate each paired device independently and encrypt traffic.
- **MVP** Support incremental sync with stable event identifiers and cursors.
- **MVP** Recover from interrupted connections without silently losing events.
- **MVP** Show host availability and stale mobile data clearly.
- **Later** Document user-managed VPN access outside the LAN.
- **Out of scope** Public internet port forwarding or a required Poverview cloud service.

## Privacy and quality

- Store only data needed for enabled features.
- Keep credentials out of the general application database and source control.
- Use operating-system credential storage where available.
- Make integrations and collection configurable and revocable.
- Avoid collecting source-code contents unless a future feature explicitly requires it.
- Never expose the sync service to untrusted networks by default.
- Provide stable storage migrations, automated tests, actionable errors, and documented installation and upgrade paths.
