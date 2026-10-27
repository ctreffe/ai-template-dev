# AI Dev Template Idea Backlog

This is the lightweight intake for reusable improvements to this source
template. It is separate from every derived-project roadmap. Capturing an idea
does not approve implementation, create a project commitment or authorize a
cross-repository change.

Derived projects do not require an `IDEAS.md` by default. Project-specific
findings belong in that project's roadmap or Decision Record process.
A retrospective running in this source-template repository may capture a
candidate under normal authorized in-scope edit rules. A derived-project
transfer may enter only with exact cross-repository control-word authorization;
otherwise it remains a `Pending Idea Transfer`.

## Status Model

- **Captured** — retained for later review; no implementation decision exists.
- **Exploring** — alternatives, evidence or constraints are being assessed.
- **Promoted** — accepted into an identified roadmap or decision process.
- **Deferred** — retained but intentionally inactive.
- **Rejected** — closed with a short rationale.

## Entry Format

```markdown
### IDEA-NNNN: Short title

- **Status:** Captured | Exploring | Promoted | Deferred | Rejected
- **Source:** Optional approved project or template evidence
- **Opportunity:** Problem or useful outcome
- **Recurrence:** Why this may matter beyond one project
- **Reusable elements:** Existing patterns or artifacts to assess
- **Benefit:** Expected value
- **Risk:** Adoption or transfer risk
- **Boundaries:** Access, domain and non-goals
- **Next decision:** Smallest maintainer-owned decision
- **References:** Optional durable evidence or promoted destination
```

## Ideas

### IDEA-0001: Interactive review-code for existing code and changes

- **Status:** Promoted
- **Source:** Project-local skill design and accepted interactive change-review rounds; generic applicability remains unvalidated.
- **Opportunity:** Explain and assess existing code or concrete changes before planning work or accepting an implementation.
- **Recurrence:** Maintainers repeatedly need to understand behavior and consequences, including when collaboration context and human-maintained source code live in separate repositories.
- **Reusable elements:** Establish exact revision, scope and baseline; show verified excerpts or diffs in continuously numbered logical blocks. Explain why/how, side effects, compatibility, risks and validation limits, including surrounding callers and state. Show four blocks per round, fewer in the final round, and pause for feedback.
- **Benefit:** Smaller review decisions with explicit consequences and unresolved concerns.
- **Risk:** Rigid round sizing or automatic invocation may conflict with local workflows. Acceptance does not establish comprehensive or independent review.
- **Boundaries:** Existing-code review grants no edit authority. Keep acceptance, source-edit approval and protected Git/publication authorization separate. Invocation policy is project-owned; the originating project's automatic trigger for human-maintained source changes is not a universal template default. This is not a comprehensive project review.
- **Next decision:** None for source implementation. TVDR-0063 selects deliberate invocation, four blocks per round by default with an agreed override, and revision-bound acceptance. Independent project trials remain open.
- **References:** Governance TVDR-0063; [review-code](.agents/skills/review-code/SKILL.md).

### IDEA-0002: Explicit test-code with one agreed plan and one local report

- **Status:** Promoted
- **Source:** Structurally validated project-local coordination skill and separate bounded operational test evidence; formal invocation of a generic skill remains unvalidated.
- **Opportunity:** Plan, execute and report tests of existing behavior, suspected defects or changes, without requiring a diff.
- **Recurrence:** Unit tests alone do not establish operational workflows, integration behavior or performance under concurrent use.
- **Reusable elements:** Start on explicit maintainer invocation; reuse known requirements and agree a bounded plan before execution. Select available browser, HTTP or concurrency methods. Record actual source/runtime provenance, cases, expected outcomes, isolation, resource/stop limits and cleanup. Use one ignored local report per plan with multiple agreed attempts, preserving failures. Material expansion creates a linked new run. Verify authoritative outcomes independently of the UI and explain method-specific coverage limits.
- **Benefit:** Traceable diagnosis and comparable evidence without new reports for each retry or silent scope expansion.
- **Risk:** Coordination can be mistaken for an implemented runner or full coverage. HTTP clients do not exercise browser JavaScript; visible success does not prove stored results are correct.
- **Boundaries:** Make target, data and external-effect restrictions explicit and project-specific. Testing grants no source fixes, installation, Git actions or publication. Environment readiness and operational test success remain distinct; missing setup requires an agreed package, potentially IDEA-0003.
- **Next decision:** None for source implementation. TVDR-0063 selects explicit-only test-code, one ignored local report per agreed plan and project-owned runners. Operational trials remain project-owned and unvalidated here.
- **References:** Governance TVDR-0063; [test-code](.agents/skills/test-code/SKILL.md); [report template](templates/TEST_REPORT.md).

