# Mudlet Scripts for Aardwolf

A collection of Mudlet add-ons and scripts for Aardwolf MUD, distributed as native Mudlet packages (`.mpackage`).

---

## Key Highlights

> [!NOTE]
> **Download anywhere, install from anywhere!**
> You can download the package files (`.mpackage`) to **any folder on your computer** (such as your `Downloads` folder or Desktop). There is **no need** to move the files into your Mudlet directory or a special folder before installing.
> - If you download individual `.mpackage` files directly, you do **not** need to extract them; Mudlet handles package installation automatically.
> - If you downloaded the repository archive via GitHub's **`Code` > `Download ZIP`**, **unzip / extract** that ZIP archive first on your computer to access all individual `.mpackage` files inside. Do **not** import the repository ZIP file itself into Mudlet.

> [!IMPORTANT]
> **Your Mudlet profile does not have to be named `Aardwolf`.**
> All scripts use `getMudletHomeDir()` to load and save data from whichever Mudlet profile is currently active. Your settings, character configurations, and databases are safely preserved under `<profile>/persistence/` and are not deleted or overwritten when updating packages.

---

## Installation

### Step 1: Download the Packages

You can obtain the packages in either of two ways:

- **GitHub ZIP (`Code` > `Download ZIP`):** Download the repository archive and **unzip / extract** it to a folder on your computer. All individual `.mpackage` files will be inside the extracted folder ready for you to pick and install.
- **Direct Download:** Download only the specific `.mpackage` files you want from the repository file list or the links below to anywhere on your computer (such as your `Downloads` folder or Desktop).

> [!IMPORTANT]
> **Do not import the repository ZIP archive into Mudlet.** Mudlet cannot install the repository ZIP as a single package.
> You must **unzip** the downloaded archive first, then choose only the individual `.mpackage` files you want to install. Do **not** unzip the `.mpackage` files themselves — Mudlet installs `.mpackage` files directly.

---

### Step 2: Install into Mudlet

Open Mudlet and connect to your Aardwolf character/profile (so your main game terminal window is open and active). Then install each package using either method below:

#### Option A: Package Manager (Recommended)

1. In Mudlet, open the **Package Manager**:
   - Press `Alt+O`, or
   - Click **Toolbox** > **Package Manager** from the menu.
2. Click **Install** (or **Install New Package**).
3. Navigate to wherever you downloaded the package files (e.g., your `Downloads` folder).
4. Select the `.mpackage` file and click **Open** to install. Repeat for each package you wish to use.
5. Save your Mudlet profile.

#### Option B: Drag and Drop (Fresh Installations)

> [!NOTE]
> Drag and drop is best suited for fresh, first-time installations. If you already have an older version of a package installed, Mudlet will not overwrite it via drag-and-drop — you must first uninstall the old package in **Package Manager** (`Alt+O`) or use **MCheck** to update automatically.

1. Make sure your active Mudlet game window is visible on screen.
2. Open your file browser to where you downloaded the `.mpackage` files.
3. Drag and drop the `.mpackage` file directly onto the open Mudlet window.

---

## Keeping Add-ons Updated

Updating is safe because package updates never touch or overwrite your personal profile settings and history stored in `<profile>/persistence/`:

### Via MCheck (Recommended — Fully Automated)

