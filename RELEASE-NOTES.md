# ReLith — Changelog

ReLith is a modern sourceport of *No One Lives Forever*. Version numbers here are the
**port's**, not the game's — the underlying game is still NOLF v1.003.

## 0.4.0 — test build (not yet published)

### Quest — one-time reinstall required

- **This build is properly signed, so you must uninstall the old one first.** Every ReLith
  up to 0.3.1 was signed with Android's shared debug key — a key anyone has, which means
  anyone could have published an "update" for it. This build uses a real key, and Android
  will not install an app over one signed by a different key. **Back up your saves,
  uninstall, install, restore**: `INSTALL.md` has the exact paths and commands. It is a
  one-time step; every release after this one installs over the top as a normal update.
- **The app finally reports its own version.** The APK claimed to be `0.1.0` build 1 no
  matter what it actually was. The version is now derived from the source, and the build
  number rises with every release, which is what lets Android offer an update at all.
- **Your device settings file carries over.** Runtime settings were renamed from `NOLF_*` to
  `RELITH_*` (and `nolf_env.cfg` to `relith_env.cfg`); an existing file is migrated once on
  first launch instead of being silently ignored.

### VR hands and body

- **Your hands are the game's own detailed first-person hands.** The simplified IK gloves are
  replaced by the authored hands from each weapon's first-person model, with sleeves, cuffs and
  wrists fitted to Cate's body. This is now always on — the old toggle is gone.
- **Hands match what you are wearing.** Space suit, scuba, winter and other outfits show their
  own gloves instead of always wearing the Action gloves, and the sunglasses gadgets use the
  detailed hands too.
- **Every weapon and gadget has hands**, including ones whose model names its hand bones
  differently (the barrette, the coin), and the flashlight no longer drops you to low-detail
  hands.
- **Left-handed play mirrors the weapon and hand models** (Main Hand: Left), including
  silencers, laser sights and scopes.
- **The body's legs pick a real run.** Running plays the proper running gait instead of a
  sped-up walk; plain walking keeps the walk cycle.
- **The waist no longer separates from the legs while walking**, most visible in mirrors.
- **Space-suit body height is steady.** In the space station the suit body stands on its
  authored neutral pose instead of bobbing with weapon and posture layers.
- **Unarmed fists move independently** and no longer fire firearm effects.

### Weapons and aiming

- **Pistols can be steadied with your off hand.** Gripping near a pistol (P38, revolver, Luger,
  Contender) adds a support hand that sits at its authored place on the gun and never steers
  your aim. Rifles gain a one-handed mode.
- **Accuracy works like the original.** Moving, turning the aim hand and firing widen weapon
  spread and recover over time; looking around with your head never affects it.
- **The dynamic crosshair spreads outward.** Thin bars move away from the centre as accuracy
  drops (Counter-Strike style) instead of the whole crosshair growing.
- **The VR crosshair no longer rolls with your head**, and it honours the crosshair opacity,
  colour and style settings.
- **Reloading takes only the ammo you own.** With 3 in the clip and 5 in reserve on a 10-round
  weapon, a reload now gives 8/0, not a phantom 10/0.
- **Throwing the lipstick holds at the arming pose while you hold the trigger**, then throws on
  release, instead of playing the scripted swing early.
- **Lighter and Walther line up with your controller**, and every weapon ships with
  individually reviewed angle and two-hand calibration.
- **Muzzle flashes, fire sparks and pickups are the original effects.** Muzzle light, flash and
  particles follow the gun; sparks are real particle systems; pickups rotate and bob as authored.
- **The sunglasses zoom shows the head-aimed view again**, not the view from your gun hand.
- **Code breakers stay behind after cracking a keypad** so you can pick them back up.

### VR calibration

- **Fresh installs get calibration made for their platform.** Quest and PC VR now ship
  separate hand and per-weapon calibration, captured on each platform's own controllers
  (the two runtimes report the controller grip differently). Your own recalibration still
  overrides the shipped values.
- **Resetting a two-hand calibration survives a restart.** A reset used to be undone the next
  time the game started, because the shipped defaults were re-applied over it.

### Controls

- **Run/walk is a toggle on the locomotion stick click** (Always Run by default in VR). The
  off-hand grip is now only a grab, and the tooltips describe the new scheme.
