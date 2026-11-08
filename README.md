# WindWakerCOOP-PC

**WindWaker COOP** is online co-op for **two to four players** for The Legend of Zelda: The Wind Waker HD on Windows.
It is a modified version of the native PC port [ZeldaWWHDRecomp](https://github.com/ZeldaWWHDRecomp/ZeldaWWHDRecomp).

Every player sees the others' Links, with their animations, equipment and tunic colour. The world is shared:
- story progress, switches, chests, keys and visited rooms;
- enemies (tested mainly in Dragon Roost Cavern);
- carried and broken objects;
- pigs and pickups.

**This is an experimental Public Alpha.** It is not stable and it is not bug-free. Expect crashes, sync problems and
rough edges, back up your save, and please report what you find (see "Reporting a bug").

Downloads are on the **[Releases](../../releases)** page. This repository holds only this README, the license and the
release files. It contains no game.

## Which release do I download?

| Release | What it is | Co-op protocol |
|---|---|---|
| **0.5.0-coop.6** (Public Alpha) | **The current release.** Crash fixes from the second playtest, carried objects, pigs and household objects shared, Teleport to Player anywhere in the world, World Warp, Catch Up. | **5** |
| 0.5.0-coop.5 (prerelease) | The test build of the second playtest. | 5 |
| 0.5.0-coop.4 (Alpha) | The first public Alpha. | 4 |

**Everyone in a game must use exactly the same release.** A different release is refused by the host as a
"different game build", even when the protocol number is the same, as for 0.5.0-coop.5 and 0.5.0-coop.6. The
launcher shows the release and the protocol on its **Install** tab.

**Already playing 0.5.0-coop.4 or 0.5.0-coop.5?** There are two ways:
- **Easiest and safest:** a fresh install of 0.5.0-coop.6 into a new folder (see "First-time setup"). Then copy your old
  folder's `data\save` into the new folder's `data`, with the game closed.
- **Or use the update:** open the launcher's **Updates** tab and press **Install**. Afterwards, press **Settings > Run
  game setup / repair once** (see "Updates" below).

## What you need

- Windows 10 or 11, 64-bit, with a graphics card that supports Vulkan: any reasonably recent NVIDIA, AMD or Intel
  graphics with up-to-date drivers.
- About **10 GB** of free disk space, and an internet connection for the first setup. Setup downloads a compiler.
- **Your own copy of The Legend of Zelda: The Wind Waker HD for Wii U, USA version.** See "Your game files".
- To play over the internet: **Radmin VPN** (free) on every PC. See "Playing over the internet".

## Your game files

The releases contain **no Nintendo game code, game data, assets or keys**, and nobody here can give you any. You need
the files of your own game, dumped from your own Wii U console and disc, in one of these forms:

- a disc image (`.wud` or `.wux`);
- a Cemu / WUP archive;
- an extracted game folder: the one that contains the folders `code`, `content` and `meta`.

It must be the **USA** version (title ID `00050000-10143500`), which setup checks. Your files are only read, never
changed.

## First-time setup

1. **Download** `WindWakerCOOP-PC-0.5.0-coop.6-windows-x86_64.zip` from the [Releases](../../releases) page. You do
   not need the `-source.zip`: that is the source code.
2. **Unzip** the whole zip into a new, empty folder of its own, for example `C:\Games\WindWakerCOOP`. Do not use
   `Program Files`, a network drive, or another release's folder.
3. **Start `WindWaker COOP.exe`** in that folder. The program is not signed, so Windows SmartScreen may warn that it
   is unknown. Choose "More info", then "Run anyway".
4. The launcher says the game is not set up yet. Press the big **Set up the game** button on the **Play** tab, and
   choose your game files when it asks.
5. **Wait.** Setup checks your files, then builds the game for your PC from them. This often takes **10 to 30 minutes**
   and happens only once. When it is done, the **Play**, **Host** and **Join** buttons work.

The built game, your saves and your settings live in the `data` folder inside the release folder. If something breaks
later, **Settings > Run game setup / repair** builds the game again.

## Updates (automatic)

The launcher checks for a new release when it starts; you can turn that off in Settings. When one is out, it is shown
on the **Updates** tab.
1. Close the game.
2. Press **Install** and wait.

The launcher then:
- downloads the release and checks its files;
- backs up your current program files, saves and settings into `data\backup`;
- installs the new program files and rebuilds the game for the new version.

**Your game files, saves and settings stay as they are.** If any step fails, the previous version is put back and
the reason is shown. Your installation is never deleted.

**Updating from 0.5.0-coop.4 or 0.5.0-coop.5: press Settings > Run game setup / repair once after the update.** The
updater in those releases may skip rebuilding the game when your game files are inside the release folder. The launcher
would then keep starting the old game, and hosts would refuse you as a "different game build". The repair rebuilds the
game and keeps your saves. The updater in 0.5.0-coop.6 does not have this problem.

Prereleases (test builds, marked "Pre-release" on the Releases page) are never offered as updates.

## Backing up and restoring your save

Your saves are in the `data\save` folder of the release folder.
- **To back up:** with the game closed, copy `data\save` to a safe place. Do this before trying Catch Up or the
  Debug tab's save edits.
- **To restore:** with the game closed, put your copy back as `data\save`, replacing it.
- **Updates:** the updater also keeps copies in `data\backup`.

## Playing together

One player **hosts**; the others **join** the host. Only the host has to be reachable over the network. A session has
2 to 4 players, chosen by the host.

### Host

1. On the **Play** tab, type your nickname.
2. Under **Host a game**, keep the UDP port **7777**, choose the number of players (2 to 4) and press **Host game**.
3. The first time, **Windows Firewall** asks whether `Wind Waker HD.exe` may use the network. Allow it, and tick
   **both Private and Public**: VPN networks are often counted as "public".
4. The launcher shows **Friends join: HOST_IP:7777** with your real address, for example `26.12.34.56:7777`. Press
   **Copy** and send it to your friends. The Session panel shows *Hosting*, then *Waiting for players*, then who
   joined.

### Join

1. On the **Play** tab, type your nickname.
2. Under **Join a game**, type the host's address **with the port**, exactly as the host sent it:
   `HOST_IP:7777` (for example `26.12.34.56:7777`).
3. Press **Join game**. The Session panel changes from *Connecting* to *Connected* when the host has answered.

## Playing over the internet: Radmin VPN (recommended)

Radmin VPN is a free Windows program that puts PCs anywhere in the world into one virtual network, as if they were on
the same Wi-Fi. It needs **no router settings, no port forwarding and no account**. Every PC in the network gets an
address that starts with `26.`. Radmin VPN is a separate product by Famatech, not part of this project.

1. **Everyone** installs Radmin VPN from https://www.radmin-vpn.com and starts it.
2. **The host creates a network:** press **Create network**, choose a network name and a password, and tell the
   friends both.
3. **The friends join it:** press **Join network** and type the network name and password. You are connected when
   the host's PC appears in the list with a green icon.
4. **The host finds their Radmin address**, an IPv4 address `26.x.y.z`, in either of two places:
   - in the launcher: the **Internet play** panel on the **Play** tab shows **Your Radmin VPN address: 26.x.y.z** with a
     **Copy** button, a few seconds after Radmin VPN has joined the network;
   - in Radmin VPN: the address next to your own computer's name at the top of the window. You can also right-click
     your computer and choose **Copy IP address**.
5. **The host** presses **Host game** (see "Host") and sends `26.x.y.z:7777` with the real numbers.
6. **The friends** type `26.x.y.z:7777` into **Join a game** and press **Join game**.

Radmin VPN has a text and voice chat inside the network, handy for sending the address. The co-op connection itself is
not encrypted: play with people you trust.

**Other ways:**
- **Same Wi-Fi or LAN:** use the host's LAN address, which the launcher shows too.
- **Tailscale:** free but needs an account. It works like Radmin VPN, with the host's `100.x.y.z` address.
- **No VPN:** the host must forward **UDP port 7777** on their router to their PC and give friends their public IP
  address. A VPN is easier and safer.

Only IPv4 addresses work. There is no IPv6, matchmaking or invite code.

## In the game: the Co-op tab

Press **Esc** (or **F1**) in the game to open Settings, then choose the **Co-op** tab. It lists the other players, where
they are, and two separate actions.

### Teleport to Player ("Go to")

Moves **only your Link** next to that player, anywhere in the world: the same room, another island, inside a house,
or in a dungeon.
- **The same place:** it happens at once.
- **Somewhere else:** your game asks theirs where they are, changes stage the game's own way to the spawn point
  nearest them, and then puts you beside them.
  - If they moved on meanwhile, it follows once.
  - It waits while they are in a scene.

It refuses, and tells you why:
- while you or they are in a cutscene, a menu or a stage change;
- while they are in the air or swimming away from the sea;
- while they are in a boss or mini-boss room.

Teleport copies **no progress**: a place your story has not reached yet looks as your own save has it.

### Catch Up to Player

Copies that player's **current** progress into your game, **including what they have not saved yet**: items, hearts,
rupees, songs, story, dungeon items, keys and charts. It also puts you where they are. Your own nickname and in-save
options are kept.

> **Warning: Catch Up REPLACES your progress. It does not merge it.** Where the other player is behind you, you
> **lose** items, hearts, rupees or story progress. Read the comparison it shows ("Theirs" and "Yours now") before
> you press **Apply**.

The steps:
1. Press **Catch Up to NAME**. The snapshot is sent and checked (SHA-256, version, build). A damaged or interrupted
   transfer applies nothing.
2. The tab shows their progress next to yours. Press **Apply (backup first)**, or **Discard**.
3. Before anything changes, your save folder and your current game are backed up to `data\save-coop-backups\<date>-catchup-from-NAME`.
   These backups are never deleted automatically.
4. The progress is applied at a safe moment, when your Link is under control. If applying fails, your backup is loaded
   back.
5. **Save in the game** to keep it, as after any pickup.

**To undo a Catch Up:** tick **"I want to restore my last backup"** and press **Restore Backup** on the Co-op tab. This
loads your game as it was just before the Catch Up; save in the game afterwards to keep that. If you already saved
over it, close the game and copy the backup's `save` folder back as `data\save`, replacing it.

| | Teleport ("Go to") | Catch Up |
|---|---|---|
| Moves your Link next to them | yes | yes, after applying |
| Changes your items and story | **never** | **yes: replaced by theirs** |
| Asks first and makes a backup | not needed | always |

## Debug tab (testing and getting unstuck)

Off by default. To turn it on, go to the launcher's **Settings** and tick **Debug tools in the game**. It then appears
as a **Debug** tab in the game's Settings. It acts on **your game only**:
- **World Warp:** checked places.
  - Islands: Outset, Windfall, Dragon Roost Island, Forest Haven (island and inside), and the Forsaken Fortress
    (outside and inside).
  - Dungeons: Dragon Roost Cavern, the Tower of the Gods, Forbidden Woods, the Earth and Wind Temples and Ganon's Tower.
  - Houses: Link's House and Orca's House.

  A warp writes no story flags. Places marked `*` come later in the story and may look unfinished with an early save.
  The open Great Sea is not offered: its only spawn points are the boat's.
- **Recover:** "Return to last safe position", and "Unstuck", which re-enters the room at a safe spot.
- **Cheats and one-time save edits:** infinite health, moon jump, all items and so on. The save edits change your
  save, so back it up first.

## When it does not connect

| Problem | What to try |
|---|---|
| "The host did not answer" when joining | Is the host's game running and hosting **right now**? Compare the address and the port character by character (`26.x.y.z:7777`). |
| Is it the VPN or the game? | On the joining PC: Start menu, type `cmd`, press Enter, then type `ping 26.x.y.z` with the host's address. If the ping fails, the problem is the Radmin network: is it the same network name and password? Are both PCs green? Try restarting Radmin VPN. |
| The ping works, but the game gets no answer | The host's Windows Firewall is blocking the game. Go to Windows Security > Firewall & network protection > Allow an app through firewall > `Wind Waker HD.exe`, and tick **Private** and **Public**. Other security programs may need the same. Each release folder has its own `Wind Waker HD.exe`, so a new folder is asked about again. |
| "Radmin VPN not found" in the launcher | Start Radmin VPN, join the network and wait a few seconds; the launcher looks again by itself. Check that the network adapter "Radmin VPN" is enabled. |
| "This UDP port is already in use" (host) | Another copy of the game, or another program, uses UDP 7777. Close it, or host on another port such as 7778 and tell the friends to type `:7778`. |
| "Different game build" / "different protocol" | Not everyone has the same release. Check **Install** tab > co-op release on every PC, and update everyone to 0.5.0-coop.6. |
| "The host's game is full" | The host chose fewer players than are joining. |
| It connects but looks jerky | Internet latency. A wired connection, and no big downloads in the background, help. |
| Setup fails / the game does not start | Use **Settings > Run game setup / repair**. Check that your game is the USA Wii U version. Update your graphics driver. |

## Known limitations (Public Alpha)

- **Untested on two real PCs:** carried objects, pigs, worldwide Teleport and Catch Up pass the project's automated
  tests: two to three games on one PC, also over a simulated bad connection.
- **Catch Up:**
  - It replaces progress; it never merges.
  - Nothing is offered when a player joins.
  - It has not been tried with saves far into the story.
- **Teleport:**
  - Never into boss or mini-boss rooms, even after the boss is beaten.
  - Not tried onto a player who is sailing.
- **Unstuck** cannot leave a scene that never ends.
- **Enemies:**
  - Shared enemies have been tested in Dragon Roost Cavern and in one Forsaken Fortress fight; elsewhere they are
    untested.
  - Enemy behaviour that starts when Link comes near follows the **host's** Link. For example, a Chuchu hanging from
    the ceiling drops only when the host walks under it.
  - In a joining player's game, an enemy can attack that player when the host's enemy is not attacking.
  - Only Bokoblins, Chuchus and Moblins copy the host's animation exactly.
- **Inventory:** no shared inventory. Only the player who opens a chest gets its item.
- **Pickups:** if two players take the same rupee at once, the second gets it taken back. A duplicate heart or ammo
  pickup is not taken back.
- **Not shared:**
  - shelves, tables and plants;
  - a pig's anger;
  - dishes being pushed;
  - pressure switches (per player).
- **Master Sword shine:** another player's Master Sword shine stays still while your own sword is put away.
- **Testing:** long sessions and full dungeon runs with several players have had little testing.

## Reporting a bug

Please report crashes, sync problems (something different for two players) and anything else odd. Write down what
happened, roughly when, and where (island, house, dungeon). Screenshots help.

Then attach, from the release folder:
- **the diagnostics:** in the launcher, **Install** tab > **Copy diagnostics**, then paste;
- **after a crash:** the newest `data\captures\crash-*.log`. Its co-op section lists the session and the last co-op
  events;
- **the game log:** `data\logs\game.log`, and `game-previous.log` for the run before.

The logs contain nicknames, session addresses (such as `26.x.y.z`) and folder names: read them before sending and
remove anything you don't want to share. Never send game files, saves of other people, or keys.

## License and source

WindWakerCOOP-PC is a modified version of ZeldaWWHDRecomp and, like it, licensed under the **Mozilla Public License
2.0** ([LICENSE](LICENSE)). Every release comes with:
- the matching source archive (`...-source.zip`);
- `SHA256SUMS.txt`, to check the downloads.

The Legend of Zelda and The Wind Waker are trademarks of Nintendo. This project is not affiliated with or endorsed by
Nintendo.
