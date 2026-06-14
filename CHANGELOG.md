# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.6.4] - 2026-06-14

### Added
- **12 new add/remove trait-toggle pairs in Health & Congenital**, closing the gap where multiple traits in the bulk-clear sweep (`remove_diseases`, which orchestrates 5 sub-sweeps) had no individual add toggle:
  - **Mixed-positive (scarred family)**: `scarred_mid` (Grievously Scarred), `scarred_high` (Horrifically Scarred). HF DLC gate on the `add_*` side mirrors vanilla's `potential = { has_dlc = "Holy Fury" }` on the trait. Remove side ungated. Mutex with `scarred` handled by vanilla `opposites`.
  - **Negative health states (base game)**: `incapable`, `lovers_pox`, `maimed`.
  - **Negative health states (Reaper's Due limb-loss family)**: `disfigured`, `mangled`, `one_eyed`, `one_handed`, `one_legged`, `severely_injured`. No DLC gate — the trait IDs load without RD and `add_trait` works regardless, so the cheat decision stays available for non-RD players.
  - **Hidden trait**: `sick_incapable` (RD `hidden = yes`, `incapacitating = yes`). Decision exposed despite no trait icon on the character sheet — `incapacitating = yes` produces visible engine effects (bed-curtain portrait background, incapacitated icon on portrait, regent takeover for the realm) that confirm the add worked. Remove dismisses the regent and restores the normal portrait.
- **24 new SCMP localisation entries** in `cheats_menu_intrigue_traits.csv` for the 12 new decision keys (`add_*` / `remove_*` labels plus `_desc` tooltips).

### Changed
- **4 trait-pair blocks moved from Misc to Health & Congenital**: `blinded`, `lunatic`, `possessed`, `scarred`. All members of `remove_all_afflictions_effect` (the bulk-clear orchestrator). Each block's `has_character_flag = show_misc` rewritten to `show_health` (both `add_*` and `remove_*` potentials). Decision keys unchanged, so existing localisation entries continue to apply.
- **Cosmetic-negative cluster (Fat, Malnourished) reordered above negative-health-states** within Health & Congenital — cosmetic body-composition states are milder than event-driven death-track conditions.
- **Misc Traits shrinks from 12 → 8 entries** — now contains Augustus, Heresiarch, Peasant Leader, Child of Concubine, Cannibal, Eunuch, Excommunicated, Homosexual.
- **README trait-pair count bumped from "over 150" to "170"** — actual count of non-bulk add toggles after v0.6.4.
- **README Optional DLC section updated**: Holy Fury entry notes `add_scarred_mid` / `add_scarred_high` are hidden without HF. The Reaper's Due entry notes the 6 limb-loss toggles and `sick_incapable` stay available — trait IDs load without RD.

## [0.6.3] - 2026-06-14

### Changed
- **Trait menu sections reorganized into logical groups.** Order changed from chronological-by-add to player-intent groups: core character (Cheat Traits, Virtues, Sins, Personality, Education, Health & Congenital), combat / champion (Leadership, Warriors, Holy War Rewards, Warrior Lodge, Chinese Commander, Raiding), lifestyle / status (Lifestyles, Religious Markers, Kinslayer, Misc Traits, Memes), bulk-on-others (Vassal Traits, Dynasty & Spouse Traits). Combat cluster ordered by audience breadth (universal → religion-locked → culture-locked → DLC-locked).
- **Within-section reorders** for sections where chronological-of-add ordering was incoherent:
  - **Cheat Traits**: alphabetical by display name (Beloved, Immortal, Master Builder, Master Commander, Master Landowner, Master Plotter).
  - **Personality**: alphabetical by the positive member of each trait pair, with pairs adjacent (e.g., brave/craven, gregarious/shy, just/arbitrary). Single-negative traits (cruel, stubborn) last.
  - **Education**: canonical CK2 stat order (Diplomacy / Martial / Stewardship / Intrigue / Learning) instead of the inherited Sketchy order.
  - **Health & Congenital**: ordered good-to-bad — sweeps first, then positive genetic alphabetical by display (Attractive / Genius / Quick / Strong), then mixed-positive (Giant / Left-Handed), then negative health states, then cosmetic-negative (Fat / Malnourished).
  - **Leadership**: grouped (Standard 12 → Unit-specialty 4 → Terrain 5), alphabetical by user-facing display within each group.
  - **Lifestyles**: alphabetical by display name — Master Schemer / Master Seducer / Master Seductress group with the M's (between Impaler and Mystic), and faqih placed immediately after scholar (religion-mirrored pair — the only positional exception).
  - **Holy War Rewards**: alphabetical by primary trait display name across religions (Ares' Own → Crusader [+king/+queen] → Eagle Knight [+Sun Warrior] → Gond-i Shahanshah → Hound of Dievas → Kailash Guardian → Kanai → Mujahid → Nyame's Shield → Perun's Chosen → Skylord → Ukko's Hammer → Valhalla Bound).
  - **Warrior Lodge**: alphabetical by user-facing display (Aeneator → Fearsome → Forest Ambusher → Marauder → Mountain Guardian → Pillar of the Plains → Scorcher → Shield of the Tundra → Spirit Warrior).
  - **Chinese Commander**: alphabetical by display (Way of the Dog → Dragon → Leopard → Tiger).
  - **Misc Traits**: positive traits first (Augustus, Heresiarch, Peasant Leader), then Child of Concubine as transition (remove-only birth-marker), then negative traits alphabetical (Blinded, Cannibal, Eunuch, Excommunicated, Homosexual, Lunatic, Possessed, Scarred).
- Mechanical refactor only — zero semantic changes. Decision keys, brace counts, and token multisets verified identical to v0.6.2.
- **README trait-toggles category list** reordered to match the new menu order (virtues / sins / personality / beauty&physique / combat&leadership / warriors / HWR / warrior lodge / chinese commander / raiding / lifestyle / religious markers / kinslayer / memes).
- **Education group comment** ("# set_<X>_education strips ALL 20 education traits...") moved to sit before `set_diplomacy_education` (the new first set_X under DMSIL order) instead of remaining attached to set_martial_education in its post-reorder position 2.

## [0.6.2] - 2026-06-14

### Added
- **3 new Tier 3 DLC menu sections** = 18 new add/remove trait-toggle pairs covering vanilla's DLC-themed combat / commander / raiding trait families.
  - **Chinese Commander** (new section, 4 traits): `logistics_expert` (Way of the Dog), `master_of_flame` (Way of the Dragon), `sapper` (Way of the Leopard), `levy_coordinator` (Way of the Tiger). Vanilla restricts natural acquisition to Han culture / Chinese-court characters; cheat menu allows free assignment per established precedent (no clean cultural alternative).
  - **Warrior Lodge** (new section, 9 traits): `norse_leader`, `tengri_leader`, `baltic_leader`, `finnish_leader`, `slavic_leader`, `west_african_leader`, `zun_leader`, `bon_leader`, `hellenic_leader`. Each `add_*` decision gated to its associated reformed-pagan religion (matching vanilla's award religion). Section itself gated via new `has_warrior_lodge_religion_trigger` — non-lodge religions don't see the empty menu (matches Holy War Rewards section-gating pattern).
  - **Raiding** (new section, 5 traits): `viking` (Norse-pagan gate), `pirate` (no gate — vanilla's `potential` block allows Norse pagans directly, so any character can naturally have it), `ravager` (no gate, upgrade trait), `seaking` (male sex-gate), `sea_queen` (female sex-gate). One CleanSlate compat helper added for `seaking` → `sea_king` (vanilla → CleanSlate rename).
- **1 new trait compat helper**: `add_seaking_trait_effect` / `remove_seaking_trait_effect` / `has_seaking_trait_trigger` (routes vanilla `seaking` ↔ CleanSlate `sea_king`).
- **1 new religion compat trigger**: `has_warrior_lodge_religion_trigger` — covers 9 reformed-pagan religions (Norse, Tengri, Baltic, Finnish, Slavic, West African, Zun, Bon via existing `is_bon_religion_trigger`, Hellenic). Used by `show_warrior_lodge` to hide the empty menu for non-lodge religions.

### Changed
- **README Optional DLC section** — added Jade Dragon entry (Chinese Commander toggles stay available) and The Old Gods entry (Viking / Pirate / Ravager raiding toggles stay available). Holy Fury entry reorganized: kinslayer behavior flows together, then Warrior Lodge leaders and Sea King / Sea Queen pair noted as staying available without HF.
- **README modder error.log count** — bumped 30 → 31 (one new compat helper for `seaking` adds one inactive-branch `unknown trait` warning per stack).

## [0.6.1] - 2026-06-13

### Added
- **3 new menu sections + 3 Misc additions** = 13 new add/remove trait-toggle pairs (all same-ID across vanilla and CleanSlate, no new compat helpers needed).
  - **Warriors** (new section): `adventurer`, `berserker`, `gladiator`, `shieldmaiden`, `varangian`. Named combat / champion traits with real stat impact. `add_shieldmaiden` is sex-gated to female (the vanilla trait has female-only description text — `female_compliment` with no male equivalent — and looks broken on male characters). `remove_shieldmaiden` stays ungated for cross-sex cleanup. Other 4 warrior traits have no gates — vanilla's berserker (Norse) restriction has no cross-religion alternative, so cheat menu allows free assignment per established precedent.
  - **Religious Markers** (new section): `reincarnation` (Hindu/Buddhist), `saoshyant` and `saoshyant_descendant` (Zoroastrian). No religion gates — cheat menu, no parallels.
  - **Memes** (new section): `cat`, `horse` — vanilla joke traits with `-10` to all stats, `inherit_chance = 100`, blocked marry/inherit/hold. Useful for testing edge cases (e.g., dynasty-cat inheritance).
  - **Misc additions**: `augustus`, `heresiarch`, `peasant_leader`. The latter two have `rebel_inherited = yes` in vanilla — sticky-trait removal is the original Sketchy use case.

## [0.6.0] - 2026-06-13

### Added
- **New Holy War Rewards menu section** with 16 add/remove toggle pairs covering every religion's GHW veteran trait. `crusader` moves here from Misc; new additions: `crusader_king`/`crusader_queen` (sex-mirrored Christian), `mujahid` (Muslim), `valhalla_bound` (Germanic pagan), `kailash_guardian` (Bon — vanilla `bon` / CleanSlate `bon_pagan`), `peruns_chosen` (Slavic), `ares_own` (Hellenic), `nyames_shield` (West African), `gondi_shahansha` (Zoroastrian), `eagle_warrior`/`sun_warrior` (Aztec), `romuvas_own` (Baltic), `tengri_warrior` (Tengri), `ukkos_shield` (Finnish), `shaddai` (Jewish). Religion gates on the `add_*` decisions mirror vanilla's `add_kinslayer_trait_effect`-style cascade: each religion only sees its own GHW reward as an add option. Sex split on the Christian pair. All `remove_*` decisions stay ungated for cleanup after religion changes.
- **5 new compat helpers** for CleanSlate-renamed GHW veterans: `eagle_warrior`→`eagle_knight`, `romuvas_own`→`hound_of_dievas`, `shaddai`→`kanai`, `tengri_warrior`→`skylord`, `ukkos_shield`→`ukkos_hammer`. Decision keys use vanilla names (per existing convention); display labels show CleanSlate names (per existing convention).

### Changed
- **`add_crusader` is now religion-gated to Christians.** A non-Christian who previously could cheat-click "Add Crusader" will no longer see it; mujahid / valhalla_bound / kailash_guardian / etc. are now the religion-appropriate alternatives. `remove_crusader` stays ungated for cleanup after religion changes.

## [0.5.1] - 2026-06-13

### Added
- **New Kinslayer menu section** with 4 add/remove toggle pairs: `kinslayer`, `familial_kinslayer`, `dynastic_kinslayer`, `tribal_kinslayer`. Sticky-trait removal is the original Sketchy use case; previously these were only removable via console. Government gates on the `add_*` decisions mirror vanilla's `add_kinslayer_trait_effect` cascade: `add_tribal_kinslayer` is gated `has_dlc = "Holy Fury"` + `is_tribal = yes`; the other 3 are gated `OR = { NOT has_dlc = "Holy Fury" is_tribal = no }` so a tribal character on a no-HF setup still sees the non-tribal toggles (matching vanilla's fallback to those traits when HF is absent). Remove decisions stay ungated for cleanup after government changes.
- **3 Misc Traits singletons**: `eunuch`, `cannibal`, `excommunicated`. Cannibal routes through a new compat helper (vanilla `cannibal_trait` → CleanSlate `cannibal`).

### Fixed
- **`add_fair` was silently removing the wrong trait** — the decision had `hidden_tooltip = { remove_trait = quick }`, but `quick` isn't an opposite of `fair` (vanilla declares `ugly` as fair's only opposite). Dropped the line; engine `opposites` handles fair/ugly correctly.

### Changed
- **README Optional DLC section** — added Holy Fury entry noting `add_tribal_kinslayer` is HF-gated; reordered entries alphabetically.
- **Trait-toggle count bumped** — README mentions ~100 trait pairs now (up from "over 80") and adds kinslayer to the category list.
- **Opposites-handling cleanup** — dropped redundant `hidden_tooltip = { remove_trait = ... }` from `add_genius` and `add_quick`. Engine `opposites` auto-removes; the explicit removes were over-defensive and inconsistent with the rest of the codebase.

## [0.5.0] - 2026-06-13

### Added
- **17 new trait-toggle decision pairs.** Single-stack base-game traits get direct `add_trait`/`remove_trait`; CleanSlate-renamed traits route through new compat helpers in `scmp_trait_compat.txt` + `scmp_trait_compat_triggers.txt`. See diff for specifics.
  - Lifestyles: `celibate`, `falconer`, `poet` (closes the lifestyle set to 18/18; post-WoL former-lifestyle traits, base game).
  - Leadership / Terrain: `mountain_terrain_leader` — joins the existing flat/rough/desert/jungle compat group (CleanSlate ID `mountain_expert`).
  - Personality / non-inheritable physique: `sturdy`, `groomed`, `uncouth`.
  - Health & Congenital: `depressed`, `drunkard`, `infirm`, `stressed`, `wounded` (previously remove-only via `remove_health_traits_effect`); `giant` and `lefthanded` as standalone toggles (mixed-value traits with combat/intrigue upsides, so excluded from the strictly-negative `remove_defects` sweep).
  - Physique cosmetic: `fat`, `malnourished` — CleanSlate IDs (vanilla `is_fat`/`is_malnourished`); compat helpers added.
  - Religion-mirrored learning lifestyle: new `faqih` pair gated to Muslims; existing `add_scholar` gated to non-Muslims. Mirrors vanilla's mutual-`opposites` declaration between the two traits; parallels the existing sex-aware seducer/seductress pattern. `remove_scholar`/`remove_faqih` stay unrestricted so a character who converts between religions can clean up the now-wrong-religion trait (vanilla doesn't auto-swap on conversion).

