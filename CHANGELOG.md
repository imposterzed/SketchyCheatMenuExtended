# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.0] - 2026-06-08

### Added
- **Initial baseline fork** of [Sketchy Cheat Menu](https://steamcommunity.com/sharedfiles/filedetails/?id=608738995) by [Sketchy](https://steamcommunity.com/id/sketchy77) (upstream last updated 2019-10-19). Content pulled verbatim from the SteamCMD-archived workshop files.
- **Project setup for git tracking** — separate launcher `.mod` + content folder layout, MIT `LICENSE` with attribution to the original author, `.gitignore`, `.gitattributes` (Windows-1252 working-tree for `.txt`/`.csv`), README, this changelog.
- **Mod files** — launcher `SketchyCheatMenuPlus.mod` + descriptor `SketchyCheatMenuPlus/descriptor.mod`. Renamed to "Sketchy Cheat Menu Plus", replaced the upstream tag list with `{ "Decisions" "Cheats" "QoL" "Compatibility" }`, added `dependencies = { "CleanSlate" }` so CleanSlate's `cleanslate_active` flag is set before this mod loads.
