# Product vision

## Definition

Poverview is a local-first project overview ecosystem that brings the current state and development activity of software projects into one clear workspace.

## The problem

Project information is fragmented across local repositories, hosting platforms, CI systems, and build tools. Developers switch between tools to understand what is happening across their projects.

Poverview aims to provide one coherent overview without requiring projects to move to a particular hosting platform.

## Product shape

### Poverview Desktop

The Linux desktop application is the primary product. It should help a developer discover and organize local repositories, connect optional GitHub accounts, review development activity, inspect configured build and test results, explore timelines and statistics, and manage Android companion devices.

### Poverview Android

The Android application is a read-only companion. It provides an overview of monitored projects, project details, recent activity, selected statistics, offline access to synchronized information, and pairing status.

Android is not intended to edit repositories, trigger builds, merge pull requests, or administer projects.

## Principles

1. Local-first, not cloud-dependent.
2. Local repositories are first-class projects; GitHub is optional.
3. Android is read-only; desktop remains the management surface.
4. Consent is required before executing project commands.
5. Every collected fact should identify its source and update time.
6. Local networking must use authentication and encrypted transport.
7. Deliver a useful personal workflow before attempting team collaboration.

## Audience and sequencing

The initial audience is an individual developer monitoring their own projects. The architecture should not block future team workflows, but team collaboration is not an MVP requirement.

## Initial non-goals

- Replacing GitHub, GitLab, or other hosting platforms.
- Building a full issue tracker or code review interface.
- Remote code editing or terminal access from Android.
- A mandatory hosted backend or subscription.
- Automatic execution of arbitrary project scripts.
- Guaranteed instant Android notifications while the app is closed.
- Full remote multi-user collaboration in the first release.

## Success criteria

The first useful release should let a developer add local repositories, see meaningful Git state in one place, optionally connect GitHub, and view a synchronized read-only subset on Android over a trusted local network.
