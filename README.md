# WindWakerCOOP-PC

Online co-op for **two to four players** for the Wind Waker HD native PC port (a modified
[ZeldaWWHDRecomp](https://github.com/ZeldaWWHDRecomp/ZeldaWWHDRecomp)), for Windows. Every player sees the others'
Links, and the world is shared: story progress, switches, chests, keys, and (being tested) enemies.

**This is an experimental Alpha.** Expect bugs, and please report them (see "Reporting a bug").

Downloads are on the **[Releases](../../releases)** page. This repository holds only this README, the license and the
release files; it contains no game.

## Which release do I download?

| Release | What it is | Co-op protocol |
|---|---|---|
| **0.5.0-coop.5** (Alpha, multiplayer test) | **Prerelease.** Fixes enemies with two players in one room, smoother movement of the other Links, an easier launcher. Not yet verified on two real PCs: this release is for that test. | **5** |
| 0.5.0-coop.4 (Alpha) | The first public Alpha (the regular "latest" release). | 4 |

**Everyone in a game must use exactly the same release.** Protocol 5 (0.5.0-coop.5) and protocol 4 (0.5.0-coop.4)
cannot play together: the host refuses the other game as "another build". The launcher shows the release and the
protocol on its **Install** tab.

The launcher's update check offers only regular releases, never prereleases. So 0.5.0-coop.4 does **not** update
itself to 0.5.0-coop.5: install 0.5.0-coop.5 by hand into a new folder (below).

## What you need

- Windows 10 or 11, 64-bit, with a graphics card that supports Vulkan (any reasonably recent NVIDIA, AMD or Intel
  graphics with up-to-date drivers).
- About **10 GB** of free disk space and an internet connection for the first setup (it downloads a compiler).
- **Your own copy of The Legend of Zelda: The Wind Waker HD for Wii U, USA version** (see below).
- To play over the internet: **Radmin VPN** (free) on every PC, see "Playing over the internet".

## Your game files

The releases contain **no Nintendo game code, game data, assets or keys**, and nobody here can give you any. You need
the files of your own game, dumped from your own Wii U console and disc, in one of these forms:

- a disc image (`.wud` or `.wux`),
- a Cemu / WUP archive, or
- an extracted game folder (the one that contains the folders `code`, `content` and `meta`).

It must be the **USA** version (title ID `00050000-10143500`); setup checks this. Your files are only read, never
changed.

## First-time setup

1. **Download** `WindWakerCOOP-PC-<version>-windows-x86_64.zip` from the [Releases](../../releases) page. (You do
   not need the `-source.zip`; it is the source code.)
2. **Unzip** the whole zip into a new, empty folder of its own, for example `C:\Games\WindWakerCOOP-0.5.0-coop.5`.
   Not into `Program Files`, not onto a network drive, and not over another release's folder.
3. **Start `WindWaker COOP.exe`** in that folder. Windows SmartScreen may warn that the program is unknown (it is
   not signed): choose "More info" and then "Run anyway".
4. The launcher says the game is not set up yet. Press the big **Set up the game** button on the **Play** tab and
   choose your game files when it asks.
5. **Wait.** Setup checks your files and then builds the game for your PC from them. This often takes **10 to 30
   minutes** and happens only once. When it is done, the **Play**, **Host** and **Join** buttons work.

The built game, your saves and your settings live in the `data` folder inside the release folder. If something
breaks later, **Settings > Run game setup / repair** builds it again.

### Coming from 0.5.0-coop.4

Keep your 0.5.0-coop.4 folder as it is and set up 0.5.0-coop.5 in a **new** folder (steps above). In step 4 you can
choose the same game files as before. To keep playing your save, copy the old folder's `data\save` folder into the
new folder's `data` folder (replace it) after setup has finished, while the game is closed.

## Playing together

One player **hosts**; the others **join** the host. Only the host has to be reachable over the network.

### Host

1. On the **Play** tab, type your nickname.
2. Under **Host a game**, keep the UDP port **7777**, choose the number of players (2 to 4) and press **Host game**.
3. The first time, **Windows Firewall** asks whether `Wind Waker HD.exe` may use the network: allow it and tick
   **both Private and Public** (VPN networks are often counted as "public").
4. The launcher shows **Friends join: HOST_IP:7777** (your real address, for example `26.12.34.56:7777`). Press
   **Copy** and send it to your friends. The Session panel shows *Hosting*, *Waiting for players*, then who joined.

### Join

1. On the **Play** tab, type your nickname.
2. Under **Join a game**, type the host's address **with the port**, exactly as the host sent it:
   `HOST_IP:7777` (for example `26.12.34.56:7777`).
3. Press **Join game**. The Session panel changes from *Connecting* to *Connected* when the host answered.

## Playing over the internet: Radmin VPN (recommended)

Radmin VPN is a free Windows program that puts PCs anywhere in the world into one virtual network, as if they were
on the same Wi-Fi. It needs **no router settings, no port forwarding and no account**. Every PC in the network gets
an address that starts with `26.`. Radmin VPN is a separate product by Famatech, not part of this project.

1. **Everyone** installs Radmin VPN from https://www.radmin-vpn.com and starts it.
2. **The host creates a network:** press **Create network**, choose a network name and a password, and tell the
   friends both.
3. **The friends join it:** press **Join network** and type the network name and password. When the host's PC
   appears in the list with a green icon, you are connected.
4. **The host finds their Radmin address** (an IPv4 address `26.x.y.z`):
   - in the launcher: the **Internet play** panel on the **Play** tab shows **Your Radmin VPN address: 26.x.y.z**
     with a **Copy** button (it appears a few seconds after Radmin VPN joined the network), or
   - in Radmin VPN: the address next to your own computer's name at the top of the window, or right-click your
     computer and choose **Copy IP address**.
5. **The host** presses **Host game** (see "Host") and sends `26.x.y.z:7777` (the real numbers).
6. **The friends** type `26.x.y.z:7777` into **Join a game** and press **Join game**.

Radmin VPN also has a text and voice chat inside the network, handy for sending the address. The co-op connection
itself is not encrypted: play with people you trust.

**Other ways:** players on the same Wi-Fi or LAN can use the host's LAN address (shown in the launcher too).
Tailscale (free, needs an account) works like Radmin VPN with the host's `100.x.y.z` address. Without any VPN, the
host must forward **UDP port 7777** on their router to their PC and give friends their public IP address; a VPN is
easier and safer. Only IPv4 addresses work; there is no IPv6, matchmaking or invite code.

## When it does not connect

| Problem | What to try |
|---|---|
| "The host did not answer" when joining | Is the host's game running and hosting **right now**? Compare the address and the port character by character (`26.x.y.z:7777`). |
| Is it the VPN or the game? | On the joining PC: Start menu, type `cmd`, press Enter, then type `ping 26.x.y.z` (the host's address). If the ping fails, the problem is the Radmin network (same network name and password? both green? restart Radmin VPN). |
| The ping works, but the game gets no answer | The host's Windows Firewall blocks the game. Windows Security > Firewall & network protection > Allow an app through firewall > `Wind Waker HD.exe`: tick **Private** and **Public**. Other security programs may need the same. Each release folder has its own `Wind Waker HD.exe`, so a new folder is asked about again. |
| "Radmin VPN not found" in the launcher | Start Radmin VPN, join the network and wait a few seconds; the launcher looks again by itself. Check that the network adapter "Radmin VPN" is enabled. |
| "This UDP port is already in use" (host) | Another copy of the game or another program uses UDP 7777. Close it, or host on another port such as 7778 and tell the friends to type `:7778`. |
| "You and the host run different game builds" / "different co-op versions" | Not everyone has the same release (for example 0.5.0-coop.4 and 0.5.0-coop.5). Check **Install** tab > co-op release and protocol on every PC, and use the same release everywhere. |
| "The host's game is full" | The host chose fewer players than are joining. |
| It connects but looks jerky | Internet latency. A wired connection and no big downloads in the background help. |
| Setup fails / the game does not start | **Settings > Run game setup / repair**. Check that your game is the USA Wii U version. Update your graphics driver. |

## Known Alpha limitations

- **0.5.0-coop.5 has not been tested on two real PCs yet.** Its fixes pass the project's automated tests (two games
  on one PC, including a simulated internet connection); the real test over Radmin VPN is still to come.
- Shared enemies have been tested in Dragon Roost Cavern (and one fight in Forsaken Fortress); elsewhere they are
  untested.
- Enemy behaviour that starts when Link comes near follows the **host's** Link: a Chuchu hanging from the ceiling
  drops only when the host walks under it.
- In a joining player's game, an enemy can attack that player at moments when the host's enemy is not attacking.
- Only Bokoblins, Chuchus and Moblins copy the host's animation exactly; other enemies may look less exact.
- No shared inventory: only the player who opens a chest gets its item. Pigs and many objects (rocks, rupees,
  carried objects) are not fully shared yet. Pressure switches are per player.
- Long sessions and a full dungeon run with two players have had little testing.

## Reporting a bug

Write down what happened and roughly when (screenshots help). Then, in the launcher: **Install** tab > **Copy
diagnostics**, and paste it into your report. The game log is `data\logs\game.log` in the release folder (the
previous run is `game-previous.log`). Both contain nicknames, session addresses and folder names: read them before
sending and remove anything you don't want to share. Never send game files or keys.

## License and source

WindWakerCOOP-PC is a modified version of ZeldaWWHDRecomp and, like it, licensed under the **Mozilla Public License
2.0** ([LICENSE](LICENSE)). Every release has the matching source archive (`...-source.zip`) and `SHA256SUMS.txt`
to check the downloads.

The Legend of Zelda and The Wind Waker are trademarks of Nintendo. This project is not affiliated with or endorsed by
Nintendo.
