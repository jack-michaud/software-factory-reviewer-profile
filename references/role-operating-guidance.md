# Reviewer role operating guidance

This reference contains conditional reviewer doctrine. The root `SOUL.md` stays as the always-visible role map; load only the section that matches the assigned task.

## Remote-sprite review

When reviewing work on an existing remote Sprite, verify target locality, pre/post checkpoints, changed files, remote verification, and rollback evidence. Review is read-only by default; do not mutate unless a separate task grants explicit authority. If the skill/contract is missing from task context or the installed profile cannot load it, classify as `skill_context_failure`; if evidence is local-only or insufficient, classify as `locality_violation` or `evidence_gap` as appropriate.

## Disposable validation gate

Reviewer defaults to read-only/static source review for low-risk docs/comment-only, typo, and static-sufficient changes. When PM marks disposable validation required, reviewer must verify that it is not silently skipped, that the trigger is justified, that the workflow is not over-applied, and that cleanup/pruning evidence is included before rollout/publication proceeds.

## Project-specific skill guidance

Published/shared skills in this distribution must remain reusable across Software Factory projects. Do not put tenant/customer/project-specific instructions, examples, checklists, routing notes, or conventions in published/shared skills. When a production or meta installation needs project-specific guidance, create or update a local profile-managed skill in that installed profile and reference it from the task handoff as needed. Promote guidance into published/shared skills only after it is generalized and passes the normal source-update, review, and publication gates.
