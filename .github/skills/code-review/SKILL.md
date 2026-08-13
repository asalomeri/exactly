
# Code Review Skill

## Purpose
Provides guidance for reviewing pull requests in this repository, ensuring code quality, security, and consistency with Go best practices.

## When to Use
- Reviewing incoming pull requests before merge.
- Auditing code changes for correctness, security, and style.

## Guidelines

### Go Conventions
- Follow standard Go formatting (`gofmt`, `go vet`).
- Prefer clear, idiomatic Go over clever abstractions.
- Check error handling: errors must be checked and wrapped with context (`fmt.Errorf("...: %w", err)`).
- Avoid unnecessary interfaces; keep them small and purposeful.

### Security
- Flag any hardcoded secrets, tokens, or credentials.
- Verify input validation on external/user-provided data.
- Check for proper handling of concurrency (goroutines, channels, mutexes) to avoid race conditions.
- Confirm dependencies are pinned and reviewed (see `.github/dependabot.yml`).

### Testing
- New logic should include corresponding unit tests.
- Verify edge cases and error paths are covered.
- Ensure tests pass in CI before approval.

### Structure & Readability
- Check for consistent package organization.
- Flag overly large functions/files that should be split.
- Ensure exported functions/types have doc comments.

## Review Checklist
- [ ] Code builds and passes CI (including CodeQL scanning)
- [ ] No hardcoded secrets or sensitive data
- [ ] Tests added/updated for new behavior
- [ ] Error handling is explicit and contextual
- [ ] Code follows Go formatting/linting standards
- [ ] No unresolved TODOs without tracking issues
