# 🎨 ComfyUI AI Suite

> **Track, archive, and restore your AI generations across ComfyUI, Photoshop and After Effects — one project, one dashboard, one click.**

[![Latest release](https://img.shields.io/github/v/release/surrendrart-hub/Surr-Comfui-AI-suite?color=FF1493&label=latest)](https://github.com/surrendrart-hub/Surr-Comfui-AI-suite/releases/latest)
[![License](https://img.shields.io/badge/license-GPL%20v3-blue.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Windows-lightgrey.svg)]()
[![Surrendr Studio](https://img.shields.io/badge/by-Surrendr%20Studio-FF1493)](https://www.surrendr.art)

> 📦 **Release-only repository** — this repo hosts the official compiled binaries.
> For source code, architecture docs and tutorials, see the
> **[main source repo](https://github.com/surrendrart-hub/Surr-MiniTool-Comfui-PipeLine)**.

---

## 🤔 Why does this exist?

When you produce with a pipeline mixing **ComfyUI + Photoshop + After Effects**, you quickly end up with:

- Overflowing `ComfyUI/output/` folders
- `.psd` files scattered across your disk
- `.aep` projects you can never find again
- No idea which workflow produced which render
- No clean way to "go back" to a previous state

**ComfyUI AI Suite** solves all that. Each project gets a **single tidy folder** with everything versioned, and a central dashboard to navigate, search, and restore any past state in one click.

```
                          ┌──────────────────────────────────┐
                          │   📊  AI Tracker Dashboard         │
                          │       (Windows .exe — Tkinter)    │
                          └────────────────┬─────────────────┘
                                           │ scan / restore
                                           ▼
                     <storage>/<project>/journal/<date>/<vNN>/
                          ├── workflows/   ← JSON + screenshot
                          ├── inputs/      ← .psd, .aep, source images
                          └── outputs/     ← generated PNG/MP4
                                           ▲
            ┌──────────────────────────────┼─────────────────────────────┐
            │                              │                             │
    ┌───────┴────────┐         ┌───────────┴──────────┐        ┌─────────┴──────────┐
    │ 🎨 ComfyUI     │         │ 🖌 Photoshop         │        │ 🎬 After Effects   │
    │  custom_nodes  │         │  UXP panel + bridge   │        │  CEP panel         │
    └────────────────┘         └──────────────────────┘        └────────────────────┘
```

---

## 📥 Download — v2.0

👉 **[Releases page →](https://github.com/surrendrart-hub/Surr-Comfui-AI-suite/releases)**

| Asset | What it is | How to install |
|---|---|---|
| **`AI_Tracker_Setup_v2.0.exe`** ⭐ | Dashboard Windows installer (Inno Setup) | Double-click → install wizard |
| `AI_Tracker_v2.0.exe` | Dashboard portable (no installer) | Double-click anywhere |
| `ai-tracker-comfyui_v2.0.zip` | ComfyUI plugin (full source) | Unzip into `<ComfyUI>/custom_nodes/` |
| `AI_Tracker_Photoshop_v0.7.9.ccx` | Photoshop UXP plugin | Double-click → Adobe UXP Developer Tool |
| `AI_Tracker_AE_v0.1.0.zxp` | After Effects CEP plugin (signed) | Open with [Anastasiy's Extension Manager](https://install.anastasiy.com/) |

> 💡 You don't have to install everything — pick only the plugins for the apps you actually use.

---

## ✨ Features at a glance

### Dashboard `AI_Tracker.exe`
- 📁 **1 project = 1 clean folder**, custom storage path per project
- 📅 **Date versioning** (`v01`, `v02`, …) continuous across days
- 📤 **Outputs** (top) + 📥 **Inputs / Data** (bottom) auto-split gallery
- 🠝 **One-click restore** : push a saved workflow back to ComfyUI with its inputs
- 💬 Comments per version
- 🎬 Smart drag & drop (images, videos, .blend, .aep, .psd, .hip, .prproj, .ai)
- 🧰 Integrated software launcher (configure once, launch from each project)
- 🏠 HOME button (refreshes + navigates to project home)
- 🎨 Banner per project (40% opacity background in the journal panel)

### ComfyUI plugin
- **`💾 Save`** in top-bar → screenshot canvas + workflow JSON + inputs auto-snapshot
- **`+`** → create a new vNN version at next save
- **`📂 Load…`** → modal lists all captures, click to restore
- **Project/Version dropdowns** synced with the dashboard
- 2 custom nodes : **`Surr_AT_SaveImage`** + **`Surr_AT_SaveVideo`** with on-demand `📤 Push to project`
- Screenshot paired with the workflow JSON (`workflows/<stem>.png + .json`)

### Photoshop plugin (UXP, PS 2025+)
- Panel **AI Tracker** with `Save PNG` + `Save PSD`
- Project/Version dropdowns synced via Python bridge (port 8765)
- Sidecar `.meta.json` per save (dimensions, color_mode, layer_count, etc.)

### After Effects plugin (CEP, AE 2026+)
- Panel **AI Tracker** with `Save AEP`
- Preserves the project's internal path (`save+copy` pattern)
- Sidecar `.meta.json` with composition info (width/height/fps/duration)

---

## 🚀 Quick start (~ 5 min)

### 1. Install the dashboard
1. Download `AI_Tracker_Setup_v2.0.exe` from [Releases](https://github.com/surrendrart-hub/Surr-Comfui-AI-suite/releases)
2. Windows SmartScreen may complain (binary not Microsoft-signed) → **More info** → **Run anyway**
3. Follow the wizard (default options are fine), check the desktop shortcut
4. Launch → **⚙ Settings** → **📁 Storage** → pick a folder where your projects will live (e.g. `D:\AI_Tracker_Storage\`)

### 2. Create your first project
1. **⚙ Settings → ➕ Create project**
2. Title : `My first test` · category : `Other` · **Create**
3. Your project appears in the left panel

### 3. (Optional) Install the ComfyUI plugin
```powershell
# In your ComfyUI installation
cd C:\path\to\ComfyUI\custom_nodes
# Unzip ai-tracker-comfyui_v2.0.zip here (one subfolder `ai-tracker-comfyui` should appear)
```
Restart ComfyUI. You should see in the console:
```
[AI Tracker - ComfyUI] v0.1.0 loaded
[AI Tracker] ✅ v0.1.0 ready (1 project(s) discovered)
```
Reload your ComfyUI browser tab. The **AI Tracker** top-bar appears.

### 4. First save
- In ComfyUI, pick your project + version in the top-bar dropdowns
- Build a workflow → **Queue Prompt** → wait for the result
- Click **💾 Save** → workflow + screenshot + inputs are archived
- Go to the dashboard → your project → **v01** appears in the journal panel

That's it. Every save, every render, every source file lives in one tidy place from now on.

---

## 🔗 Shared conventions across plugins

All 4 components share the same storage layout and state file:

### Storage layout
```
<storage>/<slug>/journal/<YYYY-MM-DD>/<vNN>/
  ├── workflows/<stem>.{json,png}         ← ComfyUI workflow + canvas screenshot
  ├── inputs/<name>.{psd,aep,png,jpg,mp4} ← Sources (PS/AE/LoadImage refs)
  └── outputs/<name>.{png,mp4}            ← Generated renders
```

### Shared state file `current_project.json`
```json
{
  "project": "<slug>",
  "version": "v07",
  "updated_at": "ISO",
  "updated_by": "dashboard" | "ai-tracker-comfyui" | "after-effects" | "photoshop"
}
```

This is how the 4 components stay in sync — switch project in ComfyUI, the dashboard and the PS/AE panels follow.

---

## 🔧 Troubleshooting

| Symptom | Fix |
|---|---|
| Windows blocks the installer | More info → Run anyway (binary isn't Microsoft-signed) |
| ComfyUI plugin doesn't appear | Check it's in `custom_nodes/ai-tracker-comfyui/` (not nested deeper); check ComfyUI boot logs; restart cleanly |
| Dashboard doesn't see my project | **⚙ Settings → 📁 Storage** → check the path matches where the plugin writes |
| PS plugin can't reach the dashboard | Make sure the Python bridge is running: `python bridge.py` (port 8765) |
| AE plugin doesn't load | Enable PlayerDebugMode: `reg add "HKCU\Software\Adobe\CSXS.12" /v PlayerDebugMode /t REG_SZ /d 1 /f` |
| I see the same gallery for all projects | Click **🔄 Refresh** in the left panel after editing storage paths |

---

## 📜 License

[GNU General Public License v3.0](LICENSE) (GPL-3.0)

Free software — use, modify, redistribute under the terms of GPL v3. Any derivative work must remain under GPL v3 (copyleft).

Copyright © 2026 Surrendr Studio · https://www.surrendr.art

---

## 🙋 Support

- 🐛 Bug? → [Open an issue on the source repo](https://github.com/surrendrart-hub/Surr-MiniTool-Comfui-PipeLine/issues)
- 💬 Question or feature request? → [Discussions on the source repo](https://github.com/surrendrart-hub/Surr-MiniTool-Comfui-PipeLine/discussions)
- 🌐 Studio website → [surrendr.art](https://www.surrendr.art)

---

## 🔗 Useful links

| Link | What |
|---|---|
| [Releases](https://github.com/surrendrart-hub/Surr-Comfui-AI-suite/releases) | All compiled binaries (this repo) |
| [Source code + docs](https://github.com/surrendrart-hub/Surr-MiniTool-Comfui-PipeLine) | Dashboard + plugins source, INSTALL.md, TUTORIAL.md, CHANGELOG.md |
| [Anastasiy's Extension Manager](https://install.anastasiy.com/) | Free .zxp installer for the AE plugin |
| [Adobe UXP Developer Tool](https://developer.adobe.com/photoshop/uxp/devtool/) | For installing the .ccx Photoshop plugin |
| [ComfyUI](https://github.com/comfyanonymous/ComfyUI) | The host for the ComfyUI plugin |

---

> **ComfyUI AI Suite** · by [Surrendr Studio](https://www.surrendr.art) · [GPL-3.0](LICENSE) · Windows-only · Released 2026
