<div align="center">

# KLP Launcher · 苦力怕启动器

**A Minecraft launcher for Chinese-speaking players: manage instances, mods, worlds and servers, with an AI assistant that actually does the work.**

Free · No ads · Nothing bundled · In closed beta

[Website](https://klp-launcher.com/en/) · [中文说明](README.zh-CN.md) · [Privacy](PRIVACY.md) · [Terms](LICENSE) · [Changelog](CHANGELOG.md)

</div>

---

> [!IMPORTANT]
> **This repository does not contain source code.** It holds the user-facing documentation,
> changelog, legal terms and issue tracker. The launcher itself is copyright of the KLP team,
> all rights reserved — see [LICENSE](LICENSE).

> [!NOTE]
> **The launcher is applying for Minecraft API access from Mojang. Until that is approved,
> no download is offered.** It will be published on the [website](https://klp-launcher.com/en/)
> as soon as it goes through. To ask about progress, write to admin@klp-launcher.com.

## What this is

KLP Launcher is a desktop program that runs on your own computer. Managing instances, downloading game files and launching the game all happen locally and never pass through our servers.

Technically it is a **shared Rust core with native UI per platform**: the domain logic (download engine, Java detection, launch pipeline, authentication, log parsing) is written once in Rust; the desktop client is built on Tauri 2 and Svelte 5, and a separate SwiftUI client for macOS shares the same core.

## Features

### Instances and mods

- **Fully isolated instances** — each instance keeps its own mods, config and worlds, so changing one never touches another. Switching versions needs no reinstall.
- **One-click mods** — search, install, update and disable from the same list. **Dependencies are pulled in automatically**, and version conflicts are flagged before you install.
- **Automatic world backups** — back up on a schedule or snapshot by hand, and roll back to any point in time.
- **Import existing instances** — point it at a `.minecraft` directory or another launcher's instance folder; mods, worlds and config are all recognised, and **the original directory is left untouched**.
- **Loaders** — Fabric, Forge, NeoForge, Quilt, and OptiFine.
- **Java handled for you** — the runtime an instance needs is downloaded automatically from Adoptium, so there is nothing to install yourself.

### Downloads

- Regional mirror nodes with multi-threaded downloads and **adjustable concurrency** (the source can be switched, or concurrency lowered to stay under a rate limit).
- Content comes from **Modrinth** and **CurseForge** — mods, modpacks, resource packs and shaders, browsable by category.
- Before installing, it tells you which instances the item fits and what dependencies are missing.
- Every download and install is collected in one task centre: pause, cancel, retry.

### AI assistant

It can read your instances, mod lists and crash logs. Find a mod, install a modpack, track down a conflict — one sentence is enough.

- **Confirm before it acts** — every write, change or deletion opens a confirmation card first, spelling out what it will do and which instances it affects. Cancel any line item. Nothing runs until you approve it.
- **Destructive actions marked apart** — irreversible things like deleting an instance list exactly what goes and what stays.
- **Bring your own model** — point it at your own model endpoint and API key in settings. **Conversations never pass through our servers**; we cannot receive or store them. Leave the fields empty and the feature simply does not run, or turn it off entirely.
- **Crash log analysis** — when the game crashes, the launcher reads the log, points at the mod and the line, and suggests a fix you can act on.

### Server directory

Filter by version, play style and loader, with live player counts and latency. Hitting *Join* matches the right instance for that version, adds whatever mods are missing, and runs a check before you connect.

## Supported systems

| System | Status |
|---|---|
| Windows 10 / 11 (x64) | Supported |
| macOS 12 and later (Apple Silicon) | Supported |
| macOS (Intel / x86) | No build |
| Linux | Not supported yet |

**The portable and installed builds are functionally identical**; they differ only in where data lives. The portable build keeps its data next to the program, so the whole folder can travel on a USB stick and uninstalling means deleting it. The installed build stores data in your user directory. On read-only media the portable build falls back to storing data the way the installed build does.

## Privacy

Full details in [PRIVACY.md](PRIVACY.md). In short:

- **No telemetry, analytics or usage statistics**, and no automatic crash reporting.
- **We do not collect** passwords, tokens, or the contents of your saves, worlds or mod files.
- Sign-in uses Microsoft's **official device code flow** — your password never passes through any field in the launcher. Tokens go only to the official Microsoft, Xbox Live and Minecraft endpoints, never to our servers.
- The launcher asks `api.klp-launcher.com` for three things only (update checks, news and server listings, the AI system prompt). **All downward, carrying no identifying information.**
- AI conversations go directly to the model provider you configured. Our server **has no endpoint that receives them at all**.

The policy also states two known costs of the current implementation rather than glossing over them: on Windows, Linux and in portable mode, tokens sit in a 0600 local file rather than OS-encrypted storage; and the AI performs no redaction on the logs and paths it sends out.

## Reporting problems

- **Bugs and feature requests**: open an [issue](https://github.com/damesck233/klplauncher-TauriDesktop/issues/new/choose).
- **Anything else** (install failures, crashes, privacy, terms): write to admin@klp-launcher.com.

The project is in closed beta and every message gets read.

## Legal

**You must own Minecraft yourself.** The launcher does not provide, distribute or resell a game licence, and does not support any use that bypasses authentication. See [LICENSE](LICENSE).

---

<div align="center">

**NOT AN OFFICIAL MINECRAFT PRODUCT.**
**NOT APPROVED BY OR ASSOCIATED WITH MOJANG OR MICROSOFT.**

Minecraft is a trademark of Mojang Studios.

© 2026 KLP Team · All rights reserved

</div>
