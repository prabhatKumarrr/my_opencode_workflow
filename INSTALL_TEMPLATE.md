# Install Intent-Driven Workflow Template

This guide is for OpenCode installing this workflow into a new project or an
existing brownfield project. Installation transfers approved workflow files;
it does not implement product features or certify application correctness.

## 1. Scope and Safety

- Inspect the source and target before proposing writes.
- Preserve product code, tests, history, configuration and user-owned changes.
- Show the exact file plan and conflicts; obtain approval before writing.
- Follow applicable target and ancestor AGENTS.md instructions.
- Do not install dependencies, plugins, browser binaries or MCP servers.
- Do not modify secrets, environment files, databases or deployment settings.
- Do not commit, stash, create branches/worktrees, merge, push or create PRs
  without explicit approval.
- Do not overwrite directories wholesale or replace existing instructions.
- Do not run openspec init or openspec update implicitly.
- Stop for unresolved conflicts; do not invent a precedence decision.
- Installation/bootstrap is a tooling operation, not permission to implement
  behaviour without an active change.

This guide covers first-time adoption. Upgrades, migrations and shared-skill
repairs require a separately approved scope.

## 2. Select and Inspect the Source

Canonical source repository:

https://github.com/prabhatKumarrr/my_opencode_workflow

Prefer a user-selected local checkout when available. Confirm its path,
branch and working-tree state.

If no checkout is available, explain the source download/clone operation and
obtain approval before creating a checkout outside the target project.

An approved HTTPS clone command is:

```sh
git clone https://github.com/prabhatKumarrr/my_opencode_workflow.git <source-directory>
```

Replace the placeholder with the approved destination; never clone over the
target project or an existing directory.

Read the source README.md, AGENTS.md, openspec/config.yaml, schema, skills,
commands and agent definitions relevant to installation.

Record the source checkout and revision used in the installation summary.
If required files exist only as local modifications or untracked files,
explain that a fresh remote clone will not contain them. Ask whether to use
that local state or wait for an approved published source.

Do not assume that current upstream files match a reviewed local fork.

## 3. Inspect the Target

Determine whether the target is:

- A new empty project: workflow bootstrap only; no application scaffolding.
- An existing project: preserve its implementation and established tooling.
- An existing OpenSpec installation: reconcile rather than reinitialise.

Inspect, when present:

- README.md, AGENTS.md, PROJECT_NOTES.md and applicable nested instructions.
- Git root, branch, worktrees, status and existing untracked files.
- Product manifests, package manager, lockfiles, tests and CI.
- opencode.json, opencode.jsonc and .opencode configuration.
- Existing commands, agents, skills, plugins and MCP configuration.
- openspec/config.yaml or config.yml, local schemas, specs and changes.
- ADRs, glossaries, acceptance-tests/ and generated-output ignore rules.

Use read-only discovery first. Do not expose secrets while inspecting settings.

If the target has no Git repository, ask before git init. Do not assume its
initial branch is main. If main is absent or a different integration branch
is used, stop and obtain a decision about main setup or a separately approved
workflow adaptation. Never rename branches silently.

For an existing OpenSpec setup, resolve its actual root using the installed
CLI. Check registered-store selection when applicable. If the root is an
ancestor or external store rather than the intended target, stop and clarify
scope before creating a second root or editing shared planning files.

Check tool availability and versions without installing anything. The source
was reviewed with OpenSpec 1.15.0 and OpenCode v2.3.0; these are reference
versions, not proof that every older or newer release is compatible.

Missing or incompatible tools are blockers to runtime validation, not
permission to install or regenerate configuration.

## 4. Present the Installation Plan

Before editing, provide:

1. Source and target paths and source revision/state.
2. Target type, branch and resolved OpenSpec scope.
3. Exact files to add, merge, preserve or omit.
4. Configuration, skill-ID, command-name and agent-name conflicts.
5. Existing instructions that conflict with template gates.
6. Specs-zone/code-zone checkpoints and approvals needed.
7. Deferred project setup and validation limitations.

