# Quick Start Guide

This guide walks you through your first baking and texturing loop using BakeBridge.

>[!TIP]
> **You only need to select your meshes in the viewport the very first time you run BakeBridge (or when adding new meshes).** Once the `Low Poly` and `High Poly` collections are created, you can change settings or run the bridge without selecting anything – BakeBridge will automatically find your meshes inside the collections!

---

## Step 1: Naming Your Meshes (Auto-Collection)

BakeBridge handles collection organization and naming for you. You only need to name your meshes with the correct suffixes:

1. **Low-Poly Meshes**: Use suffixes like `_l`, `_lp`, `_low`, or `_lowpoly` (e.g., `Sword_l`).
2. **High-Poly Meshes**: Use suffixes like `_h`, `_hp`, `_high`, or `_highpoly` (e.g., `Sword_h`).

*BakeBridge will automatically create the `Low Poly` and `High Poly` collections and normalize the suffixes to `_low` and `_high` for Substance Painter.*

---

## Project Directory & Naming Structure

BakeBridge keeps your project folder completely organized. The name of the **Project Folder** you select in the Blender N-panel (e.g., `D:\Testing\BakeBridge\Throne\`) is inherited as the base asset name for all meshes, project files, and textures.

When you run BakeBridge, it automatically sets up the following folder structure inside your selected project folder:

```text
📁 Selected_Project_Folder/  (e.g. D:\Testing\BakeBridge\Throne\)
│
├── 📁 source/
│   └── 📄 Throne.spp               <-- Substance Painter project file
│
├── 📁 meshes/
│   ├── 📦 Throne_low.fbx           <-- Cleaned low-poly export
│   └── 📦 Throne_high.fbx          <-- Cleaned high-poly export
│
└── 📁 textures/
    ├── 🖼️ T_Throne_BaseColor.png   <-- Exported textures (appends material name if multi-material)
    ├── 🖼️ T_Throne_Normal.png
    ├── 🖼️ T_Throne_ORM.png
    └── 📄 texture_manifest.json   <-- Tells Blender how to wire these maps
```

*This clean folder layout keeps your source files, meshes, and textures completely separated and matches professional game studio pipeline standards.*

---

## Step 2: Configure Settings & Overrides

1. Open the **BakeBridge - SP** tab in the Blender sidebar (N-Panel).
2. Set all the baking settings you want (resolution, format, map packing, normal space). *Note: You do not need to select any meshes to configure these settings, as they are saved per blend file.*
3. **If you want to use Per-Material Resolution Overrides:**
   * **Click the "Run Pre-Process" button first**.
   * Running the pre-process scans your meshes and detects all assigned materials, which populates the override list in the Blender UI so you can configure each one.

---

## Step 3: Run Geometry Pre-Processing

Before exporting, BakeBridge runs a pre-processing engine to prepare your meshes (merging double vertices, recalculating normals, setting smooth shading, and adding a Triangulate modifier).

You can run this in two ways:

* **Way A: Manually**
  1. Click **Run Pre-Process** under the Pre-Process settings box.
  2. Your meshes will be cleaned up and organized immediately, allowing you to inspect them inside Blender before exporting.
* **Way B: Automatically**
  1. Simply click **Run BakeBridge** (below). The addon will automatically run the pre-processing engine for you in the background during the export.

---

## Step 4: Run the Bridge & Bake

1. Set your **Bake Mode** in the panel and click **Run BakeBridge**:
   * **Setup Only**: Opens Substance Painter, creates/opens the project, and configures your baker settings (no automatic bake).
   * **Test Bake**: Runs a quick test bake at **512** resolution (auto-lowered resolution for speed), then restores your settings.
   * **Full Quality**: Runs a high-resolution, anti-aliased bake when you are ready to compile your final look.

### Fixing Mesh Errors:
If you notice a shading error or mesh issue after baking:
1. Simply fix the geometry directly in Blender.
2. Click **Run BakeBridge** again.
3. The addon will export the updated meshes, automatically refresh the open project inside Substance Painter, and run the bake again on the selected mode.

---

## Step 5: Paint & Send Textures Back

Once you are done painting in Substance Painter:

1. Click the **BakeBridge (BB)** logo button on the Substance Painter toolbar.
2. Select your texture format, bit depth, and resolution.
3. Ensure **"Open Blender if closed"** is checked.
4. Click **Export & Send**:
   * The plugin will export the textures in your selected format and write a manifest.
   * If Blender is closed, it will automatically launch Blender, open your `.blend` file, and wire the textures.
   * The background watcher in Blender will import the maps and wire them up to the Principled BSDF node in your Blender scene automatically.

---

Now your textures are live in Blender – that is the full loop!
