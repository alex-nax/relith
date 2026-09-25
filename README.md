# ReLith — No One Lives Forever, rebuilt

<img src="assets/relith-icon.png" alt="ReLith icon" width="96">

ReLith is a modern sourceport of *The Operative: No One Lives Forever* (2000). It replaces
the original LithTech engine with a new one and plays the campaign in **VR on Meta Quest**,
in **PC VR** (OpenXR), or flat on a monitor.

**ReLith is the engine only. It ships no game content** — you need your own copy of
No One Lives Forever, and ReLith reads its original data files directly.

[Download the latest release](https://github.com/alex-nax/relith/releases/latest)
· [Install on Windows](INSTALL-WINDOWS.md) · [Install on Quest](INSTALL-QUEST.md)
· [Controls](CONTROLS.md) · [Release notes](RELEASE-NOTES.md)

## Platforms

| Platform | Mode | Package |
|---|---|---|
| Meta Quest (standalone) | VR | APK, sideloaded |
| Windows 10/11, 64-bit | PC VR (OpenXR: SteamVR, Virtual Desktop, Meta app) and flat | ZIP |

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

## Credits

ReLith bundles **MODERNIZER** by **HeyThereCoffeee (haekb)** —
<https://heythere.coffee/nolf/> — the community modernization mod, loaded automatically.
This add-on is not made by or supported by Monolith Productions, or any of its affiliates and subsidiaries.

No One Lives Forever is © its rights holders; ReLith is an unofficial fan project and is not
affiliated with or endorsed by them. The ReLith engine code is MIT licensed; the third-party
components and their licences are listed in [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md)
and [licenses/](licenses/).
