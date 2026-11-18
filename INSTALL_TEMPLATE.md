# Install Intent-Driven Workflow Template

This guide is for OpenCode installing this workflow into a new project or an
existing brownfield project. Installation transfers approved workflow files;
it does not implement product features or certify application correctness.

## 1. Scope and Safety

- Inspect the source and target before proposing writes.
- Preserve product code, tests, history, configuration and user-owned changes.
- Show the exact file plan and conflicts; obtain approval before writing.
- Follow applicable target and ancestor AGENTS.md instructions.
- Do not install dependencies, plugins, browser binaries or MCP servers except
  the CodeGraph components explicitly included in an approved installation plan
  under section 7.1. Default selection alone is not approval.
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
permission to install or regenerate configuration. The approved CodeGraph
setup in section 7.1 is the only installation exception in this guide.

For CodeGraph, distinguish CLI availability/version, effective OpenCode MCP
configuration/connection, and the target project's index root/health. Inspect
existing local and applicable global configuration without exposing secrets;
do not assume a CLI executable or .codegraph/ directory proves working setup.
Check that an ancestor or another worktree's index is not being mistaken for
this target's index.

If the target contains independent nested Git repositories, identify every
Git boundary and stop before assuming single-repository lifecycle semantics.

Present a separate multi-repository adaptation plan covering:
- Canonical planning-root/store resolution.
- Root versus child Git ownership and ignore rules.
- Per-repository integration branches, permissions and zone checkpoints.
- Task-to-repository mapping and worktree behavior.
- Per-repository CodeGraph indexes and verified query routing.
- Contract ownership, test ownership and revision-specific integration evidence.

Do not initialize parent Git, remove child OpenSpec roots, create submodules
or rewrite reusable lifecycle skills implicitly. Installing files at a parent
directory does not establish safe multi-repository orchestration.

## 4. Present the Installation Plan

Before editing, provide:

1. Source and target paths and source revision/state.
2. Target type, branch and resolved OpenSpec scope.
3. Exact files to add, merge, preserve or omit.
4. Configuration, skill-ID, command-name and agent-name conflicts.
5. Existing instructions that conflict with template gates.
6. Specs-zone/code-zone checkpoints and approvals needed.
7. Deferred project setup and validation limitations.
8. CodeGraph, default-selected: detected state, components to reuse/install,
   exact commands and affected paths, installation location, telemetry choice,
   watcher/background-process effects, and any deferred indexing.

Wait for approval of this plan before installing, connecting or initialising
CodeGraph. The user may deselect it. Approval covers only the listed operations;
new writes, global changes or repair work outside that scope require approval.

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

### Bundled Skill Baseline

The source currently contains 35 skills. Include their complete directories
in the proposed file plan; do not silently omit a skill required by copied
configuration or lifecycle guidance.

| Group | Source | Skill IDs |
| --- | --- | --- |
| OpenSpec lifecycle | `.opencode/skills/` | `openspec-explore`, `openspec-new-change`, `openspec-propose`, `openspec-continue-change`, `openspec-update-change`, `openspec-apply-change`, `openspec-verify-change`, `openspec-sync-specs`, `openspec-archive-change`, `openspec-bulk-archive-change`, `openspec-bulk-apply-change` |
| Council | `.opencode/skills/` | `adversarial-authoring` |
| Planning, testing and Git | `.agents/skills/` | `grill-me`, `c4-diagrams`, `architectural-decision-records`, `gherkin-authoring`, `glossary`, `openspec-git-discipline`, `spec-as-source`, `acceptance-test-authoring`, `test-driven-development` |
| Ponytail | `.agents/skills/` | `ponytail`, `ponytail-review`, `ponytail-audit`, `ponytail-debt` |
| Frontend design and motion | `.agents/skills/` | `emil-design-eng`, `animate`, `gestures`, `choreograph`, `animation-performance`, `mobile-native`, `review-animations`, `improve-animations`, `break-ui`, `remove-animations` |

