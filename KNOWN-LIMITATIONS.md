# Known limitations

ReLith is in preview. What is known and not yet addressed:

- **No game content is included.** You need your own NOLF data files; see the install guides.
- **Quest builds are sideloaded** (SideQuest or adb); there is no store listing.
- **Third-person spectator** (`vr_spectator 3`) has no camera collision yet and clips through
  walls in tight interiors; spectator modes `1` and `2` are the reliable ones indoors.
- **The flat and VR Windows executables are the same code.** The flat one still contains the
  VR code, and the VR one falls back to a normal window when no OpenXR runtime is running
  (the log says `falling back to flat mode`).
- **The bonus chapter** "Rest and Relaxation" needs `NOLFGOTY.REZ`; without it the chapter is
  greyed out.

The [release notes](RELEASE-NOTES.md) list what changed in each build.
