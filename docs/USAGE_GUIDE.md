# How to Use the WP AI Engineering Blueprint

This guide explains how to apply the blueprint to a real WordPress plugin or theme project. The blueprint provides reusable instructions and checklists; it does not automatically install itself into every AI tool.

Repository: https://github.com/ShoaibSiddiqi/wp-ai-engineering-blueprint

## Choose your setup

### Option A — Recommended: keep the blueprint inside each project

This keeps the master blueprint available to the AI agent and makes the standards easy to update.

1. Clone the blueprint:
   ```bash
   git clone https://github.com/ShoaibSiddiqi/wp-ai-engineering-blueprint.git
   ```
2. In your plugin/theme project, create a folder for the reference copy. You can use a Git submodule if you are comfortable with Git, or copy the files into a normal folder.
   - Suggested path: `.engineering/wp-ai-engineering-blueprint/`
   - If copying files manually, do not copy the blueprint repository's nested `.git/` directory.
3. Create an `AGENTS.md` at the **root of the plugin/theme project**. Use the template below.
4. Copy `specs/PROJECT_SPEC_TEMPLATE.md` to the project as `specs/PROJECT_SPEC.md` and fill it out.
5. Open the plugin/theme project root in Codex or your coding agent.
6. Ask the agent to read the root `AGENTS.md`, the project specification, and only the blueprint documents relevant to the task.

**Root `AGENTS.md` template for a project using the blueprint:**

```md
# Project Instructions

Before planning or changing code:
1. Read `.engineering/wp-ai-engineering-blueprint/AGENTS.md`.
2. Read `specs/PROJECT_SPEC.md` if it exists.
3. Read only the relevant blueprint documents under
   `.engineering/wp-ai-engineering-blueprint/docs/`.
4. Inspect this project's existing code and conventions before proposing changes.

Follow the blueprint as the default engineering standard, but adapt it to this project's
declared WordPress/PHP versions, architecture, requirements, and existing public interfaces.
If a requirement conflicts with the blueprint, explain the conflict before proceeding.
Implement incrementally, test your changes, and report commands/results honestly.
```

**Git submodule option (advanced):**

Run from the root of your plugin/theme repository:

```bash
git submodule add https://github.com/ShoaibSiddiqi/wp-ai-engineering-blueprint.git .engineering/wp-ai-engineering-blueprint
```

When cloning a project that uses a submodule, initialize it with:

```bash
git submodule update --init --recursive
```

To intentionally update the pinned blueprint version later, review the upstream changes and update the submodule pointer. Do not blindly pull new standards into a release branch without review.

### Option B — Copy a snapshot

Copy `AGENTS.md`, the relevant files from `docs/`, and the project specification template into your project. This is straightforward, but the copied files will not update when the master repository changes. Periodically compare them with the master blueprint.

## Using it with different AI tools

### Codex

- Open the actual plugin/theme repository as the working project.
- Keep the project's root `AGENTS.md` in place. Codex uses `AGENTS.md` for repository instructions.
- If instructions are not being followed, explicitly ask Codex to inspect the file paths above before coding.
- For a new project, you can ask Codex to help fill in `specs/PROJECT_SPEC.md` before it generates implementation code.

### Claude Code

At the plugin/theme project root, create `CLAUDE.md` with this content:

```md
@AGENTS.md

For each task, also inspect `specs/PROJECT_SPEC.md` if present and read the relevant
documents under `.engineering/wp-ai-engineering-blueprint/docs/`.
Load only what is relevant to the current task; do not read every document unnecessarily.
```

Claude Code reads `CLAUDE.md` for project instructions. The `@AGENTS.md` line imports the shared project instructions when the file is available.

### ChatGPT without Codex

A normal ChatGPT conversation does not automatically load a repository's files just because its URL was mentioned. Provide the necessary context by uploading the relevant files, pasting the applicable instructions, or using a supported repository/file connection. For repeated coding work, use a coding workspace that can inspect and modify the project files.

### Other coding assistants

Use the tool's supported project-instruction mechanism. Ensure the instructions and blueprint documents are actually available in the coding workspace; storing them on GitHub alone does not make the agent read them.

## Start a new plugin or theme

1. **Describe the product.** Complete `specs/PROJECT_SPEC.md`: purpose, users, feature acceptance criteria, compatibility, data handling, integrations, and out-of-scope items.
2. **Ask for a plan first.** Do not start with a prompt asking for the entire plugin at once.
3. **Build one feature at a time.** Review each change and keep diffs small.
4. **Verify.** Run configured checks from `docs/QUALITY_GATES.md` and applicable tests.
5. **Review before release.** Use `docs/SECURITY.md` and `docs/RELEASE_CHECKLIST.md`.
6. **Report honestly.** Require actual command output and a list of checks not run. Never assume generated code is secure or production-ready.

## Reusable prompts

### A. Plan before coding

```text
Read the project's root AGENTS.md, specs/PROJECT_SPEC.md, and the relevant documents
in .engineering/wp-ai-engineering-blueprint/docs/. Inspect the existing codebase.
Do not edit files yet. Summarize the requirements, assumptions, architecture options,
security risks, compatibility concerns, acceptance criteria, and a small-step plan.
Identify any important questions before implementation.
```

### B. Implement one feature

```text
Implement [FEATURE ID / NAME] according to specs/PROJECT_SPEC.md and the project
instructions. First identify the files to change. Follow existing conventions and
the relevant blueprint security and architecture guidance. Make a small, reviewable
change, add/update tests, run available checks, inspect the diff, and report exact
commands and results. Do not claim a test passed if it was not run.
```

### C. Review code

```text
Review the current diff against the project instructions and relevant blueprint
checklists. Prioritize exploitable security issues, broken behavior, backward
compatibility, data loss, missing tests, performance and accessibility. Report
findings with file/line references and severity. Do not change files yet.
```

## Token use and maintenance

The blueprint can reduce repeated explanations and help the agent focus on established patterns, but token savings are not guaranteed. Reading large instruction files also consumes context. Keep `AGENTS.md` concise, point to detailed documents, and ask the agent to load only the relevant documents for the task.

Treat the master repository as the source of truth. Review updates before adopting them in existing projects. The blueprint is guidance, not an automated security certification; generated code still needs engineering review and testing.
