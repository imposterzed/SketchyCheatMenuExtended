# Contributing to Sketchy Cheat Menu Plus

Thanks for your interest in contributing! This document covers bug
reports, feature requests, and code contributions.

- For what the mod does, see the [README](README.md).
- For the technical ramp-up (file layout, encoding rules, CK2 modding
  gotchas, commit conventions), see [AGENTS.md](AGENTS.md).

## Reporting bugs

Open a [new issue](../../issues/new/choose) and pick the **Bug report**
template. For mod-vs-mod conflicts, use the **Compatibility issue**
template.

For "how do I..." questions, please use
[Discussions](../../discussions) instead.

## Suggesting features

Open a [new issue](../../issues/new/choose) and pick the **Feature
request** template. Please describe the use-case — what does the player
gain that the current cheat menu doesn't already provide?

## Contributing code

Bug fix PRs are welcome. For new features, please open a
feature-request issue first to discuss the design before spending time
on a PR.

The technical reference (file layout, encoding, commit conventions,
graphics) lives in [AGENTS.md](AGENTS.md). The notes below cover only
the in-game testing parts that an automated agent can't do for you.

### Testing your changes in-game

There's no automated test suite — verification is in-game. The fastest
loop:

1. Copy or junction the mod into your CK2 mod directory
   (`Documents/Paradox Interactive/Crusader Kings II/mod/`).
2. Launch CK2 with Sketchy Cheat Menu Plus enabled.
3. Check `logs/error.log` for any lines mentioning the mod's files —
   clean = parse OK.
4. Load a save or new game. Right-click your character → **Cheats
   Enable** to unlock the rest of the menu.
5. Trigger the decision you added / changed and verify the effect in-game.

### Reaching specific test conditions

The cheat menu bypasses most vanilla gates by design, but some
decisions still gate on religion, culture, government, or DLC (the
Iqta obligation family needs a Muslim feudal holder; the vanilla-
obligation cheats surface only when Conclave is disabled; etc.). Two
ways to reach a specific state:

- **Bookmark filter** — the 1066 / 867 / 769 / 936 / 1337 bookmarks
  cover most religion / culture / government combinations. Picking a
  ruler who already meets the condition is faster than converting.
- **Console** — see the table below.

### Console commands

Open the console with `~`.

| What | Command |
|---|---|
| Show character info on hover | `charinfo` |
| +5000 gold | `cash` |
| +Prestige / +Piety | `prestige 5000` / `piety 5000` |
| Hop to another ruler | `play <charID>` (hover with `charinfo` on) |
| Change religion | `religion <charID> <religion>` ([religion IDs](https://ck2.paradoxwikis.com/Religion#List_of_religions)) |
| Change culture | `culture <charID> <culture>` ([culture IDs](https://ck2.paradoxwikis.com/Cultures#List_of_cultures)) |
| Change government | `government <gov>` (e.g. `government iqta_government`) |
| Add a law | `add_law <law>` (e.g. `add_law status_of_women_4`; [law IDs](https://ck2.paradoxwikis.com/Laws)) |

### Debug event sub-mod

The sibling `SketchyCheatMenuPlusDebug` sub-mod (opt-in via the
launcher) exposes the `SCMPD.*` event family for hard-to-reach test
setups — bloodline grants, religion conversions, province modifier
applications, title-flag setters. Load it when your test needs one of
those.

### Pull request workflow

1. Fork the repo.
2. Create a branch from `main` for your change.
3. Make and test your changes (see Testing above).
4. Commit with the [convention from AGENTS.md](AGENTS.md#conventions)
   (release-prefixed subject `vX.Y.Z - <topic>`, optional bullet body,
   CHANGELOG entry in the same commit).
5. Open a PR against `main` with a brief description of what changed
   and why.

## License

By contributing, you agree that your contributions are licensed under
the same **MIT License** that covers the rest of the project. No CLA
required.
