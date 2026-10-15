# SpeedCube

SpeedCube is a client for [Cube 2: Sauerbraten](http://sauerbraten.org) built for speedrunning. It adds a run timer, personal-best ghosts, splits, demos of your best runs, statistics, and offline **flagrun** and **race** modes, so you can practise and set times without a server. It is based on the vanilla 2020 Edition engine, and the network protocol is unchanged: it still connects to normal servers.

> **Status: early beta (Windows only).** Times are measured on your own computer and are not verified by a server.

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

### Ghosts, splits and demos
- Your personal best is recorded as a ghost, one per mode, map and flag side. It runs next to you on your next try.
- Automatic splits and a live difference to your best run (needs a ghost).
- Your best run of each map and mode is saved as a demo in `demo/flagrun/<map>/<mode>/` or `demo/race/<map>/`. Normal online demos stay in the main `demo` folder (use `/savedemo` after a game).
- Demo controls: **P** pause, **R** restart, **left/right** rewind and forward, **Backspace** stop.
- Your best runs also record every frame's inputs next to the ghost (for run verification later).

### Practice checkpoints
- `/checkpoint` makes your spot your spawn and starts a practice timer from it. `/gocheckpoint` returns, `/clearcheckpoint` removes it. F5 and F6 can be bound to these in the settings.
- Flagruns: the practice timer stops when you pick up any flag. Race: it stops at the finish. Practice runs never count.

### Statistics and 3D board
- Statistics pages for flagruns and race: maps, runs finished, time played and deaths.
- A read-only 3D stats board floats beside each flag base in flagruns. Move it with the sliders or `/runboardhere` (one position per flag side).
- Map statistics page with your best times, average and a "watch best demo" button.

### Server browser
- Click a server to preview its players before you join.
- Favorite servers in your own named tabs (rename, add and delete tabs).

### Fair play
- Times only count on the original, unedited map. The first time a flagrun or race map is used, its checksum is stored; if the map file changes later, timed runs are off. Practice still works.

## Install (Windows)
1. Install **Cube 2: Sauerbraten** (2020 Edition) from [sauerbraten.org](http://sauerbraten.org).
2. Download the SpeedCube zip and unzip it over your Sauerbraten folder. It adds `bin64/speedcube.exe`, `data/menus.cfg`, `data/speedcube/` and `speedcube.bat`.
3. Start the game with `speedcube.bat`.

Your settings, ghosts, demos and statistics are saved in `Documents\My Games\Sauerbraten`.

## Commands
Type `/speedcube` in the game for the list that fits your current mode. The most used ones:

| Command | What it does |
|---|---|
| `/flagrun insta|effic|nw <map>` | start an offline flagrun |
| `/race <map>` | start an offline race |
| `/restart` | load the current map again |
| `/checkpoint`, `/gocheckpoint`, `/clearcheckpoint` | practice checkpoint |
| `/runboardhere` | move the 3D board to where you look |
| `/hudedit` | move and resize the timer, speedometer and stats panel |
| `/resetrun` | throw away the current run |
| `/raceinfo` | explains why a race timer is (not) running |
| `/watchrundemo <map>` | watch your best run of a map |

## Settings
Main menu > **Settings** (or Esc > speedcube settings): run timer, ghost and splits, 3D board, speedometer and HUD layout.

## Building from source
Windows: open `src\vcpp\sauerbraten.sln` in Visual Studio (Desktop development with C++), choose **Release x64** and build. Copy the result to `bin64\speedcube.exe`.
Linux: install the SDL2 development packages, then run `make clean && make -j4 install` in `src`. The Linux and Mac builds have not been tested yet.

## Credits and licence
SpeedCube is a modified version of Cube 2: Sauerbraten by Wouter van Oortmerssen, Lee Salzman, Mike Dysart and others, released under the zlib licence. It is not the original game. The idea of the flagrun and race modes comes from the flagrun and Speedyruns servers.
