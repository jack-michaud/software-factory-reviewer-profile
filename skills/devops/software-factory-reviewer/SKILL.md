---
name: software-factory-reviewer
description: Reviewer role boundaries for Software Factory.
version: 0.1.2
---
# Software Factory Reviewer

Verify artifacts independently with read-only checks unless a separate task grants mutation authority.

## Remote Sprite Development Review

For reviews of existing remote Sprite work, load `remote-sprite-development` and independently check the builder evidence package: target Sprite locality, pre/post checkpoints, remote changed files/diffs, verification commands/results, and rollback procedure. Reviewer scope is read-only unless a separate task explicitly grants mutation authority. Fail or block with `skill_context_failure` when the skill/contract is missing, `locality_violation` for local-only proof, and `evidence_gap` for insufficient command/diff/test evidence.

## Conditional disposable/test-profile validation review

Use read-only/static review by default. Low-risk docs/comment-only changes, typo fixes, and changes where acceptance criteria can be fully verified from public source diffs should remain static-review-only unless PM or the human explicitly requires disposable validation.

When PM requires disposable/test-profile validation, gate the source and handoff for all of the following:

- PM explicitly named the validation as required and identified the behavior-risk trigger.
- The trigger is appropriate: SOUL/profile behavior, skill behavior, Kanban protocol, profile install/delete/config/model/provider, role boundary, credential/env-var loading, remote-sprite workflow guidance, or prior production/meta failure.
- Disposable validation is not being over-applied to low-risk work without a reason.
- Builder/installer guidance uses randomly suffixed disposable profile names, canonical Hermes profile install/delete commands, non-secret evidence capture, and blocks rather than guessing on command shape or authority.
- PM-required validation is not silently skipped; unavailable validation must produce a blocked task/comment with concrete evidence.
- Cleanup/pruning is represented as a gated follow-up after rollout/docs evidence is preserved, unless explicit human retention is recorded.
- The chain limits repeated remediation to at most two iterations before orchestrator/human escalation.

Precedent checks: disposable install evidence should include root distribution metadata such as `distribution.yaml` verification when relevant and may use an approved fallback executable if the expected local Hermes wrapper is broken; evidence should name the fallback without leaking private state; approved non-secret disposable-validation artifacts should be preserved before cleanup; cleanup should use canonical profile deletion after rollout/docs evidence is preserved.


## Source-update review locality

For source-update reviews, verify against the PM Source Map and builder handoff. Inspect the named standard worktree/path, such as `/home/sprite/worktrees/<repo-name>/<task-id>-<short-slug>`, or the public remote coordinates named in the handoff. Do not use private installed profile state, secrets, logs, memories, raw Kanban databases/workspaces, or runtime profile directories as source truth.

Require evidence for repo URL, local repo/worktree path, branch, commit hash, changed files, diff or diff-stat, validation output, target-profile coverage, publish/push status, and whether superproject submodule pointers or generated profile repos changed. If commits are not pushed, require either an approved source-controlled patch/diff bundle or a PM-named reviewer-accessible standard local worktree path. Block with the exact missing public coordinate or unblock condition when source authority, path access, branch/worktree authority, or validation evidence is ambiguous.
