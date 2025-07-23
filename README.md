# Fess Parent POM

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/org.codelibs.fess/fess-parent/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.codelibs.fess/fess-parent)

A Maven parent POM that centralizes dependency version management for the Fess (Full tExt Search System) ecosystem.

## Overview

The `fess-parent` project serves as the central dependency management hub for all Fess-related libraries and applications. It provides consistent versioning across the entire Fess ecosystem, ensuring compatibility and simplifying maintenance.

**Fess** is a powerful, user-friendly full-text search server built on top of OpenSearch. It provides a comprehensive search solution with web crawling capabilities, making it easy to search across websites, file systems, and databases.

## Key Features

- **Centralized Dependency Management**: Manages versions for 50+ dependencies
- **Java 21 Support**: Built with modern Java standards
- **OpenSearch 3**: Latest search engine capabilities
- **Maven Plugin Management**: Pre-configured plugins with optimal settings
- **License Management**: Automated Apache License header management
- **Code Formatting**: Consistent code style across projects

## Usage

### As a Parent POM

Add this as your parent POM in your project's `pom.xml`:

```xml
<parent>
    <groupId>org.codelibs.fess</groupId>
    <artifactId>fess-parent</artifactId>
    <version>15.2.0-SNAPSHOT</version>
</parent>
```

## Development

### Prerequisites

- Java 21 or higher
- Maven 3.6 or higher

### Building

```bash
# Clean and compile
mvn clean compile

# Install to local repository
mvn clean install

# Deploy to remote repository (maintainers only)
mvn clean deploy
```

### Code Quality

```bash
# Format code
mvn formatter:format

# Check/add license headers
mvn license:check
mvn license:format

# Generate test coverage reports
mvn clean test jacoco:report
```

### Testing

```bash
# Run unit tests
mvn test

# Run integration tests
mvn failsafe:integration-test

# Run all tests with coverage
mvn clean verify
```

## Maven Plugin Configuration

This parent POM provides optimized configurations for:

- **Compiler Plugin**: Java 21 with UTF-8 encoding
- **Surefire/Failsafe**: Test execution with proper isolation
- **License Plugin**: Automated Apache license header management
- **Formatter Plugin**: Consistent code formatting
- **GPG Plugin**: Artifact signing for releases
- **Central Publishing**: Maven Central deployment

## Repository Structure

```
fess-parent/
├── pom.xml           # Main parent POM
├── README.md         # This file
└── LICENSE           # Apache License 2.0
```

## Release Process

This project follows semantic versioning and uses the Maven Release Plugin:

1. All artifacts are signed with GPG
2. Released to Maven Central via Central Publishing Plugin
3. Follows the pattern: `major.minor.patch`

## Contributing

We welcome contributions! Please follow these guidelines:

### Prerequisites

- Fork the repository
- Create a feature branch
- Follow existing code style and conventions

### Development Workflow

1. **License Headers**: Ensure all Java files have proper Apache license headers
   ```bash
   mvn license:format
   ```

2. **Testing**: Add tests for any new functionality
   ```bash
   mvn test
   ```

### Submitting Changes

1. Ensure all tests pass
2. Follow conventional commit messages
3. Create a pull request with a clear description
4. Address any feedback from code review

## Related Projects

- **[Fess](https://github.com/codelibs/fess)**: Main search server application
- **[Fess Crawler](https://github.com/codelibs/fess-crawler)**: Web crawling engine
- **[Fess Suggest](https://github.com/codelibs/fess-suggest)**: Search suggestion system

## Support

- **Documentation**: [https://fess.codelibs.org/](https://fess.codelibs.org/)
- **Issues**: [GitHub Issues](https://github.com/codelibs/fess/issues)
- **Discussions**: [Discussion Forum](https://discuss.codelibs.org/)

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

