# My Custom Coding Workflow Setup
An [OpenSpec](https://github.com/Fission-AI/OpenSpec) and [OpenCode](https://opencode.ai/) template with the `proposal -> specs -> design -> adr -> tasks` workflow enabled, plus optional collaboration workflows for teams that choose to adopt them.

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

## Optional: Enable Superpowers

[Superpowers](https://github.com/obra/superpowers) provides guided practices such
as brainstorming, planning, debugging, verification, worktrees, and
subagent-driven parallel work. It is not enabled by default in this template.

To enable it, add the plugin entry to `opencode.json`:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "plugin": ["superpowers@git+https://github.com/obra/superpowers.git"]
}
```

If your configuration already has a `plugin` array, append the entry while
preserving your existing plugins and other settings. Restart OpenCode to load it.

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

## Schema

`openspec/config.yaml` already selects the bundled [`intent-driven` schema](openspec/schemas/intent-driven/schema.yaml). Learn how to tailor artifact workflows in [OpenSpec Custom Schemas](https://intent-driven.dev/blog/2026/02/12/openspec-custom-schemas/).

## Skills

Standard OpenSpec lifecycle skills in `.opencode/skills/` — names are self-explanatory:
`openspec-new-change`, `openspec-propose`, `openspec-continue-change`, `openspec-explore`,
`openspec-apply-change`, `openspec-verify-change`, `openspec-sync-specs`, `openspec-archive-change`

| Skill | Location | Purpose | Enabled Or Updated By |
|-------|----------|---------|-----------------------|
| `openspec-bulk-apply-change` | `.opencode/skills/` | Applies multiple active changes in isolated worktrees with delegated verification; never merges or archives. | Invoke the skill directly; no `/opsx-bulk-apply` command file is present. |
| `adversarial-authoring` | `.opencode/skills/` | Runs author and reviewer agents in sequence to reduce model bias in drafts. | Refer to the skill under rule in the rules section of `openspec/config.yaml`. |
| `grill-me` | `.agents/skills/` | Interrogates plans and designs with probing questions to surface hidden assumptions. | Refer to this skill under rules section in `openspec/config.yaml`. |
| `c4-diagrams` | `.agents/skills/` | Visualises system architecture using C4 model levels in ASCII or Mermaid. | Refer to this skill under `design` rule in `openspec/config.yaml`. |
| `architectural-decision-records` | `.agents/skills/` | Captures architectural decisions with rationale, tradeoffs, and supersession chains. | Automatically invoked or can be explicilty referred to under `adr` rule in `openspec/config.yaml`. |
| `gherkin-authoring` | `.agents/skills/` | Drafts and improves Gherkin scenarios for observable, domain-language behaviour. | Required by `spec-as-source` during the `specs` phase. |
| `glossary` | `.agents/skills/` | Maintains business and technical terminology and companion glossary references for specification artifacts. | Can be referred to under `proposal` and/or `design` rule in `openspec/config.yaml`. |
| `openspec-git-discipline` | `.agents/skills/` | Enforces that proposals reach `main` before apply, and implementation merges before archive. | Enabled through `AGENTS.md`. |
| `spec-as-source` | `.agents/skills/` | Adds executable acceptance specifications to the intent-driven workflow. | Already enabled under both the `specs` and `tasks` rules in `openspec/config.yaml`. |
| `acceptance-test-authoring` | `.agents/skills/` | Configures the acceptance runner, extraction, linting, and step definitions for `spec-as-source`. | Required by `spec-as-source` when configuring or changing acceptance-test infrastructure. |
| `test-driven-development` | `.agents/skills/` | Guides strict red-green-refactor TDD: one behaviour per test, minimal implementation to pass, refactoring on green, with best-practice patterns and collaborator mocking guidance. | Required by apply guidance in `openspec/config.yaml` and `AGENTS.md`; also loaded by `senior-dev` when delegated. |

Current activation rules and protocols are in `openspec/config.yaml` and `AGENTS.md`.

The `openspec-bulk-apply-change` skill is installed. No `/opsx-bulk-apply`
command file is present, so invoke the skill directly. Bulk apply requires
two or more eligible changes and explicit approval before creating isolated
worktrees; it never merges or archives.

## Experimental: Spec As Source

The `spec-as-source` skill is an opt-in layer on the intent-driven schema that uses fenced Gherkin in OpenSpec specifications as the source for generating acceptance tests. It is already enabled in this repository under both the `specs` and `tasks` rules in `openspec/config.yaml`.

Acceptance stack selection is deferred until a target project is chosen.
Before scaffolding, confirm and record `stack: javascript` or `stack: python`
in that project's `openspec/config.yaml`. Create the root `acceptance-tests/`
project through the first change's setup tasks; it is not scaffolded here.

During `specs`, `spec-as-source` requires `gherkin-authoring` to author the fenced Gherkin scenarios. During `tasks`, it replaces the standard task template with acceptance-test-first work: configure and run the acceptance suite, then implement application work. Use `acceptance-test-authoring` to configure the runner, extraction, linting, and step definitions that execute the specifications. See [Behavior-Driven Development and Spec-Driven Development with OpenSpec](https://intent-driven.dev/blog/2026/07/17/behavior-driven-development-sdd-openspec/).

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