## [0.4.2] - 2026-06-13

### Changed
- **DLC gating on 2 decisions** whose backing effect is DLC-introduced and would silently fail (or log an error) without that DLC. Added `has_dlc` to the appropriate gate block of:
  - `make_consort` → `has_dlc = "Conclave"`. `add_consort` is a Conclave scripting command (per vanilla `ChangeLog.txt`); without Conclave the effect no-ops.
  - `clear_your_focus` → `has_dlc = "Zeus"`. `clear_focus` is used only inside WoL's own `ze_*` files in vanilla. Matches the existing `get_favor` gate.
- **README — Optional DLC section corrected.** The inherited description claimed several decisions were "hidden, no-op, or reduced functionality" without their DLC, but most of those traits are defined in `common/traits/*.txt` (which CK2 loads regardless of DLC) and work fine as cheats. After empirical verification the section now distinguishes:
  - DLC-effect-dependent decisions (`get_favor`, `make_consort`, `clear_your_focus`) — explicitly gated.
  - Decisions naturally soft-gated by their own triggers (`add_society_points`/`increase_society_rank` via `is_in_society = yes`; `upgrade_hospital_fully` via `has_hospital = yes`) — no DLC gate needed.
  - DLC-themed trait toggles whose trait IDs are in vanilla data and remain usable as cheats: the 16 Way of Life lifestyle traits, the Reaper's Due `physician` trait (`02_traits.txt:2136`), and the Rajas of India `war_elephant_leader` trait (`02_traits.txt:930`).

