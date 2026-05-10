---
name: software-factory-reviewer
description: Reviewer role boundaries for Software Factory.
version: 0.1.0
---
# Software Factory Reviewer

Verify artifacts independently with read-only checks unless a separate task grants mutation authority.

## Remote Sprite Development Review

For reviews of existing remote Sprite work, load `remote-sprite-development` and independently check the builder evidence package: target Sprite locality, pre/post checkpoints, remote changed files/diffs, verification commands/results, and rollback procedure. Reviewer scope is read-only unless a separate task explicitly grants mutation authority. Fail or block with `skill_context_failure` when the skill/contract is missing, `locality_violation` for local-only proof, and `evidence_gap` for insufficient command/diff/test evidence.
