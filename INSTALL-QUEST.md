# ReLith (No One Lives Forever) — Quest install

ReLith is the **engine only**. It ships no game content: you need your own copy of
No One Lives Forever. The engine reads your original data files directly.

You need: a Meta Quest, a USB cable, and [SideQuest](https://sidequestvr.com)
(the app is sideloaded, so SideQuest — or any adb — is required either way).

---

## Already have ReLith installed? Read this first (one time only)

**Skip this if you are installing ReLith for the first time.**

Builds up to and including **0.3.1** were signed with Android's throwaway debug key.
This one is signed properly, and Android will not install an app over one signed with a
different key — it refuses with `INSTALL_FAILED_UPDATE_INCOMPATIBLE`. So this upgrade,
and only this one, means: **back up your saves → uninstall → install → restore**. Every
release after this one installs straight over the top as a normal update.

### 1. Find out where your saves are

Saves sit next to your game files, so it depends on which folder you copied those into:

| Your game files are in… | Saves are in… | Uninstall deletes them? |
|---|---|---|
| `nolf/` — a plain folder in main storage (what step 4 below sets up) | `/sdcard/nolf/Save/` | No. Back them up anyway. |
| `Android/data/net.relith.nolf/files/nolf/` | `Android/data/net.relith.nolf/files/nolf/Save/` | **Yes** — and your game files with them |

The second folder is where ReLith puts things when it never got storage access. If that is
you, uninstalling costs you the ~1.1 GB of game data too, and you will re-copy it in step 4.

### 2. Back them up

**With SideQuest:** plug the headset in and open SideQuest's file manager (the folder icon,
top right, "Manage files on the headset").

1. Open the folder your game files are in (see the table above): `nolf`, or
   `Android/data/net.relith.nolf/files/nolf`.
2. Copy the **`Save`** folder to your computer (select it, then the download/save-to-computer
   button). It holds `Slot01.sav`, `Slot02.sav`, … and `Quick.sav`.
3. Copy **`autoexec.cfg`** from the same folder too — your unlocked missions live in it, not
   in `Save`.

Nothing else is yours: the mod, the config defaults and the fallback font all come out of
the app itself on every launch.

**With the command line (adb)** — run both, and ignore the one that says the path does not
exist:

```
adb pull /sdcard/nolf/Save ./relith-saves
adb pull /sdcard/Android/data/net.relith.nolf/files/nolf/Save ./relith-saves
adb pull /sdcard/nolf/autoexec.cfg .
adb pull /sdcard/Android/data/net.relith.nolf/files/nolf/autoexec.cfg .
```

### 3. Uninstall, install, restore

**With SideQuest:**

1. Open SideQuest's installed-apps list (the grid icon, top right, "Currently installed
   apps"), find **net.relith.nolf** and choose **Uninstall** from its options.
2. Install the new APK (step 2 below) and launch it once with storage access granted
   (step 3 below) so the folders exist again.
3. In the file manager, open `nolf` and upload your saved **`Save`** folder and
   **`autoexec.cfg`** back into it (drag them in, or use the upload button).

**With the command line (adb):**

```
adb uninstall net.relith.nolf
```

Install the new APK (step 2 below) and launch it once with storage access granted (step 3
below). Then push your saves back into the same path you pulled them from:

```
adb push ./relith-saves/. /sdcard/nolf/Save/
adb push ./autoexec.cfg /sdcard/nolf/
```

---

## 1. Put the headset in developer mode

1. In the phone Meta app: **Menu → Devices → your headset → Developer Mode → On**.
2. Plug the headset into the computer.
3. Put the headset on and **Allow USB debugging** when it asks. Tick "always allow".

## 2. Install the app

In SideQuest, use the **"Install APK file from folder"** button (the box-with-arrow
icon, top right) and choose `relith-nolf.apk`.

## 3. Launch it once and grant storage access

Open it from **App Library → Unknown Sources → ReLith**.

The first launch asks for storage access and **will not start without it** — it
needs to read your game data and save your progress. A Settings page should open
automatically:

1. Find **ReLith** in the list.
2. Turn on **"Allow access to manage all files"**.
3. Go back and launch ReLith again.

If the page does not open by itself:
**Settings › Apps › Special app access › All files access › ReLith**.

Once granted, you will see a **"Game data not found"** screen. That is expected —
and launching has now created the folder you are about to copy into. Close the app.

## 4. Copy your game files

Copy the files listed below into this folder on the headset:

```
nolf/
```

That is a plain `nolf` folder in the headset's main storage — the same place you
see Downloads and Pictures. In SideQuest use the file-manager icon (a folder, top
right) and drag your files in.

If you prefer the command line:

```
adb push NOLF.REZ /sdcard/nolf/
```

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

Roughly 1.1 GB in total. Everything else in a NOLF install — `.flt` filters,
`.M3D` drivers, `cshell.dll`, `WidescreenGOTY.rez`, `EReg/`, `Movies/`, `Save/` —
is Windows-only or unused here. Do not copy it.

**Already bundled, do not copy:** the MODERNIZER mod (HD fonts, menu arrows) and
the merged mission list ship inside the app. If you copy your own
`Custom/MODERNIZER.REZ`, yours is used instead.

### Installing from the original discs

The data sits loose on the discs — no installer needed:

- **Disc 1** → `Data\` holds `NOLF2.REZ`, `NOLFGOTY.REZ`, `nolfu003.rez` and the
  `*cres.rez` files.
- **Disc 2** → `Data\` holds `NOLF.REZ`.

Copy them straight from both discs into the folder above.

## 5. Play

Launch ReLith again. You should get the main menu.

---

## Troubleshooting

**"Game data not found" after copying.** The archives must sit directly inside
`nolf/`, not in a further subfolder.

**It asks for storage permission every launch.** The toggle did not stick — check
**Settings › Apps › Special app access › All files access** and make sure ReLith
is on.

**Menus show but all the text is missing.** No `cres` archive — copy
`nolfu003cres.rez` (or `nolf003cres.rez` / `NOLFCRES003.REZ`).

**The bonus chapter is greyed out.** `NOLFGOTY.REZ` is missing; that archive holds
the chapter's levels. Copy it and it becomes selectable.

**SideQuest cannot see the `nolf` folder.** Make sure the app was launched at
least once with permission granted (step 3) — it creates the folder.

---

ReLith engine code is MIT licensed. It bundles the community MODERNIZER mod by
**HeyThereCoffeee** (`haekb`) — *"This add-on is not made by or supported by
Monolith Productions, or any of its affiliates and subsidiaries."* See `NOTICES` in
the source repository. You must own a copy of the game.
