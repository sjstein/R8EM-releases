# R8EM User Guide
## Run8 Enhancement Manager

---

## Table of Contents

1. [Overview](#overview)
2. [Initial Setup](#initial-setup)
3. [The Enhancement Library](#the-enhancement-library)
4. [Suggested Workflow](#suggested-workflow)
5. [Working with Profiles](#working-with-profiles)
6. [DLC Ownership Tracking](#dlc-ownership-tracking)
7. [Baseline Comparison](#baseline-comparison)
8. [Reference — Menus and Buttons](#reference--menus-and-buttons)

---

## Overview

R8EM (Run8 Enhancement Manager) is a desktop tool for managing visual and audio enhancements to Run8 Train Simulator V3. It allows you to:

- Maintain a personal library of enhancement files (texture replacements, sound replacements, and more)
- Install and revert enhancements to your Run8 installation with a single click
- Group enhancements into **profiles** so you can switch between different sets instantly
- Compare your current Run8 installation against a known-good baseline to detect unexpected changes
- Track which DLC packs you own so that missing DLC content is correctly identified

R8EM supports the following enhancement types:

| Type | Description |
|---|---|
| Rolling stock repaint | Texture replacements for rolling stock (locomotives, freight cars, etc.) |
| Sound | Audio replacements for desktop sound files |
| Terrain Texture | Ground and terrain texture replacements |
| Track Texture | Track and rail texture replacements |
| Vegetation Texture | Tree and vegetation texture replacements |
| Splendid Asset | New or replacement Splendid Visual asset files (`.rn8`, `.tx8`) |
| Terrain Tile | Replacement terrain tiles (`.tr4`) for one region |

Enhancements can be individual files (`.tx8`, `.tkb`, `.wav`, `.rn8`, `.tr4`) or **ZIP archives** containing one or more enhancement files.

### Terrain tile and scenery packs

A pack may contain both assets and tiles. Put assets in a `Splendid Assets` folder and tiles in a `TerrainTiles` folder inside the ZIP; R8EM detects the folders and sets the type to **Multiple**.

- Assets install into `Content\V3Routes\Splendid Assets`. Existing files are backed up first; new assets are simply added and removed again on uninstall.
- Tiles install into `Content\V3Routes\Regions\<region>\TerrainTiles`. Tile filenames are the same in every region, so R8EM asks **which region the pack belongs to** when you install it (one region per pack). Tile backups are kept per region under `BACKUPS\Terrain Tile\<region>`.

---

## Initial Setup

### NOTE: Ideally you will start from a fresh, unmodified (enhanced) version of Run8. 
- You can verify the integrity of your installation at any time by choosing `File -> Compare to base R8 installation`.
	- This will scan your existing installation and report any files that are either missing, or don't match their original signature.
	- Files that are missing may just indicate content you don't currently own. 

### 1. Place R8EM in its own folder

R8EM is a self-contained application. Extract / Copy the three files from the release ZIP into a dedicated folder of your choice:

- `R8EM.exe` — the main application
- `UpdaterHelper.exe` — handles automatic updates (must remain in the same folder)
- `R8_baseline.json` — the baseline hash database (must remain in the same folder)

> R8EM will create an `Enhancement Library` folder and a `BACKUPS` folder alongside itself the first time it runs.

### 2. Set your Run8 installation directory

On first launch, R8EM will prompt you that no Run8 directory is configured. Open **File → Settings** and click **Browse** to navigate to your Run8 V3 installation folder (the folder containing `Run-8 Train Simulator V3.exe` - typically C:\Run8Studios\Run8 Train Simulator V3).

Click **OK** to save. R8EM will use this path whenever it installs or reverts enhancements.

### 3. Download the DLC catalog (optional but recommended)

If you own any Run8 rolling stock DLC packs, open **File → Download DLC Catalog**. This downloads a catalog file that R8EM uses to distinguish between content you own and content you do not own during baseline comparisons.

After downloading, go back to **File → Settings** and check each DLC pack you own in the **Owned DLC Packs** list. Click **OK** to save.

---

## The Enhancement Library

R8EM manages enhancements from a folder called `Enhancement Library`, located in the same directory as `R8EM.exe`. This is where you store all your enhancement files.

**Organising your library:**

- You can place files directly in the `Enhancement Library` folder, or organise them into subfolders — R8EM scans recursively.
- ZIP archives are treated as a single enhancement entry in the list. R8EM will install all compatible files from the ZIP automatically.
- The library is never modified by install or revert operations — R8EM only reads from it. Your original enhancement files are always preserved.

**Adding enhancements to the library:**

Use **Enhancements → Add Enhancement(s)** (or drag files) to copy new enhancement files into the library. Alternatively, copy or move files directly into the `Enhancement Library` folder and then use **Enhancements → Refresh Library** to update the list.

---

## Suggested Workflow

### First-time setup if you already have enhancements downloaded

1. Complete the [Initial Setup](#initial-setup) steps above.
2. Copy your enhancement files (or ZIP archives) into the `Enhancement Library` folder.
3. Click **Enhancements → Refresh Library** (or restart R8EM) to populate the list.
4. R8EM will attempt to auto-detect the type of each enhancement. If a type was not detected, select the correct type from the dropdown in the **Type** column.
5. Select enhancements you want to install by checking the checkbox in the leftmost column.
6. Click **Install Selected** to apply them to your Run8 installation. R8EM backs up the original files automatically.

### Adding enhancements to your library 

1. Download enchancements from any of the various sources found online. They can be indvidual, or grouped within a zip file. 
2. In the Enhancements dropdown choose **Add Enhancement(s)...**
3. Select the file(s) you just downloaded and press "Open". Those enhancements will be **copied** to the _Enhancement Library_ directory within the R8EM installation directory.
4. (Optional) - Delete the original enhancements you just downloaded - an exact copy now lives within the _Enchancement Library_ directory.


### Day-to-day use

1. Launch R8EM.
2. If you have a profile you normally use, select it in the Profiles panel and click **Install Profile**.
3. Launch Run8 and enjoy your enhancements.
4. When finished, revert your changes by selecting enhancements and clicking **Revert Selected**, or by using **Enhancements → Revert All**.

### Previewing before installing

Before installing, you can preview texture and audio enhancements:

- Select one or more enhancements in the list and click **Preview**.
- For textures, a preview window opens showing the image. If multiple textures are selected (or a ZIP contains multiple textures), use the **left/right arrow keys** to navigate between them.
- For audio files, the file plays immediately in a small playback dialog.

### Deleting an enhancement from your library

If you no longer want an enhancement in R8EM:

1. Make sure it is not currently installed (revert it first if needed).
2. Check its checkbox to select it.
3. Click **Delete Selected** (or **Enhancements → Delete selected**).
4. Confirm the deletion. R8EM will remove the file from the `Enhancement Library` folder permanently.

---

## Working with Profiles

Profiles let you save a named collection of enhancements so you can install or revert the entire set in one step. This is useful when you want to switch between different sets of enhancements quickly — for example, a "screenshot session" set versus a "daily use" set.

### Creating a profile

1. Select the enhancements you want to include by checking their checkboxes.
2. Click **Create Profile from Selected** (or **Enhancements → Create Profile from selected**).
3. Give the profile a name and optionally a description. Click **OK**.

The new profile appears in the **Profiles** panel on the right side of the window.

### Installing a profile

1. Select the profile in the Profiles list.
2. Click **Install Profile** (or **Profiles → Install selected**).

R8EM will install every enhancement in the profile. The active profile is highlighted in green in the Profiles list, and its name is shown in the status bar at the bottom of the window.

> **Note:** If you manually install or revert individual enhancements while a profile is active, the profile name in the status bar will show an asterisk (`*`) to indicate the active profile's state has been modified.

### Reverting a profile

Reverting a profile restores all original game files that the profile had replaced. Select the active profile and click **Profiles → Install selected** again — R8EM will detect it is already active and offer to revert it — or revert individual enhancements using **Revert Selected**.

### Editing a profile

- **Edit** — opens the profile to add or remove individual enhancements from it.
- **Rename** — changes the profile's name.
- **Delete** — permanently removes the profile (does not uninstall enhancements).

### Creating a profile launcher

1. Select a currently configured profile in the profile list.
2. Choose **Create Launcher From Selected** in the Profiles menu.
3. R8EM will prompt you for a filename and location. It will then create a batch file with that name you can use to automatically switch to the selected profile and start Run8.


### Tips for profiles

- Profiles reference enhancements by their content hash, not by filename. Renaming an enhancement file in the library will not break an existing profile.
- A single enhancement can belong to multiple profiles.
- If an enhancement referenced by a profile is missing from the library, R8EM will warn you when you try to install that profile.
- The profile launcher can be used to configure different settings for different servers, settings, or eras. For example, "SoCal_Winter" could be used to install winter assets for the Southern California route, or "Eighties" to install 1980s repaints for use on an era specific play session.


---

## DLC Ownership Tracking

Run8 has a number of optional DLC rolling stock packs. If you do not own a particular pack, the corresponding model files will not be present in your installation, and baseline comparisons would incorrectly flag them as missing.

R8EM handles this by letting you declare which DLC packs you own:

1. Use **File → Download DLC Catalog** to download the catalog (requires an internet connection).
2. Open **File → Settings** and check each pack you own in the **Owned DLC Packs** list.
3. Click **OK**.

Once configured, baseline comparisons will categorise any absent files from unowned packs as **Not Owned** rather than **Missing**, keeping the results meaningful.

On startup, if the catalog is loaded and a Run8 directory is configured, R8EM will also scan your owned pack file lists against disk and warn you if expected files are absent.

---

## Baseline Comparison

The baseline comparison checks your current Run8 installation against the `R8_baseline.json` file (which represents a clean, unmodified installation). This is useful for:

- Verifying your installation is clean before applying enhancements.
- Identifying files that have been unexpectedly changed or are missing.
- Seeing which enhancements R8EM has currently installed.

To run a comparison, open **File → Compare to Baseline**. A progress dialog will appear while the scan runs. You can cancel at any time with the **Cancel** button.

Results are grouped into four categories:

| Category | Meaning |
|---|---|
| Modified files | Files that exist but differ from the baseline (enhancements are installed here) |
| Missing files | Files in the baseline that are absent from your installation |
| Extra files | Files in your installation that are not in the baseline |
| Not Owned files | Files absent because they belong to a DLC pack you do not own |

The results can be exported to a text file using the **Export** button in the results window.

---

## Reference — Menus and Buttons

### File menu

| Item | Action |
|---|---|
| Settings | Set your Run8 installation directory and owned DLC packs |
| Check for Updates | Check GitHub for a newer version of R8EM |
| About R8EM | Version information |
| Compare to Baseline | Scan your Run8 installation against the baseline |
| Download DLC Catalog | Download the latest DLC catalog from the R8EM releases page |
| Quit | Exit R8EM |

### Enhancements menu

| Item | Action |
|---|---|
| Add Enhancement(s) | Import new files into the Enhancement Library |
| Install selected | Install checked enhancements into Run8 |
| Revert selected | Restore original files for checked enhancements |
| Revert All | Restore all original files for every installed enhancement |
| Delete selected | Permanently delete checked enhancements from the library |
| Create Profile from selected | Save the checked enhancements as a named profile |
| Preview | Preview the selected texture or audio enhancement |
| Refresh Library | Re-scan the Enhancement Library folder |

### Profiles menu

| Item | Action |
|---|---|
| Install selected | Install the selected profile |
| Edit selected | Modify the enhancements in the selected profile |
| Rename selected | Rename the selected profile |
| Delete selected | Delete the selected profile |
| Create launcher | Create a desktop shortcut that launches Run8 with a specific profile active |

### Main buttons

| Button | Action |
|---|---|
| Install Selected | Install checked enhancements |
| Create Profile from Selected | Save checked enhancements as a profile |
| Revert Selected | Restore originals for checked enhancements |
| Delete Selected | Permanently delete checked enhancements from the library |
| Preview | Preview the selected texture or audio file |
