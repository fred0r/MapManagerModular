<h1 align="center">
  <a href="https://github.com/Mistrick/MapManagerModular"><img src="https://user-images.githubusercontent.com/18553678/128012021-a57c9845-d029-419e-9006-fa43ffff188a.png" width="500px" alt="Map Manager Modular"></a>
</h1>

<p align="center">Modular map management system with rich features.</p>

<p align="center">
    <a href="https://github.com/Mistrick/MapManagerModular/releases/latest">
    <img src="https://img.shields.io/github/downloads/Mistrick/MapManagerModular/total?label=Download%40latest&style=flat-square&logo=github&logoColor=white"
         alt="Build status">
    <a href="https://github.com/Mistrick/MapManagerModular/actions">
    <img src="https://img.shields.io/github/workflow/status/Mistrick/MapManagerModular/CI/master?style=flat-square&logo=github&logoColor=white"
         alt="Build status">
    <a href="https://github.com/Mistrick/MapManagerModular/releases">
    <img src="https://img.shields.io/github/v/release/Mistrick/MapManagerModular?include_prereleases&style=flat-square&logo=github&logoColor=white"
         alt="Release">
    <a href="https://www.amxmodx.org/downloads-new.php">
    <img src="https://img.shields.io/badge/AMXModX-%3E%3D1.9.0-blue?style=flat-square"
         alt="AMXModX dependency">
</p>
      
<p align="center">
  <a href="#about">About</a> •
  <a href="#requirements">Requirements</a> •
  <a href="#installation">Installation</a> •
  <a href="#updating">Updating</a> •
  <a href="#downloads">Downloads</a> •
  <a href="#features">Features</a> •
  <a href="#wiki">Wiki</a>
</p>

---

## About
- TODO

## Requirements
- HLDS installed;
- Installed AMXModX ([`v1.9`](https://www.amxmodx.org/downloads-new.php) or [`v1.10`](https://www.amxmodx.org/downloads-new.php?branch=master));
      
## Installation
- [Download the latest](https://github.com/Mistrick/MapManagerModular/releases/latest) stable version from the release section.
- Extract the `cstrike` folder to the root folder of the HLDS server;
- Make sure that all plugins are running and in the correct order, using the `amxx list` command.

## Updating
- Put new plugins and lang-files (`plugins/*.amxx` & `data/lang/*.txt`) into `amxmodx/` folder on the HLDS server;
- Restart the server (command `restart` or change the map);
- Make sure that the versions of the plugins are up to date with the command `amxx list`.

## Downloads
- [Release builds](https://github.com/Mistrick/MapManagerModular/releases)
- [Dev builds](https://github.com/Mistrick/MapManagerModular/actions/workflows/CI.yml)
      
## Features
- TODO

## Wiki
Do you **need some help**? Check the _articles_ from the [wiki](https://github.com/Mistrick/MapManagerModular/wiki).

---

## fred0r fork changes

### Nomination plugin
- **Recent maps display** (`say recentmaps`) — shows currently blocked recent maps from the blocklist, ordered by recency. Output auto-splits across chat lines if the list is long.
- **Player-count filter** (`mapm_nom_filter_by_players "0"`) — when enabled, maps whose `MinPlayers`/`MaxPlayers` from `.ini` files don't match the current real player count are hidden from the nomination menu and rejected on nomination with a reason message. HLTV is excluded from the player count; bots remain at admin's discretion.

### Scheduler plugin
- **HLTV-aware player count** — all player count checks exclude HLTV via `get_players(..., "h")` (bots are counted as players). An empty server with only HLTV connected now correctly skips auto-voting.
- **mapcycle.txt fallback when empty** — when no real players are online, `amx_nextmap` syncs from the server's `mapcycle.txt` instead of MapManager's own rotation. Reverts to `[not yet voted on]` when players join.
- **Admin changelevel passthrough** — `amx_map` / `rcon changelevel` no longer gets overridden by the scheduler's intermission handler.

### Blocklist
- **CVAR default** `mapm_blocklist_ban_last_maps` changed from `10` to `8`.
- **Hard cap at 20** — the CVAR value is clamped to 20 internally to prevent excessive heap allocation in the recent-maps display array.

### Other
- **German translation** (`[de]` section) added to `mapmanager.txt`.