- **Falling damage is back, with an option to turn it off.** A new Options → Debug section holds
  a Fall Damage toggle, on by default; swimming, ladders, scripted falls and loading a save are
  protected.

### Vehicles

- **Ride the motorcycle and snowmobile with your hands on the bars.** Your arms are solved onto
  the grips, you steer by leaning or turning the bars, and the view sits at the rider's seated
  eye. The game recenters automatically when you mount.
- **Analog throttle and brake through the triggers.** Hold the brake at a stop to reverse, and
  the throttle hand rumbles; a tooltip at the motorcycle tutorial explains the controls.
- **The vehicle's gauges and parts move.** Speedometer and tachometer needles, the handlebars,
  the snowmobile windshield and the motorcycle's wheels animate with your riding.
- **Crashes hurt and push, and ramming enemies works again.** Impacts damage and deflect you
  like the original, and riding into enemies at speed kills them, as the tutorial promises.
- **The snowmobile leaves a ledge at the edge** instead of hopping early or stopping as if
  it hit a wall, and no longer freezes on slopes or catches an invisible bump at crests (the
  snowstorm launch).
- **Landing a long vehicle jump is survivable.** Fall damage on a vehicle accounts for the
  reduced gravity vehicles fall with, so the damage matches how hard you actually land.
- **Leaving a level while riding dismounts cleanly**, instead of breaking the body in the next
  level.
- **No more footsteps while riding**, no leaned body after mounting in seated mode, and the
  snowmobile's low-detail hood no longer shows through your view.
- **Trees no longer pop at the screen edges while riding** in the motorcycle tutorial.

### Graphics

- **Environment maps are on by default and correct.** Shiny surfaces and chrome reflect with the
  original's mapping and lighting, in each eye separately, on every platform.
- **Models are lit like the original.** Character and prop lighting now uses the original's
  generated light grid and light rules (no more double-counted lights, spotlights keep their
  cone), direct sunlight reaches models outdoors, and world-lit models are no longer half as
  bright as they should be.
- **Flickering and rotating lights animate**, and lighting in the m07 intro cinematics no longer
  leaves characters too dark.
- **Mirrors work.** The hotel mirrors show a real reflection, including your own body, head and
  weapon.
- **The scenery outside the train moves.** Trees scroll past the windows in the correct
  direction on both sides and the sky drifts; the same fix brings back moving clouds, the sky
  reflected in the opening level's sea, and shiny surfaces at UNITY HQ.
- **Tropical water tiles properly** instead of stretching one tile across the pool (m10s01).
- **Shadows no longer show through walls and tables**, and nearby shadows no longer pop or
  shrink when you move a step.
- **Trees no longer flicker.** Foliage made of back-to-back leaf cards drew two faces at the same
  depth; it now renders steadily.
- **Blood decals appear again** as proper splats, without the dark square behind them.
- **Seam cracks along brush edges are gone.** The original's T-junction fix is now drawn, which
  removes the one-pixel "sparkle" seams on about 6% of world polygons.
- **Transparent effects sort by distance.** Sprites, particles and see-through models are drawn
  far to near in one list, so they stop popping in front of each other.
- **Cut-out textures are cut out.** Chromakeyed models and worldmodels no longer draw their
  transparent parts solid or with halos.
- **Animated textures on walls play**, glow sprites (camera lenses, laser tripwire ends) scale
  like the original, and lens flares are restored (off by default in VR).
- **Wall displays sit on their panels in stereo** (the space-station console display), instead of
  floating in front of them.
- **The Turbulence airliner's sky is no longer a lit cube**, and the far sky above the ski slopes
  no longer shows a black rectangle.
- **Snowfall reaches the ground** in the opening level instead of cutting off mid-air.
- **The beer vats are visible from above**, and jumping out of water no longer loses the jump
  at the rim.
- **The left eye no longer goes black near the pool** in the first mission.

### Characters and levels

- **Characters stand on the floor.** Actors no longer float after a fresh level transition (the
  Hamburg club), sit in mid-air on the train, stand in the air (t06s01), sink under the level
  (m10s02) or fall through thin floors (the frozen lake).
