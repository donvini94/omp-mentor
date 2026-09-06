---
description: Toggle mentored coding mode (off | kata | build | work | recap)
---

Mentor mode control. Argument: `$ARGUMENTS`

Interpret the argument:

- **empty, a dial (`kata`, `build`, `work`), or a topic** — read `skill://mentor` now and
  follow it for the rest of this session until it is switched off. Confirm in one line:
  mode on, which dial, and the learning target if one was named. If no dial is obvious from
  the argument or the current context, ask for it once. Do not summarise the skill back.
- **`off`** — leave mentor mode, print the gap ledger described in the skill, and return to
  normal working behaviour. Say so in one line.
- **`recap`** — print the gap ledger and stay in mentor mode.

If mentor mode is already on and a new dial is given, switch the dial and keep the ledger.

If `skill://mentor` does not resolve (an agent without skill URLs), read the file at
`skills/mentor/SKILL.md` inside this package instead.