All packages in this repository are tracked in the central index. If you have [MCheck](https://raw.githubusercontent.com/Noobgonewild/Mudlet-scripts/main/mcheck.mpackage) installed:

> [!NOTE]
> MCheck scans and updates add-ons that are **already installed** in your active profile. It cannot perform a first-time installation of an uninstalled add-on. Once you have installed your desired packages once via Option A or B above, MCheck manages future updates seamlessly:

```text
mcheck scan
mcheck update <number>
```

MCheck automatically retrieves the latest verified `.mpackage` from the repository, validates its SHA-256 checksum, and performs the uninstall/reinstall cycle without manual intervention.

### Via Package Manager (Manual Update)

Because Mudlet will not overwrite an already installed package via drag-and-drop or direct re-installation, you must remove the older package first:

1. Download the updated `.mpackage` file.
2. In Mudlet, open the **Package Manager** (`Alt+O`).
3. Select the package you want to update and click **Uninstall**.
   *(Note: Uninstalling a package only removes its scripts/triggers; your settings, history, and databases in `<profile>/persistence/` remain completely intact).*
4. Click **Install** (or drag and drop the new file onto the Mudlet window) to install the updated version.
5. Save your profile or reload if needed.

---

## Before Choosing Packages

Some packages have dependencies or important safety notes:

- **DINV required:** `g_Brandish.mpackage`, `g_envenom.mpackage`, `g_shinykeep.mpackage`, and `m_enchanter.mpackage` use the [Mudlet-DINV](https://github.com/Noobgonewild/Mudlet-DINV) API. Install and initialize DINV first.
- **DINV optional:** `Hadar_Spellup_Caster.mpackage` works standalone, but its automatic aura integration uses DINV when available.
- **S&D database required:** `mobsearch.mpackage` reads `SnDdb.db` directly from the active Mudlet profile directory. If [Search & Destroy](https://github.com/Noobgonewild/Mapper-and-S-D) is installed, run `snd db` to verify the resolved database path.
- **MMapper optional for navigation:** Mob searches work without MMapper, but `mgo <row>` calls `mapper goto <room-id>` if [MMapper](https://github.com/Noobgonewild/Mapper-and-S-D) is installed.
- **Optional market prices:** Fantasy Cards and Archaeology look for `persistence/mmarket.db` for price information; their other features work completely without it.
- **Destructive command warning:** `kdedup` keeps one copy of each key, then unkeeps and destroys duplicate copies. Read `kdedup help` before running it.
- **Card and inventory integration:** `g_winds.mpackage` card duplicate checking uses `lft` (from `g_Fantasy_Cards_Mudlet`) and DINV when available.

---

## Available Packages

### Character, Equipment, and Combat

| Package | What it does | Start / Help command |
| :--- | :--- | :--- |
| `Bypass_Mudlet.mpackage` | Applies configured skill bypasses automatically after level changes. | `bypass apply` |
| `g_autotrain.mpackage` | Plans and performs weighted stat training using character class and subclass. | `autotrain help` |
| `g_Brandish.mpackage` | Uses DINV to manage and brandish charge-safe staves automatically. Disabled until configured. | `gbr help` |
| `g_character.mpackage` | Geyser character-stats window and configurable status bars with mastery, instinct, and resistance reporting. | `gstats help` or `gchar config` |
| `g_envenom.mpackage` | Uses DINV to maintain venom on owned or borrowed weapons and restore equipment safely. | `genv help` |
| `g_group_monitor.mpackage` | Draggable GMCP group monitor with invites, filters, and health alerts. | `gmon help` |
| `g_shinykeep.mpackage` | Uses DINV events to keep newly tracked shiny items for selected tiers. | `shinykeep help` |
| `Hadar_Spellup_Caster.mpackage` | Spellup caster with spellup, aura, visibility, and landing helpers. | `had help` (`hsp`/`hsu` to cast) |
| `m_enchanter.mpackage` | DINV-backed enchanting analyzer and command helper, including guarded batch enchanting. | `eqa help` and `eqb help` |
| `m_Loqui practice.mpackage` | Loqui Practice helper for selecting and practicing skills by class, priority, exclusions, and limits. | `lph help` |
| `msleep.mpackage` | Sleeps shortly before a tick when vitals are low, then wakes; optional camp, fire, and PK-room behavior. | `ts help` |

### Navigation and Hunting

### Navigation and Hunting

| Package | What it does | Start / Help command |
| :--- | :--- | :--- |
| `g_areapicker.mpackage` | Lists areas appropriate for your current level, with alignment and offset controls. | `lvl help` (`lvl` to list) |
| `g_maze solver.mpackage` | In-memory maze exploration helper driven by room GMCP. | `#maze_help` |
| `g_winds.mpackage` | Winds of Fate epic helper: obelisk side tracking, pedestal step sequence, group command broadcasting, cooldown reporting, and card dupe lookups. | `winds help` (`winds`, `reportsides`, `cmd`) |
| `mobsearch.mpackage` | Searches mobs and rooms in S&D's `SnDdb.db`, reports results, and can hand a room to MMapper. | `msearch help` |

### Communication and Reminders

| Package | What it does | Start / Help command |
| :--- | :--- | :--- |
| `g_channels.mpackage` | Multi-tab communications window with history, search, timestamps, gags, and a `gchan` output channel. | `gcom help` |
| `g_rainbow_chat.mpackage` | Adds configurable color gradients to outgoing Aardwolf tells and channels. | `rainbow help` |
| `g_RemindMe.mpackage` | Threshold reminders for level, remort, tier, quest points, trivia points, trains, practices, and gold. | `remindme help` |

### Collections, Tracking, and Utilities

| Package | What it does | Start / Help command |
| :--- | :--- | :--- |
| `g_Fantasy_Cards_Mudlet.mpackage` | Tracks Fantasy Card sets, owned and missing cards, scans, summaries, and optional market costs. | `lft help` |
| `g_keydedup.mpackage` | Consolidates duplicate keys onto the keyring and destroys extra copies. | `kdedup help` |
| `m_aarchaeology.mpackage` | Tracks archaeology collections, bags, reports, sounds, and optional market costs. | `arch help` |
| `m_dulltracker.mpackage` | Tracks sessions, activity timers, XP, gold, combat, areas, milestones, and analytics in SQLite. | `dull help` |
| `mcheck.mpackage` | Central update manager for keeping installed add-ons synchronized with the repository. | `mcheck` |

---

## Troubleshooting

### Mudlet says the command is unknown
- Press **Alt+O** and confirm the individual package appears in the list of installed packages.
- Ensure you installed it while the intended profile was active. Packages installed in one profile do not automatically transfer to another.
- If updating an existing package, make sure to uninstall the older version in **Package Manager** before installing the new file.

### A package cannot find DINV
Install and initialize [DINV](https://github.com/Noobgonewild/Mudlet-DINV) first, reconnect if needed, and confirm DINV is ready before using Brandish, Envenom, ShinyKeep, or Enchanter.

### MobSearcher cannot open its database
Run `snd db` to confirm that Search & Destroy has opened a valid `SnDdb.db` directly inside your Mudlet profile directory (`lua openMudletHomeDir()`). MobSearcher looks specifically for `SnDdb.db`.

### Settings or history seem to be missing
Verify that you opened the correct Mudlet profile. Most packages save data under `<profile>/persistence/` (e.g., `dull_tracker.db`), while MobSearcher reads `SnDdb.db` from the profile root.

### Optional sounds do not play
Packages with sound support look under the active profile's `sounds` directory (`<profile>/sounds/`).

---

## Feature gallery

### Enchanter

DINV-backed item analysis and enchanting guidance. Enchanter also provides guarded batch planning and execution.

<p align="center">
  <img width="100%" alt="Enchanter analysis and recommendations" src="https://github.com/user-attachments/assets/74170d9e-7fbb-4f66-9584-39034a5bd608" />
</p>
<p align="center">
  <img width="78%" alt="Enchanter item details" src="https://github.com/user-attachments/assets/cf9a6079-8927-4b23-929f-45f71875fb76" />
</p>

### MobSearcher

Search the current S&D mob database, inspect likely rooms, report a result, or send its room ID to MMapper.

<p align="center">
  <img width="100%" alt="MobSearcher results" src="https://github.com/user-attachments/assets/b5abcab2-6e59-41c4-8604-07f52409fb7e" />
</p>

### Area Picker

Type `lvl` to show areas in the configured level range.

<p align="center">
  <img width="90%" alt="Area Picker level-range results" src="https://github.com/user-attachments/assets/643cce79-10cb-4005-ac4f-1a9f285f9bed" />
</p>

### AutoTrainer

Weighted training plans based on the current character's class and stats.

<p align="center">
  <img width="65%" alt="AutoTrainer configuration and plan" src="https://github.com/user-attachments/assets/5e97cbe1-1a65-4e07-a657-b6c9a5ae8fe7" />
</p>

### Channels

Multi-tab communication history, search, timestamps, gags, and the `gchan` pseudo-channel used by other packages.

<p align="center">
  <img width="55%" alt="Channels communications window" src="https://github.com/user-attachments/assets/640afd5d-2120-465f-a69f-62d97b6e9475" />
</p>
<p align="center">
  <img width="62%" alt="GCHAN output" src="https://github.com/user-attachments/assets/a8a42edd-74d5-44e7-ba75-1d46395b403c" />
  <img width="34%" alt="GCHAN configuration" src="https://github.com/user-attachments/assets/4975ddfb-e27c-4985-9295-7d62c0b533f2" />
</p>

### KeyDedup

Review the warning and command help before allowing it to destroy duplicate key copies.

<p align="center">
  <img width="45%" alt="KeyDedup results" src="https://github.com/user-attachments/assets/ded1082d-5eae-4cd7-b2a8-0cf0df2ec0b3" />
</p>

### Character window and status bars

The character package supports compact or detailed layouts, vertical or horizontal displays, and clickable configuration.

<p align="center">
  <img width="24%" alt="Vertical character statistics" src="https://github.com/user-attachments/assets/09ad7879-19a6-469d-ad37-4f5b6877ceb8" />
  <img width="46%" alt="Character window configuration" src="https://github.com/user-attachments/assets/cfd1a3b8-9ebe-4c54-813f-f16c011c5fa7" />
  <img width="22%" alt="Compact vertical character bars" src="https://github.com/user-attachments/assets/772a4743-1811-4010-908b-a1f2aa40ceaa" />
</p>
<p align="center">
  <img width="62%" alt="Wide horizontal character status bars" src="https://github.com/user-attachments/assets/3cf147f2-476a-4d23-b511-b14d86ae5fa0" />
</p>
<p align="center">
  <img width="34%" alt="Compact character status bar layout one" src="https://github.com/user-attachments/assets/a2d1ab2a-aafa-428d-97bf-f485a3e10a00" />
  <img width="34%" alt="Compact character status bar layout two" src="https://github.com/user-attachments/assets/c96b3bc6-eb73-4e29-8b45-d3b060633237" />
  <img width="19%" alt="Narrow vertical character status bars" src="https://github.com/user-attachments/assets/ff8ac538-597f-4b5f-a1be-71dc1f1ae59b" />
</p>

### RemindMe

Configurable reminders when character resources or progression values cross a threshold.

<p align="center">
  <img width="40%" alt="RemindMe notification" src="https://github.com/user-attachments/assets/02a2de6f-652d-4457-b8ca-cc2b4baec017" />
</p>

### Group Monitor

Several compact layouts for tracking group members, health, status, and alerts.

<p align="center">
  <img width="24%" alt="Group Monitor layout one" src="https://github.com/user-attachments/assets/853e7a79-00f7-4a57-ac07-4da5c432799b" />
  <img width="24%" alt="Group Monitor layout two" src="https://github.com/user-attachments/assets/5fa27f9d-d507-47d6-9516-0d7f0c3072d0" />
  <img width="24%" alt="Group Monitor layout three" src="https://github.com/user-attachments/assets/760b9ace-7b5a-4208-ae9c-bb3593781b87" />
  <img width="24%" alt="Group Monitor layout four" src="https://github.com/user-attachments/assets/353cbd37-fe21-4d32-9821-9ffc32b8fccc" />
</p>

### Plugin Updater (Mcheck)

Tool to check for available updates. It searches for DINV/mmapper/SnD and scripts in this repository.

<p align="center">
  <img width="1149" height="403" alt="Mcheck addon updater" src="https://github.com/user-attachments/assets/5cc7b251-c82e-4d31-a455-29eddb9f9081" />
  <img width="784" height="665" alt="Mcheck addon updater" src="https://github.com/user-attachments/assets/712c715a-b9f2-42a9-9277-8e24354f41b8" />

</p>
---

## Useful Links

- [Mudlet Package Manager manual](https://wiki.mudlet.org/w/Manual:Package_Manager)
- [Mudlet file locations](https://wiki.mudlet.org/w/Mudlet_File_Locations)
- [DINV Repository](https://github.com/Noobgonewild/Mudlet-DINV)
- [MMapper and S&D Repository](https://github.com/Noobgonewild/Mapper-and-S-D)
- [MCheck Addon Index](https://raw.githubusercontent.com/Noobgonewild/Mudlet-scripts/main/mcheck-index.json)

These are community packages and may contain bugs. Review each package's in-game help before enabling automation that sends commands or changes inventory.