- **Characters' heads turn to look at you**, and several dropped character effects now play.
- **The deployed robo-poodle walks up slopes and faces the right way.**
- **Inge fights properly after loading an autosave** of her boss fight.
- **The space-station code breaker works.** After loading a save, the gadget you select is the
  one the game thinks you own.
- **The elevator bomb in the first mission can be reached**; an invisible blocker no longer stops
  the use ray short of it.

### Cutscenes and dialogue

- **Cutscenes no longer fast-forward after loading an autosave**, and Dr. Schenker can be
  talked to again (m02s03).
- **VR cutscenes respect the brightness setting.**

### Audio and music

- **Music plays like the original DirectMusic score.** Each play draws its own variations,
  segments follow their authored command tracks, boundaries are seamless, and mood changes wait
  for the next measure instead of cutting in.

### Menus

- **Menus follow the original layouts.** Rows, fonts, scrolling, page arrows and clickable areas
  now match the authored screens, and controller navigation is reliable.
- **New and restored screens**: Crosshair options (six original styles, colour and opacity),
  Effects options (tracers, shell casings, muzzle light, weather, impact and debris detail), and
  the Load/Save, Briefing, Objectives, Escape, Inventory and outfitting screens on their
  original layouts.
- **The MODERNIZER credit is shown on the opening splash screen only**, not on the main menu.

### Saves

- **Saves keep every object.** A save written while objects were being removed could drop
  dozens of them on load (37 in the opening level).

### PC VR

- **Colours are right on PC VR.** The image was overbright with crushed blacks; the headset now
  gets the colour format desktop runtimes expect.
- **The VR executable starts in VR** without `--vr`, and no longer silently falls back to a flat
  window if the headset is not ready.
- **The desktop window always shows something now**, and opens at 2560×1440. Windows display
  scaling no longer squeezes it (or Game Bar recordings) into a corner.
- **Spectator camera** (`vr_spectator`): a smoothed follow camera, on by default, so the
  desktop is watchable rather than a raw headset mirror. `1` follows, `2` freezes for a
  locked-off shot, `0` turns the extra view off; `vr_spectator_smooth` and `vr_spectator_fov`
  tune it. It never leaves Cate's head, and it hides the HP/ammo readouts.
- **Third-person spectator** (`vr_spectator 3`): a chase camera behind and above Cate, with
  her head restored. `vr_spectator_distance` and `vr_spectator_height` frame the shot. It has
  no camera collision yet, so it will clip through walls in tight interiors.
- **In menus and cutscenes the desktop mirrors the menu** the right way up, instead of a frozen
  world or the loading screen.
- **The setup screen shows on the desktop** when game data is missing, with instructions for
  copying it on a PC.

### Performance

- **Levels load faster and use far less video memory.** Lightmaps are packed into one atlas per
  level (the opening level's world upload went from about 1.5 s to 0.4 s), and the loading
  screen now overlaps the load instead of starting after it.
- **The train level runs smoothly.** Mirrors are only re-rendered when they are in your room,
  instead of once per mirror per eye down the whole corridor.
- **No more per-frame rebuilding of reflections and sky** when the spectator window and the eyes
  want different sizes.
- **Shaders are cached on disk** where the driver supports it, so later launches skip
  recompiling them.

### Stability

- **Fixed crashes**: in m02s03 when a guard pathed through a removed door, in m05s03 combat, on
  the m10s03 → m10s04 transition, and when leaving a level (reported in m15s01).

### Reporting

- **The in-game bug reporter works on PC VR.** Its submission key was never bundled into the
  desktop build, and the VR build could silently compile without the reporter at all.
  Setting `RELITH_KEY` in your own environment still overrides the shipped key.
- **Session recording for bug reports.** A toggle in the feedback menu records what the game
  draws to a replay file that can be attached to a report.

### Installing

- **Game data goes next to the executables now** — no `nolf\` subfolder. The engine looks
  in `nolf/` first and then beside the binary, so an existing install keeps working.
- **MODERNIZER is bundled** on Windows the way it already was on Quest, and loads
  automatically. Your own `Custom\MODERNIZER.REZ` still takes precedence, and deleting the
  bundled copy plays without it.
- Intro cutscenes are found in either layout (their paths were pinned to `nolf/Movies`).

### Known issues

- Dropping into water can apply falling damage that the original would not.
- On Quest 2, the VR menu panel can render black except for the line under the pointer.

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
