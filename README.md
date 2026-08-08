# Fess Parent POM

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Maven Central](https://img.shields.io/maven-central/v/org.codelibs.fess/fess-parent?label=Maven%20Central)](https://central.sonatype.com/artifact/org.codelibs.fess/fess-parent)

The Maven parent POM for [Fess](https://fess.codelibs.org/) (Full tExt Search System) and its related modules. It centralizes dependency version management, plugin configuration, and build conventions so that every project in the Fess ecosystem builds consistently.

## Overview

`fess-parent` is a `pom`-packaging project with no source code of its own. Modules across the Fess ecosystem — the main application, crawler, suggest, and the various data store and web application plugins — declare it as their parent to inherit:

- Managed versions for the framework, search engine, and third-party libraries used throughout Fess
- A shared set of Maven plugins pinned to known-good versions
- Common build settings such as the Java release level, source encoding, license-header enforcement, and code formatting
- Artifact signing, plus the `scpexe` wagon used to publish releases to the CodeLibs Maven repository

Keeping these definitions in one place ensures compatible versions across modules and reduces the effort of upgrading dependencies.

## Requirements

- Java 21 or later
- Maven 3.8 or later

## Usage

Declare `fess-parent` as the parent of your module:

```xml
<parent>
    <groupId>org.codelibs.fess</groupId>
    <artifactId>fess-parent</artifactId>
    <version>15.7.0</version>
    <!-- Refer to the Maven Central badge above for the latest release -->
</parent>
```

Dependency and plugin versions are exposed as Maven properties (for example `${lastaflute.version}`, `${opensearch.version}`, and `${tika.version}`), so child modules can reference the managed versions directly.

### Snapshots

Snapshots of `fess-parent` itself are published to the Central Portal snapshot repository; snapshots of the modules that inherit from it are published to the CodeLibs snapshot repository. Both, along with the CodeLibs release repository, are already configured in this POM, so child modules resolve them without extra setup.

## Build

Because this is a parent POM, building it simply installs the POM into your local repository:

```bash
# Install the POM into the local Maven repository
mvn clean install

# Deploy to the remote repository (maintainers only)
mvn clean deploy
```

The plugin and build configuration defined here (compiler, Surefire/Failsafe, JaCoCo, license, formatter, and others) takes effect in the child modules that inherit from this POM, not in `fess-parent` itself.

## What This POM Manages

- **Framework**: LastaFlute, Lasta Di, DBFlute, MailFlute
- **Search engine**: OpenSearch and the OpenSearch runner
- **Fess modules**: crawler, suggest, and the Fesen HTTP client
- **Runtime**: Tomcat and its boot integration
- **Libraries**: Apache Tika, PDFBox, POI, Lucene, Jackson, Guava, Log4j, and many more
- **Testing**: JUnit 4, JUnit Jupiter, and UTFlute
- **Plugins**: the Maven plugins used to compile, test, format, license-check, sign, and publish Fess modules

## Release

Releases follow semantic versioning (`major.minor.patch`) and are produced with the Maven Release Plugin:

1. Artifacts are signed with GPG under the `release` profile.
2. `fess-parent` itself is published to Maven Central through the Central Publishing Plugin. It stays there deliberately: a parent POM can only be fetched from repositories the consuming project already knows about, so keeping it on Maven Central lets every child — including third-party plugins — resolve it without configuring an extra repository first.
3. Every module inheriting from this POM publishes to the CodeLibs Maven repository over `scpexe`, using the `distributionManagement` declared in its own POM.

## Contributing

Contributions are welcome. A typical workflow:

1. Fork the repository and create a topic branch.
2. Make your change — for a version update, edit the relevant property in `pom.xml`.
3. Verify the POM builds with `mvn clean install`.
4. Open a pull request with a clear description of the change.

Please use conventional commit messages and keep each change focused.

## Related Projects

- [Fess](https://github.com/codelibs/fess) — the main full-text search server
- [Fess Crawler](https://github.com/codelibs/fess-crawler) — web, file system, and data store crawler
- [Fess Suggest](https://github.com/codelibs/fess-suggest) — search suggestion library

## Support

- Documentation: https://fess.codelibs.org/
- Issues: https://github.com/codelibs/fess/issues
- Discussions: https://discuss.codelibs.org/

## License

Licensed under the [Apache License, Version 2.0](LICENSE).
