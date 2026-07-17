# Troubleshooting & FAQ

Because all core code bugs and crashes have been resolved, the only issues you might encounter are related to initial setup steps or external software limitations. Here is how to handle them.

---

## 1. Substance Painter fails to launch Blender after export

### Symptoms:
Clicking the **BB** button in Substance Painter exports your textures successfully, but Blender does not open or reload them.

### Cause:
Substance Painter's plugin does not have the path to your Blender executable saved yet. 

### Solution:
* You must **run the bridge from Blender to Substance Painter at least once** to sync the paths.
* Running `Run BakeBridge` in Blender automatically writes the current `blender_path` to Substance Painter's local settings. Once registered, Substance Painter will know exactly how to open Blender.
* Also, verify that the **"Open Blender if closed"** checkbox is checked in the Substance Painter export dialog.

---

## 2. The "BB" Button does not appear in Substance Painter on first run

### Symptoms:
You ran the bridge from Blender, but Substance Painter opened without the custom toolbar button.

### Cause:
Substance Painter has the plugin installed, but it is not activated in the Python preferences.

### Solution:
* Go to the top menu bar in Substance Painter and select **Python**.
* Locate **`bakebridge_sp`** in the dropdown list.
* Click it to place a checkmark next to it. Once enabled, the custom **BB** button will appear on your toolbar immediately.
* *Note: This is a one-time setup step required only when installing the plugin for the first time. Substance Painter will remember this setting on all future launches.*

---

## 3. Substance Painter is busy or ignores the bridge command

### Symptoms:
Clicking **Run BakeBridge** in Blender launches Substance Painter, but the project does not load or bake.

### Cause:
Substance Painter has a blocking modal dialog open (such as an unsaved project warning, an export menu, or a settings window) which prevents scripts from running.

### Solution:
* Go to your Substance Painter window and close any active warning popups or menus.
* Go back to Blender and click **Run BakeBridge** again.

---

## 4. Grayscale PNG Viewport Glitch (Blender 4.3+)

### Symptoms:
The Blender console shows:
`ERROR Failed to create GPU texture from Blender image`
And your imported textures look extremely metallic, black, or corrupted in the viewport.

### Cause:
This is a bug specific to **Blender 4.3 and above** (it does not occur in Blender 4.2 LTS). Blender's modern Vulkan/Metal-based GPU texture manager (introduced with EEVEE Next) sometimes fails to compile single-channel grayscale PNG files (which Substance Painter exports for Roughness and Metallic maps in PBR mode) when set to `"Non-Color"` spaces.

### Solution:
* In the Blender BakeBridge settings panel, change the **File Format** from **PNG** to **TGA** (Targa) or **EXR** (which is the industry standard for high-quality, high-dynamic-range maps).
* Both TGA and EXR files are written as multi-channel (RGB) files even if they contain grayscale information, which completely bypasses the Blender 4.3+ grayscale PNG bug.
