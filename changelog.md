# Changelog

All notable changes to the BakeBridge project will be documented in this file.

## Versioning Policy

The overall release version always matches the Blender Addon version.

* **Blender-only fix** – Blender Addon version bumps, Substance Painter plugin version stays unchanged.
* **Substance Painter change** – Both versions bump together. This is required because Blender's Extension auto-update feature triggers off the Blender Addon version – bumping it ensures users receive the updated Substance Painter plugin files automatically.

---
## [1.0.1] - 2026-07-17

### Fixed
* Resolved all Python API deprecation warnings (`name`, `file_path`, `material`) on Substance Painter 12.1+.
* Improved compatibility layer to dynamically handle property/method differences across SP versions.

### Changed
* Bumped version to v1.0.1 for the Blender addon, Substance plugin, and auto-updater.

### Added
* Verified and tested full compatibility with **Blender 5.2**.

## [1.0.0] - Initial Release

### Versions
* **Blender Addon Version**: `1.0.0`
* **Substance Painter Plugin Version**: `1.0.0`

### Blender Addon
* **Mesh Prep Engine**: Implemented automatic collection matching and suffix normalization (`_low` and `_high`) to prepare meshes for baking.
* **Geometry Processing**: Added support for merging double vertices, recalculating normals, smooth shading, and adding a non-destructive Triangulate modifier.
* **Preset Manager**: Created a system to save, load, and delete custom export and baker quality configurations.
* **Material Overrides**: Added support for configuring target resolutions per material slot in Blender scene settings.
* **Auto-Importer**: Implemented a background file watcher that automatically imports exported PBR texture sets and wires them directly into the Principled BSDF shader node.

### Substance Painter Plugin
* **One-Click Startup**: Enabled automatic project creation, FBX mesh loading, and baker configuration on startup.
* **Bake Modes**: Implemented three modes: **Setup Only** (opens template), **Test Bake** (bakes at 512px with no anti-aliasing for speed), and **Full Quality** (anti-aliased final bake).
* **Custom Toolbar**: Added a custom Qt toolbar button featuring the stylized **BB** logo.
* **Export Dialog**: Built a PySide-based export interface supporting preset selection, format, bit depth, and per-material resolution overrides.
