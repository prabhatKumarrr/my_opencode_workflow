# AGENTS.md — My Custom Workflow Protocols

Reusable rules only; project state belongs in existing project docs and OpenSpec artifacts. Do not assume a framework or deployment model.

## 1. Scope and Safety

- Follow higher-priority instructions, explicit user scope, and applicable nested `AGENTS.md` files. Inspect before editing; preserve architecture, contracts, conventions, and user changes.
- Edit only authorized files. This includes generated outputs, council notes, glossary references, and skill preferences; ask before expanding scope, even when a skill requires them.
- Ask before broad refactors, deletions, dependencies, database/migration changes, auth/payment changes, breaking APIs, production operations, secrets/environment edits, or unrelated external access.
- Never expose secrets or sensitive data, hardcode credentials, discard user work, rewrite history, or automatically stash.
- Commits, branches, worktrees, merges, pushes, PRs, and integration installation/configuration require explicit authorization. A skill's commit instruction requests a checkpoint; it does not authorize one.

## 2. Start and Authority

- Read `README.md`, `openspec/config.yaml`, relevant local instructions, and `PROJECT_NOTES.md` if present. Check git status/current branch; distinguish pre-existing changes.
- Discover commands/environment from project manifests, CI, and docs. Do not import another project's assumptions or migration policy.
- For OpenSpec work, resolve the root, selected change, relevant main specs, and dependencies through the CLI. Use returned paths/store scope; do not initialize or repair setup implicitly.
- Configuration owns schema/rules/stack; schema and CLI instructions own artifact structure/readiness; main specs own consolidated intended behaviour; active changes own deltas/design/tasks; top-level `adr/` owns durable decisions; glossaries own terminology.
- Read dependencies from disk. Surface conflicts between these sources and actual code/tests; file existence, main specs, and archive are not proof of correctness.
- Load applicable local skills; follow their detailed procedures rather than duplicating them here. Disclose unavailable tools/agents and ask before substitutions. Guidance cannot bypass permissions or workflow gates.

## 3. Intent-Driven Lifecycle

`explore -> proposal -> specs -> design -> adr -> tasks -> apply -> verify -> sync -> archive`

This is the review sequence; actual dependencies and conditional artifacts come from the selected schema/CLI. Current skill routing is configured in `openspec/config.yaml`:

| Stage | Skills |
| --- | --- |
| Proposal | `grill-me`, `adversarial-authoring`, `glossary` |
| Specs / tasks | `spec-as-source`; `gherkin-authoring` for scenarios |
| Design | `c4-diagrams`, `glossary` |
| ADR | `architectural-decision-records` |
| Implementation / acceptance | `test-driven-development` / `acceptance-test-authoring` |
| Git lifecycle | `openspec-git-discipline` |

- Explore does not implement; confirm before capturing files. Propose stops after planning and waits for a separate implementation request. Continue creates the next artifact; update reconciles existing artifacts with confirmation.
- Resolve consequential ambiguity before planning completion. Ask one focused question at a time; inspect discoverable facts first.
- Honor required council notes/glossary companions and C4 preference gates within authorized scope. Do not claim cross-model review without distinct configured models.
- Read in-force ADRs through `Supersedes:` links. Accepted ADRs are immutable; replace decisions with new numbered top-level ADRs. Each change needs its own `adr.md` review manifest, even when no new decision qualifies. Resolve unset/incompatible ADR style before drafting.

## 4. Spec-As-Source and Zone Isolation

- While enabled, follow `spec-as-source` reference templates over schema defaults: Markdown requirement/scenario headings, column-zero Gherkin fences containing steps—not structural Gherkin declarations. Specs describe observable behaviour; preserve capability paths and complete MODIFIED blocks.
- `spec.md` is canonical; never hand-edit/commit extracted features or reports. Plan acceptance work before implementation. Confirm/record the acceptance stack before scaffolding; never guess.
- Before editing, check `git status --porcelain`: changes under `openspec/` select the specs zone; outside it select the code zone. Any `tasks.md` is neutral. Never mix zones in uncommitted work or a commit; request commit/stash authorization before crossing.
- Top-level ADRs, glossaries, and skill preferences are code-zone paths even during planning. Split checkpoints accordingly. Stop for pre-existing mixed-zone changes; do not reorganize user work.
- Implement only behaviour described by an active change. Missing requirements/design conflicts require plan reconciliation, not silent scope changes. Clarify exceptions for documentation/tooling work rather than inventing requirements or disabling rules.
- Require a green effective acceptance suite before sync/archive: main specs plus active deltas, no archived/superseded scenarios, no pending/undefined steps, required HTML report. Sync/archive must preserve results.

## 5. Git Gates and Verification

- Use `openspec-git-discipline`: prefer `main` for propose (confirm otherwise); request continue checkpoints; verify exact planning state is committed on `main` before apply, including from branches/worktrees.
- Verify before merge. Archive only on `main` after implementation is committed/merged there and zone checkpoints are satisfied. Sync inline, verify integration, then archive; report absent/already-synced deltas accurately. Request the final archive/spec commit.
- Bulk operations need explicit selection, installed support, per-change gates, and conflict checks; documentation mentions alone do not establish availability.
- Use strict red-green-refactor with existing tooling: confirm the intended failure, implement minimally, rerun tests, refactor on green. Mock external boundaries; mark tasks done only after full completion.
- During apply, always load `.agents/skills/ponytail/mode.md` and apply the ponytail skill at that level to every code change; it is not used for planning artifacts. Run `ponytail-review` for implemented code and `ponytail-audit` when whole-repo optimisation is requested.
- Delegate only when requested or required by a skill/workflow; use `senior-dev`/`senior-qa` when appropriate, with explicit scope and zone isolation. The primary agent owns integration/evidence.
- Run relevant tests, acceptance/lint/type checks, `git diff --check`, and strict OpenSpec change validation for behaviour changes. Report actual results, unrun/blocked checks, changed files, limitations, and next checkpoint. Never fake success; advisory verify does not replace tests or git gates.

## 6. Extension Points

- **Project-specific rules:** Add approved commands, protected modules, API conventions, migration policy, and deployment/access boundaries here; unknowns require discovery/clarification.
- **Plugins:** Verify configuration and runtime availability; reference canonical instructions instead of duplicating them. No integration may broaden scope, bypass gates, or replace canonical state. Resolve overlaps before use; no automatic indexes/services/accounts.
- **CodeGraph (optional):** If indexed and available, use `codegraph_explore` or `codegraph explore "<question>"` first for code understanding; verify against source. Otherwise use repository search. Never initialize/rebuild automatically.
- **Future integration entry:** `<name> | activation evidence | trigger | instruction path | permissions | fallback`. Add only with approval.
