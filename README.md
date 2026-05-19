# AMPTemplates — Americas Army Game Server Templates

Custom [CubeCoders AMP](https://cubecoders.com/AMP) Generic Module templates for Americas Army server hosting.

---

## Templates Included

| Template | Game | Status |
|---|---|---|
| `aa2reborn` | Americas Army 2 Reborn (2.8.5) | ✅ Stable |
| `aa285` | Americas Army: Operations 2.8.5 | ✅ Stable |
| `aa25` | Americas Army: Operations 2.5 (AA25Assist) | ⚠️ Work in Progress |

---

## Adding This Repo to AMP

### Step 1 — Open Configuration Repositories

In your AMP panel, navigate to:

**ADS → Configuration → Instance Deployment → Configuration Repositories**

### Step 2 — Add the Repository

Enter the repository in `user/repo:branch` format:

```
demorgon989/AMPTemplates:main
```

Click **Fetch**, then refresh your browser.

### Step 3 — Create an Instance

Go to **Create Instance**, then select the game server by name from the dropdown (e.g. `AA2Reborn`, `AA:O 2.8.5`, `AA:O 2.5`). The templates from this repo will appear alongside AMP's built-in options once the repo has been fetched.

> **Note:** If the templates don't appear immediately, try clicking Fetch again and doing a hard refresh (`Ctrl+Shift+R`).

---

## Template Details

### AA2Reborn (`aa2reborn`)

Americas Army 2 Reborn is a community revival of AA2. The server binaries are distributed via the AA2Reborn project and require access to their CDN via the included `updater.py` script.

**Requirements:**
- AMP running on Linux with Docker (uses `cubecoders/ampbase:wine-stable`)
- Internet access to the AA2Reborn CDN for initial game download
- An AA2Reborn server secret (obtained from the AA2Reborn community)

**Dashboard Settings:**

| Setting | Description |
|---|---|
| Server Name | Public name shown in the server browser |
| MOTD | Message of the Day shown on connect |
| Game Port | UDP port the game listens on (default: 1716) |
| Server Secret | Auth token from AA2Reborn — required for online play |
| External IP | Your public IP, required if behind NAT |
| Auth Server | Auth server address (default: `auth.aa2reborn.com`) |
| Auth Port | Auth server port (default: 80) |

**Ports to forward:**

| Port | Protocol | Purpose |
|---|---|---|
| 1716 | UDP | Game port |
| 1717 | UDP | Query port |

---

### AA:O 2.8.5 (`aa285`)

Americas Army: Operations 2.8.5 server. Runs under Wine via Docker.

**Requirements:**
- AMP running on Linux with Docker (uses `cubecoders/ampbase:wine-stable`)
- The full AA 2.8.5 server files (`aa285-server.zip`) hosted as a GitHub Release asset in a linked repository

**Ports to forward:**

| Port | Protocol | Purpose |
|---|---|---|
| 1716 | UDP | Game port |
| 1717 | UDP | Query port |

---

### AA:O 2.5 — AA25Assist (`aa25`) ⚠️ Work in Progress

This template targets the **AA25Assist** version of Americas Army: Operations 2.5, a community-maintained variant of the classic 2.5 client/server. The template is functional but still has known issues and is under active development. It may not behave reliably in all environments.

**Requirements:**
- AMP running on Linux with Docker (uses `cubecoders/ampbase:wine-stable`)
- The AA25Assist server files hosted as a release asset

**Ports to forward:**

| Port | Protocol | Purpose |
|---|---|---|
| 1716 | UDP | Game port |
| 1717 | UDP | Query port |

---

## Docker / Linux Notes

All three templates are Linux-only and run the Windows server binaries via Wine inside AMP's `wine-stable` Docker base image. AMP must be configured to use Docker for new Generic Module instances.

If you're running AMP on Debian/Ubuntu, make sure the Docker seccomp profile allows the Wine runtime. See [AMP's Docker documentation](https://github.com/CubeCoders/AMP/wiki/Running-AMP-in-Docker) if you run into permission errors on startup.

---

## File Structure Reference

Each template consists of the following files at the repo root (all lowercase):

```
<templatename>.kvp               # Main AMP configuration (app, console, meta settings)
<templatename>config.json        # Settings manifest — generates dashboard UI fields
<templatename>metaconfig.json    # Maps dashboard fields to in-game config files
<templatename>ports.json         # Port definitions shown in AMP
<templatename>updates.json       # Defines how AMP downloads/installs the server
aao.png                          # Template icon shown in AMP instance list
```

---

## Related Links

- [CubeCoders AMP](https://cubecoders.com/AMP)
- [AMP Generic Module Wiki](https://github.com/CubeCoders/AMP/wiki/Configuring-the-%27Generic%27-AMP-module)
- [Official CubeCoders AMPTemplates Repo](https://github.com/CubeCoders/AMPTemplates)
- [AA2Reborn Project](https://aa2reborn.com)

---

## Issues / Contributing

If you run into problems with a specific template, open an issue and include your AMP version, OS, and any relevant log output from the instance console.
