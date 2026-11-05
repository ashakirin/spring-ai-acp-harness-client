# Contributing to Spring AI ACP Harness Client

Thank you for contributing to the Spring AI Community. Contributions are governed by
the organization-wide [Code of Conduct](https://github.com/spring-ai-community/.github/blob/main/CODE_OF_CONDUCT.md).

## Before You Start

- Search existing issues and pull requests before opening a new one.
- Use an issue to discuss significant features or public API changes before investing
  in an implementation.
- Do not use public issues for security vulnerabilities. Follow [SECURITY.md](SECURITY.md)
  instead.

## Development

This project requires Java 21 or newer and uses the Maven Wrapper.

```bash
./mvnw clean compile
./mvnw clean test
```

Before submitting a pull request, apply the project formatter and run the complete test
suite:

```bash
./mvnw spring-javaformat:apply
./mvnw clean test
```

The modules are grouped by role: the library in `spring-ai-acp-harness-client`, agent adapters
under `runtimes/`, Boot support under `auto-configurations/` and `starters/`, the Spring AI
`ChatModel`, terminal console and MCP OAuth under `integrations/`, test support in
`spring-ai-acp-harness-client-test` and a sample under `samples/`. Every package of a published
module is `@NullMarked` and NullAway checks main code during compilation; a new package needs its
own `package-info.java`. Build with an OpenJDK 21 such as Temurin, as CI does.

JaCoCo runs during `verify` and writes coverage reports under `target/site/jacoco` per
module. Analyze dependency usage with `./mvnw dependency:analyze`; keep the declared
dependencies intentional.

The always-on suite is fast; the live-agent suites that spend real tokens are opt-in and
skip by default:

```bash
./mvnw test -Dspring-ai-acp-harness-client.test.live=true
```

Keep changes focused, add tests for changed behavior, and update documentation when a
change affects users.

The documentation lives in `docs/` and is built with MkDocs. To preview it:

```bash
pip install mkdocs-material mike
mkdocs serve
```

## Commits and Pull Requests

- Sign every commit with a verified signature.
- Use concise, imperative commit subjects.
- Keep history linear; rebase instead of adding merge commits.
- Submit changes through a pull request. Direct changes to `main` are not accepted.
- Ensure all required status checks pass.
- Confirm that your contribution is compatible with the Apache License 2.0.

By submitting a contribution, you agree that it may be distributed under this project's
[Apache License 2.0](LICENSE).
