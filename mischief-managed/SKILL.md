---
name: mischief-managed
description: Use when finishing a Claude Code session and wanting to capture decisions, discussions, code changes, and follow-ups as a searchable Obsidian note.
---

# Done — Session Summary to Obsidian

Save to `{{VAULT_PATH}}/Claude-Sessions/`. Target: **1 Bash + 1 Write**. Linear adds parallel MCP calls. Never split into extra tool calls.

## 1. Metadata (one Bash call)

**If in a git repo** (session context says `Is a git repository: true`):
```bash
git rev-parse --abbrev-ref HEAD 2>/dev/null || echo ""; basename "$(git rev-parse --show-toplevel 2>/dev/null)" 2>/dev/null || echo ""; date +%Y-%m-%d-%H%M; pwd; git remote get-url origin 2>/dev/null || echo ""
```
→ `BRANCH`, `REPO`, `DATETIME`, `DIR`, `REPO_URL`

**If not in a git repo** (use `DIR` from session context's working directory):
```bash
date +%Y-%m-%d-%H%M
```
→ `DATETIME` only. `BRANCH` = basename of `DIR`. No `REPO` or `REPO_URL`.

## 2. Reflect + Detect Linear (single pass)

Review the full conversation and extract in one pass:

| Extract | Format |
|---------|--------|
| Summary | 2-3 sentences |
| Slug | 2-4 word kebab-case for filename (action-oriented) |
| What Was Discussed | Bullets with context |
| Key Decisions | `decision — rationale` |
| Code Changes | `` `path` — what and why `` |
| Questions & Follow-ups | `- [ ] item` |
| Topic Tags | 2-4 lowercase hyphenated |

Omit empty sections. Keep bullets concise.

**Linear detection (simultaneous — no separate scan):**

1. **Known mappings** (auto-post, no confirmation needed):

   | Repo / Directory | Linear Project | Team Key |
   |---|---|---|
   | `my-project` | `My Project` | `ENG` |

   Edit this table to match your own repo-to-Linear-project mappings. Remove it entirely if you don't use Linear.

2. **Auto-detected** (needs confirmation): `linearIssueId` in CLAUDE.md or post frontmatter, issue IDs in conversation (e.g., `ENG-123`), `mcp__claude_ai_Linear__*` tool calls.

## 3. Write Note + Linear Fetch (parallel)

**Issue these tool calls in parallel:**

**A) Write** to `{{VAULT_PATH}}/Claude-Sessions/{DATETIME}-{SLUG}.md`:

```
---
date: {DATETIME}
branch: {BRANCH}
repo: {REPO}          ← omit if no repo
directory: {DIR}
tags: [claude-session, {tag1}, {tag2}]
---
# Session: {SLUG} — {Mon DD, YYYY}
## Summary / ## What Was Discussed / ## Key Decisions / ## Code Changes / ## Questions & Follow-ups
## Related Sessions ← only if identifiable, otherwise omit
```

**B) Linear fetch** (if items detected): call `get_project` / `get_issue` for all items simultaneously.

If no Linear context detected, skip B and ask once: *"Tracked in Linear? Give ID(s) or I'll skip."* If no → step 5.

## 4. Linear Sync

**Known mappings → auto-post:** Draft status update (2-3 sentences + repo link if `REPO_URL` set). Convert SSH URLs to HTTPS. Call `save_status_update` (health: `onTrack` unless blockers). Tell user what was posted.

**Auto-detected items → confirm first:** Draft all comments/state changes, present together in one message, post after user confirms.

Repo link format: `**Repo:** [repo-name](REPO_URL)`

## 5. Confirm

File path + one-line summary. Then print the sign-off. Pick one variation randomly each time:

**Variation 1 — Mission complete**
```
     [___]
    .---.
    (@>@)    ~ Mischief managed. ~
   /(   )\
    `---´    Session logged. Now go touch grass.
```

**Variation 2 — Waddle out**
```
     [___]
    .---.
    (@>@)>   ~ Mischief managed. ~
   /(   )\
    `---´    *waddles off with the session note*
```

**Variation 3 — Smug**
```
     [___]
    .---.
    (^>^)    ~ Mischief managed. ~
   /(   )\
    `---´    Another one for the vault. You're welcome.
```

**Variation 4 — Sleepy**
```
     [___]
    .---.
    (->-)    ~ Mischief managed... zzz ~
   /(   )\
    `---´    Session logged. Tremork needs a nap.
```
