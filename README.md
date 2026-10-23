# Mai LocalHost

Local Roblox Studio host / join tool with an UI, auto-update and built-in UDP proxy.

---

## Why is the.exe ~3 MB?

The app is shipped as a file. That size comes from:

Packed inside the exe | What it is |

|------------------------|------------|

| LocalSounds | All the custom sound files (mp3/ogg) embedded in the binary |

| Guna.UI2 | UI library (buttons, panels, etc.)

| Newtonsoft.Json | JSON helper

| app code | UI, updater, UDP proxy, Studio launcher |

On first run sounds are extracted next to the exe into a LocalSounds folder then copied into Roblox Studio’s content\sounds so they work in-game. You do not need to ship a sounds folder or DLLs.

---

## Requirements

- Windows

- Roblox Studio installed

- Optional: a UDP tunnel (e.g. Playit.gg, cloudflared ngrok UDP) if friends join from outside your network

---

## How to use

### 1. First launch

1. Run MaiLocalHost.exe

2. Wait for the loading screen:

Checks for updates

Finds Roblox Studio

Extracts & installs LocalSounds into Studio

3. When you see Localsound correctly installed click the launch button

### 2. Create a server (host)

1. Open the Create tab (sidebar)

2. Enter:

UserId. Your Roblox user id

Port. Local port Studio will use (same port as ur tunnel you did created)

Tunnel. the real public address comes from your tunnel app

3. Click Create

4. Studio opens a server + a local client so you can play on your host

To let others join run a UDP tunnel that forwards a public host:port to your PC’s chosen port then send them that public address.

### 3. Join a server

1. Open the Join tab

2. Enter the host’s tunnel as host:port

Example: abc.trycloudflare.com:25565

3. Click Join

4. The app starts an UDP proxy and opens Studio as a client through 127.0.0.1

Close the app (or stop the process) when you’re done so the proxy stops.

### 4. Moving the window

Drag the black bar (title area).

Click the title text without dragging to return to Home and show the sidebar again.

---

## Auto-update

On startup the app reads:

https://raw.githubusercontent.com/MaickaLovesYou/MaiLocalHost/main/update.json

Example:

{

"version": "1.0.1"

"url": "https://github.com/MaickaLovesYou/MaiLocalHost/releases/download/Releases/MaiLocalHost.exe"

"changelog": "bug fixes"

}

- If the remote version is newer than this build → downloads the new exe replaces itself restarts

- If you’re already up to date → continues normally

- If the network fails → continues without blocking

You only need the one.exe; no installer.

---

## Troubleshooting

| Problem | What to try |

|---------|-------------|

| Studio not found | Install Roblox Studio, then relaunch |

| Update loops Clear %TEMP%\MinaLocalHostUpdate and make sure the release exe’s version matches update.json |

| Join fails | Check host:port that the host’s tunnel is UDP and online and firewall allows the app |

| Missing sounds, in Studio | Run the app once so it can extract & copy LocalSounds; don’t delete the extracted folder while testing |

| Antivirus blocks replace | Allow the app / temp updater script once |

---

## Credits

- UI & packaging: Mai LocalHost

- UDP proxy / Studio launch flow inspired by mattslocalhosting

---

## License

Use freely for local Studio hosting. Don’t reupload as your own without credit.
