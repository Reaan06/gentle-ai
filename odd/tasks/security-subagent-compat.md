# security-subagent-compat

## Goal
Add `gentle-ai-security` subagent compatibility across supported Gentle AI agent runtimes, including OpenCode background subagents, and document/publication workflow through an issue and reviewable PR slices if the implementation exceeds 400 changed lines.

## Acceptance Criteria
- `gentle-ai-security` is bundled for every supported agent runtime that has subagent/agent asset support.
- OpenCode installs/syncs `gentle-ai-security` alongside `gentle-ai-explore`, `gentle-ai-worker`, and `gentle-ai-verify` where background subagents are enabled.
- The security agent explicitly accepts Gentle AI package context and can be routed by orchestrator instructions for attack-surface/Sec-TDD work.
- Tests verify embedded assets and runtime-specific manifests/config outputs include the security agent.
- A GitHub issue describes the specification and planned work; PR delivery is split if the final authored diff exceeds 400 changed lines.

## Tasks
- [x] Map current subagent asset architecture and identify runtime gaps.
- [x] Create/update issue with specification and implementation plan.
- [x] Add `gentle-ai-security` assets for applicable runtimes.
- [x] Wire catalogs/manifests/config generation so the agent is installed/synced.
- [x] Add or update tests covering asset inclusion and OpenCode compatibility.
- [x] Run focused verification and assess changed-line budget for PR slicing.
- [x] Deliver a dependent feature-branch chain with scoped checks and issue linkage.

## Evidence
- Branch: `feat/security-subagent-compat`
- Issue: https://github.com/Gentleman-Programming/gentle-ai/issues/5176
- Delivery strategy: feature-branch chain selected by user. Tracker from `main`; OpenCode child targets tracker; native-agent child targets OpenCode child. Each PR stays below 400 changed lines.
- Candidate scope: 404 authored diff lines including this feature document (53 tracked changes, 325 new agent assets, 26 document lines before this update); recount each slice before publishing.
- Commits: tracker `a0db5bfc7b85d68b23456d9b2d74f12d61c2de70`; OpenCode slice `313d5399cc9238a13f69c644045f197a0cadf7c3`; native slice `803c0e8494131dbb2918cdb069cb139363d175f7`, `0617968f`, `02bee07f` (plus this evidence update).
- PRs: tracker https://github.com/Gentleman-Programming/gentle-ai/pull/5177 (29 lines); OpenCode https://github.com/Reaan06/gentle-ai/pull/1 (83 lines); native https://github.com/Reaan06/gentle-ai/pull/2 (305 lines before this evidence update). Child PRs live in the fork because upstream push permission is unavailable.
- Verification: focused OpenCode install, native agent, asset, model picker, and OpenCode tests; `go build ./...` and `go run ./internal/gofmtcheck` passed after formatting. Broad `TestSync` timed out at 120s during an external Codex version probe; full `go test ./...` and Docker E2E not run.
- Issue creation: confirmed read-back from target host; `status:approved` absent. User explicitly requested opening PRs regardless; tracker blocked. Upstream `type:docs` label could not be applied (permission denied); fork children have `type:feature`.
- Native review: inspected candidate, but no approved review authority or receipt was obtained; do not claim native review closure.
