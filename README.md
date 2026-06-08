# Sketchy Cheat Menu Plus

A fork of [Sketchy Cheat Menu](https://steamcommunity.com/sharedfiles/filedetails/?id=608738995) by [Sketchy](https://steamcommunity.com/id/sketchy77) (upstream last updated 2019-10-19).

## What it does

Sketchy Cheat Menu Plus adds a comprehensive in-game cheat menu accessible through right-click character, settlement, and realm decisions. After enabling cheats with the **Enable Cheats** decision on yourself, every cheat decision becomes available; turn them off again with **Disable Cheats** when you're done. AI characters never see these decisions.

### Self cheats

Heal any affliction (diseases, wounds, scars, depression, lunacy), set any of the 5 tier-4 educations, modify your stats up or down, fix or upgrade your genes, grant good genetic traits to your dynasty, change your nickname, become immortal, clear your focus / ambition, or grant yourself the 5 custom cheat traits (Mastermind, Builder, Landlord, Conspirator, Beloved) that boost every skill.

### Character cheats

Right-click any character to:

- **Mind control** — possess them and use their decisions as if you were them.
- **Dynasty changes** — adopt them into your dynasty, disown them, have them join your dynasty, or kill their entire dynasty.
- **Removal** — kill them, imprison them, revoke all their titles.
- **Relationships** — force marry, impregnate, make consort, defriend, or make them your rival.
- **State changes** — change their religion / culture / ethnicity, modify their stats, heal them, or lower their threat level.

### Trait toggles

Paired add/remove decisions for over 80 traits across virtues, sins, personality, lifestyle, combat / leadership, beauty / physique, and other categories. Bulk operations apply virtues or remove sins from all your vassals or dynasty members at once.

### Spawning

Spawn children or siblings at chosen ages, spawn a wife, or spawn specialized courtiers (marshal, spymaster, steward, chancellor, priest, commander, physician). Also spawn armies (10k or 100k men) and fleets on demand.

### Settlement cheats

Right-click any settlement to fully upgrade the holding, convert it to a different type (castle / temple / city / tribal / nomad), delete it, or max out a hospital's facilities.

### Realm-wide cheats

Become independent, set your government to feudal, convert your realm or the entire world to a different culture / religion / ethnicity, grant gold / prestige / piety / tech / society points, maximize religious authority, triple your levies, reveal all realm plots, or quick-move armies anywhere on the map.

## Requirements

### Base game

- **Crusader Kings II `3.3.x`.** The base game is enough to install and use the mod.

### Optional DLC

Several decisions reference DLC-specific content. Without the relevant DLC the decision is either hidden, a no-op, or has reduced functionality, but the mod still loads cleanly:

- **Way of Life** — `get_favor` (explicitly DLC-gated; won't appear without WoL), `clear_your_focus`, and 16 trait-toggle decisions for Way of Life lifestyle traits (schemer, impaler, seducer, seductress, gardener, architect, administrator, hunter, duelist, strategist, gamer, hedonist, socializer, mystic, scholar, theologian).
- **Conclave** — `make_consort` (uses Conclave's `add_consort` effect).
- **Monks and Mystics** — `add_society_points` and `increase_society_rank` use this DLC's society system.
- **The Reaper's Due** — `add_physician` / `remove_physician`, `spawn_physician`, and the hospital max-out decision (uses the `pilgrims_inn_1` building from TRD's hospital system).
- **Rajas of India** — `add_war_elephant_leader` / `remove_war_elephant_leader`.

## Installation

**Manual install:** drop `SketchyCheatMenuPlus/` and `SketchyCheatMenuPlus.mod` into:

```
Documents/Paradox Interactive/Crusader Kings II/mod/
```

…then enable **Sketchy Cheat Menu Plus** in the launcher.

## Compatibility

Sketchy Cheat Menu Plus is a content mod that doesn't overwrite base-game files, so it should work alongside vanilla and most other mods as the original Sketchy Cheat Menu did.

### CleanSlate

This mod declares `dependencies = { "CleanSlate" }` in its `.mod` descriptor so it loads after CleanSlate when present. At v0.1.0 the mod content is unchanged from upstream Sketchy and doesn't account for CleanSlate's trait renames — CleanSlate users may experience trait-toggle failures because some decisions reference vanilla trait IDs that CleanSlate has renamed.

### CK2+

Historically OK with upstream; not verified for this fork.

### AGOT (A Game of Thrones)

Historically incompatible with upstream; not verified for this fork.

## Development

The mod's script and localisation files (`.txt`, `.csv`) are stored in git as **Windows-1252** with CRLF line endings (enforced by `.gitattributes`) because CK2 reads them that way. Markdown files (this README, the changelog) are plain UTF-8.

For contributors:

- **Accented localisation edits must be saved as Windows-1252,** not UTF-8 — a UTF-8 save corrupts accents.
- A UTF-8/LF editor may flag files as needing CRLF reconciliation; run `git add --renormalize .` before committing.

## Credit & License

All design, content, and assets belong to [Sketchy](https://steamcommunity.com/id/sketchy77). Fork © 2026 imposterzed — MIT, see [LICENSE](LICENSE).
