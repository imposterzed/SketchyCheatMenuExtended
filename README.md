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

Paired add/remove decisions for 274 traits across virtues, sins, personality, beauty / physique, combat / leadership, warriors, holy war rewards, warrior lodge, chinese imperial, raiding, lifestyle, religious markers & doctrine, ordained clergy, christian status, muslim status, dharmic identity, birth markers, zodiac, childhood, kinslayer, memes, and other categories. Bulk operations apply virtues or remove sins from all your vassals or dynasty members at once.

### Spawning

Spawn children or siblings at chosen ages, spawn a wife, or spawn specialized courtiers (marshal, spymaster, steward, chancellor, priest, commander, physician). Also spawn armies (10k or 100k men) and fleets on demand.

### Settlement cheats

Right-click any settlement to:

- **Fully upgrade the holding** — every base building plus applicable culture, religion, terrain, bloodline, and title-conditional buildings (Theodosian Walls on Constantinople, HF-bloodline fortifications, Hellenic deity shrines, MR Arsenal on a patrician's family palace, Steppe / Desert / Monastic / Great Pillar buildings on matching provinces, etc.).
- **Convert** to a different type (castle / temple / city / tribal / nomad). Strips the old holding's buildings first to avoid the game freeze that vanilla `convert_to` causes.
- **Build** a new holding in an empty county slot (castle / temple / city / tribal / nomad), or an extra (hospital / fort / trade post). Right-click the county capital.
- **Delete** the holding.
- **Upgrade a hospital fully** (Reaper's Due) — right-click the county capital.
- **Upgrade a trade post fully** (The Republic) — right-click the trade post.

### Realm-wide cheats

Convert your realm or the entire world to a different culture / religion / ethnicity, grant gold / prestige / piety / tech / society points, maximize religious authority, triple your levies, reveal all realm plots, or quick-move armies anywhere on the map.

### Government

Switch government types via cheat-menu shortcuts. Each conversion only appears from source governments where the engine accepts it:

- **Become Independent** — works from any vassal state.
- **Change to Feudalism** — from Tribal (non-Muslim) or Nomadic\* sources.
- **Change to Iqta** — from Tribal (Muslim) or Nomadic\* sources.
- **Change to Tribal** — from Feudal / Iqta / Monastic Feudal / Chinese Imperial / Nomadic\* sources.
- **Change to Nomadic** (Horse Lords) — from Feudal / Tribal / Iqta / Monastic Feudal / Order / Chinese Imperial sources.

\* From Nomadic source, the variant carries "(Destroy Horde)" — settles the horde and demotes your realm.

### Inheritance Laws

Set inheritance laws on your primary title via cheat-menu shortcuts.

**Succession** — Byzantine Elective, Eldership (Holy Fury), Elective Gavelkind, Elective Monarchy, Gavelkind, Nomadic (Horse Lords), Open, Open Elective, Patrician Elective (The Republic), Primogeniture, Princely Elective, Seniority, Tanistry, Ultimogeniture.

**Gender succession** — Agnatic, Agnatic-Cognatic, Absolute Cognatic, Enatic, Enatic-Cognatic. On Iqta, Holy Order, and Merchant Republic sources, gender succession decisions carry "(Hidden)" suffix — vanilla's Inheritance UI doesn't display gender on those govs but the engine still applies the law.

### Realm Laws

Set realm laws on your primary title via cheat-menu shortcuts.

**Crown Authority** — Min, Low, Medium, High, Max.

**Investiture** — Free, Papal.

**Controlled Realm Inheritance** — Free, Illegal.

**Vassal War Declaration** — Allowed, External, Illegal.

**Centralization** — Min, Low, Medium, High, Max.

**Tribal Organization** — Min, Low, Medium, High, Max.

**Viceroyalty** — None, Kingdoms, Duchies.

**Status of Women** — Tradition, Marginal, Significant, Notable, Full.

**Revoke Title** — None, Allowed, Religious.

**Administration** — Feudal, Late, Imperial.

### Obligation Laws

Shift vassal-contract obligations toward tax or toward levy via cheat-menu shortcuts. Each cycles a 9-state slider (`_0` Heavily Tax Focused → `_4` Balanced → `_8` Heavily Levy Focused) one step per click; hides at boundaries.

**Noble Obligations** — castle-tier vassal contract (non-Muslim).

**Iqta Obligations** — castle-tier vassal contract (Muslim).

**Burgher Obligations** — city-tier vassal contract.

**Church Obligations** — temple-tier vassal contract.

**Tribal Obligations** — tribal-tier vassal contract.

### Council Laws

Toggle 8 council voting powers between ruler and council on your primary title via cheat-menu shortcuts. Cascade prerequisites dropped.

**Council Power** — Abolish, Empower.

**War Declaration** — Ruler, Council.

**Grant Titles** — Ruler, Council.

**Revoke Titles** — Ruler, Council.

**Imprisonment** — Ruler, Council.

**Banishment** — Ruler, Council.

**Execution** — Ruler, Council.

**Council Authority** — Limited, Full.

## Requirements

### Base game

- **Crusader Kings II `3.3.x`.** The base game is enough to install and use the mod.

### Optional DLC

The mod works without any DLC. Some cheats are tied to DLC systems and behave differently depending on what you have installed:

- **Charlemagne** — without it, the Viceroyalty toggle is hidden.
- **Conclave** — without it, `make_consort` is hidden. The 2 consort-themed birth-marker toggles (`child_of_concubine` / `child_of_consort`) stay available. The 12 Childhood toggles stay available. Administration is 3-state (Feudal / Late / Imperial) with Conclave; without Conclave it's binary Feudal ↔ Imperial. The Controlled Realm Inheritance, Vassal War Declaration, Status of Women, Revoke Title, all 5 Obligation Laws families, all 8 Council Voting Power families, and `build_fort` are hidden without Conclave; the Crown Authority cycle is hidden with Conclave (replaced by those Conclave realm laws).
- **Holy Fury** — without it, `add_tribal_kinslayer` is hidden; the 3 non-tribal kinslayer toggles (kinslayer / familial_kinslayer / dynastic_kinslayer) stay visible even for tribal characters, mirroring vanilla's fallback when HF is off. `remove_tribal_kinslayer` is ungated for cleanup. The 9 Warrior Lodge leader toggles and the Sea King / Sea Queen pair stay available. `add_scarred_mid` (Grievously Scarred) and `add_scarred_high` (Horrifically Scarred) are hidden without HF — the vanilla traits gate themselves to HF. Base `add_scarred` and all three `remove_*` counterparts stay available for cleanup. The 12 Zodiac toggles stay available. The 4 Pagan Branches toggles (Syncretist / Spiritualist / Militant / Tribalist) stay available. `set_succ_eldership` is hidden without HF. `set_succ_hre_elective` stays available. `upgrade_castle` / `upgrade_temple` / `upgrade_city` / `upgrade_tribal` stay available without HF. The HF-bloodline buildings inside them (Oppressive Fortifications / Special Fortifications / Monumental Shrines / Planned Infrastructure), Hellenic deity shrines, and Great Pillars require HF (the establish-pillar decision sets the province flag the building gates on).
- **Horse Lords** — without it, `set_nomadic`, the three `_nomad` Destroy-Horde variants (`set_feudal_nomad` / `set_iqta_nomad` / `set_tribal_nomad`), `set_succ_nomad_succession`, `convert_nomad`, and `build_nomad` are hidden.
- **Jade Dragon** — without it, the 4 Chinese Commander toggles (Way of the Dog / Dragon / Leopard / Tiger) and the 3 Kowtow tier toggles (Tier I / II / III) stay available.
- **Legacy of Rome** — `set_succ_byzantine_elective` stays available.
- **Monks and Mystics** — without it, the society cheats (`add_society_points`, `increase_society_rank`) don't appear, since you can't be in a society.
- **Rajas of India** — `add_war_elephant_leader` / `remove_war_elephant_leader` stay available. The 6 Dharmic Ordained Clergy toggles (`bhikkhu` / `bhikkhuni` / `muni` / `aryika` / `sanyasi` / `sanyasini`), the 10 Dharmic Identity toggles (3 castes + 4 Hindu branches + 3 Buddhist branches), `add_indian_pilgrim`, and the Dharmic GHW reward `kailash_guardian` don't appear, since you can't be of a Dharmic religion (Hindu / Buddhist / Jain) without Rajas.
- **Sunset Invasion** — the Aztec Holy War Reward (`eagle_warrior` / `eagle_knight`) and `bad_priest_aztec` don't appear, since you can't be Aztec without Sunset. The 3 Bloodthirsty Gods toggles (Haemophiliac / Haemophant / Haemoarch) stay available.
- **Sword of Islam** — `set_iqta` stays available without it. Muslim-specific mechanics layered on top (polygamy, decadence, peasant revolts) require SoI to function.
- **The Old Gods** — `set_tribal` and the Viking / Pirate / Ravager raiding toggles stay available without it. Tribal-specific gameplay (retinues, prestige raiding, Adopt Feudalism path) requires TOG.
- **The Reaper's Due** — without it, `scmp_build_hospital` and `upgrade_hospital_fully` are hidden. `add_physician` / `remove_physician` / `spawn_physician` stay available, as do the 6 limb-loss toggles (one_eyed / one_handed / one_legged / disfigured / mangled / severely_injured) and `sick_incapable`.
- **The Republic** — without it, `set_succ_patrician_elective`, `build_trade_post`, and `upgrade_trade_post_fully` are hidden. The Merchant Republic Arsenal inside `upgrade_city` requires The Republic.
- **Way of Life** — without it, `get_favor` and `clear_your_focus` are hidden. The 16 lifestyle-trait toggles (schemer, seducer, hedonist, scholar, theologian, etc.) stay available.

## Installation

**Manual install:** drop `SketchyCheatMenuPlus/` and `SketchyCheatMenuPlus.mod` into:

```
Documents/Paradox Interactive/Crusader Kings II/mod/
```

…then enable **Sketchy Cheat Menu Plus** in the launcher.

## Compatibility

Sketchy Cheat Menu Plus is a content mod that doesn't overwrite base-game files, so it should work alongside vanilla and most other mods as the original Sketchy Cheat Menu did.

### Sketchy Cheat Menu (upstream)

Save-compatible with upstream Sketchy Cheat Menu. All inherited data (custom traits, the dynasty-777777 "Outcast" formerly "Lowborn", event modifiers, custom buildings) keeps its original ID. Switching from upstream just requires swapping the mod selection in the launcher.

### CleanSlate

Full support. This mod ships with `dependencies = { "CleanSlate" }` declared, so it works with CleanSlate enabled and on plain vanilla.

Trait IDs are auto-adapted. CleanSlate renames several traits and sets a `cleanslate_active` global flag at startup; when that flag is present, this mod's trait-toggle decisions use CleanSlate's trait names instead of vanilla's.

Aztec culture and building IDs are also auto-adapted. CleanSlate renames the Aztec culture and its cultural building IDs; the `convert_*` strip helpers and the `upgrade_castle` / `upgrade_tribal` culture-aware adds pick the matching ID set under each stack.

**CleanSlate users — make sure you're on the latest version from [GitHub](https://github.com/ck2plus/CleanSlate)** — the startup flag is a recent addition. Without it, the mod uses vanilla IDs throughout, so trait-toggle and Aztec-building operations silently fail on a CleanSlate stack.

### CK2+

Historically OK with upstream; not verified for this fork.

### AGOT (A Game of Thrones)

Historically incompatible with upstream; not verified for this fork.

## For modders

**Mod detection.** Two flags let other mods detect this mod and the characters it spawns:

- **Detect the mod.** Sketchy Cheat Menu Plus sets the global flag `scmp_active` at `on_startup` (on new games and on every save load). Check for it with `has_global_flag = scmp_active` — the same way this mod detects CleanSlate's `cleanslate_active`.
- **Identify a spawned character.** Each character spawned via the menu's spawn decisions is tagged with a per-character flag — `scmp_spawned_child`, `scmp_spawned_sibling`, `scmp_spawned_wife`, `scmp_spawned_vassal`, `scmp_spawned_marshal`, `scmp_spawned_spymaster`, `scmp_spawned_steward`, `scmp_spawned_chancellor`, `scmp_spawned_priest`, `scmp_spawned_commander`, or `scmp_spawned_physician` — so you can match them with `has_character_flag`.

**error.log notes.** CK2's static parser validates every trait ID in a trigger context — both `scripted_trigger` bodies and `limit = { ... }` blocks inside scripted_effects. The CleanSlate compat triggers deliberately reference both vanilla and CleanSlate trait IDs across branches so the runtime picks the right one — but the parser flags the inactive branch's IDs as "unknown trait" warnings (~67 on either stack). These are cosmetic; runtime gating on `has_global_flag = cleanslate_active` ensures only the active stack's IDs are evaluated.

**Dev/test events.** Hard-to-reach paths (e.g., verifying the dynasty 777777 "Outcast" label, granting HF bloodlines for `upgrade_X` testing) have console-grant helpers in a sibling sub-mod, **Sketchy Cheat Menu Plus - Debug**. Enable it in the launcher alongside SCMP to use the `SCMPD.*` events — e.g. `event SCMPD.1 <charID>` assigns the target to dynasty 777777; `event SCMPD.2`–`SCMPD.5 <charID>` grant the 4 HF building-related bloodlines. The base mod doesn't ship these events.

## Development

The mod's script and localisation files (`.txt`, `.csv`) are stored in git as **Windows-1252** with CRLF line endings (enforced by `.gitattributes`) because CK2 reads them that way. Markdown files (this README, the changelog) are plain UTF-8.

For contributors:

- **Accented localisation edits must be saved as Windows-1252,** not UTF-8 — a UTF-8 save corrupts accents.
- A UTF-8/LF editor may flag files as needing CRLF reconciliation; run `git add --renormalize .` before committing.

## Credit & License

All design, content, and assets belong to [Sketchy](https://steamcommunity.com/id/sketchy77). Fork © 2026 imposterzed — MIT, see [LICENSE](LICENSE).
