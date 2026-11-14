# Changelog

All notable changes to this project are documented here.
The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and the project uses [Semantic Versioning](https://semver.org/).

## [1.0.2] - 2026-11-14

### Added
- `SKILL.md`: **Plan compatibility (Free, Pro, Max, Team)** section. The skill checks which tools it actually has and says which fallback it uses; no web search → licence "not checked" with the official register link, best verdict `Suspicious`, no rate or official figure from memory, asks the user to paste the official page or rate. Lite mode for Free usage limits: shortest useful answer, one section per message, then "more?".
- `evals/evals.json`: new cases for lite mode and the no-web / no-code fallback.

## [1.0.1] - 2026-11-11

### Fixed (blind eval round 1)
- The first line is one single next action: one step, never two joined by "and" / "və" / "и".


## [1.0.0] - 2026-11-11

### Added
- First release: `SKILL.md`, `references/`, `evals/evals.json`, Agensi build script (`scripts/build-agensi-zip.ps1`) and listing texts (`LISTING.md`).
