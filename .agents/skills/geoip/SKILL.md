```markdown
# geoip Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill covers the development patterns and workflows used in the `geoip` Go codebase. It documents coding conventions, commit styles, and step-by-step guides for common repository workflows such as dependency updates, feature additions, bug fixes, and configuration changes. By following these patterns, contributors can maintain consistency and efficiency across the project.

## Coding Conventions

### File Naming

- Use **snake_case** for all file names.
  - Example: `lookup.go`, `merge.go`, `private.go`

### Import Style

- Use **relative imports** within the project.
  - Example:
    ```go
    import (
        "geoip/lib"
        "geoip/plugin/special"
    )
    ```

### Export Style

- Use **named exports** for functions, types, and variables that should be accessible outside their package.
  - Example:
    ```go
    // In lib/lookup.go
    package lib

    func LookupIP(ip string) (string, error) {
        // implementation
    }
    ```

### Commit Messages

- Follow **conventional commit** patterns.
- Prefixes: `feat`, `chore`, `fix`, `docs`, `release`, `refactor`, `refine`
- Example:
  ```
  feat: add support for new plaintext output format
  fix: correct CIDR parsing in private plugin
  ```

## Workflows

### Update Go Dependencies
**Trigger:** When you need to update project dependencies or bump library versions  
**Command:** `/update-deps`

1. Edit `go.mod` and `go.sum` to update dependencies.
2. Commit changes with a message indicating dependency update.
   - Example commit: `chore: update go module dependencies`

---

### Update GitHub Actions Workflow
**Trigger:** When you want to upgrade CI/CD workflow or fix build issues  
**Command:** `/update-ci`

1. Edit `.github/workflows/build.yml` to update actions or workflow logic.
2. Commit changes with a message indicating workflow update.
   - Example commit: `chore: update GitHub Actions workflow`

---

### Add or Refine CIDR List
**Trigger:** When you need to update IP ranges for providers or private networks  
**Command:** `/update-cidr`

1. Edit `config.json` or `plugin/special/private.go` to update CIDR/IP lists.
2. Commit changes with a message referencing the provider or private list.
   - Example commit: `refine: update Cloudflare CIDR ranges`

---

### Add New Command or Feature
**Trigger:** When introducing a new CLI command or significant feature  
**Command:** `/add-command`

1. Add new `.go` source files for the command/feature (e.g., `merge.go`, `lookup.go`, `plugin/...`).
2. Update `README.md` to document the new feature/command.
3. Edit or add related files (e.g., `config-example.json`, `lib/...`) as needed.
4. Commit changes with a relevant message.
   - Example commit: `feat: add merge command for IP lists`

---

### Fix Bug in Plugin or Lib
**Trigger:** When fixing a bug in data parsing or processing  
**Command:** `/fix-bug`

1. Edit plugin or lib source files to fix the bug (e.g., `plugin/*/*.go`, `lib/*.go`).
2. Commit with a message describing the fix.
   - Example commit: `fix: handle invalid IP input in parser`

---

### Add or Update Plaintext Format Support
**Trigger:** When improving or extending plaintext format handling  
**Command:** `/update-plaintext-format`

1. Edit `plugin/plaintext/*.go` to add or refine format support.
2. Update `config-example.json` if new options are added.
3. Commit with a message describing the plaintext format change.
   - Example commit: `feat: support custom suffix in plaintext output`

---

### Release Config and Workflow Update
**Trigger:** When releasing a new output type or changing output directory/configuration  
**Command:** `/release-config`

1. Edit `config.json` to update output options or directories.
2. Optionally edit `.github/workflows/build.yml` for build changes.
3. Commit with a message indicating a release or config update.
   - Example commit: `release: add new output directory for reports`

---

## Testing Patterns

- Test files follow the pattern `*.test.*`.
- The specific test framework is not identified, but standard Go testing conventions likely apply.
- Example test file: `lookup.test.go`
- Example test function:
  ```go
  func TestLookupIP(t *testing.T) {
      result, err := LookupIP("8.8.8.8")
      if err != nil || result != "Google" {
          t.Errorf("Expected Google, got %v, err: %v", result, err)
      }
  }
  ```

## Commands

| Command                    | Purpose                                                        |
|----------------------------|----------------------------------------------------------------|
| /update-deps               | Update Go module dependencies                                  |
| /update-ci                 | Update GitHub Actions workflow configuration                   |
| /update-cidr               | Add or refine CIDR/IP address lists                            |
| /add-command               | Add a new CLI command or major feature                         |
| /fix-bug                   | Fix bugs in plugin or library code                             |
| /update-plaintext-format   | Add or enhance plaintext input/output format support            |
| /release-config            | Release new output options or configuration changes            |
```
