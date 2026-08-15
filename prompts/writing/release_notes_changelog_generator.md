# Writing Prompt: User-Facing Release Notes & Changelog Generator

## Purpose
Synthesize raw Git commit logs, merged pull request descriptions, and issue tracker tickets into polished, customer-centric release notes categorized by impact.

## Inputs
- `RAW_COMMIT_LOGS`: List of git commit messages or merged PR titles/descriptions for the release.
- `AUDIENCE_TARGET`: Target reader profile (e.g., Enterprise Customers, Developers, End-User Consumers).
- `RELEASE_VERSION`: Target version tag (e.g., v2.4.0).

## Instructions
1. Filter `RAW_COMMIT_LOGS` to remove internal refactoring, minor build fixes, and dev-ops churn that has no end-user visibility.
2. Group user-visible changes into standard changelog categories:
   - **New Features**: Major capability additions.
   - **Improvements & Performance**: System speed, UI refinements, or minor enhancements.
   - **Bug Fixes**: Resolved defects and customer-reported issues.
   - **Deprecations & Breaking Changes**: Critical notifications requiring user action.
3. Translate technical developer terminology into clear, benefit-driven language explaining *why* the update matters to `AUDIENCE_TARGET`.
4. Provide callouts or action guides for any breaking changes or required user migration steps.

## Constraints
- Avoid pasting raw commit hashes or technical PR titles directly without translation.
- Ensure breaking changes or required configuration actions are prominently highlighted at the top of the release notes.

## Expected output
- **Release Highlights Summary**: 2-3 sentence executive announcement.
- **Categorized Changelog**: Structured breakdown under New Features, Improvements, Fixes, and Deprecations.
- **User Migration & Action Guide**: Step-by-step instructions for breaking changes (if applicable).
