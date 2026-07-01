# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.12.3] - 2026-06-30

### Changed
- Updated the mod thumbnail for SCMP.

## [0.12.2] - 2026-06-30

### Added
- **Outcast dynasty (777777) coat of arms** — black X on blood-red field, replacing the engine's random fallback.

## [0.12.1] - 2026-06-30

### Added
- **Proper4KUI Patch trait icons** (`SketchyCheatMenuPlusProper4KUIPatch/gfx/traits/`) — 43×43 hi-res variants of the 5 SCMP-custom cheat trait icons.

### Changed
- Redesigned 5 SCMP-custom cheat trait icons (Beloved, Master Builder, Master Commander, Master Landowner, Master Plotter), preserving Sketchy 2019's gold-ring + dark-purple-disk framework.
- Trait descriptions filled in (previously `...`) with sex-aware getters.
- Removed redundant `immortal` / `immortal_desc` overrides from `traits.csv`.
- `triple_levies` modifier icon changed from `13` to `1` — `13` rendered as Military on vanilla but Prestige on CleanSlate due to CleanSlate's reindexed strip. `1` (Martial / crossed swords) renders consistently on both stacks.
- `triple_levies` description rewritten with sex-aware getter.

### Fixed
- 5 SCMP-custom trait DDS files were 24×25 (Sketchy 2019 off-by-one); resaved at 24×24.
- `enable_triple_levies` description double-period typo.

## [0.12.0] - 2026-06-29

