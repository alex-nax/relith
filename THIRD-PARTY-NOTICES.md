# Third-party notices

The components ReLith ships and their licences. Full licence texts are in
[licenses/](licenses/).

```text
# NOTICES

Third-party and community content distributed with ReLith (the NOLF Improved
sourceport). Our own engine code is MIT (see LICENSE); this file covers what we
ship alongside it. Licensing policy and the reasoning behind each decision live
in `docs/distribution.md`.

--------------------------------------------------------------------------------

## MODERNIZER (bundled when supplied at build time)

`MODERNIZER.REZ` is bundled in Quest and Windows releases when supplied so a fresh install has the community
modernization (HD fonts, menu arrows, jukebox, widescreen-friendly UI) without a
second download.

- **Author: HeyThereCoffeee** (GitHub / itch.io handle **`haekb`**)
  - https://heythere.coffee/nolf/
  - https://haekb.itch.io/nolf-modernizer
  - https://github.com/haekb

- **Required notice:** *"This add-on is not made by or supported by Monolith
Productions, or any of its affiliates and subsidiaries."*

- Distributed free of charge only, and it requires a legitimate copy of
  No One Lives Forever — the mod does nothing without the game's own data, which
  users must supply separately.

MODERNIZER carries no permissive open-source licence; its author binds it to
Monolith's NOLF Source-Code EULA. Bundling it is a deliberate maintainer decision
(`docs/distribution.md` §1a) taken because the mod is already distributed freely
by the community and it materially eases first-time setup. **If the author or any
rights holder asks us to stop, the asset is withdrawn** — it is a build-time input
(`android/app/build.gradle`, `stageModernizer`), deliberately not committed to
this repository, so removing it is a one-line change and leaves no trace in git
history. The engine degrades gracefully without it (F366).

--------------------------------------------------------------------------------

## FontData.fnt (bundled in relith.rez)

A 10 KB font-metrics index, bundled as a **fallback only**: it is loaded from
`relith/FontData.fnt` and consulted solely when the user's own copy is absent,
so an install that has one (including a MODERNIZER-patched index carrying
`FONT_LARGE_0_HD`) always wins.

It is bundled because an install built from the original GOTY discs has no copy
at all — the file is on neither disc and inside no `.rez` archive — and without it
every menu string renders invisible (F394).

Provenance is not fully established: the copy we ship is dated 2023, two decades
after the game, so it is community-era rather than a disc file. Treated under the
same maintainer decision as MODERNIZER (`docs/distribution.md` §1a) and withdrawn
on request by the same route.

--------------------------------------------------------------------------------

## play-bik

Bink video decoding, derived from LGPL sources (e.g. FFmpeg's bink decoder) and
therefore distributed under the LGPL. SPDX: LGPL-2.1. Source: https://github.com/alex-nax/play-bik
(the exact revision is in the ReLith gitlink). Licence and derivation:
licenses/play-bik-LICENSE. Binary bundles include play-bik-source.tar.gz;
RELINK.md explains rebuilding and replacing this runtime shared plugin.

--------------------------------------------------------------------------------

## Game data

Users supply their own legally-obtained No One Lives Forever game archives;
ReLith does not bundle the user's NOLF.REZ, NOLF2.REZ or NOLFGOTY.REZ.
The bundled exceptions recorded in `docs/distribution.md` sections 1a/2 are
`relith.rez` (the merged mission descriptor, setup/permission resources and
FontData.fnt fallback) and MODERNIZER when supplied at build time. MODERNIZER
includes NOLF-derived resources, not only its author's original interface art.
Those resources retain their original terms and do not become MIT-licensed.

--------------------------------------------------------------------------------

## openal-soft (statically linked)

OpenAL Soft 1.24.1, by the OpenAL Soft contributors.
Source: https://github.com/kcat/openal-soft/tree/1.24.1
Original licence: LGPL-2.0-or-later; COPYING is the GNU Library General Public
License version 2 and source headers permit any later version. ReLith uses the
LGPL-2.1 option. The original text is in licenses/openal-soft-COPYING and the
complete LGPL-2.1 text is in licenses/LGPL-2.1.txt. Binary bundles provide the
actual corresponding source in relink.tar.gz (openal-soft-source.tar.gz), plus
native objects/archives and the original link commands. See RELINK.md.
Verbatim COPYING source:
https://raw.githubusercontent.com/kcat/openal-soft/1.24.1/COPYING

## fluidsynth (statically linked)

FluidSynth v2.5.3, by the FluidSynth contributors.
SPDX: LGPL-2.1-or-later.
Source: https://github.com/FluidSynth/fluidsynth/tree/v2.5.3
The complete licence is in licenses/fluidsynth-LICENSE. Binary bundles provide
the actual corresponding source in relink.tar.gz (fluidsynth-source.tar.gz),
plus native objects/archives and the original link commands. See RELINK.md.
Verbatim licence source:
https://raw.githubusercontent.com/FluidSynth/fluidsynth/v2.5.3/LICENSE

## SDK-derived NOLF game code

src/game/nolf and shared SDK-derived code are adapted from the NOLF SDK by
Monolith Productions, available at https://github.com/osgcc/no-one-lives-forever.
They retain the SDK release terms, not the engine MIT licence. The release-term
review remains open in docs/distribution.md section 3.2; this notice does not
claim to resolve it or to grant new rights over SDK or game content.

## Other linked dependencies

Each library retains its upstream terms. Some are platform-specific; including a
notice does not claim that the library is present in every binary.

- glm 1.0.1: MIT / Happy Bunny licence; https://github.com/g-truc/glm
- stb_image, stb_image_write and stb_truetype: MIT / public-domain dual licence;
  https://github.com/nothings/stb
- glad v2.0.8: MIT / public-domain generated loader; https://github.com/Dav1dde/glad
- minimp3: CC0-1.0; https://github.com/lieff/minimp3
- OpenXR-SDK release-1.1.43: Apache-2.0; https://github.com/KhronosGroup/OpenXR-SDK
- oboe 1.9.0 (Android): Apache-2.0; https://github.com/google/oboe
- SDL2 (desktop, system package): Zlib; https://github.com/libsdl-org/SDL
- Mbed TLS v3.6.2: Apache-2.0 OR GPL-2.0-or-later (Apache option used);
  https://github.com/Mbed-TLS/mbedtls
- fmt (OpenAL dependency): MIT; https://github.com/fmtlib/fmt
- PFFFT (OpenAL dependency): BSD-style terms; see licenses/openal-LICENSE-pffft
- gcem (FluidSynth dependency): Apache-2.0; https://github.com/kthohr/gcem
- iklib, pinned at 620bff1a44904e441c44b588c3339c57d73bb9bc and statically linked into every
  binary carrying the VR body solve (F1706): MIT; https://github.com/alex-nax/iklib
  (private owner repository); licence text in licenses/iklib-LICENSE

These verbatim texts are in licenses/. doctest is used by tests, not shipped.
```
