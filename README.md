# Aardwolf Mudlet Scripts

A collection of optional Mudlet XML packages for [Aardwolf MUD](https://www.aardwolf.com/). Install only the packages you want.

> [!IMPORTANT]
> **Your Mudlet profile does not have to be named `Aardwolf`.** The packages use the profile that is open when you install them, and saved data is resolved from that profile's home directory.
>
> **`scripts` is only the recommended folder name.** You may call the folder anything you like, and the XML files can technically be installed from anywhere. Moving an XML file into that folder does **not** install it—you must also install it through Mudlet's Package Manager.

## Quick installation

1. On this repository's GitHub page, choose **Code → Download ZIP**, then extract the ZIP.
2. Open the Aardwolf profile in Mudlet where you want the packages installed.
3. In Mudlet's command line, enter this to open the active profile directory directly in your system's file browser:

   ```text
   lua openMudletHomeDir()
   ```

   To print the exact path in Mudlet as well, enter:

   ```text
   lua echo(getMudletHomeDir() .. "\n")
   ```

4. Inside the profile directory that opened, create a folder named `scripts` if it does not already exist.
5. Copy only the `.xml` packages you want from the extracted repository into that folder.
6. Press **Alt+O** in Mudlet to open **Package Manager**.
7. Select **Install New Package**, browse to the XML file, and install it. Repeat for each package you chose.
8. Run the package's help command from the tables below.

Do not install the repository ZIP as one package. Each XML file is a separate Mudlet package.

### Recommended profile layout

```text
<your Mudlet profile>/
├── scripts/                 downloaded XML installers; folder name is optional
│   ├── g_areapicker.xml
│   ├── g_character.xml
│   └── ...
├── persistence/             settings and databases created by the packages
├── sounds/                  optional sound files used by some packages
└── SnDdb.db                 required here only by mobsearch.xml
```

The package code is stored in the Mudlet profile after installation. Keeping the downloaded XML files under `scripts` simply makes future updates easier to find.

## Before choosing packages

Some packages have dependencies or important safety notes:

- **DINV required:** `g_Brandish.xml`, `g_envenom.xml`, `g_shinykeep.xml`, and `m_enchanter.xml` use the [Mudlet-DINV](https://github.com/Noobgonewild/Mudlet-DINV) API. Install and initialize DINV first.
- **DINV optional:** `Hadar_Spellup_Caster.xml` works without DINV, but its automatic aura integration uses DINV when available.
- **S&D database required:** `mobsearch.xml` reads `SnDdb.db` directly from the active Mudlet profile directory. It does **not** use the old `Aardwolf.db` filename. If S&D is installed, run `snd db` to see the required and resolved database path.
- **MMapper optional for navigation:** mob searches work without MMapper, but `mgo <row>` calls `mapper goto <room-id>`.
- **Optional market prices:** Fantasy Cards and Archaeology look for `persistence/mmarket.db` for price information. That database is normally supplied by mbot, which is not included in this repository; the packages' other features still work without it.
- **Deprecated:** `g_globalCampaignAnnouncer DEPRECATED (included in SnD).xml` is already included in S&D. Do not install it when you use S&D.
- **Destructive command:** `kdedup` keeps one copy of each key, then unkeeps and destroys the duplicates. Read `kdedup help` before running it.

## Packages in this repository

### Character, equipment, and combat

| File | What it does | Start/help command |
| --- | --- | --- |
| `Bypass_Mudlet.xml` | Applies the configured skill bypasses after level changes. | `bypass apply` |
| `g_autotrain.xml` | Plans and performs weighted stat training using the character's class and subclass. | `autotrain help` |
| `g_Brandish.xml` | Uses DINV to manage and brandish charge-safe staves automatically. Disabled until configured. | `gbr help` |
| `g_character.xml` | Geyser character-stats window and configurable status bars, with mastery, instinct, and resistance reporting. | `gstats help` or `gchar config` |
| `g_envenom.xml` | Uses DINV to maintain venom on owned or borrowed weapons and restore equipment safely. | `genv help` |
| `g_group_monitor.xml` | Draggable GMCP group monitor with invites, filters, and health alerts. | `gmon help` |
| `g_shinykeep.xml` | Uses DINV changes to keep newly tracked shiny items for selected tiers. | `shinykeep help` |
| `Hadar_Spellup_Caster.xml` | Spellup caster with spellup, aura, visibility, and landing helpers. | `had help` (`hsp`/`hsu` to cast) |
| `m_enchanter.xml` | Current DINV-backed enchanting analyzer and command helper, including guarded batch enchanting. | `eqa help` and `eqb help` |
| `m_Loqui practice.xml` | Loqui Practice helper for selecting and practicing skills by class, priority, exclusions, and limits. | `lph help` |
| `msleep.xml` | Sleeps shortly before a tick when vitals are low, then wakes; optional camp, fire, and PK-room behavior. | `ts help` |

### Navigation and hunting

| File | What it does | Start/help command |
| --- | --- | --- |
| `g_areapicker.xml` | Lists areas appropriate for the current level, with offset and alignment controls. | `lvl help` (`lvl` to list) |
| `g_maze solver.xml` | In-memory maze exploration helper driven by room GMCP. | `#maze_help` |
| `mobsearch.xml` | Searches mobs and rooms in S&D's `SnDdb.db`, reports results, and can hand a room to MMapper. | `msearch help` |

### Communication and reminders

| File | What it does | Start/help command |
| --- | --- | --- |
| `g_channels.xml` | Multi-tab communications window with history, search, timestamps, gags, and a fake `gchan` output channel for other packages. | `gcom help` |
| `g_globalCampaignAnnouncer DEPRECATED (included in SnD).xml` | Legacy Global Campaign warning/announcement package. Its functionality is included in S&D. | `gqwarn help` |
| `g_rainbow_chat.xml` | Adds configurable color gradients to outgoing Aardwolf tells and channels. | `rainbow help` |
| `g_RemindMe.xml` | Threshold reminders for level, remort, tier, quest points, trivia points, trains, practices, and gold. | `remindme help` |

### Collections, tracking, and utilities

| File | What it does | Start/help command |
| --- | --- | --- |
| `g_Fantasy_Cards_Mudlet.xml` | Tracks Fantasy Card sets, owned and missing cards, scans, summaries, and optional market costs. | `lft help` |
| `g_keydedup.xml` | Consolidates duplicate keys onto the keyring and destroys the extra copies. | `kdedup help` |
| `m_aarchaeology.xml` | Tracks archaeology collections, bags, reports, sounds, and optional market costs. | `arch help` |
| `m_dulltracker.xml` | Tracks sessions, activity timers, XP, gold, combat, areas, milestones, and historical analytics in SQLite. | `dull help` |

## Updating or removing a package

To update a package:

1. Download the new XML.
2. Open **Package Manager** with **Alt+O** in the same Mudlet profile.
3. Uninstall the old copy of that package.
4. Install the new XML.

Package settings and history are generally stored under the profile's `persistence` directory and are not removed just because the XML package is uninstalled. Do not delete that directory when you only want to update a package.

To remove a package permanently, uninstall it in Package Manager. Delete its saved data only if you also want to reset or discard that package's settings and history.

## Troubleshooting

### Mudlet says the command is unknown

- Press **Alt+O** and confirm the individual XML appears as an installed package.
- Make sure you installed it while the intended profile was open. Packages installed in one profile do not automatically appear in another.
- Copying an XML into `scripts` is not enough; install it through Package Manager.
- If you installed an older copy, uninstall it before installing the current XML.

### A package cannot find DINV

Install DINV first, reconnect if needed, and confirm DINV is ready before using Brandish, Envenom, ShinyKeep, or Enchanter.

### MobSearcher cannot open its database

Run:

```text
snd db
```

S&D should report a found, healthy `SnDdb.db` whose resolved path is directly inside the same profile directory printed by `getMudletHomeDir()`. Do not put `SnDdb.db` inside `scripts` or `persistence`, and do not use the old `Aardwolf.db` file—the current MobSearcher looks only for `SnDdb.db`.

### Settings or history seem to be missing

Verify that you opened the same Mudlet profile as before. Most packages save under that profile's `persistence` directory; DullTracker creates `persistence/dull_tracker.db`, while MobSearcher reads S&D's separate `SnDdb.db` from the profile root.

### Optional sounds do not play

Packages with sound support look under the active profile's `sounds` directory. Use that exact directory under the profile reported by `getMudletHomeDir()`.

## Feature gallery

### Enchanter

DINV-backed item analysis and enchanting guidance. The full `m_enchanter.xml` also provides guarded batch planning and execution.

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

## Useful links

- [Mudlet Package Manager manual](https://wiki.mudlet.org/w/Manual:Package_Manager)
- [Mudlet file locations](https://wiki.mudlet.org/w/Mudlet_File_Locations)
- [DINV](https://github.com/Noobgonewild/Mudlet-DINV)
- [MMapper and S&D](https://github.com/Noobgonewild/Mapper-and-S-D)

These are community packages and may contain bugs. Review each package's in-game help before enabling automation that sends commands or changes inventory.
