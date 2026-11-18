# My Custom Coding Workflow Setup

An OpenCode + OpenSpec workflow template combining intent-driven planning,
executable acceptance specifications, strict TDD, Ponytail implementation
discipline, frontend-gated Emil design/motion skills, and approval-gated
project integrations.

The review sequence is:

`explore -> proposal -> specs -> design -> adr -> tasks -> apply -> verify -> sync -> archive`

Actual artifact dependencies and conditional steps come from the selected
schema and CLI. Installation does not implement product features or certify
application correctness.

## Walkthrough (Covers intent-driven-development by Hari Krishnan)

[![Spec-Driven Development with OpenSpec and OpenCode](https://img.youtube.com/vi/o1w3V3DElV4/maxresdefault.jpg)](https://www.youtube.com/watch?v=o1w3V3DElV4)

Read the full walkthrough:

[Spec-Driven Development with OpenSpec and OpenCode](https://intent-driven.dev/blog/2026/05/10/spec-driven-development-openspec-opencode/)

[SDD with Multi-Model Spec Review and Glossary](https://intent-driven.dev/blog/2026/06/27/sdd-adversarial-authoring-glossary/)

## How To Use This Template

### Start A New Project From This Template

Clone this repository, open it with OpenCode, and start working from the bundled
OpenSpec configuration, commands, skills, and schema.

### Add This Template To An Existing Project

Open your existing project with OpenCode and ask it to install the template:

```text
Read and understand https://raw.githubusercontent.com/prabhatKumarrr/my_opencode_workflow/refs/heads/main/INSTALL_TEMPLATE.md and follow the instructions there.
```

## What This Template Uses

- OpenSpec for setup, proposal, specification, design, ADR, and task artifacts.
- Custom schemas from https://github.com/intent-driven-dev/openspec-schemas.
- A bundled local copy of the `intent-driven` custom schema from
  https://github.com/intent-driven-dev/openspec-schemas/tree/main/openspec/schemas/intent-driven
  for the full `proposal -> specs -> design -> adr -> tasks` lifecycle.
- OpenSpec git discipline so proposals land on `main` before apply, and
  implementation lands on `main` before archive.
- OpenCode skills for repeatable collaboration and implementation workflows,
  including C4 diagrams, ADR authoring, and OpenSpec lifecycle commands.
- A bundled `test-driven-development` skill plus `senior-dev` and `senior-qa`
  subagents in `.opencode/agent/` for test-first implementation and
  acceptance-test work. These specialists are available for delegation;
  automatic routing is not configured. TDD is required by apply guidance in
  `openspec/config.yaml` and the protocols in `AGENTS.md`.
- A `grill-me` style of rigorous design interrogation, inspired by
  https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md.
- ADRs for durable architectural decisions.
- C4 diagrams for communicating architecture boundaries and relationships.
- Gherkin-style requirements and scenarios for observable behaviour.

The bundled OpenSpec schema is a local copy of the `intent-driven` schema from
https://github.com/intent-driven-dev/openspec-schemas/tree/main/openspec/schemas/intent-driven.

## Current Stack and Installation Status

| Layer | Included state | Activation |
| --- | --- | --- |
| OpenSpec lifecycle | 11 bundled lifecycle skills and 10 slash commands | Explicit workflow request, subject to local gates |
| Planning and architecture | Grill-me, adversarial authoring, glossary, C4 and ADR skills | Artifact-specific rules in `openspec/config.yaml` |
| Executable acceptance specifications | Spec-as-source, Gherkin and acceptance-authoring skills with JavaScript/Python reference packs | Enabled here; target acceptance stack/setup deferred |
| TDD | Bundled skill and implementation guidance | Required during apply |
| Ponytail | Four bundled skills; recorded mode `full` | Implementation, change review and requested audits |
| Emil design and motion | Ten bundled skills, including local adaptations | Frontend work only; choose the relevant skill |
| Specialist agents | Four bundled definitions | Requested or workflow-required delegation |
| OpenCode plugins | No plugins configured or local plugin directory bundled | Separate review and approval required |
| CodeGraph | Setup policy included; no template MCP entry or index bundled | Default-selected in installation plans; setup requires approval |
| Playwright | Deferred project integration; no browser runner or MCP configuration bundled | Separate target-project assessment and approval |

The repository contains 35 unique skills: 12 under `.opencode/skills/` and
23 under `.agents/skills/`. Globally available tools or skills are not
automatically part of this template.

A bundled skill is an instruction package, not an installed application
dependency, enabled plugin, running MCP server, or proof of runtime discovery.
Workflow rules guide agents; they do not by themselves provide CI enforcement
or permission-level guarantees.

## Project Integrations and Exclusions

### CodeGraph: Default-Selected, Approval-Gated

[CodeGraph](https://github.com/colbymchenry/codegraph) accelerates targeted
code discovery through a local graph and CLI/MCP access.

Installation distinguishes:
- CLI executable/package availability and version.
- Project or global OpenCode MCP configuration and runtime connection.
- The correct project's index, coverage and freshness.

A globally accessible CLI can serve separate project indexes. Project-local
configuration or indexing does not prove that the CLI package is locally
installed, and a local CLI does not guarantee all caches or state stay inside
the repository.

Reuse healthy existing setup. Install missing components, configure MCP,
initialise indexes or repair existing state only after approval of exact
operations. Disclose telemetry, watchers/background processes and exclusions.

Use narrow queries, verify consequential findings against live source, and
keep repository-search fallback. Token savings are workload-dependent.
CodeGraph does not replace requirements, tests, reviews or Git gates.

See [installer section 7.1](INSTALL_TEMPLATE.md#71-codegraph--default-selected-approval-gated-setup).

### Playwright: Deferred Browser-Testing Integration

[Playwright](https://playwright.dev/docs/library) is not installed or enabled
by this template.

The bundled acceptance examples use HTTP clients and HTML parsing. They do
not automatically execute client-side JavaScript or verify hydrated UI,
browser interactions, layout or multi-origin browser behavior.

For an approved JavaScript acceptance setup, Cucumber can remain the runner
while the Playwright library drives browsers from hooks and page objects.
This does not require a new `stack:` value or a second test runner.

Playwright Test is a separate runner choice. Playwright MCP is a separate
agent-tool integration. Neither is implied by choosing the browser library;
interactive browser exploration is not a replacement for repeatable tests.

Before setup, agree dependency ownership, browser downloads, lifecycle,
test isolation, application startup, reports/artifacts and CI execution.
Preserve effective-spec composition, zero pending/undefined steps and the
required acceptance HTML report.

### Not Included or Automatically Enabled

- Superpowers: optional upstream project, not configured or selected for
  automatic installation. Any future adoption needs compatibility review
  against this workflow's planning, TDD, delegation and Git gates.
- Impeccable and taste-skill: not selected or bundled.
- Additional plugins, MCP servers, browser binaries and test runners require
  separate approval.

Do not enable integrations by copying an unreviewed configuration example.
Verify current upstream compatibility and the installed OpenCode version first.

## Workflow

The intent-driven workflow moves through these artifacts in order:

```text
proposal -> specs -> design -> adr -> tasks
```

- `proposal` captures why the change matters.
- `specs` describe observable behaviour with Gherkin-style scenarios.
- `design` explains the implementation approach and trade-offs.
- `adr` records durable architectural decisions.
- `tasks` turn the accepted intent, behaviour, design, and decisions into work.

### Activation and Verification Gates

| Stage | Required routing |
| --- | --- |
| Proposal | `grill-me`, `adversarial-authoring`, `glossary` |
| Specifications | `spec-as-source`; `gherkin-authoring` for fenced scenarios |
| Design | `c4-diagrams`, `glossary`; confirm diagram format and rigor |
| ADR review | `architectural-decision-records`; recorded preference `madr-minimal` |
| Tasks | `spec-as-source`; acceptance-first ordering and `Frontend scope: yes | no | partial` |
| Apply | `test-driven-development`, recorded Ponytail mode and relevant frontend-only skills |
| Verification | `/opsx-verify` first; stop on failure, then `ponytail-review`, then `review-animations` if motion changed |
| Sync/archive | Green effective acceptance suite, required report and local Git/zone gates |

`AGENTS.md` defines frontend path fallback, permission boundaries and zone
isolation. Backend-only work must not load frontend design/motion skills.
Frontend scope does not mean loading every frontend skill.

Specs-zone and code-zone edits must remain separate while uncommitted;
any `tasks.md` is neutral. Top-level ADRs, glossaries and preference files
are code-zone paths even during planning.

Planning must reach `main` before apply; implementation must reach `main`
before archive under the current policy. Other integration-branch conventions
require an explicitly approved adaptation, not an automatic branch rename.
Git mutations always require authorization.

## Schema

`openspec/config.yaml` already selects the bundled [`intent-driven` schema](openspec/schemas/intent-driven/schema.yaml). Learn how to tailor artifact workflows in [OpenSpec Custom Schemas](https://intent-driven.dev/blog/2026/02/12/openspec-custom-schemas/).

## Skills

### OpenSpec Lifecycle Skills and Commands

All skills below live under `.opencode/skills/`.

| Skill | Bundled command | Purpose |
| --- | --- | --- |
| `openspec-explore` | `/opsx-explore` | Investigate without implementation |
| `openspec-new-change` | `/opsx-new` | Start a change |
| `openspec-propose` | `/opsx-propose` | Produce a planning package |
| `openspec-continue-change` | `/opsx-continue` | Create the next artifact |
| `openspec-update-change` | `/opsx-update` | Reconcile existing planning artifacts |
| `openspec-apply-change` | `/opsx-apply` | Implement approved tasks |
| `openspec-verify-change` | `/opsx-verify` | Review implementation against artifacts |
| `openspec-sync-specs` | `/opsx-sync` | Merge selected deltas into main specs |
| `openspec-archive-change` | `/opsx-archive` | Finalize one eligible change |
| `openspec-bulk-archive-change` | `/opsx-bulk-archive` | Archive explicitly selected eligible changes |
| `openspec-bulk-apply-change` | None | Apply eligible changes in isolated worktrees with delegated verification |

Invoke bulk apply through its skill; no `/opsx-bulk-apply` command is bundled.
Bulk operations require per-change gates, conflict checks and explicit
authorization for worktrees or other Git operations.

| Skill | Location | Purpose | Enabled Or Updated By |
|-------|----------|---------|-----------------------|
| `openspec-bulk-apply-change` | `.opencode/skills/` | Applies multiple active changes in isolated worktrees with delegated verification; never merges or archives. | Invoke the skill directly; no `/opsx-bulk-apply` command file is present. |
| `adversarial-authoring` | `.opencode/skills/` | Runs author and reviewer agents in sequence to reduce model bias in drafts. | Required by the `proposal` rule; configured author/reviewer agents produce a draft and review, with the primary agent synthesizing the artifact and council notes. |
| `grill-me` | `.agents/skills/` | Interrogates plans and designs with probing questions to surface hidden assumptions. | Refer to this skill under rules section in `openspec/config.yaml`. |
| `c4-diagrams` | `.agents/skills/` | Visualises system architecture using C4 model levels in ASCII or Mermaid. | Refer to this skill under `design` rule in `openspec/config.yaml`. |
| `architectural-decision-records` | `.agents/skills/` | Captures architectural decisions with rationale, tradeoffs, and supersession chains. | Required by the `adr` rule in `openspec/config.yaml`; confirm the recorded style before drafting. |
| `gherkin-authoring` | `.agents/skills/` | Drafts and improves Gherkin scenarios for observable, domain-language behaviour. | Required by `spec-as-source` during the `specs` phase. |
| `glossary` | `.agents/skills/` | Maintains business and technical terminology and companion glossary references for specification artifacts. | Required by the `proposal` and `design` rules; companion files and glossary edits remain permission-gated. |
| `openspec-git-discipline` | `.agents/skills/` | Enforces that proposals reach `main` before apply, and implementation merges before archive. | Enabled through `AGENTS.md`. |
| `spec-as-source` | `.agents/skills/` | Adds executable acceptance specifications to the intent-driven workflow. | Already enabled under both the `specs` and `tasks` rules in `openspec/config.yaml`. |
| `acceptance-test-authoring` | `.agents/skills/` | Configures the acceptance runner, extraction, linting, and step definitions for `spec-as-source`. | Required by `spec-as-source` when configuring or changing acceptance-test infrastructure. |
| `test-driven-development` | `.agents/skills/` | Guides strict red-green-refactor TDD: one behaviour per test, minimal implementation to pass, refactoring on green, with best-practice patterns and collaborator mocking guidance. | Required by apply guidance in `openspec/config.yaml` and `AGENTS.md`; also loaded by `senior-dev` when delegated. |

Current activation rules and protocols are in `openspec/config.yaml` and `AGENTS.md`.

The `openspec-bulk-apply-change` skill is installed. No `/opsx-bulk-apply`
command file is present, so invoke the skill directly. Bulk apply requires
two or more eligible changes and explicit approval before creating isolated
worktrees; it never merges or archives.

### Ponytail Skills

All four skills live under `.agents/skills/`.

| Skill | Purpose | Activation |
| --- | --- | --- |
| `ponytail` | Smallest complete implementation without unnecessary abstraction | Required during apply at the level in `ponytail/mode.md` |
| `ponytail-review` | Review correctness, safety, tests, performance and unnecessary code | After successful OpenSpec verification for implemented code |
| `ponytail-audit` | Read-only whole-repository quality audit | Requested whole-repo audit or optimization assessment |
| `ponytail-debt` | Report `shortcut:` and legacy `ponytail:` comments | Requested debt inventory; persistence requires approval |

Recorded mode: `full`. Preserve it during installation unless another mode
is explicitly selected. Apply-mode Ponytail is not a planning-artifact rule.
No Ponytail plugin, `ponytail-gain` or `ponytail-help` is bundled.

### Frontend Design and Motion Skills

All ten skills live under `.agents/skills/`. They apply only to frontend scope.

| Skill | Use |
| --- | --- |
| `emil-design-eng` | UI interaction polish and general design-engineering judgment |
| `animate` | Build purposeful animations |
| `gestures` | Drag, swipe, sheets and interruptible touch interactions |
| `choreograph` | Coordinate multiple moving elements |
| `animation-performance` | Diagnose frame-budget and animation-performance issues |
| `mobile-native` | Mobile-web interaction and platform polish |
| `review-animations` | Review changed motion against the craft standards |
| `improve-animations` | Read-only motion audit and conversation-only implementation plans |
| `break-ui` | Stress-test UI with realistic worst-case data |
| `remove-animations` | Remove unnecessary motion within approved change scope |

Local safeguards:
- Preserve vendored adaptations and complete supporting files during updates.
- Explicitly load `review-animations` when required; its
  `disable-model-invocation: true` hides automatic advertising, not explicit loading.
- `improve-animations` creates no files. Approved findings flow into an active
  change's `tasks.md`; no `plans/`, `animation-plans/` or separate execute workflow.
- A `break-ui` dev-only data toggle must be removed before task completion and
  must never be committed.
- `remove-animations` cannot expand beyond the active change's stated scope.
- Animation libraries shown in skill examples are not installed dependencies.

## Experimental: Spec As Source

The `spec-as-source` skill is an opt-in layer on the intent-driven schema that uses fenced Gherkin in OpenSpec specifications as the source for generating acceptance tests. It is already enabled in this repository under both the `specs` and `tasks` rules in `openspec/config.yaml`.

Acceptance stack selection is deferred until a target project is chosen.
Before scaffolding, confirm and record `stack: javascript` or `stack: python`
in that project's `openspec/config.yaml`. Create the root `acceptance-tests/`
project through the first change's setup tasks; it is not scaffolded here.

During `specs`, `spec-as-source` requires `gherkin-authoring` to author the fenced Gherkin scenarios. During `tasks`, it replaces the standard task template with acceptance-test-first work: configure and run the acceptance suite, then implement application work. Use `acceptance-test-authoring` to configure the runner, extraction, linting, and step definitions that execute the specifications. See [Behavior-Driven Development and Spec-Driven Development with OpenSpec](https://intent-driven.dev/blog/2026/07/17/behavior-driven-development-sdd-openspec/).

## Known Limitations and Readiness

The template supplies workflow instructions and reference tooling, not a
verified application installation.

Known acceptance-composition limitations:
- JavaScript and Python helpers currently identify nested capabilities by
  their first path segment, which can cause collisions.
- After standalone sync, active ADDED deltas can run alongside their synced
  baseline scenarios, producing duplicates.

Request a separately scoped repair before relying on the affected paths.
Documentation updates do not repair these helpers.

Multi-repository orchestration is not preconfigured or end-to-end verified.
A central planning root with independent application repositories needs
explicit planning-scope resolution, per-repo Git gates, CodeGraph routing,
test ownership and revision-specific integration evidence. Copying this
template into a parent directory is not sufficient.

Bulk apply also requires target-specific validation of store, worktree and
effective-suite interactions. Schema validation alone does not establish
installation or integration readiness.

## Further Reading

- Template overview: [Spec-Driven Development with OpenSpec and OpenCode](https://intent-driven.dev/blog/2026/05/10/spec-driven-development-openspec-opencode/)
- Schema customization: [OpenSpec Custom Schemas](https://intent-driven.dev/blog/2026/02/12/openspec-custom-schemas/)
- Durable architecture: [Architectural Decision Records with Spec-Driven Development using OpenSpec](https://intent-driven.dev/blog/2026/04/29/spec-driven-development-with-adr/)
- Multi-model review and glossary: [SDD with Multi-Model Spec Review and Glossary](https://intent-driven.dev/blog/2026/06/27/sdd-adversarial-authoring-glossary/)
- Parallel implementation: [OpenSpec, Git WorkTrees and OpenCode](https://intent-driven.dev/blog/2026/04/01/openspec-git-worktrees-opencode/)
- Spec-As-Source Spec-Driven Development: [Behavior-Driven Development and Spec-Driven Development with OpenSpec](https://intent-driven.dev/blog/2026/07/17/behavior-driven-development-sdd-openspec/)
- Brownfield adoption: [Spec-Driven Development with Brownfield Projects](https://intent-driven.dev/blog/2026/03/10/spec-driven-development-brownfield/)
- SDD + BDD + TDD: [How TDD and BDD Actually Fit Into Spec-Driven Development](https://intent-driven.dev/blog/2026/08/23/tdd-bdd-spec-driven-development/)

## Agents

Specialist agents used within skills, in `.opencode/agent/`:

| Agent | Purpose |
|-------|---------|
| `adversarial-author` | Writes an initial draft of a specification artifact or design document. |
| `adversarial-reviewer` | Reviews the author's draft with challenges and improvement suggestions. |
| `senior-dev` | Implements src work test-first through strict red-green-refactor, following the `test-driven-development` skill. |
| `senior-qa` | Authors acceptance tests, step definitions, and runner configuration, following the `acceptance-test-authoring` skill. |

Configured council models:
- Author: `opencode/deepseek-v4.1-flash-free`
- Reviewer: `openai/gpt-6.1-sol`

Confirm both are available in the target environment before claiming
cross-model review; do not substitute models silently.

The council agents are instructed not to edit files, but their current
frontmatter permits editing. Treat read-only behavior as an instruction,
not a permission-enforced guarantee.

`senior-dev` and `senior-qa` have no pinned model in their definitions.
Delegation remains subject to explicit user requests or skill/workflow
requirements; agent availability does not authorize automatic parallel work.
