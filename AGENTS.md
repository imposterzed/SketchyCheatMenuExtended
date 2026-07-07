# Agent Guide

Quick orientation for AI coding agents (and humans) ramping up on this
codebase. Read this before editing files.

## What this mod is

Crusader Kings II mod: an in-game cheat menu accessible through right-click
character, settlement, and realm decisions. After enabling cheats with the
**Enable Cheats** decision on yourself, every cheat decision becomes
available; turn them off again with **Disable Cheats** when you're done. AI
characters never see these decisions.

The mod ships ~900 decisions across ~20 sub-menus (self cheats, character
cheats, mind control, government changes, inheritance / realm / obligation
/ council laws, trait toggles for ~274 traits, settlement upgrades,
character spawning, etc.). A companion Debug sub-mod
(`SketchyCheatMenuExtendedDebug`) ships `event SCMED.*` console events for
hard-to-reach test paths.

The user-facing summary lives in `README.md`. Version history is in
`CHANGELOG.md`.

## Critical gotchas — read these first

### 1. File encoding: Windows-1252 + CRLF for `.txt` and `.csv`

CK2 reads `.txt` (script) and `.csv` (localization) files as
**Windows-1252 with CRLF line endings**. The repo's `.gitattributes`
checks these files out as Win-1252+CRLF on disk while storing the blobs
as UTF-8 in git for readable diffs.

**Practical rule:** if you edit a file with accented characters and save
it with a UTF-8 editor, the accents corrupt once git reinterprets the
bytes. Use a Win-1252-aware tool (a small Python script with `cp1252`
encoding, or a text editor configured for Windows-1252 + CRLF). After
editing, run `git add --renormalize .` and confirm `git status` is
clean.

Plain-ASCII edits (no accented chars) are unaffected. `.md` files are
plain UTF-8 and need none of this.

### 2. Scripted-effect invocation: `= yes`, never `= {}`

When calling a scripted effect, use:

    some_scripted_effect = yes

NOT:

    some_scripted_effect = { }

The `= { }` form silently doesn't execute and causes confusing debugging.

### 3. `replace_path` conflicts with overhauls

Large overhaul mods (CleanSlate, HIP, AGOT, ...) use `replace_path` in
their `.mod` file to claim shared folders like `common/traits` and
`common/dynasties`. Without a `dependencies` hint in this mod's `.mod`
file, the overhaul silently suppresses our content in those folders.

`SketchyCheatMenuExtended.mod` already declares `dependencies = { "CleanSlate" }`
because SCME is designed for CleanSlate compatibility. If you add
content in folders that other overhauls also replace, add those
overhauls to the dependencies list the same way.

### 4. Section-toggle flag pattern

Every SCME decision except `Enable Cheats` itself gates on
`has_character_flag = cheats_enabled` in its `potential`. That's the
master switch. Sub-menu decisions also gate on a section-specific
`show_<section>` flag (roughly 35 of them, one per sub-menu — grep
`has_character_flag = show_` in `decisions/` for the current list).

New sub-menu decision → both flags required in `potential`:

    potential = {
      ai = no
      has_character_flag = cheats_enabled
      has_character_flag = show_<section>
    }

Missing either flag → decision silently doesn't appear when the player
opens the menu. The `Show X` / `Hide X` toggle decisions set/clear the
section flag; the master `Enable Cheats` / `Disable Cheats` decisions
set/clear `cheats_enabled`.

## Repo layout

```
SketchyCheatMenuExtended.mod                            top-level mod descriptor
SketchyCheatMenuExtended/                               base mod content
  descriptor.mod                                    inner descriptor (mirror)
  sketchycheatmenu.jpg                              mod thumbnail
  decisions/cheats_menu*.txt                        one file per sub-menu
  common/scripted_effects/*.txt                     per-topic effect helpers
  common/scripted_triggers/*.txt                    per-topic gate helpers
  common/dynasties/disown_them.txt                  Outcast dynasty (id 777777)
  common/event_modifiers/cheat_modifiers.txt        triple_levies etc.
  common/traits/*.txt                               custom cheat traits + icons
  gfx/interface/*.dds                               decision icons (28×28)
  gfx/traits/*.dds                                  custom trait icons (24×24)
  interface/*.gfx                                   sprite registrations
  localisation/*.csv                                Win-1252 loc strings
SketchyCheatMenuExtendedDebug.mod                       debug sub-mod descriptor
SketchyCheatMenuExtendedDebug/                          SCMED.* events for testing
SketchyCheatMenuExtendedProper4KUIPatch.mod             hi-res patch descriptor
SketchyCheatMenuExtendedProper4KUIPatch/                50×50 icons + 43×43 traits
docs/                                               README banner, gallery, thumbs
CHANGELOG.md                                        version history (Keep a Changelog)
README.md                                           user-facing docs
```

## Testing

**There are no automated tests** — verification happens in-game only.

As an agent, you can:

- Verify syntactic correctness (brace balance, proper file encoding,
  reference consistency).
- Cross-check references (e.g., a `picture = GFX_X` line in a decision
  must match a `spriteType { name = "GFX_X" ... }` declaration in the
  `.gfx` file; a `text = some_key` in script must match a row in a
  `.csv`).
- Confirm trait IDs you add or remove exist in both vanilla CK2 and
  CleanSlate. Some vanilla trait IDs don't exist under CleanSlate;
  check CleanSlate's `common/traits/` files if in doubt.

You **cannot** verify in-game behavior. After making changes, surface
them to the maintainer for in-game testing, and capture any uncertain
edge cases as explicit questions in your handoff.

