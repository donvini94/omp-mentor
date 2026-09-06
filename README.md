# omp-mentor

A mentored coding mode for AI coding agents. One skill, one slash command, no code.

`/mentor` puts the agent into a mode where it stops writing your code and starts making you
write it. It reads, greps, runs your tests and reads the real docs; it does not `edit` or
`write` the file you are learning on, and it does not hand you a solution you can paste.
Help arrives on a four-rung ladder that only escalates after a real attempt.

It is built for the case where you already know the theory and are short on repetitions:
someone with a degree or a decade of adjacent experience who never had a stretch of daily
coding, working through Rust, Python, ML notebooks, kata sites, or an unfamiliar stack at
work.

## What is in the box

| Path                    | What it is                                                     |
| ----------------------- | -------------------------------------------------------------- |
| `skills/mentor/SKILL.md` | The whole protocol: constraints, hint ladder, review axes, ledger |
| `commands/mentor.md`     | The `/mentor` slash command that switches it on and off        |

The skill carries `hide: true`, so it never appears in the agent's autoload list and can
never fire on its own. Nothing happens until you type `/mentor`.

## Install

### Oh My Pi

```
omp plugin install github:donvini94/omp-mentor
```

Or copy the two directories by hand:

```
git clone https://github.com/donvini94/omp-mentor
cp -r omp-mentor/skills/mentor   ~/.omp/agent/skills/mentor
cp    omp-mentor/commands/mentor.md ~/.omp/agent/commands/mentor.md
```

### Claude Code

```
cp -r omp-mentor/skills/mentor      ~/.claude/skills/mentor
cp    omp-mentor/commands/mentor.md ~/.claude/commands/mentor.md
```

Restart the agent so it picks the files up.

### Anything else

Any agent that reads `SKILL.md`-style skill folders works. If yours has no slash commands,
start a session by telling it: *read `skills/mentor/SKILL.md` and follow it until I say
mentor off.*

## Use

```
/mentor kata     # LeetCode, deep-ml, Codecrafters. No code from the agent, at any rung.
/mentor build    # Your own project. Design questions before code.
/mentor work     # Day job with a deadline. You ship; learning moments come as one-liners.
/mentor recap    # Print the gap ledger so far.
/mentor off      # Leave mentor mode and print the ledger.
```

Two things worth knowing before the first session:

- Say **"ship it"** whenever the deadline wins. The agent writes the code and appends a
  four-line debrief of what you can and cannot explain, and the gap goes in the ledger.
- The ledger is the point. At the end you get what you solved unaided, what needed hints
  and how deep, and what you accepted without understanding — with one source per gap.

## Adapt it to yourself

The shipped skill describes one default learner. Yours is different. Do not send a pull
request changing the profile; change your own copy.

Paste this into your agent, in a session where it can edit your installed copy:

> Interview me so you can adapt `skills/mentor/SKILL.md` (my installed copy) to me. Ask one
> question at a time, and do not write anything until the interview is done. Cover:
>
> 1. My background: what I have shipped, what I have only read about, where the theory is
>    solid and the practice is thin.
> 2. The languages and stacks I am actually trying to get fluent in, and the ones I only
>    pass through.
> 3. Where I code: kata sites, my own projects, a day job, coursework — and which of those
>    I want mentored.
> 4. My default dial, and what should happen when I do not say one.
> 5. Tone: how blunt do you get about a defect, and do I want any encouragement at all.
> 6. What "stuck" means for me — how long I should struggle before you move up a rung.
> 7. Whether you may write code outside the learning target, and where that boundary sits.
> 8. What I am aiming at beyond syntax: interviews, leading a team, a specific system I
>    want to be able to build alone. That decides which review axes matter.
> 9. Which project standards you should use as the review rubric, if any exist.
>
> Then rewrite the "Who you are working with", "Dials" and "Review" sections of my copy to
> match, leave the hard constraints and the hint ladder alone, and show me the diff.

The hard constraints and the ladder are the load-bearing parts. Softening "the agent does
not write the learning target" turns this back into ordinary autocomplete.

## Why it looks like this

- **No persona.** No teaching character, no catchphrases, no emoji. An adult learning to
  program does not need a mascot, and the persona costs context that the protocol can use.
- **No praise inflation.** "Great question" teaches nothing. Verdicts are plain, defects
  are named where they are.
- **The agent's tools are the constraint.** In a chat sidebar a mentor cannot type into
  your repo. An agent can, so the skill has to forbid it explicitly, or the Socratic method
  collapses the first time it patches the file for you.
- **Questions are not free.** Facts about a language, a library or an error message get
  handed over directly. The design decision and the code stay yours.
- **It ends.** `/mentor off` prints the ledger and the agent goes back to being an agent.

## License

MIT. See `LICENSE`.
