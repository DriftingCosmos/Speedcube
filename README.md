[README-github.md](https://github.com/user-attachments/files/33929172/README-github.md)
# SpeedCube

SpeedCube is a client for [Cube 2: Sauerbraten](http://sauerbraten.org) built for speedrunning. It adds a run timer, personal-best ghosts, splits, demos of your best runs, statistics, practice tools and offline **flagrun**, **race** and **campaign** timing, so you can practise and set times without a server. It is based on the vanilla 2020 Edition engine, and the network protocol is unchanged: it still connects to normal servers.

> **Status: early beta (Windows only).** Times are measured on your own computer and are not verified by a server. The campaign tools (demos, practice and door checkpoints) are new and still being tested, so expect rough edges.

## Features

### Run timer and speedometer
- Run timer that starts when you leave the flag base with the flag and stops when you score. Your time does not depend on your ping.
- Speedometer (horizontal or full 3D speed) and a stats panel with personal best, last run, top speed and finished runs.
- Move and resize everything with the mouse using `/hudedit`.

### Offline flagrun modes
- `/flagrun insta|effic|nw <map>`: instagib, efficiency or weaponless runs, without a server.
- Take either flag from either base. A run counts for the side of the flag you took it from.
- No spawn wait, no capture limit, no game clock. Edit mode is disabled in these modes.

### Race mode
- `/race <map>`: race on custom maps with a finish marker. Spawn with the pistol and a grenade; the timer runs from spawn to the finish.
- `/restart` loads the map again, for example after editing it.
- Optional race timer on servers (**speedcube settings** > run timer > "also time races").

### Campaign (singleplayer and DMSP)
- **Timer and statistics:** offline campaign maps get the same run timer, personal bests, run history and stats panel. The timer starts on your first spawn, keeps running through deaths (they are counted) and stops when the level ends: all monsters killed or the end trigger. In the DMSP modes a death reloads the map, which starts a new run. Edit mode turns the timed run off until `/restart`.
- **Mission statistics:** the **Campaign** menu has a statistics tab with every mission, its runs, time played and personal best.
- **Door splits:** every door or switch you open for the first time is a split, compared with the same one in your best run (green = ahead, red = behind, "new" = not in your best run). Doors that a switch opens are not counted again: the switch you pressed is the split. The last three splits are shown on screen. A run's splits are saved when it is a new personal best, or when the mission has no splits yet.
- **Ghost:** your best run is recorded as a ghost and races next to you, as in the other modes. The splits do not depend on the ghost.
- **Practice:** `/checkpoint` saves a snapshot of you, every monster, doors, platforms, crates, barrels and items. `/gocheckpoint` (and dying) puts everything back, `/practiceend` stops the section, and the level end also stops it. In DMSP maps dying takes you back to the checkpoint instead of reloading the map. Practice runs never count.
- **Door checkpoints:** every door you open in a run saves a full checkpoint. `/nextdoor`, `/prevdoor` and `/doorcheckpoint <n>` start a practice from one (F7 and F8 can be bound in the settings). The practice section ends at the next door and is compared with the same stretch of your best run. Practice runs never overwrite the checkpoints of a real run, and the manual `/checkpoint` still works.
- **Demos:** your best run is saved as a campaign demo with the monsters (`demo/campaign/`, about 1 MB for a long level). Watch it from **Campaign** > **watch your best runs..** or with `/watchcampdemo <map>`. Everything is recorded: your shots with their effects, ammo, armour, every sound (including the ones around you), doors and triggers, platforms, crates and barrels, picked up items and the monsters including their shots. The demo timer shows the time of the run.

### Ghosts, splits and demos (flagrun and race)
- Your personal best is recorded as a ghost, one per mode, map and flag side. It runs next to you on your next try.
- Automatic splits and a live difference to your best run (needs a ghost).
- Your best run of each map and mode is saved as a demo in `demo/flagrun/<map>/<mode>/` or `demo/race/<map>/`. Normal online demos stay in the main `demo` folder (use `/savedemo` after a game).
- When you watch a flagrun or race demo, the timer shows the time of the run itself (0:00 when the run starts, your final time at the finish), not the time since the recording began.
- By default only your best run of each map and mode keeps its demo. Turn on **save the demo of every run** in speedcube settings > run timer to keep all of them (flagrun, race and campaign); the statistics watch button still plays the personal best.
- Demo controls: **P** pause, **R** restart, **left/right** rewind and forward, **Backspace** stop.
- Your best runs also record every frame's inputs next to the ghost (for run verification later).

### Practice checkpoints (flagrun and race)
- `/checkpoint` makes your spot your spawn and starts a practice timer from it. `/gocheckpoint` returns, `/clearcheckpoint` removes it. F5 and F6 can be bound to these in the settings.
- Flagruns: the practice timer stops when you pick up any flag. Race: it stops at the finish. Practice runs never count.

### Visuals
- **Shot trails:** choose the colour of the smoke and streak trails of your own shots (shotgun, chaingun, rocket launcher, rifle, grenade launcher, pistol) in speedcube settings.
- **3D stats boards:** a read-only board floats beside each flag base in flagruns. Move it with the sliders or `/runboardhere` (one position per flag side).

### Statistics
- Statistics pages for flagruns, race and campaign: maps, runs finished, time played and deaths.
- Map statistics page with your best times, average and a "watch best demo" button.

### Server browser
- Click a server to preview its players before you join. Switch it off with `/serverpreview 0`.
- Favorite servers in your own named tabs (rename, add and delete tabs).

### Fair play
- Times only count on the original, unedited map. The first time a flagrun or race map is used, its checksum is stored; if the map file changes later, timed runs are off. Practice still works.

## Install (Windows)
1. Install **Cube 2: Sauerbraten** (2020 Edition) from [sauerbraten.org](http://sauerbraten.org).
2. Download the SpeedCube zip from the [releases](../../releases) and unzip it over your Sauerbraten folder. It adds `bin64/speedcube.exe`, `data/menus.cfg`, `data/speedcube/` and `speedcube.bat`.
3. Start the game with `speedcube.bat`.

Your settings, ghosts, demos and statistics are saved in `Documents\My Games\Sauerbraten`.

## Commands
Type `/speedcube` in the game for the list that fits your current mode. The most used ones:

| Command | What it does |
|---|---|
| `/flagrun insta\|effic\|nw <map>` | start an offline flagrun |
| `/race <map>` | start an offline race |
| `/restart` | load the current map again |
| `/checkpoint`, `/gocheckpoint`, `/clearcheckpoint` | practice checkpoint |
| `/practiceend` | end the current practice section |
| `/nextdoor`, `/prevdoor`, `/doorcheckpoint <n>` | campaign: practise from a door |
| `/watchrundemo <map>` | watch your best flagrun or race of a map |
| `/watchcampdemo <map>` | watch your best campaign run of a map |
| `/campstat runs\|deaths\|play\|pb <map>` | campaign statistics of a map |
| `/runboardhere` | move the 3D board to where you look |
| `/hudedit` | move and resize the timer, speedometer and stats panel |
| `/resetrun` | throw away the current run |
| `/raceinfo` | explains why a race timer is (not) running |
| `/serverpreview 0\|1` | player preview in the server browser |

## Settings
Main menu > **Settings** (or Esc > speedcube settings): run timer, ghost and splits, shot trails, 3D board, speedometer and HUD layout.

## Building from source
Windows: open `src\vcpp\sauerbraten.sln` in Visual Studio (Desktop development with C++), choose **Release x64** and build. Copy the result to `bin64\speedcube.exe`.
Linux: install the SDL2 development packages, then run `make clean && make -j4 install` in `src`. The Linux and Mac builds have not been tested yet.

## Plans
- Campaign fairness rules: slow motion marked separately, a personal best per skill level, a map checksum, and separate "exit" and "all monsters" categories.
- Gold splits and a sum of best segments.
- Savestates that include projectiles in flight, and for flagruns and races.
- A per-mission statistics page with run history.
- Linux and Mac support.

## Credits and licence
SpeedCube is a modified version of Cube 2: Sauerbraten by Wouter van Oortmerssen, Lee Salzman, Mike Dysart and others, released under the zlib licence. It is not the original game. The idea of the flagrun and race modes comes from the flagrun and Speedyruns servers.