### Added
- **Proper4KUI Patch sub-mod** (`SketchyCheatMenuPlusProper4KUIPatch`) — companion mod that swaps in the 50×50 hi-res icon variant when [Proper 4K UI Project](https://steamcommunity.com/sharedfiles/filedetails/?id=3054987840) is also loaded.

### Changed
- Section-toggle decisions (`Show X` / `Hide X` plus the master enable/disable toggles) show the mod's decision icon, replacing the placeholder.
- Individual and bulk decisions no longer show an icon.

## [0.11.2] - 2026-06-29

### Added
- **Obligation Laws max-endpoint decisions** — `Max Tax` / `Max Levy` shortcuts for Noble, Iqta, Burgher, Church, and Tribal Obligations jump the slider directly to either endpoint in one click.
- 10 new GFX sprite entries in `cheats_menu_intrigue_laws_c_obligation.gfx`.

### Fixed
- `Shift Iqta Obligations Toward Tax` no longer leaves the Heavy Levy state lingering when stepping down from the top (vanilla iqta law mutex-chain quirk).

## [0.11.1] - 2026-06-28

### Added
- **Realm Laws max-shortcut decisions** — `Max Crown Authority`, `Max Centralization`, `Max Tribal Organization`, and `Max Status of Women` each set their family's law to the top tier in one click.
- 4 new GFX sprite entries in `cheats_menu_intrigue_laws_b_realm.gfx`.

## [0.11.0] - 2026-06-28

### Added
- **Bulk Council Laws decisions** — `Set All Voting Laws: Ruler` and `Set All Voting Laws: Council` flip every applicable council voting law on the player's primary title in one click. Each per-law flip respects its tribal-organization tier gate (Council Power / War — tier 1+; Grant / Revoke Titles — tier 2+; Imprisonment / Banishment / Execution — tier 3+) and the feudal-KING+ gate on Council Authority.
- 5 new scripted_triggers in `scmp_law_triggers.txt` (3 tier-eligibility helpers + 2 decision visibility triggers).
- 2 new GFX sprite entries in `cheats_menu_intrigue_laws_d_council.gfx`.

### Changed
- README Council Laws section: added bulk-decision callout.

## [0.10.5] - 2026-06-28

### Added
- **Bulk add/remove in Cheat Traits section** — `Add All Cheat Traits` grants Beloved, Immortal, Master Builder, Master Commander, Master Landowner, Master Plotter. `Remove All Cheat Traits` clears every cheat trait held.
- 1 new section-bulk scripted_effect in `scmp_bulk_effects.txt` (`clear_cheat_traits_effect`) and 2 new visibility scripted_triggers in `scmp_trait_section_triggers.txt`.
- 2 new GFX sprite entries in `cheats_menu_intrigue_traits.gfx`.

### Changed
- README Trait toggles section: Cheat Traits added as the first sub-section, plus Zodiac, Kinslayer, Misc Traits, Memes, Vassal Traits, and Dynasty & Spouse Traits added as explicit sub-sections matching in-game menu order. The catch-all "Other categories" line and the standalone Vassal/Dynasty summary line removed.

## [0.10.4] - 2026-06-28

### Added
- **Bulk add/remove in Leadership section** — `Add All Leadership` / `Remove All Leadership`. Add grants every Leadership trait the character is missing; Remove clears every Leadership trait held.
- **Bulk add/remove in Warriors section** — `Add All Warriors` / `Remove All Warriors`. Add grants Adventurer, Berserker, Gladiator, Varangian, and Shieldmaiden (female only); Remove clears every Warriors trait held.
- **Bulk add/remove in Chinese Imperial section** — `Add All Chinese Imperial` / `Remove All Chinese Imperial`. Add grants Way of the Dog, Way of the Dragon, Way of the Leopard, Way of the Tiger, and Kowtow Complete (Tier III), replacing lower kowtow tiers. Remove clears the commanders and all three kowtow tiers.
- 3 new section-bulk scripted_effects in `scmp_bulk_effects.txt` (`clear_leadership_traits_effect`, `clear_warriors_traits_effect`, `clear_chinese_imperial_traits_effect`) and 6 new visibility scripted_triggers in `scmp_trait_section_triggers.txt`.
- 6 new GFX sprite entries in `cheats_menu_intrigue_traits.gfx`.

### Changed
- README Trait toggles section: Leadership, Warriors, Holy War Rewards, Warrior Lodge, Chinese Imperial, and Raiding added as explicit sub-sections with their full trait inventory, replacing the catch-all "Other categories" lump for these six sections. Order matches in-game file order.
- Individual Leadership decision labels updated for clarity: `Defender` → `Defensive Leader`, `Unyielding` → `Unyielding Leader`.

### Fixed
- Duplicate `add_mountain_terrain_leader` / `remove_mountain_terrain_leader` loc entries collapsed to a single pair (Mountain Expert).

## [0.10.3] - 2026-06-27

### Added
- **Bulk add/remove in Sympathies sub-section of Religious Markers & Doctrine** — `Add All Sympathies` / `Remove All Sympathies`. Add grants the 5 cross-religion sympathies applicable to the character (own-religion sympathy is engine-blocked via potential) and strips Zealous as cross-section cleanup. Remove strips every sympathy held.
- 2 new scripted_effects in `scmp_bulk_effects.txt` (`clear_sympathy_traits_effect`, `clear_sympathy_mutex_effect`) and 2 new visibility scripted_triggers in `scmp_trait_section_triggers.txt` (`has_any_sympathy_trait_trigger`, `has_all_sympathy_traits_trigger` — religion-aware via trigger_if branches per religion_group).
- 2 new GFX sprite entries in `cheats_menu_intrigue_traits.gfx`.

### Changed
- README Trait toggles section restructured: previously-evaluated categories without bulk decisions (Health & Congenital, Religious Markers & Doctrine, Ordained Clergy, Christian Status, Muslim Status, Dharmic Identity, Birth Markers) promoted out of the catch-all "Other categories" lump into explicit listings with their full trait inventory. Section order matches in-game file order. Trimmed Other categories to the unevaluated sections.
- Individual sympathy decision labels renamed to match the vanilla in-game trait display names: Christendom → Christian, Indian → Eastern, Islam → Muslim, Judaism → Israelite, Pagans → Pagan, Zoroastrians → Mazdan. Decisions reordered in the menu to alphabetical by new name.

### Fixed
- Individual `add_sympathy_X` decisions now strip Zealous explicitly for tooltip parity.

## [0.10.2] - 2026-06-27

### Added
- **Bulk add/remove in Lifestyles section** — `Add All Lifestyles` / `Remove All Lifestyles`. Add grants 18 lifestyles — 16 always-stackable: Administrator, Architect, Duelist, Falconer, Game Master, Gardener, Hedonist, Hunter, Impaler, Mystic, Poet, Renowned Physician, Master Schemer, Socializer, Strategist, Theologian; plus Scholar or Faqih (religion-routed) and Master Seducer or Master Seductress (sex-routed). Add All Lifestyles adds Hedonist over Celibate; Remove All Lifestyles also strips Celibate.
- 2 new section-bulk scripted_effects in `scmp_bulk_effects.txt` (`clear_lifestyle_traits_effect`, `clear_lifestyle_mutex_effect`) and 2 new visibility scripted_triggers in `scmp_trait_section_triggers.txt`.
- 2 new GFX sprite entries in `cheats_menu_intrigue_traits.gfx` for the new decisions.

### Changed
- Individual Lifestyles decision labels updated to match the in-game trait display names: `Gamer` → `Game Master`, `Physician` → `Renowned Physician`. The Renowned Physician pair moved between Poet and Scholar in the menu order.

## [0.10.1] - 2026-06-24

### Added
- **Bulk add/remove in Personality section** — `Add All Positive Personality` / `Remove All Positive Personality` / `Add All Negative Personality` / `Remove All Negative Personality`. Positive bucket (11): Ambitious, Brave, Brawny, Zealous, Erudite, Gregarious, Groomed, Honest, Just, Shrewd, Trusting. Negative bucket (12): Content, Craven, Frail, Cynical, Shy, Uncouth, Deceitful, Arbitrary, Dull, Paranoid, Cruel, Stubborn. Add variants strip the opposing bucket; Zealous additionally strips faith sympathies, Cruel additionally strips Kind. Add All Positive adds Brawny over Sturdy; Remove All Positive also strips Sturdy.
- **Bulk add/remove in Childhood section** — `Add All Childhood Traits` / `Remove All Childhood Traits`. Add grants 10 traits (skipping the Timid/Rowdy mutex pair); Remove strips all 12.
- 5 new section-bulk scripted_effects in `scmp_bulk_effects.txt` (`clear_positive_personality_effect`, `clear_negative_personality_effect`, `clear_childhood_traits_effect`, `clear_positive_personality_mutex_effect`, `clear_negative_personality_mutex_effect`) and 6 new visibility scripted_triggers in `scmp_trait_section_triggers.txt`.
- 6 new GFX sprite entries in `cheats_menu_intrigue_traits.gfx` for the new decisions.

## [0.10.0] - 2026-06-23

### Added
- **Bulk add/remove in Virtues and Sins sections** — `Add All Virtues` / `Remove All Virtues` / `Add All Sins` / `Remove All Sins` decisions. Add variants gain missing traits and strip opposites; Remove variants clear every section trait held.
- 3 new section-bulk scripted_effects in `scmp_bulk_effects.txt` (`clear_virtue_traits_effect`, `clear_sin_traits_effect`, `clear_virtue_mutex_effect`) and 4 new visibility scripted_triggers in `scmp_trait_section_triggers.txt` (`has_any_virtue_trigger`, `has_all_virtues_trigger`, `has_any_sin_trigger`, `has_all_sins_trigger`).
- 4 new GFX sprite entries in `cheats_menu_intrigue_traits.gfx` for the new decisions.

### Changed
- Virtue and sin entries in `cheats_menu_intrigue_traits.csv` reordered to match the in-game menu order from the decisions file (kind moved to position 3 of virtues; envious moved to last sin).

## [0.9.6] - 2026-06-22

### Changed
- **Confirmation popup tightened** — the 12 upgrade and convert decisions wrap their effect in `hidden_tooltip` so the right-click preview no longer floods with per-building "X gains Y" lines.
- **`convert_X` realm capital protection** — now hides on any realm's capital across the map (yours, vassals', and foreign realms'), not just your own.
- README updated for the convert capital protection.

### Fixed
- **Great Pillars in `upgrade_tribal`** — previously gated on the province flag set by the vanilla establish-pillar decision (which already builds the pillar), making the SCMP branch a no-op. The cheat now sets the flag inline and gates on the owner + liege religion + tribal status, using 2 new compat triggers (`is_aztec_unreformed_religion_trigger` / `is_bon_unreformed_religion_trigger`) for CleanSlate's `aztec_pagan` / `bon_pagan` renames.
- **Owner-side gating across 8 conditional branches** — HF-bloodline / Hellenic shrines / MR Arsenal / pagan religion / monastic-feudal government branches in `upgrade_castle / temple / city / tribal` now check the holding's owner instead of the decision-runner. Previously, running `upgrade_X` on a vassal-owned holding could add buildings the vassal couldn't activate.

## [0.9.5] - 2026-06-21

### Added
- **Build extras** — 3 new decisions (`scmp_build_hospital` / `build_fort` / `build_trade_post`) build a hospital / fort / trade post in the county. Right-click the county capital; `scmp_build_hospital` requires Reaper's Due, `build_fort` requires Conclave, `build_trade_post` requires The Republic. `scmp_build_hospital` carries the `scmp_` prefix to avoid colliding with vanilla's `title_decisions.build_hospital`.
- **`upgrade_trade_post_fully`** — adds every applicable vanilla trade post building (29 across 7 trade-route / culture branches), each gated to its vanilla potential so saves only carry applicable buildings. Right-click the trade post itself. Requires The Republic.

### Changed
- **`upgrade_hospital_fully`** hides once fully upgraded (ceiling check on all 10 top-tier buildings).
- README updated for the new decisions.

## [0.9.4] - 2026-06-21

### Added
- **`convert_tribal`** — converts any non-tribal realm-owned holding to tribal type (not on the realm capital). Strips source-type buildings first to keep saves clean. Completes the convert_X family (castle / temple / city / tribal / nomad).
- **Build empty holdings** — 5 new decisions (`build_castle` / `build_temple` / `build_city` / `build_tribal` / `build_nomad`) build a new holding in an empty county slot. Right-click the county capital; `build_nomad` requires Horse Lords.

### Changed
- README updated for `convert_tribal` and the 5 build decisions.

## [0.9.3] - 2026-06-21

### Added
- **`upgrade_nomad`** — 192 nomad buildings across 24 families added via the new `upgrade_nomad` decision, each gated to its vanilla potential so saves only carry applicable buildings. Completes the upgrade_X family (castle / temple / city / tribal / nomad).
- **`convert_nomad`** — converts any non-nomad realm-owned holding to nomad type (Horse Lords required; not on the realm capital). Strips source-type buildings first to keep saves clean.

### Changed
- README updated for `upgrade_nomad` + `convert_nomad`.

## [0.9.2] - 2026-06-20

### Added
- **Tribal culture-aware buildings in `upgrade_tribal`** — 132 vanilla cultural buildings across 33 culture ladders added via a new gated culture helper + paired presence trigger. Each gated to its vanilla potential so saves only carry applicable buildings.
- **Great Pillars in `upgrade_tribal`** — 10 religion-keyed pillar buildings (Norse / Tengri / Slavic / Baltic / Finnish / West African / Aztec / Bon / Zun / Hellenic) added when the province has the matching `flag_great_pillar_X` set by the HF Establish Pillar decision.
- **SCMPD.16 debug event** — sets a province's culture to nahua (CleanSlate) or nahuatl (vanilla); used to test the stack-aware Aztec tribal helper.

### Changed
- README — Settlement cheats section expanded to describe the conditional-building scope; Holy Fury entry adds `upgrade_tribal` + Great Pillars.

## [0.9.1] - 2026-06-20

### Added
- **Conditional buildings in `upgrade_X`** — 41 vanilla buildings (HF-bloodline / Hellenic / Merchant Republic / terrain / government) added to `upgrade_castle` / `upgrade_temple` / `upgrade_city` / `upgrade_tribal` via new gated helpers + paired presence triggers. Each gated to its vanilla potential.
- **Additional castle culture-ladder coverage** — 8 more culture ladders added to `upgrade_castle` (Coptic, Arberian, Jurchen, Han Chinese, Roman, Sardinian, Tibetan, and Animal). Each matches its vanilla building potential; the Animal ladder fires only on CleanSlate (those cultures don't exist in vanilla).
- **14 SCMPD debug events** (`SCMPD.2`-`SCMPD.15`) in the Debug sub-mod for v0.9.1 testing: HF-bloodline grants, Hellenic temple dedications, `tomb_of_a_saint` modifier, and province-culture overrides.

### Changed
- README updated for the new conditional adds and SCMPD debug events.
- Aztec block in `add_castle_culture_buildings_effect` extracted into CleanSlate-aware helpers, mirroring the existing `remove_aztec_castle_buildings_effect` pattern.

### Fixed
- **CleanSlate culture compatibility** — `add_castle_culture_buildings_effect` and its trigger now handle both vanilla and CleanSlate culture names via new compat triggers in `scmp_culture_compat_triggers.txt`. 6 culture branches were silently failing under CleanSlate due to vanilla-only culture names. The byzantine branch now also correctly excludes Coptic and Arberian, which have dedicated buildings.

## [0.9.0] - 2026-06-20

### Changed
- **Helper file reorganization** — `scmp_holding_effects.txt` and `scmp_holding_triggers.txt` split by holding type. New files: `scmp_castle_effects.txt`, `scmp_temple_effects.txt`, `scmp_city_effects.txt`, `scmp_tribal_effects.txt`, `scmp_nomad_effects.txt`, `scmp_castle_triggers.txt`. Helper bodies byte-identical; no behavioral change.

## [0.8.7] - 2026-06-20

### Changed
- **Style guide conformance audit** — mechanical normalizations across 21 files:
  - §2.3 Empty lines — 1521 redundant blanks removed across all 3 sub-rules (no 2+ consecutive blanks; no blank right after `{`; no blank right before `}`). Largest contributor: 1243 blanks in `cheats_menu_intrigue_traits.txt`.
  - §4.1 Explicit numerical comparisons — 11 `age = N` → `age >= N` in `cheats_menu.txt`.
  - §7.3 No `;` inside CSV descriptions — 2 truncation bugs fixed in `cheats_menu_intrigue_government.csv`.
  - §2.5 Banner format — 2 files restored to canonical 3-border structure.
  - §2.6 Section header style — 4 outlier headers normalized to SCMP's `## --- TEXT --- ##` style.

## [0.8.6] - 2026-06-20

### Added
- **Set Succession: Princely Elective** (`succ_hre_elective`).
- **Set Succession: Byzantine Elective** (`succ_byzantine_elective`).

### Changed
- README — Inheritance Laws Succession list adds the two new laws; Optional DLC clarifies base-game status of both (new Legacy of Rome entry; Holy Fury entry updated).

## [0.8.5] - 2026-06-19

### Changed
- **`tier` → `real_tier` modernization** — 54 character/title-scope tier checks across cheat-menu decisions and law triggers now use `higher_real_tier_than` / `real_tier = X` instead of `higher_tier_than` / `tier = X`. Behavior is identical for non-viceroy rulers; `real_tier` correctly looks past viceroyalty in the edge cases where the two diverge.

## [0.8.4] - 2026-06-19

### Added
- **Council Laws sub-menu** (`show_council_laws` / `hide_council_laws`) — 6th top-level cheat sub-menu (between Obligation Laws and Spawn). 8 council voting power families, each set via state-named pair matching vanilla's Council Law UI:
  - **Council Power** — Set Abolish / Set Empower. Conclave; non-baron.
  - **War Declaration** — Set Ruler / Set Council. Conclave; non-baron.
  - **Grant Titles** — Set Ruler / Set Council. Conclave; non-baron.
  - **Revoke Titles** — Set Ruler / Set Council. Conclave; non-baron.
  - **Imprisonment** — Set Ruler / Set Council. Conclave; non-baron.
  - **Banishment** — Set Ruler / Set Council. Conclave; non-baron.
  - **Execution** — Set Ruler / Set Council. Conclave; non-baron.
  - **Council Authority** — Set Limited / Set Full. Conclave; feudal-family king+, not holy order.

  Tribal_organization gates mirror vanilla; cascade prerequisites in `allow` are dropped per cheat-permissive convention.

### Changed
- README "What it does" — new Council Laws subsection.
- README "Optional DLC" — Conclave entry updated.

## [0.8.3] - 2026-06-19

### Added
- **Obligation Laws sub-menu** (`show_obligation_laws` / `hide_obligation_laws`) — 5th top-level cheat sub-menu (between Realm Laws and Spawn). 5 vassal-contract families, each cycled via Shift Toward Tax / Shift Toward Levy. Each family is a 9-state slider from Heavily Tax Focused to Heavily Levy Focused; one step per click; hides at boundaries.
  - **Noble Obligations** — castle-tier contract (non-Muslim); non-baron OR patrician.
  - **Iqta Obligations** — castle-tier contract (Muslim); non-baron OR patrician.
  - **Burgher Obligations** — city-tier contract; non-baron OR patrician.
  - **Church Obligations** — temple-tier contract (non-Muslim); non-baron OR patrician.
  - **Tribal Obligations** — tribal-tier contract; non-baron OR patrician.
- **Stack-aware per-decision visibility** — the feudal / iqta split tracks the active stack (religion group on vanilla, government type on CleanSlate). Church Obligations admits muslim rulers on CleanSlate stack to match CleanSlate's Laws panel.

### Changed
- README "What it does" — new Obligation Laws subsection.
- README "Optional DLC" — Conclave entry updated.

## [0.8.2] - 2026-06-19

### Added
- **Realm Laws sub-menu** (`show_realm_laws` / `hide_realm_laws`) — 4th top-level cheat sub-menu (between Inheritance Laws and Spawn). 10 realm-law families:
  - **Crown Authority** cycle: Min, Low, Medium, High, Max. Conclave OFF; independent.
  - **Investiture**: Free, Papal. Catholic / Fraticelli; not religious head; independent.
  - **Controlled Realm Inheritance**: Free, Illegal. Conclave; non-republic, non-order; independent.
  - **Vassal War Declaration**: Allowed, External, Illegal — stepwise via External. Conclave; non-republic, non-theocracy, non-order; independent.
  - **Centralization** cycle: Min, Low, Medium, High, Max. Any duke+ non-nomadic ruler (vassals included).
  - **Tribal Organization** cycle: Min, Low, Medium, High, Max. Any tribal ruler.
  - **Viceroyalty**: None, Kingdoms, Duchies. Charlemagne; independent feudal-family emperor.
  - **Status of Women** cycle: Tradition, Marginal, Significant, Notable, Full. Conclave; non-order; religion-feature- and gender-game-rule-aware.
  - **Revoke Title**: None, Allowed, Religious — stepwise via Allowed. Conclave; non-nomadic, non-confucian-bureaucracy. Set Religious additionally hides for cosmopolitan religions and Chinese Imperial.
  - **Administration**: Feudal, Late, Imperial. With Conclave: feudal-family govs. Without Conclave: independent feudal-family emperors only (binary Feudal / Imperial).
- **Stack-aware per-decision visibility** — Status of Women and Set Revoke Title: Religious match CleanSlate's Laws panel when CleanSlate is active.

### Changed
- README "What it does" — new Realm Laws subsection.
- README "Optional DLC" — new Charlemagne entry; Conclave entry extended.

### Fixed
- Em-dash → en-dash sweep across 5 files (`scmp_government_compat_triggers.txt`, `cheats_menu_intrigue_spawn.txt`, `disown_them.txt`, `cheats_religion_modifiers.txt`, `scmp_debug_events.txt`).

## [0.8.1] - 2026-06-17

### Added
- **Inheritance Laws sub-menu** (`show_inheritance_laws` / `hide_inheritance_laws`) — new top-level cheat sub-menu, positioned between Government and Spawn in the master-toggle order. The show toggle hides for governments where no law decision applies (Republic / Theocracy / Roman Imperial).
- **Succession law decisions** (12, alphabetical by display label): Eldership / Elective Gavelkind / Elective Monarchy / Gavelkind / Nomadic / Open / Open Elective / Patrician Elective / Primogeniture / Seniority / Tanistry / Ultimogeniture. Per-decision gates are minimal — engine accepts `add_law` on any master-toggle-eligible gov; DLC gates kept only where the law genuinely requires DLC.
- **Gender succession law decisions** (5 base): `set_agnatic_succession` / `set_cognatic_succession` / `set_true_cognatic_succession` / `set_enatic_succession` / `set_enatic_cognatic_succession` — gated to govs where vanilla's Inheritance UI displays gender succession (feudal / tribal / nomadic / monastic_feudal / chinese_imperial).
- **Gender (Hidden) variants** (5, mirroring the base) — `_hidden` suffix in the decision IDs, "(Hidden)" in the button title. Surface on Iqta / Holy Order / Merchant Republic where vanilla's Inheritance UI hides the gender row; conditional `custom_tooltip` renders a gov-specific message explaining the engine still applies the law.
- **CleanSlate compat helper** — `has_scmp_inheritance_law_eligible_government_trigger` gates the `show_inheritance_laws` master toggle to the 8 govs SCMP has tested (feudal / tribal / nomadic / iqta / monastic_feudal / chinese_imperial / order / merchant_republic).

### Changed
- **README "What it does"** — new "Inheritance Laws" subsection after Government.
- **README "Optional DLC"** — Holy Fury entry extended (`set_succ_eldership` requires HF); Horse Lords entry extended (`set_succ_nomad_succession` requires HL); new The Republic entry (`set_succ_patrician_elective` requires it).

## [0.8.0] - 2026-06-16

### Added
- **Government sub-menu** (`show_government` / `hide_government`) — new top-level cheat sub-menu, 4th master toggle in order Cheats → Government → Spawn → Traits.
- **Government conversions** — `set_feudal` / `set_iqta` / `set_tribal` / `set_nomadic`, each opt-in gated to source governments where the engine accepts the conversion. Plus `set_feudal_nomad` / `set_iqta_nomad` / `set_tribal_nomad` for the destructive horde-settling path from Nomad source (title carries the "(Destroy Horde)" suffix).
- **CleanSlate compat helpers** — `is_iqta_government_trigger`, `is_monastic_feudal_government_trigger`, and `set_iqta_government_effect` handle the CleanSlate gov-type renames (`muslim_government` → `muslim_feudal_government`, `theocratic_feudal_government` → `monastic_feudal_government`).

### Changed
- **`set_feudal`** and **`become_independent`** relocated from `cheats_menu_intrigue.txt` to the new Government sub-menu.
- **README "What it does"** — new "Government" subsection at the end of the cheat categories; "Realm-wide cheats" trimmed to drop the relocated `set_feudal` / `become_independent` mentions.
- **README "Optional DLC"** — Horse Lords entry extended (Destroy-Horde variants); Jade Dragon entry trimmed.

## [0.7.0] - 2026-06-15

### Added
- **Mod-detection global flag** `scmp_active` set at `on_startup`, parallel to Elite Recruitment's `elite_recruitment_active` and the `cleanslate_active` flag this mod reads for trait-name compatibility. New file `common/on_actions/scmp_on_startup.txt`.
- **Persistent `scmp_spawned_<role>` flag** on every spawn-template character. 11 flag names across 25 templates — `scmp_spawned_child` (6 child templates), `scmp_spawned_sibling` (10 sibling templates), and one each for wife / vassal / marshal / spymaster / steward / chancellor / priest / commander / physician. Survives saves; not cleared by the existing finalize hook. Enables future bulk-cleanup decisions, bloodline-grant scoping, and inter-mod identification.

### Changed
- **`has_dlc = "Way of Life"`** replaces dev codename `"Zeus"` on the Get Favor and Clear Your Focus DLC gates.
- **`set_father` / `set_mother` clear value standardized to `0`** (matches vanilla `00_scripted_effects.txt` convention). Two sites in `cheats_menu.txt` previously used the alternate `none` form; both parse identically.
- **`cheat_trait_cleaner` description loc clarified** — lists the 6 SCMP cheat traits it strips and notes dynasty preservation.
- **README** — new "Mod detection" subsection under "For modders" documenting `scmp_active` and the per-character `scmp_spawned_<role>` flags.

### Fixed
- **`cheat_trait_cleaner` now preserves the player's dynasty** — the limit was `ai = yes` only, so AI dynasty members (heirs etc.) were being stripped of cheat traits. Now gated on `NOT = { dynasty = ROOT }`, matching the comment's original intent.

## [0.6.15] - 2026-06-15

### Added
- **Kowtow tier toggles** folded into the renamed Chinese Imperial section — 3 new add/remove pairs (`kow_tow_completed_tier_1` / `_tier_2` / `_tier_3`, displayed as "Kowtow Complete (Tier I / II / III)"). Ungated per berserker convention (no cross-religion analogue).
- **New cluster helper** `clear_kowtow_traits_effect` (3-way mutex) — vanilla declares no opposites between the kowtow tiers, but SCMP tightens to strict mutex matching the raiding / bloodthirsty_gods convention.

### Changed
- **Section renamed** "Chinese Commander" → "Chinese Imperial". Section flag `show_chinese_commander` preserved across the rename for save-compat; only the display label and section divider comment changed. Two subsection dividers (`## --- Chinese Commander --- ##` and `## --- Kowtow --- ##`) added inside.
- **README** — trait count 271 → 274; "chinese commander" entry in the category list updated to "chinese imperial"; Jade Dragon DLC entry updated to list the Kowtow toggles.

## [0.6.14] - 2026-06-15

### Added
- **Dharmic Identity section** (10 add/remove pairs) between Muslim Status and Birth Markers — three subsections:
  - **Caste** (3-way mutex via new `clear_caste_traits_effect`, `religion_group = indian_group` gate): Brahmin, Kshatriya, Vaishya. Vanilla data confirms castes apply to all 3 Dharmic religions (Hindu, Buddhist, Jain), not just Hindu.
  - **Hindu Branches** (4-way mutex via new `clear_hindu_branch_traits_effect`, `religion = hindu` gate): Shaivist, Shaktist, Smartist, Vaishnavist.
  - **Buddhist Branches** (3-way mutex via new `clear_buddhist_branch_traits_effect`, `religion = buddhist` gate): Mahayana Buddhist, Theravada Buddhist, Vajrayana Buddhist. Vajrayana was missing from the trait-reference doc — added during the audit.
- **Three new cluster helpers** in `scmp_mutex_effects.txt` for the mutex groupings.
- **2 new GFX sprite entries** (`GFX_show_dharmic_identity`, `GFX_hide_dharmic_identity`) on `decision_icon_cheats.dds`.

### Changed
- **Section show toggle gated** on `religion_group = indian_group`; each `add_X` additionally carries its own per-subsection religion gate (mirrors v0.6.10 Childhood / v0.6.13 Christian + Muslim Status per-decision pattern).
- **README Optional DLC section** — catch-up pass covering v0.6.10–v0.6.14 content. Updated Conclave / Holy Fury / Rajas of India / Reaper's Due entries; new Sunset Invasion entry.
- **README** — trait count 261 → 271; "dharmic identity" added to the category list between "muslim status" and "birth markers".

## [0.6.13] - 2026-06-15

### Added
- **Christian Status section** (9 add/remove pairs) between Ordained Clergy and Birth Markers — three subsections: Coronation (4-way mutex, ordered Most-to-Least Holy), Baptism (4-way mutex including the Orthodox `baptized_by_patriarch` the trait-reference doc missed), Other (beatified).
- **Muslim Status section** (6 add/remove pairs) — ashari/mutazilite (theological schools 2-way), mirza/sayyid (lineage 2-way), hafiz, decadent. Internal order groups mutex pairs alphabetically by first member.
- **Two new cluster helpers** in `scmp_mutex_effects.txt`: `clear_coronation_traits_effect` + `clear_baptism_traits_effect` (4-way each).
- **`add_decadent` mutex wrap** — strips zealous if present, completing the bidirectional pair started in v0.6.9's `add_zealous` (which strips decadent).
- **4 new GFX sprite entries** for the show/hide toggles, pointing to `decision_icon_cheats.dds` placeholder.

### Changed
- **Per-decision religion gates** — section show toggles gated on `religion_group = christian` / `religion_group = muslim`; each `add_X` inside additionally carries its own religion gate (mirrors v0.6.10 Childhood's `is_adult` per-decision pattern), so toggles disappear immediately if the char converts away from the section's religion while the section flag is set.
- **README** — trait count 246 → 261; "christian status" and "muslim status" added to the category list between "ordained clergy" and "birth markers".

## [0.6.12] - 2026-06-15

### Added
- **Ordained Clergy section** between Religious Markers & Doctrine and Birth Markers — 8 add/remove pairs for ordained-monk/nun traits across 4 religions: Christian (monk, nun), Buddhist (bhikkhu, bhikkhuni), Hindu (sanyasi, sanyasini), Jain (muni, aryika). Religion + sex gated on `add_X`; remove ungated for cleanup (HWR convention).
- **`has_ordained_clergy_religion_trigger`** in new `scmp_section_triggers.txt` — gates section show toggle to the 4 religions that have ordained-clergy traits. Hide stays flag-keyed so chars who converted away can still clean up.
- **2 new GFX sprite entries** (`GFX_show_ordained_clergy`, `GFX_hide_ordained_clergy`) pointing to the existing `decision_icon_cheats.dds` placeholder.

### Changed
- **Carved out** `common/scripted_triggers/scmp_section_triggers.txt` for religion-set section-gate triggers. Moved 3 triggers out of `scmp_trait_compat_triggers.txt` (which now holds purely CleanSlate trait/religion rename compat): `has_warrior_lodge_religion_trigger`, `has_holy_war_religion_trigger`, `has_ordained_clergy_religion_trigger`. File-level reorganization; no runtime change — scripted_triggers are global once loaded.
- **README** — trait count 238 → 246; "ordained clergy" inserted into the category list between "religious markers & doctrine" and "birth markers".

## [0.6.11] - 2026-06-15

### Added
- **Religious Markers & Doctrine expansion** — section renamed from "Religious Markers", divided into 5 subsections covering 22 new add/remove pairs:
  - **Pilgrimage Rewards** (3) — `pilgrim` / `hajjaj` / `indian_pilgrim`, per-religion gated (HWR convention)
  - **Eschatological** (existing 3) — subsection comment added; content unchanged
  - **Sympathy** (6) — vanilla NOT-religion-group gate mirrored on add (no self-sympathy: a Christian can't add `sympathy_christendom`, etc.)
  - **Pagan Doctrines** (7) — 4 `pagan_branch_X` + 3 `bloodthirsty_gods_X`, ungated per the berserker convention (no cross-religion analogue), each cluster routes through a new helper
  - **Religious Stigma** (7) — 6 new `bad_priest_X` per-religion gated; `bad_priest_aztec` routes through the existing `is_aztec_religion_trigger`; existing `excommunicated` migrated from Misc
- **Two new cluster helpers** in `scmp_mutex_effects.txt`: `clear_bloodthirsty_gods_traits_effect` (3-way) and `clear_pagan_branch_traits_effect` (4-way).

### Changed
- **Misc section shrinks 7 → 6 entries** — `excommunicated` migrated to the new Religious Stigma subsection. Decision key unchanged (no save-compat impact); only `has_character_flag = show_misc` → `show_religious_markers` flipped in its potential. Section flag `show_religious_markers` preserved across the rename so existing player toggles carry over.
- **README** — trait count 216 → 238; "religious markers" entry updated to "religious markers & doctrine".

## [0.6.10] - 2026-06-14

### Added
- **Childhood section** between Zodiac and Kinslayer — 12 new add/remove pairs for vanilla's childhood trait family (affectionate, brooding, conscientious, curious, fussy, haughty, idolizer, indolent, playful, rowdy, timid, willful). Alphabetical by display name. All base-game, no DLC / religion / sex / culture gates per vanilla.
- **Age-gated visibility** — `show_childhood` section toggle gated on `is_adult = no`, so the section button only appears for under-16 characters. Each `add_X` decision additionally carries `is_adult = no` in its own potential to handle the edge case where the show flag is set on a child who then ages up while the section is open (per-decision gate hides the toggles even with the flag still set; `hide_childhood` stays available to clean up).
- **Engine-mutex wrap** — `rowdy ↔ timid` is the only mutually-declared opposites pair in the childhood family (the other 10 have no opposites). `add_rowdy` / `add_timid` strip the partner via if/limit before adding, matching v0.6.9's bidirectional convention.
- **2 new GFX sprite entries** (`GFX_show_childhood`, `GFX_hide_childhood`) pointing to the existing `decision_icon_cheats.dds` placeholder.

### Changed
- **README** — trait count 204 → 216; "childhood" added to the categories list.

## [0.6.9] - 2026-06-14

### Added
- **Engine-mutex tooltip wraps** across 86 `add_*` decisions — when a trait's vanilla `opposites` (in either direction) includes another trait the character holds, the add decision's tooltip now renders "Lose Y" alongside "Gain X". Mirrors v0.6.8's if/limit pattern for the manual-mutex consort and zodiac pairs.
- **New file** `common/scripted_effects/scmp_mutex_effects.txt` — 5 cluster helpers for the multi-way mutex groupings (intellect / scarred / kinslayer / raiding / holy war rewards). Each cluster's `add_*` decisions invoke its helper before adding the trait.
- **Two strict compat helpers** (in `scmp_trait_compat_triggers.txt` + `scmp_trait_compat.txt`) for sex-agnostic seducer/seductress mutex — needed by `add_celibate` (strips both lifestyle sex-variants) and the cross-sex wraps on `add_seducer` / `add_seductress`. The existing sex-aware compat returns the sex-matched variant; the strict versions check / remove specifically.

### Changed
- **86 `add_*` decisions** rewritten with the engine-mutex wraps. 32 cluster-helper calls + 54 per-decision bare-or-compat wraps. See diff for full coverage.
- **Bidirectional opposites logic** — wraps cover engine mutex in either direction. Example: adding `feeble` now strips `sturdy`, since `sturdy.opposites = { feeble robust }` declares it, even though vanilla `feeble.opposites = { robust }` doesn't declare the reverse.
- **Raiding strict mutex** — `add_viking` now strips `pirate`, tightening vanilla's asymmetric 4-vs-3 declaration to bidirectional 5-way.
- **Holy War Rewards cluster** — `clear_holy_war_rewards_traits_effect` strips all 16 GHW veteran traits across religions. Real engine-mutex per vanilla; tooltip lines only render for whichever GHW trait the character actually holds (typically none / one, given religion gating).
- **README error.log paragraph updated** — count ~63 → ~67 (4 new parse-time refs from the two strict compat helpers' `else` / `trigger_else` branches).

## [0.6.8] - 2026-06-14

### Changed
- **Tooltip cleanup pass** — wrapped 224 unconditional `remove_trait = X` calls in `if = { limit = { trait = X } remove_trait = X }` so tooltips only render the removes that actually fire on the target character. Mechanical refactor; identical behavior, cleaner UX. Affected sites:
  - All 5 bulk-clear helpers in `scmp_health_effects.txt` (61 wraps)
  - `clear_zodiac_traits_effect` in `scmp_zodiac_effects.txt` (12 wraps — fixes v0.6.7 tooltip noise on `add_zodiac_*`)
  - All 16 compat helpers in `scmp_trait_compat.txt` (48 wraps — wrapping removes inside the CleanSlate-routed if/else branches)
  - `remove_defects` decision (11 wraps)
  - `add_child_of_concubine` / `add_child_of_consort` decisions (1 each — the v0.6.7 manual mutex)
  - 5 `set_X_education` cascades — the existing `hidden_tooltip` wrappers unwrapped, each inner remove wrapped in `if/limit` for informative tooltips (90 wraps)
- **The 55 existing `hidden_tooltip` blocks elsewhere stay untouched** — they wrap cross-character iterations (`any_character`, `any_realm_character`, etc.) or finalize-flag cleanups where per-character iteration noise is worse than tooltip silence.
- **Consolidated two long-standing inline-duplication patterns** (flagged in code comments since v0.3.1, never deduped until now):
  - **`clear_education_traits_effect`** — new helper in new file `scmp_education_effects.txt`. The 5 `set_X_education` cascades now call the helper instead of each carrying their own ~20 inline `if/limit` blocks. Cascade effects shrink from ~85 lines to 3. Order also normalized to remove-then-add (matching the consort-pair / zodiac convention).
  - **`clear_birth_defects_effect`** — new helper added to `scmp_health_effects.txt`. `remove_defects`, `self_genes`, and `fix_genes` now all call the helper instead of carrying inline copies of the same 11-trait list. `self_genes` and `fix_genes` also gain filtered tooltips (their inline removes weren't wrapped in v0.6.8's first pass).
  - Duplication-acknowledging comments at `cheats_menu.txt:121-124` and above `remove_defects` removed (the duplication they flagged is now resolved).
- **README error.log paragraph updated** — count bumped 31 → ~63, with explanation for the doubling.

## [0.6.7] - 2026-06-14

### Added
- **Birth Markers section** between Religious Markers and Zodiac — 6 trait pairs covering vanilla's universal birth-marker traits. Pair-grouped order: Bastard / Legitimized Bastard (vanilla `opposites` mutex), Born in the Purple (singleton), Child of Concubine / Child of Consort (sex-coded-by-parent — `add_*` effects include manual mutex via inline `remove_trait` since vanilla declares no `opposites` between them), Twin (singleton). All base-game, no DLC or religion gates. Existing `remove_child_of_concubine` moves from Misc into this section; new `add_child_of_concubine` added for symmetry.
- **Zodiac section** between Birth Markers and Kinslayer — 12 trait pairs covering the Western zodiac signs in astrological calendar order (Aries → Pisces). Ungated per established SCMP convention (v0.6.1 berserker, etc.): single-religion vanilla content with no cross-religion alternative stays ungated in the cheat menu. Strict one-zodiac-at-a-time mutex via new `clear_zodiac_traits_effect` helper invoked by each `add_zodiac_*` effect — vanilla's pair-only `opposites` (Aries↔Libra etc.) isn't strict enough when the cheat menu bypasses natural one-sign-at-birth assignment.
- **New scripted_effects file** `scmp_zodiac_effects.txt` — contains the `clear_zodiac_traits_effect` helper (removes all 12 zodiac traits).

### Changed
- **Misc Traits shrinks from 8 → 7 entries** (lost `remove_child_of_concubine` to Birth Markers).
- **README updated** — trait count 186 → 204; categories list + DLC notes updated for Zodiac (HF) and consort-themed birth markers (Conclave).

## [0.6.6] - 2026-06-14

### Added
- **Cycle Freckles decision** in Health & Congenital — single state-aware cycling button that progresses through the 5 hidden freckle variants in vanilla trait-ID numerical order. Cycle: None → Variant 1 (`freckles`) → Variant 2 (`freckles_2`) → Variant 3 (`freckles_3`) → Variant 4 (`freckles_4`) → Variant 5 (`freckles_5`) → None. Implemented as 6 mutually-exclusive single-decision blocks (`cycle_freckles_none` / `_1` / `_2` / `_3` / `_4` / `_5`), each visible only when the player's current freckle state matches. The button label shows the CURRENT state in parens (e.g., "Cycle Freckles (Variant 2)" means the player has `freckles_2`); clicking advances to the next variant. All 5 underlying traits are vanilla `hidden = yes` cosmetic-only (no stat effect, only the 3D portrait changes). Engine mutex via vanilla `opposites` is unaffected. Lives in a new "Cosmetic / Portrait" conceptual cluster above the existing Cosmetic-Negative cluster (Fat / Malnourished).
- **12 new SCMP localisation entries** in `cheats_menu_intrigue_traits.csv` for the 6 cycle decisions (main + desc).

### Changed
- **README trait count bumped from 181 to 186** — the 5 freckle variants are now individually accessible via the cycle button.

## [0.6.5] - 2026-06-14

### Added
- **11 new add/remove trait-toggle pairs for the genetic birth-defect cluster**, in a new "Negative Genetic / Birth Defects" group within Health & Congenital (placed between cosmetic-negative and negative-health-states clusters). Closes the per-trait gap by the same logic as v0.6.4: every trait already covered by a bulk-clear sweep (here the inline `remove_defects` button at the top of Health & Congenital) gets an individual add/remove toggle. The 11 traits: clubfooted, dwarf, harelip, hunchback, imbecile, inbred, lisp, slow, stutter, ugly, weak. All base-game; 5 have vanilla `opposites` pairings the engine handles automatically (ugly ↔ fair, imbecile ↔ genius, slow ↔ quick, weak ↔ strong, dwarf ↔ giant).
- **22 new SCMP localisation entries** in `cheats_menu_intrigue_traits.csv` for the 11 new decision pairs.

### Changed
- **README trait-pair count updated from "170" to "181"** — actual count of non-bulk add toggles after v0.6.5.

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
