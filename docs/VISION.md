# Product vision

**Status:** Product direction. See [Product philosophy](PRODUCT_PHILOSOPHY.md) for the decisions explicitly confirmed so far and the questions that remain open.

## Definition

Poverview is a local-first project companion that helps an individual developer keep track of multiple software projects and remember where they left off.

Its promise is:

> **Never lose your place.**

Poverview connects the developer's existing tools and project repositories. It is not intended to replace an IDE, terminal, Git client, or hosting platform.

## The problem

When a developer works on several projects and switches between them, context gets lost. Returning to a project means reconstructing what happened, what remains unfinished, and what the next step should be.

Poverview reduces that friction through automatic activity collection, a unified overview, an activity timeline, and a project-level Resume Point.

## Product experience

The product brings together three complementary views:

- An overview of all tracked projects and their known state.
- A timeline of activity across projects.
- A project context view that explains where work was left and how to resume.

The Resume Point is central. It combines observed information from local Git and optional integrations with user-authored notes and next steps. It updates automatically when useful facts arrive, but the user can always edit or replace it. Poverview must distinguish facts from inference.

The experience should be a quiet hybrid companion: unobtrusive during normal work and useful when opened, with notifications only when they add value.

## Scope and audience

The initial audience is an individual software developer. The first version focuses on software projects and local Git repositories, whether or not they have a GitHub remote. GitHub integration is optional.

The longer-term vision may extend to other technical projects such as electronics, homelabs, Raspberry Pi/ESP32 work, and 3D printing/CAD. This is not required for the first version.

## Device model

The intended product has a Linux desktop application and an Android companion.

Desktop is the primary device because it has access to the user's project workspace and local repositories. Android is not read-only: it keeps a local copy of synchronized project metadata and context and can edit supported notes and Resume Points.

Both devices may make changes. Desktop has primary status, but synchronization must preserve Android edits and must not silently discard conflicts.

## Local-first and privacy

Poverview does not depend on a Poverview-operated cloud backend or mandatory account. Devices synchronize directly when reachable, initially over a trusted LAN and potentially over a user-managed VPN such as Tailscale.

Android retains the last synchronized information for offline use and catches up when the desktop becomes reachable again.

Project source code stays on the desktop and is not copied to Android. Synchronization is limited to project metadata, Git activity, history, notes, Resume Points, and other explicitly supported context. Communication must be authenticated and encrypted.

Local persistence, for example with SQLite, is expected and is not a hosted backend.

## Automation and user control

Core functionality should use understandable deterministic mechanisms rather than depend on an LLM or hosted AI service. Automation should reduce manual work, not pretend to know more than the available evidence supports.

Poverview may surface inactivity or suggest lifecycle changes, but the user decides whether a project is active, paused, archived, or completed. No lifecycle change should happen automatically based only on inactivity.

## Initial non-goals

- Replacing the developer's existing tools or workflow.
- A mandatory cloud service, hosted backend, or account.
- Requiring AI/LLM functionality for core features.
- Synchronizing source-code contents to Android.
- Automatically executing arbitrary project scripts.
- Automatically pausing, archiving, completing, or deleting projects.
- Building team collaboration as a first-version requirement.

## Success criteria

The first useful release should let a developer select a project workspace, discover and track local Git repositories, optionally connect GitHub, understand activity across projects, and reliably resume work from a useful editable Resume Point. An Android companion should retain synchronized context offline and safely exchange edits with the desktop over a direct encrypted connection.