Read existing files before proposing their merge. Include JSONC as well as
JSON and alternative YAML filenames; do not create a competing configuration
file merely because one preferred filename is absent.

When rules conflict, show the conflict and ask the user. Do not silently
weaken target safeguards or template gates.

## 5. Approved File Manifest

Use this allowlist, expanded into exact paths during review.

| Source | Target action |
| --- | --- |
| AGENTS.md | Create if absent; otherwise merge all approved applicable protocols |
| openspec/config.yaml | Create or reconcile the target's existing configuration |
| openspec/schemas/intent-driven/** | Copy required schema and templates; review collisions |
| .opencode/commands/*.md | Add missing commands; review same-name definitions |
| .opencode/skills/** | Copy lifecycle/adversarial skills with supporting files |
| .opencode/agent/*.md | Copy compatible specialist definitions; review collisions |
| .agents/skills/** | Copy selected supporting skills with all required support files |
| opencode.json | Create only if no applicable config exists; otherwise reconcile intentionally |

Preserve complete skill directories, including references, templates, mode
and preference files. Do not copy only SKILL.md.

Keep local adaptations to Emil skills. Do not replace them with upstream
downloads or run third-party skill installers.

Do not transfer:

- Source .git, dependencies, caches, logs or generated outputs.
- Source product specs, active changes, archives, ADRs or glossary entries.
- Source application code, tests, credentials or machine-specific settings.
- Optional plugin examples as enabled configuration.

Create a local OpenSpec skeleton only when explicitly approved. An existing
target's specs, changes and architectural history remain its own.

README.md changes and copying explanatory notes require separate explicit
selection. These notes are optional documentation, not operating authorities.

Do not overwrite the target .gitignore with the source copy. Report missing
workflow-related ignore rules and request exact additions when needed.

## 6. Install Through Zone Checkpoints

Follow target rules and the template's specs/code isolation.

- Specs zone: non-tasks.md files under openspec/.
- Code zone: non-tasks.md files outside openspec/.
- Any tasks.md is neutral.

Before every edit batch, inspect git status --porcelain.

If pre-existing mixed-zone changes exist, stop and ask. Never reorganise,
stash, commit or discard them automatically.

Install one approved zone at a time. For a clean target, the normal sequence
is approved OpenSpec configuration/schema files first, then an authorised
checkpoint before code-zone instructions, skills, commands and agents.

Ask the user to commit or explicitly approve a stash before crossing zones.
Do not execute either operation without permission. A temporary exception,
if explicitly granted, applies only to its named scope; never infer one.

When merging AGENTS.md, preserve the complete approved operating protocol,
not just the OpenSpec git-discipline bullet. Confirm coverage of:

- Scope, safety, authority and permission boundaries.
- Intent-driven lifecycle and artifact-specific skill routing.
- Spec-as-source, acceptance-first work and zone isolation.
- Planning-on-main before apply and implementation-on-main before archive.
- Immutable accepted ADRs and glossary/council companion permissions.
- TDD, Ponytail mode and change-level frontend detection.
- OpenSpec verify, then Ponytail review, then conditional motion review.
- Conversation-only animation audits and no separate execute-plan workflow.
- Temporary worst-case toggle cleanup and scoped animation removal.
- Delegation restrictions and evidence/reporting requirements.

Do not enable Superpowers, Impeccable, taste-skill, Playwright or CodeGraph
as part of this installation. No plugin is enabled by the template config.

## 7. Reconcile Project Choices Without Guessing

Preserve the selected intent-driven schema and artifact rules unless the user
explicitly approves a different workflow. If the target already uses another
schema, show the difference and ask before changing its default.

The source enables:

- Proposal: grill-me, adversarial-authoring and glossary.
- Specs/tasks: spec-as-source and required Gherkin/acceptance subskills.
- Design: c4-diagrams and glossary.
- ADR: architectural-decision-records.
- Apply: TDD, Ponytail mode and frontend-gated Emil skills.
- Archive: inline sync subject to local git and acceptance gates.

Keep Frontend scope: yes | no | partial in task-authoring rules and preserve
the corresponding AGENTS.md path fallback. Backend-only work must not load
frontend craft skills.

Preserve Ponytail's recorded mode unless the user selects another.
Preserve the source's madr-minimal ADR preference only when it does not
conflict with an existing target preference; otherwise ask.

Check availability of the configured author and reviewer models. Different
agent names do not establish cross-model review. If a model is unavailable,
report it and ask before substituting or changing model configuration.

Do not change the target acceptance stack or scaffold acceptance-tests/
during file transfer. If already configured, preserve and assess it.
Otherwise record stack selection and setup as deferred project work.

For React/browser behaviour, explain the HTTP-only coverage boundary.
Playwright remains an optional, separately approved project integration;
it does not require a new acceptance stack value or a second runner.

## 8. Validate the Installed Wiring

Run only read-only checks available in the target environment:

```sh
git status --short
git diff --check
openspec schemas --json
openspec schema validate intent-driven
openspec list --json
openspec list --specs
```

Run OpenSpec checks in the confirmed planning root, carrying any supported
selected-store flags. Do not treat an ancestor/store root as the target root
without approval.

Also verify:

- Selected schema resolves to the intended local schema.
- Schema/templates and config rules agree with the approved workflow.
- Skill IDs are unique across relevant sources and support paths resolve.
- Commands and corresponding lifecycle skills remain consistent.
- Specialist agents are discoverable and their model choices are available.
- All required AGENTS.md gates survived the merge.
- Existing plugins, permissions, models, commands and settings were preserved.
- No product history, generated outputs or unintended files were copied.

In OpenCode, confirm command, agent and skill discovery after reload if
needed. Use supported runtime discovery; file existence alone is insufficient.

Explicitly load review-animations when the motion-review gate requires it.
OpenCode V2 supports disable-model-invocation: true, which hides automatic
advertising but still permits explicit skill loading.

Do not create a sample change, run authoring agents, start an application,
download browsers or generate acceptance output merely to claim installation
passed. Offer such smoke tests separately with their exact scope and effects.

If a required check is unavailable or fails, report installation as partial
or blocked. Do not claim end-to-end readiness from schema validation alone.

Known unresolved workflow defects must remain visible in the handoff.
Installation does not repair shared acceptance-composition logic. If the
selected source still has nested-capability collisions or duplicate active
ADDED scenarios after standalone sync, report those limitations and request
a separate repair before relying on the affected acceptance paths.

## 9. Handoff and First Use

Report:

- Source checkout/revision and whether local pending changes were used.
- Exact files added, merged, preserved and omitted.
- Resolved conflicts and decisions still needed.
- Validation commands/results and checks not run.
- Whether runtime discovery and both council models were confirmed.
- Pending zone/git checkpoints.
- Deferred acceptance setup, browser coverage and known limitations.

Distinguish "workflow files installed" from "application workflow verified".

For greenfield projects, start with an approved product change; include the
minimal application skeleton and acceptance setup in its tasks.

For brownfield projects, inspect existing behaviour, tests, specs and ADRs
before proposing a scoped change. Do not invent baseline specs or migrate
existing tests during installation.

Use /opsx-explore for investigation, /opsx-new plus /opsx-continue for
incremental planning, or /opsx-propose for a complete planning package.
Planning stops before implementation. A separate apply request and the
main/zone checkpoints are still required.

Bulk apply is invoked through openspec-bulk-apply-change; no corresponding
local slash command is bundled. Use it only for eligible independent changes
with explicit worktree approval and confirmed planning scope.

Before sync/archive, require the project's green effective acceptance suite,
zero pending/undefined steps and the required HTML report. Verify before
merge; archive only from main after implementation is committed/merged there.
Keep sync inline, verify integration and request the final commit.

Never turn an installation request into an automatic feature implementation,
test-framework migration, git operation or plugin installation.
