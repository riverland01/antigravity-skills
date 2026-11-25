# Antigravity Skills

Curated Antigravity skills packaged in `.agents/skills/` so they **auto-load** whenever you attach this repository to an [Antigravity Remote Project](https://antigravity.google/docs/remote-agents) (or open it as part of a multi-folder local project).

## Included Skills

| Skill | Purpose | Source | Edition |
| --- | --- | --- | --- |
| [`orchestrate`](.agents/skills/orchestrate/SKILL.md) | Coordinate complex work through selective delegation, synthesis, and verification | [`riverland01/Skills`](https://github.com/riverland01/Skills/tree/main/orchestrate/antigravity) | Antigravity (verbatim) |
| [`grill-me-general`](.agents/skills/grill-me-general/SKILL.md) | Clarify and stress-test ideas, plans, decisions, or briefs with adaptive questioning and a durable decision record | [`riverland01/Skills`](https://github.com/riverland01/Skills/tree/main/grill-me) | Adapted for Antigravity |
| [`colab-operator`](.agents/skills/colab-operator/SKILL.md) | Operate Google Colab GPU/TPU runtimes, execute scripts/notebooks, sync files, and manage sessions via `colab` CLI | [`googlecolab/google-colab-cli`](https://github.com/googlecolab/google-colab-cli/tree/main/skills/colab-operator) | Verbatim |

> **Naming note:** Named `grill-me-general` so it coexists cleanly with Antigravity's built-in `/grill-me` command (including `/plan /grill-me`) without overriding it.

## Using with an Antigravity Remote Project

Local skills in `~/.gemini/config/skills/` are not available in Remote Agent sessions. Instead, attach this repository as a **GitHub Resource**:

1. Open your Remote Project in the Antigravity App or at [antigravity.google.com](https://antigravity.google.com).
2. Go to **Project Settings → Resources → Add Resource → GitHub** (or add it while creating a new remote project).
3. Select this repository (`antigravity-skills`).
4. Start a conversation—Antigravity clones the repository into the remote workspace and automatically discovers every skill under `.agents/skills/<name>/SKILL.md`.

> **Tip on private repositories:** Antigravity Remote Projects require all attached **private** repositories in a project to belong to the same GitHub owner/org. Keeping this repository **public** lets you attach it alongside private repos from any owner.

## Repository Layout

```text
.agents/
└── skills/
    ├── colab-operator/
    │   └── SKILL.md
    ├── grill-me-general/
    │   ├── SKILL.md
    │   └── references/
    │       ├── design-sources.md
    │       ├── question-lenses.md
    │       └── session-record.md
    └── orchestrate/
        ├── SKILL.md
        └── references/
            └── design-sources.md
sources.json    # Upstream provenance and pinned commits
```

Antigravity scans `.agents/skills/` one level deep and loads each `<skill-name>/SKILL.md` automatically.

## Adding or Updating Skills

1. Place each new skill directly under `.agents/skills/<skill-name>/` with a `SKILL.md` file containing valid YAML frontmatter (`name` and `description`) plus any `references/`, `scripts/`, `examples/`, or `resources/` directories.
2. Record its upstream repository, path, and commit SHA in [`sources.json`](sources.json).
3. Commit and push to `main`. New Remote Agent conversations will pick up the updated skills automatically.
