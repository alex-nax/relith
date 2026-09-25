# ReLith — a new engine for LithTech 2 games

<img src="assets/relith-icon.png" alt="ReLith icon" width="96">

ReLith is a modern replacement for Monolith's **LithTech 2.x** engine. It runs the original
games' own data and game logic on a new engine built for today's hardware — with **VR on Meta
Quest** and **PC VR** (OpenXR) as first-class modes.

**Now playable:** *The Operative: No One Lives Forever* (2000).
**Next:** *Aliens versus Predator 2* — in development on the same engine.

**ReLith is the engine only. It ships no game content** — you need your own copy of the
game, and ReLith reads its original data files directly.

[Download the latest release](https://github.com/alex-nax/relith/releases/latest)
· [Install on Windows](INSTALL-WINDOWS.md) · [Install on Quest](INSTALL-QUEST.md)
· [Controls](CONTROLS.md) · [Release notes](RELEASE-NOTES.md)

## Platforms

| Platform | Mode | Status |
|---|---|---|
| Meta Quest (standalone) | VR | available — APK, sideloaded |
| Windows 10/11, 64-bit | PC VR (OpenXR: SteamVR, Virtual Desktop, Meta app) | available — ZIP |
| Windows, macOS | Flat (monitor) | coming soon |

## Start here

1. Have your copy of No One Lives Forever ready — an existing installation or the original
   discs (the data files sit loose on them).
2. From the release's **Assets** list, download the package for your platform. GitHub's
   automatic **Source code** downloads are not the game.
3. Follow the install guide for your platform: [Windows](INSTALL-WINDOWS.md) ·
   [Quest](INSTALL-QUEST.md). Each guide ends with a troubleshooting section.

## Reporting a problem

The in-game **Feedback** screen (main menu) sends a report together with a save of the exact
moment you opened it — that is the fastest way to get a bug fixed. You can also
[open an issue](https://github.com/alex-nax/relith/issues/new/choose); say which release and
platform you are on.

## Support me

ReLith is free. If you enjoy it and want to help it along:

- **Ko-fi:** <https://ko-fi.com/alex0d>
- **Ethereum and its L2s:** `0x98595c40A0f22F44239568F11060C6209E56D155`

## Credits

ReLith bundles **MODERNIZER** by **HeyThereCoffeee (haekb)** —
<https://heythere.coffee/nolf/> — the community modernization mod, loaded automatically.
This add-on is not made by or supported by Monolith Productions, or any of its affiliates and subsidiaries.

No One Lives Forever is © its rights holders; ReLith is an unofficial fan project and is not
affiliated with or endorsed by them. The ReLith engine code is MIT licensed; the third-party
components and their licences are listed in [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md)
and [licenses/](licenses/).
