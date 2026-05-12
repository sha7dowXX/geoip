---
name: update-go-dependencies
description: Workflow command scaffold for update-go-dependencies in geoip.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /update-go-dependencies

Use this workflow when working on **update-go-dependencies** in `geoip`.

## Goal

Update Go module dependencies to newer versions.

## Common Files

- `go.mod`
- `go.sum`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit go.mod and go.sum to update dependencies
- Commit changes with a message indicating dependency update

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.