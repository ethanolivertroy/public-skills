# Public Skills

Agent skills and Claude Code plugins created by Ethan Troy for productivity, publishing, and workflow automation. These follow the [Agent Skills specification](https://agentskills.io/specification) and are intended to be used with Claude Code, Codex CLI, OpenCode, and compatible agent runtimes.

## Installation

### Claude Code plugin marketplace

```sh
/plugin marketplace add ethanolivertroy/public-skills
/plugin install <plugin-name>@public-skills
```

### npx skills

Install all skills from this repo:

```sh
npx skills add git@github.com:ethanolivertroy/public-skills.git
```

Install a single skill:

```sh
npx skills@latest add ethanolivertroy/public-skills/<skill-name>
```

### Manual install

Clone the repo and copy the skill directories you want into your agent's skills folder.

```sh
git clone https://github.com/ethanolivertroy/public-skills.git
```

## Skills

| Skill | Description |
| --- | --- |
| [exif-stripper](./exif-stripper) | Strip sensitive EXIF metadata from images before publishing to the web. |
| [image-generator](./image-generator) | Generate and edit images using Gemini image models. |
| [made-to-stick](./made-to-stick) | Apply the SUCCESs framework to make ideas, copy, and content more memorable. |
| [mischief-managed](./mischief-managed) | End-of-session summary to Obsidian: decisions, code changes, and follow-ups. |
| [ralph-loop](./ralph-loop) | Continuous self-referential AI loops for iterative development. |

## Notes

This repository intentionally contains only original/public skills maintained here. Previously mirrored third-party skills have been removed; install those directly from their original authors instead.