Confirm this inventory against the selected source revision. Counts are an
audit baseline, not a reason to delete or replace extra target skills.
Explain intentional omissions and resolve affected routing before installation.

Transfer all required references, scripts, templates and preferences.
Preserve Ponytail's recorded `full` mode and the selected ADR preference unless
the user approves a change. Do not add unbundled companion skills or plugins.

The source includes 10 command files and four specialist agent definitions.
Bulk apply has no bundled slash command. Skill names that resemble slash
commands do not prove that a command file exists.

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

Do not enable Superpowers, Impeccable, taste-skill or Playwright as part of this
installation. CodeGraph is default-selected but may be set up only through the
approved plan in section 7.1. It is a CLI/MCP integration, not an OpenCode plugin
entry; the base template config itself enables no plugin.

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

### Integration Status

| Component | Installation treatment |
| --- | --- |
| Bundled skills, commands and agents | Transfer approved files and verify discovery |
| OpenCode plugins | None enabled by the base source; preserve existing target configuration |
| CodeGraph CLI/MCP/index | Default-selected; execute only the approved operations in section 7.1 |
| Acceptance runner/dependencies | Defer unless already configured; establish through approved setup tasks |
| Playwright library or Test runner | Deferred project choice under section 7.2 |
| Playwright MCP | Separate optional agent-tool integration; not implied by browser testing |
| Superpowers | Not selected for automatic installation; separate compatibility review |
| Impeccable and taste-skill | Not selected or bundled |

Bundled skill examples do not authorize installing their example libraries.
Installing Markdown skills does not install test dependencies, browser binaries
or MCP servers. Global CLI availability and project-local configuration/index
scope must be assessed independently.

### 7.1 CodeGraph — Default-Selected, Approval-Gated Setup

Upstream: https://github.com/colbymchenry/codegraph

Include CodeGraph in every installation plan by default, but do not treat an
installation request or default selection as permission to execute its setup.
Perform this section only after the user approves the concrete operations.
Keep setup in the code-zone batch and respect all target permissions.

**Detect and reuse first**

A CLI available outside the target may be reused without reinstalling it in
every repository. Locate the resolved executable and inspect the relevant
package-manager installation only when needed; do not infer installation
scope from the directory in which setup was run.

Conversely, project-local CLI dependencies are possible. Preserve the target's
chosen installation/version policy; do not force a global installation.

Project-local MCP configuration and project-local graph state are separate
from CLI package scope. Do not promise that local installation keeps all
package caches, telemetry state or browser/tool artifacts inside the repo.

For multiple independent repositories, reuse the CLI and maintain separate
correct-project indexes unless a different indexing scope is explicitly
approved. Verify project selection for every MCP/CLI query. One working
backend MCP connection does not prove workspace-wide routing; use supported
explicit project selection, reviewed server entries or a verified CLI fallback.

- Locate the CLI and check its version and installed-version help.
- Inspect effective MCP configuration and runtime tool availability. Reuse a
  working global connection; do not create a duplicate project server.
- Confirm the actual code root, index location, version compatibility and health.
  Monorepos and worktrees may need separate indexes or explicit project paths.
- Do not copy the template's index, borrow another checkout's index, upgrade the
  CLI, rebuild an index or remove locks automatically.

Illustrative checks, when the installed version supports them:

```sh
codegraph --version
codegraph status <project-path> --json
```

Use the approved target path in place of the placeholder. Do not call status on
an unindexed project repeatedly. Where command telemetry has side effects, use
a reviewed per-process opt-out for discovery rather than silently enabling it.

| Detected state | Action after plan approval |
| --- | --- |
| Working CLI, MCP and correct healthy index | Reuse; no reinstall or rebuild |
| Working CLI/index, MCP unavailable | Use CLI fallback; configure MCP only if approved |
| CLI available, target unindexed | Initialise the approved code root |
| CLI missing | Install using the approved method/location, then configure/index |
| Index stale, incompatible or broken | Report; perform only the approved sync/repair |
| Empty greenfield project | Defer useful indexing until application source exists |
| Setup declined or unavailable | Use repository search; report CodeGraph as deferred/unavailable |

