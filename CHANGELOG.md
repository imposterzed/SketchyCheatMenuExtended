# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.3.1] - 2026-06-09

### Changed
- **File headers** added to all 16 legacy `.txt`/`.gfx` files. Files whose role isn't obvious from a single line get a short description block under the title.
- **Section anchors** converted from `##SECTION##` to `## ===== Section ===== ##` (3 in `cheats_menu_intrigue_spawn.txt`, 11 in `cheats_menu_intrigue_traits.txt`).
- **Inline `#` comments** added throughout — per-decision rationale, CK2 idioms, in-game UI labels (e.g. `death_murder_unknown` → "died under suspicious circumstances"), and clarifications of non-obvious behavior. See diff for specifics.

## [0.3.0] - 2026-06-09

### Changed
- **Formatting pass** across all `.txt`/`.gfx` files. Mechanical normalization only:
  - Re-indent every line to 2 spaces per brace-nesting level (was a mix of tabs, 4-space, 8-space, and tab+space hybrid).
  - Strip trailing whitespace (~240 lines across 7 files).
  - Fix inline spacing nits: `=no` → `= no` (1 case), `{X` → `{ X` and `X}` → `X }` (~20 cases, mostly in `cheats_menu_titles.txt`).
- Zero semantic changes — token sequences and brace counts identical to v0.2.0.

## [0.2.0] - 2026-06-08

### Added
- **CleanSlate trait-ID compat hooks** for the 22 vanilla trait IDs CleanSlate renames that SCMP touches, routed via `has_global_flag = cleanslate_active`. Two new directories: `common/scripted_effects/` (`scmp_trait_compat.txt`, `scmp_spawn_effects.txt`, `scmp_health_effects.txt`) and `common/scripted_triggers/` (`scmp_trait_compat_triggers.txt`, `scmp_health_triggers.txt`).
- **Expanded illness/wound coverage** beyond Sketchy's original list: `scarred_mid`, `scarred_high` (Holy Fury battle-scar variants), `blinded`, `sick_incapable`, `lovers_pox`.

### Fixed
- **13 trait-toggle decision pairs** in `cheats_menu_intrigue_traits.txt` now correctly add/remove on both stacks (previously silent failures under CleanSlate — the add_trait pointed at the vanilla ID that CleanSlate had renamed). Affected: `robust`/`brawny`, `feeble`/`frail`, `fair`/`attractive`, `schemer`/`master_schemer`, `seducer`/`master_seducer`, `seductress`/`master_seductress`, `gamer`/`game_master`, `experimenter`/`direct_leader`, `narrow_flank_leader`/`battlefield_terrain_master`, and the four terrain leaders (desert/flat/jungle/rough).
- **5 `set_<X>_education` decisions** correctly strip `martial_cleric` / `dutiful_cleric` (the tier-2 learning education trait CleanSlate renamed).
- **Disease decisions** (`self_heals`, `heal_them`, `remove_diseases`) correctly detect and remove the 8 renamed disease traits (`has_tuberculosis`/`consumption`, the 7-trait epidemic family, `syphilitic`/`great_pox`).
- **Composite decisions** (`self_genes`, `fix_genes`, `add_dynasty_genetics`) route the beauty-trait grant through the compat hook.
- **18 spawn templates** (children, siblings, wife, vassal) previously granted the beauty trait via inline `trait = fair` in `create_character` (silently failed on CleanSlate). Now route through a post-create finalization hook that applies the rename-aware grant; `spawn_wife` also gained a `flag = spawned_wife` so the hook can find her.

### Changed
- **`remove_diseases` orchestrator restructured** as 5 wiki-categorized utilities (Health / Diseases / Symptoms / Maimed / Special) + a `remove_all_afflictions_effect` orchestrator, replacing ~250 lines of inline trait-list duplication across `self_heals` / `heal_them` / `remove_diseases` × potential+effect.

## [0.1.1] - 2026-06-08

### Fixed
- **`make_consort` malformed syntax** — `decisions/cheats_menu.txt:695` had `FROM { add_consort = ROOT }` (missing `=`). CK2 parses that as a bareword followed by a block and silently misroutes the call. Now `FROM = { add_consort = ROOT }`.
- **`mind_control_disable` left orphaned flags** — disabling the mind-control toggle cleared `mind_control_enabled` on the player but left every previously-controlled character indefinitely carrying `has_character_flag = mind_controlled`. Added a `hidden_tooltip` sweep that clears the flag from all characters when the toggle goes off.

## [0.1.0] - 2026-06-08

### Added
- **Initial baseline fork** of [Sketchy Cheat Menu](https://steamcommunity.com/sharedfiles/filedetails/?id=608738995) by [Sketchy](https://steamcommunity.com/id/sketchy77) (upstream last updated 2019-10-19). Content pulled verbatim from the SteamCMD-archived workshop files.
- **Project setup for git tracking** — separate launcher `.mod` + content folder layout, MIT `LICENSE` with attribution to the original author, `.gitignore`, `.gitattributes` (Windows-1252 working-tree for `.txt`/`.csv`), README, this changelog.
- **Mod files** — launcher `SketchyCheatMenuPlus.mod` + descriptor `SketchyCheatMenuPlus/descriptor.mod`. Renamed to "Sketchy Cheat Menu Plus", replaced the upstream tag list with `{ "Decisions" "Cheats" "QoL" "Compatibility" }`, added `dependencies = { "CleanSlate" }` so CleanSlate's `cleanslate_active` flag is set before this mod loads.
