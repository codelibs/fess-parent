# CLAUDE.md

Guidance for Claude Code when working in this repository.

## What This Repository Is

`fess-parent` is the Maven parent POM for [Fess](https://fess.codelibs.org/) and its ecosystem. It contains **no source code** — the whole project is a single `pom.xml` (packaging `pom`) that centralizes:

- Dependency version management, exposed as `*.version` properties
- Maven plugin management (pinned plugin versions and shared configuration)
- Build conventions: Java 21, UTF-8, license-header enforcement, code formatting, GPG signing, and Maven Central publishing

The Fess modules (`fess`, `fess-crawler`, `fess-suggest`, `fess-ds-*`, `fess-webapp-*`, `fess-llm-*`) declare this POM as their parent and inherit the above.

## Working on This Repository

- Almost every change is an edit to `pom.xml` — usually bumping a version property or a managed plugin version.
- Version properties live under `<properties>` and are grouped by comment (Framework, Crawler, Suggest, Fesen, OpenSearch, Tomcat, Partner Library, Testing). Add or edit entries in the matching group.
- When bumping Fess module versions (`fess.version`, `crawler.version`, `suggest.version`, and related), keep them consistent with the release line being targeted.
- Do not add source directories or change `<packaging>` — this project intentionally ships only the POM.

## Validate

```bash
# Validate and install the POM into the local Maven repository
mvn clean install
```

There are no tests in this repository. A version bump is ultimately validated by building a consuming module (for example `fess`) against the locally installed parent.

## Conventions

- Use conventional commit messages (e.g. `chore(deps): bump <artifact> to <version>`).
- Keep each pull request focused on one logical change, such as a single dependency or plugin bump.
- Snapshot dependencies resolve from the CodeLibs and Central Portal snapshot repositories configured in the POM; released artifacts come from Maven Central.