**Install only missing, approved components**

If the CLI is missing, agree on its installation method and location before
running a package manager or downloaded installer. Do not silently use npm -g,
pipe remote scripts into a shell, or modify application dependencies/lockfiles.
No Node.js, system-runtime installation or PATH/profile edit is implied.

Prefer a reviewed merge of the missing OpenCode MCP entry over a blind installer.
Use the current OpenCode configuration shape and installed CodeGraph command;
preserve JSONC comments, unrelated servers, permissions and custom launch flags.
Do not introduce a competing config file or override a working global server.

If using the upstream installer, review its current behaviour and exact writes
first. It can modify both OpenCode configuration and AGENTS.md. Scope it to
OpenCode and the project, never auto-detect/all agents or global defaults:

```sh
codegraph install --target=opencode --location=local
```

Do not add --yes or --init to bypass review. Its generated instructions must not
override source verification, delegation, git gates or permission boundaries.
If those writes cannot match the approved plan, stop and use a separately
reviewed configuration merge instead. Preserve the target's CodeGraph policy
without adding a duplicate or conflicting instruction block.

**Privacy, process and index scope**

Disclose anonymous telemetry: current upstream defaults it on. Ask the user to
choose a policy before setup; no choice means pause, not implicit consent.
Apply an approved opt-out to CLI setup and the MCP process if selected.
Prefer process/server-scoped configuration over changing a global preference;
never edit environment files or global telemetry settings without approval.

The graph database is local, but this does not make the whole workflow
network-free: installation downloads, telemetry and model-provider handling of
retrieved source are separate considerations.

Explain MCP watcher/daemon startup, incremental updates and disk/CPU costs.
Agree on exclusions for sensitive, generated, vendored and out-of-scope files;
do not expand indexing into ignored child repositories without approval.

For an unindexed project with useful source, an approved initialisation may use:

```sh
codegraph init <project-path> --local-only
```

Confirm the installed version supports --local-only and review resulting paths.
This keeps graph state local to Git; it does not make CLI installation
project-local. Preserve customised ignore/config files and inspect Git status
afterwards. Never commit database, cache or private graph artifacts.

In an empty greenfield project, record indexing as deferred. Arrange initial
indexing as an explicit approved task after the application skeleton exists;
do not create fake source or initialise repeatedly to claim useful coverage.

**Use without weakening workflow gates**

For indexed code, query the correct project through the available CodeGraph MCP
tool or codegraph explore first. Keep queries narrow to avoid large context
payloads; token savings are workload-dependent, not guaranteed.

Preserve AGENTS.md's source-verification rule. Check relevant live source before
consequential edits; do not repeat broad discovery unnecessarily. Read specs,
ADRs, instructions and non-indexed configuration directly. Treat graph edges as
best-effort structural evidence, not proof of requirements or runtime behaviour.

Check freshness warnings and fall back to direct reads for pending/uncovered
files. Auto-sync can lag and is not proof of complete coverage. Missing indexes,
failed tools or unavailable MCP must have a repository-search fallback.

Approval for initial setup does not permit automatic install/init/rebuild during
later queries. Refreshes outside the approved watcher behaviour require the
normal permission checks. CodeGraph never replaces TDD, the full required
acceptance suite, reviews, strict OpenSpec validation or git checkpoints.

### 7.2 Playwright — Deferred Target-Project Integration

Playwright is not part of the file-transfer installation. Do not install
packages, browser binaries, system dependencies or MCP servers here.

During assessment, identify:
- Whether required behavior needs a real browser.
- Existing browser tools, runners and CI coverage.
- Whether HTTP-only acceptance coverage misses client-side behavior.
- The owner of frontend/backend integration tests in multi-repo targets.

