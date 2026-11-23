# Product requirements

These are planning targets, not claims of implemented functionality.

Scope labels: **MVP** means required for the first useful release; **Later** means not required to prove the core product; **Out of scope** means excluded from the initial product.

## Linux desktop

### Workspace and projects
- **MVP** Let the user select one root directory for their project workspace.
- **MVP** Discover Git repositories beneath the selected root without requiring each repository to be added manually.
- **MVP** Avoid duplicate project entries when repositories are nested.
- **MVP** Let the user explicitly ignore discovered folders.
- **MVP** Report missing, moved, or inaccessible paths clearly.
- **MVP** Never move, rename, rewrite, or otherwise modify project files as a side effect of discovery.
- **MVP** Support local Git repositories whether or not they have a GitHub remote.
- **Later** Allow manually tracked non-Git project folders.

### Git and GitHub
- **MVP** Collect branches, recent commits, and working-tree status.
- **MVP** Identify the source and collection time of each record.
- **MVP** Make GitHub integration optional and user-authorized.
- **MVP** Display linked issues, pull requests, releases, and Actions activity where API access permits.
- **MVP** Handle API errors, rate limits, permissions, and stale data visibly.
- **Later** Add other hosting providers and organization-level views.

### Resume Point, activity, and overview
- **MVP** Provide an overview of all tracked projects, project details, and a recent activity timeline.
- **MVP** Maintain an editable Resume Point for each project.
- **MVP** Combine observed activity with user-authored notes without presenting guesses as facts.
- **MVP** Preserve user-authored context when automated collection adds new information.
- **MVP** Distinguish unknown data from healthy or successful status.
- **MVP** Display results imported from supported sources or explicitly configured commands.
- **MVP** Require configuration and consent before running any local command.
- **MVP** Record command, working directory, time, exit status, and useful summary.
- **Later** Add charts, trends, filters, and configurable health indicators.

## Android companion
- **MVP** Pair with a desktop instance using an authenticated flow.
- **MVP** Display synchronized projects, details, recent activity, and Resume Points.
- **MVP** Cache synchronized data for offline use.
- **MVP** Allow edits to supported project metadata, notes, and Resume Points.
- **MVP** Queue offline edits and synchronize them when the desktop is reachable again.
- **MVP** Display last successful sync, connection state, and data freshness.
- **MVP** Never edit desktop repository files, execute local commands, or provide remote-control functionality.
- **Later** Add notification summaries within Android background-execution limits.

## Synchronization and networking
- **MVP** Synchronize directly over a trusted local network while the desktop host is running.
- **MVP** Authenticate each paired device independently and encrypt traffic.
- **MVP** Support bidirectional incremental sync with stable event identifiers and cursors.
- **MVP** Preserve supported edits made on either device, including while offline.
- **MVP** Detect and safely resolve or surface conflicting edits; never silently discard changes.
- **MVP** Recover from interrupted connections without silently losing events.
- **MVP** Show host availability and stale mobile data clearly.
- **Later** Support user-managed VPN access outside the LAN, such as Tailscale.
- **Out of scope** Public internet port forwarding or a required Poverview cloud service.

## Privacy and quality
- Store only data needed for enabled features.
- Keep credentials out of the general application database and source control.
- Use operating-system credential storage where available.
- Make integrations and collection configurable and revocable.
- Do not synchronize project source-code contents to Android.
- Never expose the sync service to untrusted networks by default.
- Provide stable storage migrations, automated tests, actionable errors, and documented installation and upgrade paths.
