# 🎨 ComfyUI AI Suite — Release Hub

> **Compiled binaries only.** This repository hosts the official compiled releases of the **ComfyUI AI Suite** — a dashboard + 3 plugins (ComfyUI · Photoshop · After Effects) that share a unified storage layout for archiving and restoring AI generations.

[![License](https://img.shields.io/badge/license-GPL%20v3-blue.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Windows-lightgrey.svg)]()

By [**Surrendr Studio**](https://www.surrendr.art)

---

## 📥 Downloads — Latest release

👉 Go to the **[Releases page](https://github.com/surrendrart-hub/Comfui-AI-suite/releases)** for all the compiled binaries.

| File | Component | Install method |
|---|---|---|
| `AI_Tracker_Setup_v2.X.exe` | **Dashboard** (Windows installer, Inno Setup) | Double-click → wizard |
| `AI_Tracker_v2.X.exe` | **Dashboard** (portable .exe, no installer) | Double-click |
| `ai-tracker-comfyui_v2.X.zip` | **Plugin ComfyUI** | Unzip into `<ComfyUI>/custom_nodes/` |
| `AI_Tracker_Photoshop_v0.X.X.ccx` | **Plugin Photoshop** | Double-click → Adobe UXP Developer Tool |
| `AI_Tracker_AE_v0.X.X.zxp` | **Plugin After Effects** | Open with [Anastasiy's Extension Manager](https://install.anastasiy.com/) |

---

## 🤔 What does the suite do?

When you work with **ComfyUI + Photoshop + After Effects**, you end up with overflowing `output/` folders, scattered `.psd`/`.aep` files, and no idea which source produced which render.

The suite gives you **one project = one clean folder** with everything versioned (workflows + sources + renders) and a dashboard to navigate, search, and restore any past state in one click.

For the **source code, architecture docs, and tutorials**, see the main repository: **[ai-tracker-suite source repo](https://github.com/surrendrart-hub/Surr-MiniTool-Comfui-PipeLine)**.

---

## 🚀 Quick start

1. Download `AI_Tracker_Setup_v2.X.exe` from Releases
2. Double-click → install wizard (you may need to bypass Windows SmartScreen: **More info** → **Run anyway**)
3. Launch from Desktop shortcut
4. Settings → 📁 Storage → choose where your projects will live
5. ➕ Create project → start tracking

For the ComfyUI / Photoshop / After Effects plugin installs, see [INSTALL.md on the source repo](https://github.com/surrendrart-hub/Surr-MiniTool-Comfui-PipeLine/blob/main/INSTALL.md).

---

## 📜 License

[GNU General Public License v3.0](LICENSE)

Copyright © 2026 Surrendr Studio · https://www.surrendr.art

---

## 🔗 Links

- 📦 **Releases** : https://github.com/surrendrart-hub/Comfui-AI-suite/releases
- 💻 **Source code + docs** : https://github.com/surrendrart-hub/Surr-MiniTool-Comfui-PipeLine
- 🌐 **Studio** : https://www.surrendr.art
- 🐛 **Issues / Support** : https://github.com/surrendrart-hub/Surr-MiniTool-Comfui-PipeLine/issues
