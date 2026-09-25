# ReLith (No One Lives Forever) — Windows install

ReLith is the **engine only**. It ships no game content: you need your own copy of
No One Lives Forever. The engine reads your original data files directly.

Requires 64-bit Windows 10/11 and a GPU with OpenGL 4.5.

---

## 1. Install the Visual C++ runtime (once)

If you have never installed it, get **Microsoft Visual C++ 2015–2022
Redistributable (x64)** and run it. Without it the executables fail to start with a
missing `VCRUNTIME140.dll` / `MSVCP140.dll`.

**Download (direct, from Microsoft):** <https://aka.ms/vs/17/release/vc_redist.x64.exe>

That is Microsoft's own permanent short link and always serves the current version.
The page listing every architecture is
<https://learn.microsoft.com/cpp/windows/latest-supported-vc-redist>.

Take the **x64** build — ReLith is 64-bit only, and the x86 one will not satisfy it.
Most machines already have this from some other game; installing it again is harmless.

## 2. Unpack

Put this whole folder anywhere you like — for example `C:\Games\ReLith`. Do not put
it inside `C:\Program Files`; the engine writes saves and config next to itself.

## 3. Copy your game files

Copy the files below **straight into this folder**, next to the executables:

```
ReLith\
  relith-nolf.exe
  relith-nolf-vr.exe
  NOLF.REZ          <- your game data goes here, beside the exes
  NOLF2.REZ
  nolfu003.rez
  ...
  Movies\           <- optional cutscenes, keep the folder
```

(A `nolf\` subfolder also still works if you already set one up — ReLith looks there
first, then here.)

### What to copy

From your NOLF installation (or straight off the discs — see below):

| File | Needed? |
|---|---|
| `NOLF.REZ` | **required** — the game |
| `NOLF2.REZ` | **required** — menus, music, interface |
| `nolfu003.rez` | **required** — the v1.003 patch |
| `nolfu003cres.rez` | **required** — menu text; without it menus are blank |
| `NOLFGOTY.REZ` | optional — adds the bonus chapter "Rest and Relaxation" |
| `FontData.fnt` | optional — ReLith carries a fallback, but copy yours if you have it |
| `Movies\` | optional — the `.bik` cutscenes; keep them in a `Movies` folder |

Roughly 1.1 GB in total. Everything else in a NOLF install — `.flt` filters, `.M3D`
drivers, `cshell.dll`, `EReg\` — belongs to the original engine and is unused here.

**MODERNIZER is already included.** ReLith bundles `MODERNIZER.REZ`, the community
modernization mod, and loads it automatically — you do not need to install it. If you
prefer your own copy, put it in a `Custom\` folder and yours wins. To play without it,
delete `MODERNIZER.REZ` from this folder.

### Installing from the original discs

The data sits loose on the discs — no installer needed:

- **Disc 1** → `Data\` holds `NOLF2.REZ`, `NOLFGOTY.REZ`, `nolfu003.rez` and the
  `*cres.rez` files.
- **Disc 2** → `Data\` holds `NOLF.REZ`.

Copy them straight from both discs into this folder.

## 4. Play

- **Flat (monitor):** run `relith-nolf.exe`.
- **VR:** start your OpenXR runtime first (SteamVR, Virtual Desktop, or the Meta/Oculus
  app), put the headset on, then run **`relith-nolf-vr.exe`**. It starts in VR — no
  command-line switch needed.

  If you want to run the VR build on the monitor for debugging, pass `--flat`.

> **Preview note.** The two executables are the same code: the flat one still contains the
> VR code, and neither refuses to start when no OpenXR runtime is present (it falls back to
> flat with a line in the log). A genuinely VR-free flat build and a VR build that refuses
> without a runtime is tracked as F1354.

---

## What is in this folder

| File | What it is |
|---|---|
| `relith-nolf.exe` | the game, flat/monitor |
| `relith-nolf-vr.exe` | the game, VR through OpenXR (starts in VR; `--flat` to override) |
| `SDL2.dll` | windowing and input |
| `play-bik.dll` | Bink video decoding for the cutscenes (optional; skipped if absent) |
| `relith.rez` | ReLith's own small pack (merged mission list, font fallback, first-run screens) |
| `MODERNIZER.REZ` | the bundled community modernization mod — delete it to play without |
| `relith_env.cfg` | shipped defaults, including the key the in-game bug reporter submits with |
| `NOTICES` / `LICENSE` | licensing — engine code is MIT |

---

## Troubleshooting

**It closes immediately / "Game data not found".** The archives must sit in this
folder next to the executables (or in a `nolf\` subfolder) — not in a deeper
subfolder, and not still inside a zip.

**`VCRUNTIME140.dll` was not found.** Step 1 — install the VC++ redistributable
(x64): <https://aka.ms/vs/17/release/vc_redist.x64.exe>

**Menus show but all the text is missing.** No `cres` archive — copy
`nolfu003cres.rez` (or `nolf003cres.rez` / `NOLFCRES003.REZ`).

**The bonus chapter is greyed out.** `NOLFGOTY.REZ` is missing; that archive holds
the chapter's levels.

**Cutscenes are skipped.** Either `play-bik.dll` is missing from this folder, or
you did not copy `Movies\` (it goes next to the executables, like the archives).

**VR: nothing happens in the headset.** The usual cause is the OpenXR runtime not
running, or not being the *active* one. Start SteamVR / Virtual Desktop first, then run
`relith-nolf-vr.exe`. If it opens a normal window instead, the log will say
`falling back to flat mode` — that means no runtime was found.

---

ReLith engine code is MIT licensed (`LICENSE`); see `NOTICES` for the third-party
components. You must own a copy of the game.