Record the coverage gap and deferred decision; do not silently claim browser
readiness from HTTP-client acceptance tests.

Distinguish three choices:
- Playwright library: browser automation used from an existing runner.
- Playwright Test: a separate test runner with its own lifecycle/configuration.
- Playwright MCP: agent-facing browser tools, not a repeatable acceptance suite.

For an approved JavaScript/Cucumber setup, the browser library can run through
Cucumber hooks and page objects without introducing a new stack value or a
second runner. Existing HTTP-oriented World/page-object guidance must be
explicitly reconciled for browser work; it is not a ready-made browser adapter.

Any later setup plan must name:
1. Dependency owner, package/lockfile changes and selected versions.
2. Browser binaries, download/cache locations and any system dependencies.
3. Application startup/readiness/teardown and relevant portal/API origins.
4. Browser/context lifecycle, per-scenario isolation and cleanup.
5. Test accounts, authorization boundaries and non-production test data.
6. Page-object and step-definition responsibilities.
7. Explicit timeouts, asynchronous assertions and failure diagnostics.
8. Required acceptance HTML report plus approved traces/screenshots/video,
   with sensitive-data handling, ignore rules and retention.
9. Local and CI commands, environment requirements and execution ownership.
10. Effective-spec composition checks and zero pending/undefined steps.

Preserve specs as the canonical acceptance source. Do not create a second
authoritative copy of the same scenarios merely to use another runner.

Mocked frontend tests do not establish actual frontend/backend integration.
Browser automation does not replace manual real-device checks where required
by mobile or gesture work.

Approve and implement browser setup through a separately scoped active
change. A decision to use the library does not authorize MCP installation,
and a working MCP browser session does not satisfy acceptance gates.

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
- Compare installed skill IDs against the approved source inventory; preserve
  intentional target overrides and report omissions or collisions.
- Verify all four specialist definitions and actual command discovery.
- Confirm Ponytail mode, ADR preference and frontend-only routing survived.
- Verify council model availability without executing authoring rounds merely
  as an installation test.
- Report that council read-only behavior is instruction-based while edit
  permission remains allowed; do not claim a permission-enforced sandbox.
- Distinguish configured integrations from connected tools and verified indexes.
- Record HTTP-only versus real-browser coverage and all deferred setup.
- In multi-repo targets, validate each affected Git boundary and planning/query
  scope separately; root status alone is insufficient.

In OpenCode, confirm command, agent and skill discovery after reload if
needed. Use supported runtime discovery; file existence alone is insufficient.

For approved CodeGraph setup, check index health for the exact target using
codegraph status <project-path> --json --strict when supported. Confirm a narrow
query about a known source symbol through the configured MCP tool or CLI and
check its source location/freshness. Inspect the resulting config/instruction
diff and Git status for unintended writes. A directory alone is not success.
Do not initialise, sync or repair merely because validation fails; report the
failure and request approval for any unplanned remediation.

Report CLI-only operation separately from a confirmed MCP connection. If the
project is empty or CodeGraph was deselected, record indexing as deferred or
setup as declined; do not claim graph validation passed or block the otherwise
usable core workflow solely for that optional integration.

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
- CodeGraph selection, CLI/version/location, reused or changed MCP setup, exact
  index root and health/query results, telemetry/watcher policy and fallback.
  Include deferred greenfield indexing or unapproved repairs explicitly.
- Approved versus installed skill/command/agent inventory, including omissions.
- Ponytail mode, ADR preference and frontend skill activation policy.
- Project plugin state versus inherited/global configuration when inspected.
- Acceptance stack/runner state and HTTP/browser coverage boundaries.
- Playwright library, Test runner and MCP decisions separately; list deferred
  dependencies, downloads, CI work and test ownership.
- Multi-repo adaptations actually verified versus capabilities still unsupported.

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
