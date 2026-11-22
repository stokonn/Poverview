# Release process

## Current status

Poverview is in its planning and foundation phase and has no application release yet. This document defines the intended release conventions; it does not imply that packaging, automated publishing, or release automation exists.

## Versioning

Use Semantic Versioning (`MAJOR.MINOR.PATCH`) once the project has a versioned application or other explicitly versioned deliverable.

- **MAJOR** for incompatible changes to a published public interface or data/protocol contract.
- **MINOR** for backward-compatible functionality.
- **PATCH** for backward-compatible fixes.

Use a leading `v` for Git tags, for example `v1.2.3`.

For pre-release versions, use SemVer identifiers such as:

- `v0.1.0-alpha.1`
- `v0.1.0-beta.1`
- `v0.1.0-rc.1`

Pre-releases are not stable releases. Do not remove the pre-release designation until the release criteria for a stable version are satisfied.

## Release types

- **Development snapshot:** work in progress; not presented as a supported release.
- **Pre-release:** explicitly marked alpha, beta, or release candidate; intended for evaluation and feedback.
- **Stable release:** published only after the relevant release checklist is complete and known limitations are documented.

Git tags must be immutable once published. If a release needs correction, publish a new version rather than moving an existing tag.

## Release notes

Each GitHub Release should include:

- The version and release type.
- A concise summary of user-visible changes.
- Important fixes and known limitations.
- Compatibility or migration notes where relevant.
- Installation or upgrade instructions once distributable artifacts exist.
- Links to the relevant changes or pull requests.

Do not claim that a feature, platform, or test configuration is supported unless it has been verified.

## Release checklist

Before publishing a pre-release or stable release:

- [ ] Confirm the target commit is the intended reviewed commit.
- [ ] Confirm the version and tag follow the versioning convention.
- [ ] Review the changes since the previous release or baseline.
- [ ] Run the validation relevant to the deliverable and record the results.
- [ ] Review privacy, security, and credential-handling implications.
- [ ] Update user-facing documentation and known limitations.
- [ ] Prepare accurate release notes.
- [ ] Verify that attached artifacts, if any, are the intended files.
- [ ] Mark pre-releases explicitly as pre-releases.
- [ ] For a stable release, confirm that the supported-platform and release criteria have been met.

Skip checklist items only when they genuinely do not apply, and explain why in the release notes or release record.

## Automation

Release automation is not currently configured. Do not assume that pushing a tag automatically builds, signs, or publishes Poverview. Any future automation must be documented and must not expose signing keys, credentials, or private project data.
