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

Full support. This mod ships with `dependencies = { "CleanSlate" }` declared, so it works with CleanSlate enabled and on plain vanilla.

Trait IDs are auto-adapted. CleanSlate renames several traits (physique, beauty, terrain-leader traits, the tier-2 cleric education, and others) and sets a `cleanslate_active` global flag at startup; when that flag is present, this mod's trait-toggle decisions use CleanSlate's trait names instead of vanilla's.

Aztec culture and building IDs are also auto-adapted. CleanSlate renames the Aztec culture (`nahuatl` → `nahua`) along with its cultural building IDs (`ca_culture_nahuatl_*` → `ca_culture_nahua_*`, plus the matching `tb_*` tribal counterparts); the `convert_*` strip helpers and the `upgrade_castle` culture-aware add pick the matching ID set under each stack.

**CleanSlate users — make sure you're on the latest version from [GitHub](https://github.com/ck2plus/CleanSlate)** — the startup flag is a recent addition. Without it, the mod uses vanilla IDs throughout, so trait-toggle and Aztec-building operations silently fail on a CleanSlate stack.

### CK2+

Historically OK with upstream; not verified for this fork.

### AGOT (A Game of Thrones)

Historically incompatible with upstream; not verified for this fork.

## For modders

**error.log notes.** CK2's static parser validates every trait ID referenced by a `scripted_trigger`, including IDs in branches that won't execute on the current stack. The CleanSlate compat triggers deliberately reference both vanilla and CleanSlate trait IDs across branches so the runtime picks the right one — but the parser flags the inactive branch's IDs as "unknown trait" warnings (~21 on either stack). These are cosmetic; runtime gating on `has_global_flag = cleanslate_active` ensures only the active stack's IDs are evaluated.

## Development

The mod's script and localisation files (`.txt`, `.csv`) are stored in git as **Windows-1252** with CRLF line endings (enforced by `.gitattributes`) because CK2 reads them that way. Markdown files (this README, the changelog) are plain UTF-8.

For contributors:

- **Accented localisation edits must be saved as Windows-1252,** not UTF-8 — a UTF-8 save corrupts accents.
- A UTF-8/LF editor may flag files as needing CRLF reconciliation; run `git add --renormalize .` before committing.

## Credit & License

All design, content, and assets belong to [Sketchy](https://steamcommunity.com/id/sketchy77). Fork © 2026 imposterzed — MIT, see [LICENSE](LICENSE).
