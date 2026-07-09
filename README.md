<p align="center">
  <img src="Assets/PSVita_Screen.png" alt="MOTHER: Encore - PS Vita Port">
</p>

# MOTHER: Encore (ACT 2) — PS Vita Port

A native PlayStation Vita port of **MOTHER: Encore**, the free fan-made reimagining of MOTHER 1, adapted from its original **Godot Engine** PC release. This repository contains the source patches, control rewrites, and tooling created to make the game run natively on the PS Vita hardware.

> Based on **MOTHER: Encore ACT 2 — v0.4.0.3 (Windows)**.
> Original game by **Pkdotts** and team: **https://mother-encore.itch.io/mother-encore**

---

## ⚠️ Disclaimer

**MOTHER: Encore is a free, unofficial fan reimagining of MOTHER 1 and is not affiliated with Nintendo or Shigesato Itoi.** This game offers a uniquely different experience from the original and should not be seen as a replacement for it. In other words, if you are playing MOTHER: Encore, you are not playing MOTHER 1.

We recommend supporting the MOTHER series by playing the games via official releases or by purchasing official merchandise.

**This port is also unofficial and non-commercial.** MOTHER: Encore is redistributed here under its **MIT license**, with full credit to the original authors. Please support the developers via the **[official page](https://mother-encore.itch.io/mother-encore)**.

---

## About the Game

Welcome back, to the World of MOTHER!

Back in the year 1988, in a small rural town in America, a boy named Ninten woke up to the sight of many strange phenomena. Objects coming to life, animals going crazy, people vanishing without a trace, and a great shadowy cloud atop Mt. Itoi... These are just a few of the many abnormal things happening all over America. Equipped with PSI powers, and following in his Great Grandfather's footsteps, will Ninten be able to uncover these many mysteries?

Collect Eight Melodies, explore dangerous dungeons, meet new and old friends, and enjoy the ride! This performance is gonna leave you wanting for an Encore in this celebration of the game that started it all.

Made entirely from the ground up using the Godot Engine, Encore aims to adapt the original game into a completely fresh and new experience for modern audiences. The game currently contains 2 Acts and is planned to release 8 Acts in total, each a content update adding new areas for a seamless experience once finished.

**Directed by Pkdotts.**

---

## Installation

1. Head to the **[Releases](../../releases)** tab.
2. Download the latest `MotherEncore-Vita-x.x.x.vpk` and `game_data.zip` (the Vita-ready game files).
3. Install `MotherEncore-Vita-x.x.x.vpk` on your PS Vita using VitaShell or **[FMVita](https://github.com/WolffsRoom/FMVita)** (my personalized VitaShell).
4. Extract `game_data.zip`, then connect your Vita via FTP or USB and copy the `game_data` folder into your Vita app folder at:
   `ux0:app/MOTHER001/`
   *(The file must end up exactly at `ux0:app/MOTHER001/game_data/game.pck`.)*
5. Have fun!

> This build is redistributed under MOTHER: Encore's **MIT license**, with full credit to the original authors. If you enjoy the game, please support the developers at the **[official page](https://mother-encore.itch.io/mother-encore)**.

> **UPDATE NOTICE:** If you wish to update the game, please **update the game files as well** (`game.pck`), not just the VPK.
> _Save files are not lost when uninstalling or updating (they are stored under `ux0:data/godot/app_userdata/MOTHER Encore/...`)._

---

## Controls (Controles)

<!-- TODO: add Assets/controlsvita.png control diagram -->

<div align="center">

| Control | Action | Control | Action |
|:---:|:---|:---:|:---|
| **D-Pad / Left Stick** | Move | ✕ **Cross** | Confirm / Interact |
| **△ Triangle / START** | Menu / Select | ○ **Circle** | Cancel / Back |
| **□ Square** | Crouch / Telepathy (hold) | **SELECT** | Open Map |
| **L1** | Previous party member | **R1** | Next party member |
| **Left Touch (screen)** | **L2** — Scope / markers | **Right Touch (screen)** | **R2** — Crouch / Telepathy |

</div>

> The PS Vita has no **L2/R2** (nor L3/R3) buttons. They are emulated by touching the **left** and **right** halves of the front touchscreen.

---

## Screenshots

<p align="center">
  <img src="Assets/prints/2026-07-09-000536-283215.png" width="48%">
  <img src="Assets/prints/2026-07-09-000546-276455.png" width="48%">
  <img src="Assets/prints/2026-07-09-000610-651034.png" width="48%">
</p>

---

## Main Tools Used

This port was made possible thanks to the following tools:

### **GDRE Tools**
- **Purpose:** Extract the original PCK from the free Windows release so the project could be reconstructed and opened in the Godot Engine.
- **Source:** [https://github.com/GDRETools/gdsdecomp](https://github.com/GDRETools/gdsdecomp)

### **Godot PSVita**
- **Purpose:** Compile the final `.vpk` for the Vita and adapt the essential game/engine files for the console.
- **Source:** [https://github.com/SonicMastr/godot-vita](https://github.com/SonicMastr/godot-vita)

### **vita-parse-core**
- **Purpose:** Symbolicate and analyze the Vita crash dumps (`.psp2dmp`) to trace the boot crash down to an out-of-memory condition.
- **Source:** [https://github.com/xyzz/vita-parse-core](https://github.com/xyzz/vita-parse-core)

---

## Improvements & Adaptations for the PS Vita

Since this port is based on the Godot version, several parts of the game were reworked to make it feel native on the console and fit within the Vita's ~365 MB memory budget:

**Memory & loading (boot crash fix):**
- **Lazy UI loading:** The UI manager was preloading ~11 heavy scenes (the entire battle system, shops, storage, ATM, save/keyboard/ocarina screens, dialogue boxes) at boot. These now load on demand, so their texture trees no longer flood memory before the first frame.
- **Lazy map loading:** The Map screen was instancing **every** map in the game at startup. Maps now load individually, only when opened.
- **Result:** Boot RAM dropped from **365 / 365 MB (out-of-memory crash)** to around **181 / 365 MB**, letting the game boot to the title screen and beyond.

**Data packaging:**
- The game is fully data-driven (900+ `.yaml`/`.ecs`/`.dat` files). These raw data files were explicitly included in the Vita export so the runtime stops looping on missing data.

**Engine compatibility (Godot 3.6 → 3.5 Vita fork):**
- Replaced a Godot 3.6-only API call (`is_node_ready`) with its 3.5 equivalent and restored a dropped `class_name` registration from the decompile.

**Controls and input:**
- **Gamepad-first prompts:** On-screen prompts now show the real PS Vita buttons instead of PC keyboard keys by default.
- **Touch L2/R2:** The Vita's missing L2/R2 buttons are mapped to the left/right halves of the touchscreen.
- **PC hints removed:** The title screen's "Fullscreen (F11) / Window Size (F5)" hints are hidden on console.

**Display:**
- Adapted the game to the Vita's **960×544** screen. <!-- TODO: finalize once resolution/GPU tuning is locked -->

---

## Planned Improvements
- Performance tuning (GPU load / frame pacing in heavier scenes).
- Trophy support.
- Fine-tune the on-screen control help for the Vita.

---

## Known Issues
- Some scenes are still being optimized for the PowerVR GPU (occasional slowdown). <!-- TODO: update after GPU pass -->
- Three unrecoverable developer/joke dialogue sheets from the decompile (`Snowman`, `Testing`, `shitpost`) were removed; they are not part of normal gameplay.

---

## AI Notice

This port made use of **Anthropic's Claude (via Claude Code)** to accelerate crash-dump analysis, the memory/loading refactor, and the input adaptations needed to bring the *MOTHER: Encore* Godot project to the PS Vita. <!-- TODO: adjust wording/attribution as you prefer -->

---

## Credits & Links
- **MOTHER: Encore** — created by **Pkdotts** and team — https://mother-encore.itch.io/mother-encore
- Please support the original developers and the official MOTHER series.

Follow my other work here as well:
[https://wolffsroom.wordpress.com/](https://wolffsroom.wordpress.com/)
