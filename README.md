<p align="center">
  <img src="Assets/PSVita_Screen.png" alt="MOTHER: Encore - PS Vita Port">
</p>

# MOTHER: Encore (ACT 2) - PS Vita Port

A native PlayStation Vita port of **MOTHER: Encore**, the free fan-made reimagining of MOTHER 1, adapted from its original **Godot Engine** PC release. This repository contains the source patches, control rewrites, and tooling created to make the game run natively on the PS Vita hardware.

> Based on **MOTHER: Encore ACT 2 - v0.4.0.3 (Windows)**.
> Original game by **Pkdotts** and team: **https://mother-encore.itch.io/mother-encore**

## Release Status

<p align="center">
  <img alt="Overall progress" src="https://img.shields.io/badge/Overall_progress-~55%25-2ea44f?style=for-the-badge">
  &nbsp;
  <img alt="Platform" src="https://img.shields.io/badge/PS_Vita-Godot_3.5_RC5-003791?style=for-the-badge&logo=playstation&logoColor=white">
  &nbsp;
  <img alt="State" src="https://img.shields.io/badge/State-Playable-brightgreen?style=for-the-badge">
</p>

<p align="center"><i>Bugs, crashes, poor performance, but it's playable (I guess).</i></p>

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

Every release ships **two files**: the `.vpk` (the app itself) and a `-GameData.zip` (the game data, i.e. `game_data/game.pck`). You need both.

1. Head to the **[Releases](../../releases)** tab.
2. Download the latest `MotherEncore-Vita-x.x.x.vpk` and `MotherEncore-Vita-x.x.x-GameData.zip`.
3. Install the `.vpk` on your PS Vita using VitaShell or **[FMVita](https://github.com/WolffsRoom/FMVita)** (my personalized VitaShell).
4. Extract the `-GameData.zip` - you'll get a `game_data` folder containing `game.pck`.
5. Connect your Vita via FTP or USB and copy that `game_data` folder into:
   `ux0:app/MOTHER001/`
   *(The file must end up exactly at `ux0:app/MOTHER001/game_data/game.pck`.)*
6. Have fun!

> This build is redistributed under MOTHER: Encore's **MIT license**, with full credit to the original authors. If you enjoy the game, please support the developers at the **[official page](https://mother-encore.itch.io/mother-encore)**.

> **UPDATE NOTICE:** When updating, always install **both** the new `.vpk` and the new `-GameData.zip` - a newer VPK isn't guaranteed to work with an older `game.pck`, and vice versa.
> _Save files are not lost when uninstalling or updating (they are stored under `ux0:data/godot/app_userdata/MOTHER Encore/...`)._

---

## Controls (Controles)

<div align="center">

| Control | Action | Control | Action |
|:---:|:---|:---:|:---|
| <img src="Assets/SonyButtons/up.png" height="18"> <img src="Assets/SonyButtons/down.png" height="18"> <img src="Assets/SonyButtons/left.png" height="18"> / <img src="Assets/SonyButtons/analog_l.png" height="18"> | Move | <img src="Assets/SonyButtons/cross.png" height="18"> | Confirm / Interact |
| <img src="Assets/SonyButtons/triangle.png" height="18"> | Menu | <img src="Assets/SonyButtons/circle.png" height="18"> | Cancel / Back |
| <img src="Assets/SonyButtons/square.png" height="18"> | Crouch / Telepathy (hold) | <img src="Assets/SonyButtons/analog_r.png" height="18"> | Camera |
| **L1** | Previous party member | **R1** | Next party member |
| <img src="Assets/SonyButtons/touchpad.png" height="20"> **Left half** | **L2** - Scope / markers | <img src="Assets/SonyButtons/touchpad.png" height="20"> **Right half** | **R2** - Crouch / Telepathy |

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
This is an early technical beta - expect rough edges:
- **Battle crashes:** The game still crashes when entering the first battle. Fix planned for the next version.
- **Performance:** GPU load is high and frame rate is currently low in the overworld/title; performance tuning is still in progress.
- Some scenes are still being optimized for the PowerVR GPU.
- Three unrecoverable developer/joke dialogue sheets from the decompile (`Snowman`, `Testing`, `shitpost`) were removed; they are not part of normal gameplay.

---

## AI Notice

This port made use of **Anthropic's Claude (via Claude Code)** to accelerate crash-dump analysis, the memory/loading refactor, and the input adaptations needed to bring the *MOTHER: Encore* Godot project to the PS Vita. <!-- TODO: adjust wording/attribution as you prefer -->

---

## Credits & Links
- **MOTHER: Encore** - created by **Pkdotts** and team - https://mother-encore.itch.io/mother-encore
- Please support the original developers and the official MOTHER series.

Follow my other work here as well:
[https://wolffsroom.wordpress.com/](https://wolffsroom.wordpress.com/)
