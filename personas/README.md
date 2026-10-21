# Fleet Claude Code personas (output styles)

Source of truth for the per-machine Claude Code personas (rolled out 2026-10-20, Phil-approved). Each file is a Claude Code **output style**, installed on its box at `~/.claude/output-styles/<file>.md` for the user that runs the claude session, and selected with `"outputStyle": "<name>"` in that user's `~/.claude/settings.json` (name = frontmatter `name:`, exact). `common.md` is the shared "What never changes" block already appended to each file; `RECIPE.md` is the rollout procedure.

| Box | File | name | Model |
|---|---|---|---|
| hal9000 | hal9000.md | HAL 9000 | Sonnet (`~/.hal9000-claude.sh`) |
| wopr | wopr.md | WOPR | Sonnet (`~/.wopr-claude.sh`) |
| mac-studio | m5.md | M-5 | Sonnet (`~/.m5-claude.sh`) |
| scotty / spock / mccoy | scotty.md / spock.md / mccoy.md | Scotty / Spock / McCoy | crew routes via local :3020 (unchanged) |
| max | maximilian.md | Maximilian | glm-5.2 via settings env (unchanged) |
| apol / drtheopolis | apol.md / theopolis.md | Apol / Dr. Theopolis | `auto` via max's :3020 (unchanged) |

Why output styles: eval on HAL (110 headless cases) + Claude Code docs. `--agent` replaces the whole system prompt (rejected); CLAUDE.md is a user message (weaker); output style with `keep-coding-instructions: true` keeps the coding guidance. Haiku held character poorly and once worked around a blocked command, so Anthropic-direct boxes run Sonnet (Phil: keep usage light, escalate by hand).

Gotchas: herdr attach loops parse their command at start, so editing `~/.herdr-attach-claude.sh` does nothing until the loop restarts (recreate the tmux session directly). Fresh sessions in a new dir show a trust prompt whose default is "No, exit". Weak models copy example status lines, so examples for those boxes show checking before reporting. Style edits take effect at the next session start.

To change a persona: edit here, copy to the box's `~/.claude/output-styles/`, restart that session when idle, record in the box's runbook.
