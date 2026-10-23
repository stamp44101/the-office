# The Office — ออฟฟิศพิกเซล (Pixel HQ)

Top-down pixel office for team task tracking. Runs as a claude.ai Artifact (single `index.html`, uses the `window.claude` runtime: `db`, `user`, `room`, `sample`).

- Staging: Stamp's copy artifact · Production: original artifact (owner: friend)
- Deploy: publish `index.html` to the artifact. Capabilities: `db` (rules: `rooms` read view / write owner, `rooms/{self}` write interact), `room`, `user` (profile), `sample`.

## Data (db)
| path | what |
|---|---|
| `rooms/<userId>` | desk, avatar, deco, clients (legacy `tasks[]` auto-migrates out) |
| `tasks/<id>` | owner, clientId, title, due, note, done, doneAt, doneBy, assignee (`ai` = Claude), comments[], parent, ai{brief, answers[], output, history[], versions} |
| `chat/<id>` | by, text, at — pruned after 14 days |
| `activity/<id>` | by, kind, text, to[], at — pruned after 14 days |
| `board/main` | team board text |

XP / level / streak are derived from finished tasks (nothing extra stored). Deco unlocks by level.

## World (synced from production look)
Map, lounge, coffee machine, snack corner, meeting/sofa seats, office cats, festival decor (Halloween etc.), focus timer, radio (3 generated tracks) and read-chat-aloud are ported from the production artifact. Coins/shop/missions are not: XP stays derived from finished tasks.

Dev cheats (staging): toolbar "🛠 โกง" menu — set level (presets or 1–999), clear bonus, finish focus now, call a free cat. Shortcuts `Alt+Shift+L` (Lv200) / `Alt+Shift+K` (clear). Level is a flat `rooms/<me>.xpBonus` on top of task XP.
