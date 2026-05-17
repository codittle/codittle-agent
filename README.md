# Codittle Agent

The deployment agent for **[Codittle](https://codittle.com)** — a small Rust
binary that runs on the host where your organisms (deployed apps) live and
keeps them in sync with Codittle.

This repository is the **release channel** for the Codittle Agent: it hosts
the binaries and their installers. There is no source code here.

## Download

Grab the latest build from the
[**Releases page**](https://github.com/codittle/codittle-agent/releases/latest).

| Platform | File | Notes |
|----------|------|-------|
| Linux · x86_64      | `codittle-agent-linux-x86_64.zip`   | glibc 2.31+ — most servers |
| Windows 10/11 · x64 | `codittle-agent-windows-x86_64.zip` | Per-user install, no admin |
| Linux · ARM64       | —                                   | Coming soon |
| macOS               | —                                   | Coming soon |

Every zip carries the agent binary plus its installer. Verify your download
against `SHA256SUMS.txt` on the release.

## What it does

The agent is the bridge between Codittle and your running organisms:

- **Patch delivery** — pulls and applies releases pushed from Codittle
- **Telemetry** — reports health, logs, and metrics back
- **Rollbacks** — restores a previous release when a deploy fails
- **Self-update** — keeps itself current from this release channel

It is a single self-contained binary with a built-in dashboard and TUI —
nothing else to install.

## Install — Linux

```bash
unzip codittle-agent-linux-x86_64.zip
cd codittle-agent
sudo ./install.sh
```

`install.sh` installs the binary, registers a `codittle-agent` systemd
service, and bundles a pinned Node runtime for your organisms. Run
`sudo ./install.sh --uninstall` to remove it, or `--help` for all options.

## Install — Windows

1. Extract `codittle-agent-windows-x86_64.zip`.
2. From inside the `codittle-agent` folder, run `install.bat`.
3. It installs per-user (no admin rights) and adds the agent to your `PATH`.

Remove it any time with `install.bat /uninstall`.

## Connect it

Register the agent with your Codittle instance, then start it:

```bash
codittle-agent init --server <your-codittle-url> --token <registration-token>
codittle-agent start
```

Generate a registration token from the **Deployment Suite** in Codittle
(Code Origins → Deploy → Connect Agent).

## Versioning

Releases are tagged `vMAJOR.MINOR.PATCH` (semantic versioning). Once
installed, the agent self-updates from this channel.

## Links

- **Web app** — [codittle.com](https://codittle.com)
- **Support** — [support@codittle.com](mailto:support@codittle.com)

---

<sub>The Codittle Agent is written in Rust. Reporting an issue? Include the
agent version (`codittle-agent --version`) and your OS.</sub>