## [0.4.1] - 2026-06-13

### Fixed
- **`mc_marry` silently-failing trigger typo** — `mc_marry`'s `allow` had `NOT = { is_spouse = ROOT }`. `is_spouse` isn't a CK2 trigger, so the gate fell through silently — `mc_marry` would let the mind-controlled character marry ROOT even if they were already ROOT's spouse. Replaced with `NOT = { spouse = { character = ROOT } }` per CK2 trigger syntax.
- **`mc_vassalize` silently-failing trigger typo** — `mc_vassalize`'s `allow` had `NOT = { defacto_liege = PREV }`. `defacto_liege` (no underscore) isn't a trigger; `de_facto_liege` is. Replaced with `NOT = { de_facto_liege = PREV }`. The "don't vassalize someone already your de facto liege" gate now actually fires.
- **`from_potential` on 12 self-targeted decisions** — CK2 logs `[decision.cpp:752]: Usage of from potential on self targeted decision found, use potential instead!` for each `filter = self` decision using `from_potential`. Conditions merged into the existing `potential` blocks. Affected: `cheats_disable`, `cheats_enable`, `mind_control_disable`, `mind_control_enable`, `self_heals`, `self_genes`, `self_stats`, `self_stats2`, `self_nickname`, `fall_on_sword`, `clear_your_focus`, `clear_your_ambition`.

