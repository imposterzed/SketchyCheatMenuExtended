# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

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
