# AI Dev Template

[![Status](https://img.shields.io/badge/status-stable-green)](VERSION)
[![Version](https://img.shields.io/github/v/tag/ctreffe/ai-template-dev?label=version)](CHANGELOG.md)
[![License](https://img.shields.io/github/license/ctreffe/ai-template-dev)](LICENSE)

> [!NOTE]
> **AI Collaboration**
>
> This repository maintains the AI Dev Template.
>
> The AI Dev Template is the development-oriented specialization of the generic AI Project Template.
>
> The collaboration model documents engineering practices, AI-assisted development workflows and repository conventions used by development-oriented projects.
>
> Its collaboration model is maintained in [COLLABORATION.md](COLLABORATION.md).

<br>

**[Link zur deutschen README](README.de.md)**

<br>

## Contents

- [Overview](#overview)
- [Core Principle](#core-principle)
- [AI Templateverse](#ai-templateverse)
- [When to Use This Template](#when-to-use-this-template)
- [Project Initialization](#project-initialization)
- [Collaboration Skills](#collaboration-skills)
- [External Files and Sources](#external-files-and-sources)
- [Temporary Working Files](#temporary-working-files)
- [Project Materials](#project-materials)
- [Recommended Workflow](#recommended-workflow)
- [Git Index and Protected Git Actions](#git-index-and-protected-git-actions)
- [Decision Records](#decision-records)
- [Repository Structure](#repository-structure)
- [Template and Derived Project Files](#template-and-derived-project-files)
- [How to Use This Template](#how-to-use-this-template)
- [Maintainer Tool Setup](#maintainer-tool-setup)
- [Continuous Improvement](#continuous-improvement)
- [License](#license)

## Overview

The AI Dev Template is the starting point for development-oriented projects involving code, scripts, automation, technical architecture, validation, releases and user-facing technical documentation. It provides a reusable repository foundation and collaboration method rather than a programming framework or application scaffold.

The template combines maintainer-owned intent with roadmap-first implementation, small reviewable changes, explicit validation, durable project context, documented technical decisions and repository-ready delivery. It builds on the generic AI Project Template and adds engineering-specific expectations for code readability, sensitive inputs, generated outputs and release discipline.

## Core Principle

The maintainer owns the project direction, architecture and release decisions. The assistant may help design, implement, test, document and review changes, but must preserve maintainer authority, make assumptions and limitations visible and never simulate completed code, validation, commits or files.

The repository is the authoritative engineering state. Code and documentation should be understandable to future maintainers without private chat history, and a change is not complete merely because it worked once.

## AI Templateverse

The public AI templates form a small templateverse: a family of related templates that share a repository-first, maintainer-led Human-AI collaboration model while specializing it for different project types.

- [AI Project Template](https://github.com/ctreffe/ai-template-project) is the generic starting point for structured project work, research, planning, concept work, process design and mixed projects.
- [AI Dev Template](https://github.com/ctreffe/ai-template-dev) is for development-oriented projects where code, scripts, automation, validation, architecture or release workflows are central.
- [AI Documentation Template](https://github.com/ctreffe/ai-template-docs) is for technical documentation projects such as user guides, admin guides, operating procedures, tutorials, migration guides and documentation sites.

## When to Use This Template

Use the Dev Template when implementation lifecycle, validation and release discipline are central from the beginning. Typical projects include command-line tools, scripts, automation, integration utilities, deployment tooling, libraries, prototypes that must produce validated learning and repositories that expose technical configuration or operational workflows.

Use the generic Project Template when the project is still primarily discovery, planning or mixed non-development work. A generic project may deliberately migrate toward this template when code, tests, architecture or releases become central.

## Project Initialization

After creating the repository, the maintainer invokes `$start-project`. The skill reads the repository and its setup guidance, then leads the complete initialization. The maintainer does not need to open or execute `PROJECT_SETUP.md` separately.

The simplest instruction to the agent is:

> `$start-project`

There is no initialization prompt to open or copy into the conversation.
Before the normal questionnaire, the agent offers one concise choice between
the normal lean path and the explicit `$grill-me` path for detailed engineering
planning. The choice grants no access, dependency, Git or release authority.

The agent then:

1. reads the collaboration, engineering, setup, documentation, repository and decision rules;
2. inspects the repository baseline without altering Git history;
3. follows the selected path and, on the lean path, asks no more than six
   unanswered fundamentals covering project purpose, users, the first useful
   capability and its evidence, current scope and non-goals, source or input
   access and sensitivity, and only engineering constraints needed now;
4. asks for maintainer-owned consequential decisions instead of inventing them
   and defers architecture, tooling, tests, deployment and release detail until
   concrete work requires it;
5. adapts the README files, project context, repository rules and project structure after the maintainer answers;
6. applies safe defaults for secrets, logs, dumps, screenshots, fixtures, external files and generated outputs;
7. validates only the initial technical behavior needed for the first useful outcome; and
8. hands back the initialized state with proportionate checks, unresolved decisions and suggested commit metadata.

`PROJECT_SETUP.md` remains the agent's detailed checklist and a provenance record of the initialization method. `$start-project` is the single executable entry point that activates it.

For a project that should remain local and have no remote, invoke
`$create-local-project` explicitly in this checked-out template. It verifies
the destination, creates an independent local clone without a remote and then
invokes `$start-project`; it is not a second initialization.
After successful initialization, inherited template history in `CHANGELOG.md`
and `TASK_HANDOFF.md` is replaced with project-owned state. The template-only
`IDEAS.md`, the project's copy of `$create-local-project` and their references
are removed unless a project-local idea backlog is deliberately established.
The initialization files remain as provenance.

During initialization, the inherited `README.md` and `README.de.md` become
`TEMPLATE_README.md` and `TEMPLATE_README.de.md`. They remain available as
adapted guides to workflows, skills and repository conventions. New project
READMEs in both languages introduce the actual project and link early to the
corresponding guide under "Workflows and Skills". Each pair has its own language
links, and the guides link back to the project introductions.

The guides describe the retained file and skill inventory, omit inherited
badges and distinguish template provenance from project identity and licensing.
Later selected `$sync-template` updates map upstream READMEs to these guides
while preserving project adaptations and the project introductions. Existing
projects adopt this layout only through deliberate maintenance. This source
repository keeps its original README pair. See [PROJECT_SETUP.md](PROJECT_SETUP.md)
for the initialization and interrupted-setup contract.

## Collaboration Skills

Skills are scoped workflows in [`.agents/skills/`](.agents/skills/). They guide
the agent through a particular task and load the relevant repository guidance.
Invoke a skill in chat with `$skill-name`, for example
`$review-project`. The linked skill files describe each full workflow.

- **Agent or explicit:** The agent may select the skill when the task fits;
  you can also invoke it directly.
- **Explicit:** The skill needs a deliberate invocation or explicit maintainer
  selection. An agent suggestion does not activate it.

Selecting a skill grants no additional permission for protected Git actions,
installation, external transmission or publication. Local access and domain
rules apply to every workflow.

In `commit-changes`, explicit commit authorization includes normal push to this
repository's verified existing upstream. In `commit-milestone`, explicit milestone
commit authorization also includes one matching annotated version tag and its
exact upstream push. "Commit only" excludes tags and pushes; "no push" retains
the local commit/tag; "no tag" excludes tags; "no tag push" keeps the tag local.
Other Git actions, tag movement/replacement and release publication stay separate.

`reuse-fixes` reads and updates only this repository's error knowledge. It does
not collect lessons across repositories or maintain global memory.
Active fixes use 4–8 lines per case in `TROUBLESHOOTING.md`.
[Detailed evidence](TROUBLESHOOTING_DETAILS.md) is preserved separately;
read only a matching detail section when needed.

| Skill | Invocation | Purpose |
| --- | --- | --- |
| [`start-task`](.agents/skills/start-task/SKILL.md) | Agent or explicit | Reconstruct only the context needed for a new bounded task. |
| [`handoff-task`](.agents/skills/handoff-task/SKILL.md) | Agent or explicit | Save the task outcome, evidence and next step in a compact `TASK_HANDOFF.md`. |
| [`commit-changes`](.agents/skills/commit-changes/SKILL.md) | Agent or explicit | Create an ordinary scoped commit and perform its normal upstream push with explicit commit authorization, unless push is excluded. |
| [`record-decision`](.agents/skills/record-decision/SKILL.md) | Agent or explicit | Document a durable decision using the applicable record type; source-template decisions route to Governance. |
| [`reuse-fixes`](.agents/skills/reuse-fixes/SKILL.md) | Agent or explicit | Reuse this repository's confirmed fixes, retain concise prevention and ask only for missing authority or blocking decisions. |
| [`start-project`](.agents/skills/start-project/SKILL.md) | Explicit | Initialize a new, uninitialized derived project from the retained setup guidance. |
| [`review-project`](.agents/skills/review-project/SKILL.md) | Explicit | Produce a comprehensive neutral inventory of project state and evidence gaps. |
| [`sync-template`](.agents/skills/sync-template/SKILL.md) | Explicit | Compare a derived project with its verified source template and adopt selected updates while preserving project adaptations. |
| [`check-consistency`](.agents/skills/check-consistency/SKILL.md) | Explicit | Diagnose internal contradictions between intent, roadmap, decisions, content and documentation; develop bounded options. |
| [`perform-retrospective`](.agents/skills/perform-retrospective/SKILL.md) | Explicit | Review collaboration evidence and distinguish project findings from reusable template or family candidates. |
| [`create-local-project`](.agents/skills/create-local-project/SKILL.md) | Explicit | Create a local derived repository from this source template and hand it over to initialization; removed after successful project setup. |
| [`commit-milestone`](.agents/skills/commit-milestone/SKILL.md) | Explicit | Close a reviewed milestone with metadata, comprehensive checks, a commit, annotated version tag and exact upstream pushes unless excluded. |

### Optional Planning Skills

`grill-me` and `grilling` are adopted MIT-licensed skills by Matt Pocock.
They complement the repository's own skills and are used only after explicit
selection. The normal lean initialization path remains available.

| Skill | Invocation | Purpose |
| --- | --- | --- |
| [`grill-me`](.agents/skills/grill-me/SKILL.md) | Explicit | Start the optional intensive planning interview and route it to `grilling`. |
| [`grilling`](.agents/skills/grilling/SKILL.md) | Explicit | Explore a plan, decision or idea through detailed interview rounds; use only after explicit opt-in. |

## External Files and Sources

Place newly received files in `input/intake/` before deciding how they may be used. Record safe metadata, provenance and the resulting classification in `input/CATALOG.md`; use the ignored `input/CATALOG.local.md` when filenames, paths or other details are themselves sensitive.

Catalog unchanged external services, datasets and URLs even when their content
remains outside the repository. Use stable public URLs directly and resolve
logical private or device-specific locations through ignored
`input/PATHS.local.md`.

- **`input/intake/`** is the ignored arrival area for files that have not yet been classified. Presence never authorizes assistant access.
- **`input/restricted/`** is ignored and reserved for files that only the maintainer, or explicitly approved local checks, may inspect.
- **`input/local/`** is ignored and holds files the assistant may process locally but that must not enter Git.
- **`input/versioned/`** contains reviewed external files that may be committed. Move files from here into a project-specific source, fixture or configuration location when that location communicates their durable role more clearly, while preserving provenance in the catalog.

Assistant access, Git versioning and external sharing are three separate decisions. A move between folders documents classification; it does not grant broader permission. Fixed runtime locations such as `.env`, application log directories or local databases may remain where the software requires them, but their classification and ignore rules should still be documented.

For large non-Git files that must remain available across devices, use the
provider-neutral workflow in [SYNCHRONIZED_STORAGE.md](SYNCHRONIZED_STORAGE.md).
Synchronized files remain external storage; synchronization is not Git
versioning, backup, assistant access or publication approval.

## Temporary Working Files

Use `temp/` for disposable intermediate engineering files. All contents outside
`temp/restricted/` are assistant-readable; that restricted directory must not
be enumerated or read. All temporary content is ignored, must never be versioned
and is not cataloged. Promote retained files deliberately to `materials/` or an
authoritative engineering location.

## Project Materials

Keep files in `input/` unchanged. A converted export, sanitized reproduction,
cropped screenshot, diagnostic extract or any other content change is a new
project material, not a modified input. `materials/` retains such working files
while they remain useful but have not become authoritative source code, tests,
fixtures or configuration.

Every cataloged material is assistant-readable. Record provenance and creation
or transformation in `materials/CATALOG.md`, using `Based on` input or material
IDs. Store files as **`local`** in ignored `materials/local/`, as
**`versioned`** in `materials/versioned/`, or as **`external`** at a stable
logical location in the catalog. Resolve external locations per machine in
ignored `materials/PATHS.local.md`, copied from the versioned example.

Access does not authorize Git versioning or sharing. Promote a material to
source, tests, fixtures or configuration only when that location better
expresses its durable engineering role, preserving provenance. Build outputs,
caches and disposable diagnostics do not belong in `materials/`.

Generation method does not determine location. Keep a generated file in
`materials/` when it is a durable working or source file consumed by later
engineering steps. Place it in `output/` or another documented deliverable
location when it is a project result intended for use, review, handoff, release
or delivery. Disposable generation intermediates remain in `temp/`; source,
tests, fixtures and configuration keep their authoritative locations.

## Recommended Workflow

Development proceeds through small, validated loops:

```text
Intent -> Roadmap -> Implement -> Validate -> Adjust -> Document -> Prepare commit -> Continue
```

1. Establish the current repository and working-tree baseline.
2. Confirm the active roadmap step and what it should prove or deliver.
3. Implement one logical, reviewable change.
4. Run relevant tests, scripts, linters, renderers or maintainer-local validation.
5. Fix issues found before presenting the step as ready.
6. Update code comments, technical documentation and user-facing guidance affected by the behavior.
7. Record consequential architecture, project or documentation decisions.
8. Prepare a regular working commit with an appropriate Conventional Commit prefix.
9. Close a satisfied milestone separately by harmonizing version, changelog, project context and validated status.

Routine new tasks use `start-task`. Invoke `$review-project` for a comprehensive
neutral inventory, `$sync-template` for source-template adoption,
`$check-consistency` for internal diagnosis and `$perform-retrospective` for a
separate evaluation of Maintainer-Agent collaboration.

## Git Index and Protected Git Actions

The maintainer controls Git history, normally through GitHub Desktop. Assistants may inspect status, diffs and logs, prepare working-tree changes, propose commit boundaries and provide commit summaries and descriptions.

Staging and unstaging are index operations. They do not require a control word, but they may be performed only after a specific maintainer request or authorization of the corresponding commit. Existing staged selections and unrelated changes must be preserved.

Protected actions include commits, amendments, tags, pushes, pulls, merges, rebases, resets, branch changes, stash manipulation and other Git history operations. An assistant may perform a specific protected action only when the instruction for that action contains `explicit` or `explicitly` in English, or the German word family `explizit`. File-edit approval does not authorize Git history changes, and other protected actions remain separately authorized, with the bounded commit workflows above as the specific exceptions.

When this rule requires authorization, the assistant proposes one minimum-scope,
copy-ready instruction naming the exact action, repository and material
consequence. The proposal itself is not authorization.

Regular engineering commits use prefixes such as `feat:`, `fix:`, `docs:`, `refactor:` or `test:`. Milestone commits omit the prefix, name the completed version and close work already implemented and validated through regular commits.

## Decision Records

Choose the record type by decision subject:

- **ADR — Architecture Decision Record:** architecture, interfaces, configuration formats, lifecycle behavior, deployment, security boundaries, sensitive-input handling, fixture versioning or generated-output policy.
- **PDR — Project Decision Record:** scope, roadmap, collaboration, privacy, repository structure, release model or governance.
- **DDR — Documentation Decision Record:** user documentation, reference structure, terminology, examples, screenshots or documentation QA.

Templates live in [decisions/](decisions/). Create a record when future maintainers will need the context, rationale and consequences; routine implementation details belong in code, tests or ordinary documentation instead.

## Repository Structure

### Entry Points and Project Memory

- **`README.md` and `README.de.md`** introduce the software project and explain setup, configuration, use and navigation in English and German.
- **`PROJECT_CONTEXT.md`** is the primary re-entry point for current intent, status, roadmap, baseline, validation and next steps. It should describe the present engineering state, not duplicate the changelog or architecture history.
- **`CHANGELOG.md` and `VERSION`** record completed changes and the latest completed version. They are milestone records and should not imply a release state that has not been validated.

### Collaboration and Engineering Rules

- **`AGENTS.md`** is the compact resident safety and routing contract for AI agents.
- **`COLLABORATION.md`** defines the provider-neutral development partnership, authority, evidence and completion model.
- **`PHILOSOPHY.md`** records the engineering values behind the template, including simplicity, maintainability, transparency, validated learning and integrity.
- **`DOCUMENTATION.md`** defines the roles and quality requirements of project, code-level and user-facing documentation. It treats documentation as part of the software.
- **`REPOSITORY.md`** defines naming, Git workflow, commits, versioning, releases, sensitive inputs and repository-ready delivery. It remains an active project rule after setup.

### Setup, Continuation and Review

- **`PROJECT_SETUP.md`** guides the first initialization and preserves its methodological baseline. `$start-project` is the explicit executable entry point.
- **`.agents/skills/`** contains the workflows and invocation rules described in
  [Collaboration Skills](#collaboration-skills).
- **`TROUBLESHOOTING.md`** retains confirmed corrections and concise prevention
  for `reuse-fixes` in this repository. Host facts remain ignored in
  `TROUBLESHOOTING.local.md`. Other repositories are not included.
- **`TASK_HANDOFF.md`** carries the compact versioned task checkpoint across
  sessions and computers without duplicating project history.
- **`IDEAS.md`** is a source-template backlog for reusable engineering
  candidates and is removed during normal project initialization unless a
  project-local backlog is deliberately retained.

### Decisions, External Inputs and Project-Specific Code

- **`decisions/`** contains reusable ADR, PDR and DDR templates and, in derived projects, accepted durable decisions. The folder should not become a log of every minor implementation choice.
- **`input/`** provides the catalog-based intake and classification workflow for external files and sources. Ignored zones keep unreviewed, restricted and local-only inputs out of Git.
- **`materials/`** catalogs retained assistant-readable engineering files in
  local, versioned or external storage before deliberate promotion to a more
  authoritative project role.
- **`temp/`** holds ignored, never-versioned engineering intermediates, with
  `temp/restricted/` as the inaccessible exception.
- **Project-specific source, tests, scripts and configuration** are added during initialization according to the technology and architecture chosen by the maintainer. Their layout should be documented when names and structure alone are insufficient for a new contributor.
- **Project-local environments and generated outputs** normally use ignored locations such as `.venv/`, `node_modules/`, `generated/` or `deliverables/`. Document whether generated outputs are reproducible local files, review files or release deliverables.

## Template and Derived Project Files

In a derived development project:

- replace template identity and placeholder content with the concrete project name, purpose, setup and usage;
- fill and continuously maintain `PROJECT_CONTEXT.md`;
- adapt `DOCUMENTATION.md` and `REPOSITORY.md` as ongoing rules;
- normally retain and adapt `AGENTS.md`, `COLLABORATION.md` and `PHILOSOPHY.md`;
- retain `PROJECT_SETUP.md` and the applicable repository skills as provenance and repeatable operating tools;
- add the source, test, configuration and documentation structure required by the project;
- create real Decision Records only for consequential decisions;
- keep the standardized AI Collaboration Note visible and factually accurate.

Record the source-template version and commit, initialization status, last harmonization baseline and intentional deviations in `PROJECT_CONTEXT.md`. A derived project's tested behavior and accepted decisions remain authoritative over later generic template changes.

## How to Use This Template

1. Create a repository from the template and invoke `$start-project`.
2. Choose the normal lean path or explicitly opt into `$grill-me`; on the lean
   path, answer no more than six unanswered engineering fundamentals while the
   agent applies `PROJECT_SETUP.md` and the remaining guidance automatically.
3. Review the initialized repository state, validation results and proposed first commit.
4. Let the agent capture maintainer intent and derive a validation-oriented roadmap.
5. Establish the code, test, documentation and local-tool structure needed by the concrete project.
6. Classify external files through `input/`, keep restricted and local-only inputs outside Git and prefer sanitized fixtures that reproduce behavior without unnecessary disclosure.
7. Implement one logical change at a time and validate it before recommending a commit.
8. Document public behavior, configuration, commands, risks and troubleshooting when they affect use.
9. Record durable decisions, keep `PROJECT_CONTEXT.md` current and invoke the applicable task, synchronization, consistency or retrospective skill.
10. Close milestones only after implementation, validation, documentation and version metadata form one coherent state.

## Maintainer Tool Setup

Install only the tools required by the derived project. A practical baseline for local Codex-supported development is:

- [Git for Windows](https://gitforwindows.org/) and [GitHub Desktop](https://desktop.github.com/download/);
- [PowerShell](https://learn.microsoft.com/powershell/scripting/install/installing-powershell-on-windows);
- [ripgrep (`rg`)](https://github.com/BurntSushi/ripgrep/releases) or another fast local search tool;
- [Python](https://www.python.org/downloads/) with a project-local virtual environment when needed;
- [Node.js](https://nodejs.org/en/download/) with project-local dependencies when needed;
- project-specific test, lint, render or build tools.

Prefer local environments such as `.venv/` and `node_modules/` over global installation. Keep environment files, caches, logs, unreviewed inputs and generated working files ignored unless the project deliberately versions a reviewed file or output.

## Continuous Improvement

Development projects should retain practices that have proven useful and remove unnecessary complexity. Validated negative results, recurring validation problems and maintainability lessons are legitimate project knowledge.

Use `$sync-template` to compare a project with its verified source-template baseline and adopt selected developments. Use `$check-consistency` separately to diagnose contradictions among implementation, tests, documentation and roadmap, and `$perform-retrospective` to evaluate collaboration, engineering handoffs, validation strategy and work rhythm. A finding becomes a template candidate only after its transferability, maintenance cost and effect on different development projects have been considered.

The maintainer coordinates cross-template evolution in a private governance repository named `ai-templateverse`. It records shared conventions, deliberate specializations and evidence from derived projects. The repository is intentionally not linked because template users do not need access to it.

Governance coordination does not create hidden engineering requirements. Every change that affects this template must be represented here through maintained guidance, Decision Records where appropriate, the changelog and release history. Reusable improvements must keep code, tests, configuration and user-facing documentation aligned and must not overfit one implementation experience.

## License

This project is licensed under the [MIT License](LICENSE).