### IDEA-0003: setup-test-environment for documented definition and reconstruction

- **Status:** Promoted
- **Source:** Structurally validated local skill and successful existing-definition/same-host reuse trial; first-definition dialogue, fresh-host reconstruction and independent trials remain untested.
- **Opportunity:** Define a test system in versioned documentation and reconstruct it later without repeating the full requirements interview.
- **Recurrence:** Projects need repeatable setup despite differing toolchains, topology and supported tests.
- **Reusable elements:** Inspect the existing definition first. For new/incomplete systems, ask focused questions about tests, tools, sources/versions, topology, storage, synthetic fixtures, external effects, limits and readiness. Record a portable definition and executable recipe before implementation. Later reuse that definition and resolve host-specific gaps. Distinguish preparing/building, starting, readiness and stopping/retention. Verify actual source/runtime provenance; support local development builds and explicit published-version comparisons without silent substitution.
- **Benefit:** Reproducible setup, less repeated discussion and a clear separation between readiness and test coverage.
- **Risk:** Host-specific commands, credentials, unrelated services or stale recipes can undermine reproducibility. Same-host success does not establish fresh-host restoration.
- **Boundaries:** Use project-owned bindings instead of copying one stack into the template. Keep credentials, data and host settings outside portable versioned definitions. Preserve unrelated services and applicable installation, privilege, source-write and Git permissions. Setup does not automatically invoke test-code or authorize operational tests.
- **Next decision:** None for source implementation. TVDR-0063 selects definition-first setup with project-owned recipes and separate readiness evidence. First-definition execution, fresh-host reconstruction and independent trials remain unvalidated.
- **References:** Governance TVDR-0063; [setup-test-environment](.agents/skills/setup-test-environment/SKILL.md); [definition template](templates/TEST_ENVIRONMENT.md).

### IDEA-0004: Semantic branch names with a tool-independent human-AI marker

- **Status:** Promoted
- **Source:** Derived development project (anonymized; no project, repository, maintainer, study or machine identity included). Reviewed period: 2026-10-26; bounded branch-naming discussion and its accepted project rule, not a comprehensive retrospective. Sanitized evidence: An assistant-created work branch initially used a tool-specific prefix. The maintainer selected semantic purpose prefixes and a separate human-AI collaboration marker. The accepted local format is `<type>/ai-dev/<topic>`, for example `feature/ai-dev/new-component` or `fix/ai-dev/session-routing`. Types are feature, fix, docs and chore; topics are short lowercase kebab-case names without a leading or trailing slash.
- **Opportunity:** Offer an explicit branch-naming convention in the Dev Template's repository guidance, or ask maintainers to choose one during initialization. Place the type first to group branches by purpose, followed by the fixed ai-dev segment and topic. Keep main/master names unchanged. A standing rule belongs in repository guidance with a Decision Record for project adoption; it does not need a standalone skill. Existing entry/commit workflows should consult the repository convention when they propose branch names.
- **Recurrence:** One confirmed project example. The naming decision can arise in other derived projects; recurrence across projects has not been established.
- **Reusable elements:** The three-part format, four purpose types, examples, lowercase topic guidance, type-first rationale, explicit override of tool-specific assistant defaults, and distinction between naming, disclosure and Git authority.
- **Benefit:** Branch purpose and human-AI involvement remain visible, consistently grouped and independent of the particular AI assistant.
- **Risk:** A mandatory template default could conflict with an established team's workflow or tooling. Never infer other maintainers' agreement or automatically rename existing branches. Adoption should respect repository-specific rules.
- **Boundaries:** Source recommendation only. The branch marker supplements contribution-specific commit and PR disclosures; it grants no branch creation/rename, Git, source-write or publication authority. Preserve project approval/coordination rules. Existing derived projects are outside adoption. No private code, test results, research data, paths or chat transcript are transferred.
- **Next decision:** None for source implementation. TVDR-0066 selects the optional, configurable recommendation in REPOSITORY.md with four purpose types and no extra initialization question. Existing project conventions take priority; local adoption remains optional.
- **References:** Governance TVDR-0066; [repository guidance](REPOSITORY.md#optional-names-for-ai-assisted-work-branches).
