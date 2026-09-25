# ReLith — Changelog

ReLith is a modern sourceport of *No One Lives Forever*. Version numbers here are the
**port's**, not the game's — the underlying game is still NOLF v1.003.

## Unreleased

### Quest — one-time reinstall required

- **This build is properly signed, so you must uninstall the old one first.** Every ReLith
  up to 0.3.1 was signed with Android's shared debug key — a key anyone has, which means
  anyone could have published an "update" for it. This build uses a real key, and Android
  will not install an app over one signed by a different key. **Back up your saves,
  uninstall, install, restore**: `INSTALL.md` has the exact paths and commands. It is a
  one-time step; every release after this one installs over the top as a normal update.
- **The app finally reports its own version.** The APK claimed to be `0.1.0` build 1 no
  matter what it actually was — the number was typed into the build file once and never
  touched, while the menu and the changelog moved on without it. Both are now derived from
  the source, and the build number rises with every release, which is what lets Android
  offer an update at all.

### VR

- **The desktop window always shows something now.** It used to be presented zero times in
  VR mode — the contents were whatever the driver happened to leave there, and it would not
  repaint properly when dragged or uncovered. It now renders every frame.
- **Spectator camera** (`vr_spectator`): a smoothed follow camera, on by default, so the
  desktop is watchable rather than a raw headset mirror carrying every twitch of your neck.
  `1` follows, `2` freezes for a locked-off shot, `0` turns the extra view off (the window
  still presents). `vr_spectator_smooth` and `vr_spectator_fov` tune it.
- In menus and cutscenes the desktop mirrors the menu itself instead of a frozen world.
- **Third-person spectator** (`vr_spectator 3`): a chase camera behind and above Cate, with
  her head restored — the first-person view removes it so it isn't inside the camera, which
  from behind would have shown a headless body. `vr_spectator_distance` and
  `vr_spectator_height` frame the shot. It has no camera collision yet, so it will clip
  through walls in tight interiors; `1` and `2` stay the reliable modes indoors.

### Reporting

- **The in-game bug reporter works on Windows.** It reported itself disabled because the
  shipped defaults that carry its submission key were bundled into the Quest APK but never
  into the desktop build. Setting `RELITH_KEY` in your own environment still overrides the
  shipped one.

### Installing

- **Game data goes next to the executables now** — no `nolf\` subfolder. The engine looks
  in `nolf/` first and then beside the binary, so an existing install keeps working; the
  subfolder is simply no longer something you have to know about.
- **MODERNIZER is bundled** on Windows the way it already was on Quest, and loads
  automatically. Your own `Custom\MODERNIZER.REZ` still takes precedence, and deleting the
  bundled copy plays without it.
- Intro cutscenes are found in either layout (their paths were pinned to `nolf/Movies`).

## 0.3.1 — 2026-08-22

### VR rendering

- **Single-pass stereo (multiview) is now the default.** It was previously opt-in through a
  config file, which meant a device wipe silently dropped you back to the slower two-pass
  path — and every frame measurement taken after such a wipe was made in the wrong mode. A
  default that lives in a file any wipe destroys is not a default.
- **Eye resolution is adjustable** (Display → Resolution, 70–150%). The runtime recommends
  1680×1760 per eye but permits up to 8192², so there was a lot of unused headroom. Cost
  scales with *area*: 150% linear is 2.25× the pixels.
- **Anti-aliasing** (Display → Anti-aliasing, 2×/4×). The OpenXR runtime caps swapchain
  samples at 1, so this renders multisampled in tile memory and resolves on store — the
  cheap shape on mobile GPUs.
- **Both apply immediately**, with no restart.
- **Seated / standing play modes.** Seated composes the view from a calibrated standing
  height, so the world looks the same sitting or standing. Roomscale leaning still works
  seated; physical crouch is button-only. Standing remains the default.

### Rendering fidelity

- **Detail textures.** The original blends a second, finer texture over surfaces up close —
  2462 of NOLF's 3403 textures ask for one, and the port had been discarding the request.
  Wood, stone and fabric keep their grain instead of going soft. Adjustable via
  `DetailTextureScale`.
- **Brightness now affects the world**, not only the menu panel, and the slider range is
  wider in both directions.
- **Character lighting fixed.** Lights are evaluated once at a model's origin, as the
  original does, instead of per-pixel — which had been draining most of the light off
  character-sized models and leaving them near-black.

### Saves

- **Save and load lists scroll**, and the slot count is no longer capped at five: the list
  grows as you use it.
- **Autosaves are browsable** from the Load screen.

### Fixes

- Final credits no longer lock up at the end of the game, and the bonus chapter unlocks.
- Level transitions and mission progression repaired, including loading from an autosave.
- Unlocked gadgets, weapons, attachments and powerups persist for mission select.
- Sounds attached to moving objects follow them properly.

### Known issues

- With anti-aliasing enabled, the sniper-scope overlay renders incorrectly.
- Some surfaces show a faint seam along polygon edges (under investigation; not caused by
  the detail-texture work).
