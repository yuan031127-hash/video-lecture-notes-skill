# Video Lecture Notes Skill Design

## Goal

Package the supplied Chinese engineering-course lecture workflow as a personal
Codex Skill that is locally discoverable, maintainable, and publicly reusable.

## Selected Approach

Use a lean primary Skill with progressive disclosure. Keep the execution flow,
source-integrity rules, and delivery contract in `SKILL.md`. Move detailed
lecture-writing rules, formula and visual checks, and the long output skeleton
to directly linked reference and template files. Do not ship placeholder Python
scripts that imply automation which has not been implemented or tested.

## Repository And Installation Layout

```text
video-lecture-notes-skill/
├── README.md
├── LICENSE
├── docs/superpowers/
│   ├── specs/2026-07-14-video-lecture-notes-skill-design.md
│   └── plans/2026-07-14-video-lecture-notes-skill.md
└── video-lecture-notes/
    ├── SKILL.md
    ├── agents/openai.yaml
    ├── references/
    │   ├── content-rules.md
    │   └── quality-checks.md
    └── assets/lecture-notes-template.md
```

The installable unit is only `video-lecture-notes/`. The repository-level
README, license, and design records are not copied into the personal Skill
directory.

## Trigger And Behavior

The Skill triggers for requests to turn technical course videos, recordings,
subtitles, slides, PDFs, board work, or lecture images into complete Chinese
lecture notes. It must use audio and visuals together when video is available,
preserve timestamps, distinguish source material from model supplementation,
and avoid presenting uncertain formulas or terminology as confirmed facts.

## Validation

Validation must prove that:

1. the original pasted draft fails the structural preconditions;
2. the finished folder passes the official `quick_validate.py` check;
3. every referenced local file exists;
4. `agents/openai.yaml` matches the Skill name and purpose;
5. the installed copy matches the published source tree;
6. the GitHub repository is public and its default branch contains the commit.

## Publishing

Create `yuan031127-hash/video-lecture-notes-skill` as a public repository with
the MIT license. Use an isolated nested git repository so unrelated files from
the existing workspace cannot be staged or published.

