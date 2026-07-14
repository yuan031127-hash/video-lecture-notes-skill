# Video Lecture Notes Skill Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build, locally install, verify, and publicly publish the supplied `video-lecture-notes` workflow as a personal Codex Skill.

**Architecture:** Keep the primary `SKILL.md` concise and procedural, with detailed course-writing rules and validation checklists in one-level references and a reusable Markdown template in `assets/`. Keep repository documentation outside the installable Skill folder and copy only the verified Skill directory into the personal Codex Skills location.

**Tech Stack:** Markdown, YAML, Python-based Codex Skill validators, Git, GitHub CLI.

---

### Task 1: Establish the failing source baseline

**Files:**
- Read: `C:/Users/17656/.codex/attachments/53dfc30e-ea2e-4b5c-81fa-0c48445f561c/pasted-text.txt`
- Record: `docs/superpowers/specs/2026-07-14-video-lecture-notes-skill-design.md`

- [x] **Step 1: Check the first content line and YAML delimiters**

Run a UTF-8-safe read that asserts the first line is `---` and the closing
frontmatter delimiter is exactly `---`.

- [x] **Step 2: Verify the source fails for the expected reasons**

Expected: FAIL because prose appears before the YAML frontmatter and the closing
delimiter is `-------------`.

### Task 2: Initialize the installable Skill

**Files:**
- Create: `video-lecture-notes/SKILL.md`
- Create: `video-lecture-notes/agents/openai.yaml`
- Create: `video-lecture-notes/references/content-rules.md`
- Create: `video-lecture-notes/references/quality-checks.md`
- Create: `video-lecture-notes/assets/lecture-notes-template.md`

- [x] **Step 1: Run the official initializer**

Run `init_skill.py video-lecture-notes` with `references,assets` resources and
explicit interface values for the display name, short description, and default
prompt.

- [x] **Step 2: Replace the generated primary Skill**

Write valid two-field YAML frontmatter followed by the core inspection,
transcription, visual-analysis, content reconstruction, uncertainty, and
delivery workflow. Link every optional detail file directly from `SKILL.md`.

- [x] **Step 3: Add detailed rules and template**

Move the stable domain-specific rules and full lecture-note skeleton into the
two reference files and one template file without duplicating the core flow.

### Task 3: Add public repository files

**Files:**
- Create: `README.md`
- Create: `LICENSE`

- [x] **Step 1: Write repository documentation**

Document the Skill's purpose, supported inputs, installation command, example
triggers, output structure, current limitations, and license.

- [x] **Step 2: Add the MIT license**

Use year `2026` and copyright holder `yuan031127-hash`.

### Task 4: Validate and install

**Files:**
- Verify: `video-lecture-notes/**`
- Create: `C:/Users/17656/.codex/skills/video-lecture-notes/**`

- [x] **Step 1: Run official validation**

Run `quick_validate.py` against `video-lecture-notes` and expect `Skill is valid!`.

- [x] **Step 2: Run content-integrity checks**

Verify all linked reference paths exist, no placeholders remain, metadata uses
the same Skill name, and the primary file remains below 500 lines.

- [x] **Step 3: Install the Skill**

Copy the verified installable directory to the personal Codex Skills directory,
replacing only an existing directory with the exact same Skill name after it has
been inventoried.

- [x] **Step 4: Compare source and installed trees**

Compute recursive file hashes and expect identical relative paths and hashes.

### Task 5: Commit and publish

**Files:**
- Stage: the isolated repository only

- [ ] **Step 1: Inspect repository scope**

Run `git status -sb` inside the isolated repository and confirm no path outside
that repository can be staged.

- [ ] **Step 2: Commit the verified package**

Commit with message `feat: publish video lecture notes skill`.

- [ ] **Step 3: Create and push the public repository**

Create `yuan031127-hash/video-lecture-notes-skill` as public, set `origin`, and
push the default branch.

- [ ] **Step 4: Verify GitHub state**

Query the repository visibility, URL, default branch, and remote commit SHA.
Expected: visibility `PUBLIC` and remote SHA equal to the local `HEAD`.