### Changed
- **Dynasty 777777 renamed from "Lowborn" to "Outcast"** (literal `name = "Outcast"` in `disown_them.txt`). The old name conflicted with vanilla CK2's display name for `dynasty = 0` (the actual lowborn state). The dynasty itself stays defined for save-compat with characters from earlier upstream versions.
- **README** — added Compatibility subsection documenting SCM save-compat, and a Dev/test events paragraph under For modders pointing at the new debug sub-mod.

### Added
- **`SketchyCheatMenuPlus - Debug` sibling sub-mod** for hard-to-reach test paths. Ships one event at v0.4.1: `SCMPD.1` (assigns target to dynasty 777777, used to verify the Outcast rename displays correctly). Mirror of ER's `EliteRecruitmentDebug` pattern. Enable alongside SCMP in the launcher to use.

## [0.4.0] - 2026-06-12

### Fixed
- **`convert_*` orphan-building freeze** — `convert_to` leaves the old holding's buildings on the slot, which froze the game. Each `convert_*` decision now strips the source type's buildings before `convert_to` via new helpers in `common/scripted_effects/scmp_holding_effects.txt` (one `strip_<type>_buildings_effect` per source type: castle, temple, city, tribal, nomad). The Aztec rename (`ca_culture_nahuatl_*` / `ca_culture_nahua_*`) is flag-gated.
- **`convert_*` potential over-broad capital filter** — `is_capital = yes` at settlement scope matches any county primary holding, not just the realm capital. New filter combines `is_capital = yes` with `FROM = { capital_holding = { title = ROOT } }`, so only the actual realm capital is blocked; lesser county primaries stay convertible.
- **`join_their_dynasty` scope + duplicate-gate** (`cheats_menu.txt`) — `limit = { is_married = X }` sat inside `FROM = { ... }`, so it tested the player's marital status instead of the target's; the female-ROOT branch additionally had both `if` blocks gated on `is_married = yes`. Both branches rewritten to default the non-ROOT parent slot to 0 and conditionally override to the target's spouse when married.

### Changed
- **`upgrade_castle` is now culture-aware** (decision + potential). Previously the decision added all 26 cultural-building families unconditionally (~104 inactive entries per cast). Routed through `add_castle_culture_buildings_effect` which adds only the family matching the holding's current culture. The matching trigger `has_castle_culture_buildings_trigger` re-surfaces the decision after a culture shift until the new culture's tier-4 building is built. The Aztec rename is flag-gated end-to-end. Both helpers live in new files under `common/scripted_effects/` and `common/scripted_triggers/`. Culture checks wrap in `location = { culture = X }` to read the province's current culture; bare `culture = X` at `settlement_decisions` scope reads the settlement's stored culture, which doesn't update after province culture shifts.

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
