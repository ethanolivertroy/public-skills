Agent skills and Claude Code plugins for productivity and workflow automation. These skills follow the [Agent Skills specification](https://agentskills.io/specification) and are compatible with Claude Code, Codex CLI, and OpenCode.

## Installation

### Marketplace

```
/plugin marketplace add ethanolivertroy/skills
/plugin install <skill-name>@skills
```

### npx skills

Install all skills from this repo:

```
npx skills add git@github.com:ethanolivertroy/skills.git
```

Install a single skill:

```
npx skills@latest add ethanolivertroy/skills/<skill-name>
```

### Manually

#### Claude Code

Add skill folders to `~/.claude/plugins/` (for plugins with commands and hooks) or copy `SKILL.md` into an existing plugin's `skills/` folder.

```sh
git clone https://github.com/ethanolivertroy/skills.git
```

See the [Claude Code skills documentation](https://docs.anthropic.com/en/docs/claude-code/skills-overview) for details.

#### Codex CLI

Copy skill directories into your Codex skills path (typically `~/.codex/skills/`).

See the [Agent Skills specification](https://agentskills.io/specification) for the standard skill format.

#### OpenCode

Clone the repo into the OpenCode skills directory:

```sh
git clone https://github.com/ethanolivertroy/skills.git ~/.opencode/skills/ethanolivertroy-skills
```

OpenCode auto-discovers all `SKILL.md` files under `~/.opencode/skills/`. No config changes needed — skills become available after restarting OpenCode.

## Skills

| Skill | Description |
|-------|-------------|
| [exif-stripper](./exif-stripper) | Strip sensitive EXIF metadata from images before publishing to the web |
| [ghost-content-manager](./ghost-content-manager) | Manage Ghost blog drafts — create posts, sync, and push changes |
| [grill-me](./grill-me) | Interview relentlessly about a plan until reaching shared understanding — via [mattpocock/skills](https://github.com/mattpocock/skills) |
| [image-generator](./image-generator) | Generate and edit images using Gemini image models |
| [improve-codebase-architecture](./improve-codebase-architecture) | Explore codebase for shallow modules and propose deepening refactors — via [mattpocock/skills](https://github.com/mattpocock/skills) |
| [made-to-stick](./made-to-stick) | Apply the SUCCESs framework to make ideas, copy, and content more memorable |
| [mischief-managed](./mischief-managed) | End-of-session summary to Obsidian — captures decisions, code changes, and follow-ups with optional Linear sync |
| [obsidian-skills](./obsidian-skills) | Obsidian vault skills via [@kepano/obsidian-skills](https://github.com/kepano/obsidian-skills) |
| [prd-to-issues](./prd-to-issues) | Break a PRD into vertical-slice GitHub issues — via [mattpocock/skills](https://github.com/mattpocock/skills) |
| [ralph-loop](./ralph-loop) | Continuous self-referential AI loops for iterative development |
| [readwise-assistant](./readwise-assistant) | Search highlights, save articles, and analyze reading data via Readwise |
| [tdd](./tdd) | Test-driven development with red-green-refactor loop — via [mattpocock/skills](https://github.com/mattpocock/skills) |
| [visual-explainer](./visual-explainer) | Visual explanations via [@nicobailon/visual-explainer](https://github.com/nicobailon/visual-explainer) |
| [write-a-prd](./write-a-prd) | Create a PRD through user interview and codebase exploration — via [mattpocock/skills](https://github.com/mattpocock/skills) |

### Configuration

Some skills use template variables that you'll need to replace with your own paths:

- **`{{VAULT_PATH}}`** — Your Obsidian vault path (e.g., `~/Documents/MyVault`). Used by: mischief-managed

### Third-Party Skills

Skills marked "via [mattpocock/skills](https://github.com/mattpocock/skills)" are included under the MIT license (see [THIRD-PARTY-NOTICES.md](./THIRD-PARTY-NOTICES.md)). You can also install them directly from the original repo:

```
npx skills@latest add mattpocock/skills/grill-me
npx skills@latest add mattpocock/skills/write-a-prd
npx skills@latest add mattpocock/skills/prd-to-issues
npx skills@latest add mattpocock/skills/tdd
npx skills@latest add mattpocock/skills/improve-codebase-architecture
```