For hard-to-reach scenarios (assigning a character to a specific
dynasty, granting an out-of-reach bloodline, applying a specific
province modifier), the Debug sub-mod ships `event SCMED.<N>` events
reachable from the console when both mods are loaded. Enable
`SketchyCheatMenuExtended - Debug` alongside the base mod in the launcher to
make these events available.

## Adding graphics

Graphics ship in two places, matching the dual-mod pattern:

- **Base mod:**
  - Decision icons: `SketchyCheatMenuExtended/gfx/interface/*.dds` at **28×28**.
  - Custom trait icons: `SketchyCheatMenuExtended/gfx/traits/*.dds` at **24×24**.
- **Proper4KUI Patch (optional):**
  - `SketchyCheatMenuExtendedProper4KUIPatch/gfx/interface/*.dds` at **50×50**.
  - `SketchyCheatMenuExtendedProper4KUIPatch/gfx/traits/*.dds` at **43×43**.

**Always ship the base-resolution version.** A graphic that only exists
in the P4KUI Patch is invisible to players without P4KUI installed — the
base mod must work standalone.

**Same filename in both folders.** CK2's mod-stack file resolution picks
the patch's file when both mods are loaded; matching filenames is the
mechanism. No registration of the hi-res version is needed; only the
base-mod sprite is declared in `interface/*.gfx`.

**File format:** uncompressed BGRA DDS (32 bpp) works for all UI
textures. No DXT compression needed.

Register new sprites in the appropriate `interface/*.gfx` file.
Decisions reference the sprite via `picture = GFX_<sprite_name>` in the
decision body.

**Event-modifier icons** are a different case: they index into a single
shared sprite strip (`GFX_modifier_icons`), not per-name sprites. Adding
custom modifier icons requires re-registering the whole strip, which
collides with vanilla / CleanSlate / P4KUI (each ships its own variant
of the strip). Prefer picking a semantically appropriate vanilla frame
instead.

**Dynasty coats of arms** use a 15-color palette + procedural pattern +
optional emblem. A dynasty's `coat_of_arms = { layer = { ... } }` block
selects a texture, frame index, emblem, and three color slots. The
three color slots map, in order, to: pattern-element color, field
color, emblem color. Add `religion = "catholic"` inside the block to
lock the render to a specific heraldic ruleset regardless of the
holder's religion.

## Conventions

- **Commit messages:** subject `vX.Y.Z - <topic>` (~70 chars, no
  trailing period), topic is a noun phrase. Optional short body
  explaining the "why" — present tense, no forward-looking phrases.
- **Versioning:** semver, `0.x` range until the first Steam Workshop
  release. Every commit tagged with `vX.Y.Z` (lightweight tag).
- **CHANGELOG:** [Keep a Changelog](https://keepachangelog.com/) format.
  Add entries under `[X.Y.Z] - YYYY-MM-DD` with sub-sections **Added**,
  **Changed**, **Deprecated**, **Removed**, **Fixed**, **Security** in
  that order (omit empty ones). The CHANGELOG entry ships in the SAME
  commit as the change it describes.
- **Comments in script files:** preserve the maintainer's existing
  comment voice; don't reformat or inject new commentary. Don't narrate
  removals in comments — rationale goes in the commit message and
  CHANGELOG.
- **Script style:** 2-space indent, CRLF endings, one space around `=`,
  one blank line between blocks (never two or more; no blank line
  right after `{` or right before `}`). Use `NOR` for multi-child
  negation — CK2's `NOT = { A B }` means "all false" (NOR), not NAND.
  Use `real_tier` / `higher_real_tier_than` (never plain `tier` — it
  lies under nomad/tribal mechanics).

## Things to avoid

- Editing accented `.csv` / `.txt` files with a UTF-8 editor (see
  Gotcha #1).
- Calling scripted effects with `= { }` (see Gotcha #2).
- Adding decisions without the `cheats_enabled` master gate and their
  section's `show_<section>` gate — the decision won't appear in-game
  (see Gotcha #4).
- Adding new traits without first checking whether the ID exists under
  CleanSlate — some vanilla trait IDs don't. Check
  [ck2.paradoxwikis.com/Traits](https://ck2.paradoxwikis.com/Traits)
  for the vanilla list, then confirm CleanSlate's own trait files if in
  doubt.
- Shipping graphics only in the Proper4KUI Patch — the base mod must
  work standalone.
- Adding custom event-modifier icons — engine-blocked (see *Adding
  graphics*).

## Resources

- **CK2 modding wiki:** https://ck2.paradoxwikis.com/Modding — the
  authoritative reference for CK2 modding syntax (events, decisions,
  triggers, effects, game rules, etc.).
- **Traits reference:** https://ck2.paradoxwikis.com/Traits — every
  trait ID with its modifiers.
- **CleanSlate:** https://github.com/ck2plus/CleanSlate — primary
  reference for CleanSlate-specific trait IDs, event-modifier icon
  reindexing, and replace_path folder targets.
- **Vanilla CK2 game files** — if you have access to a CK2 installation,
  the vanilla script is an invaluable reference (same syntax as the
  mod). Common locations:
  - Steam: `C:\Program Files (x86)\Steam\steamapps\common\Crusader Kings II\`
  - GOG: `C:\Program Files (x86)\GOG Galaxy\Games\Crusader Kings II\`

  Key folders:
  - `decisions/` — vanilla decision patterns
  - `common/scripted_effects/`, `common/scripted_triggers/` — every
    vanilla scripted effect/trigger
  - `common/traits/` — every vanilla trait definition
  - `common/dynasties/` — vanilla dynasty definitions (coat of arms syntax)
