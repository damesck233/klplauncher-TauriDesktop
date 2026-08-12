# Privacy Policy

**Last updated: 11 August 2026**

> 中文版：[PRIVACY.zh-CN.md](PRIVACY.zh-CN.md)
>
> This page matches <https://klp-launcher.com/en/privacy.html>; where they differ, the
> version on the website bearing the later date prevails.

KLP Launcher is a desktop program that runs on your own computer. Almost everything it does — managing instances, downloading game files, launching the game — happens locally and never passes through our servers. This page states exactly what leaves your machine, where it goes, and where things are stored. Every sentence here corresponds to specific behaviour in the launcher. If you find one that does not match what it actually does, write to us and we will fix either this page or the implementation.

## Accounts and sign-in

**The launcher never handles, displays or stores your Microsoft password.**

Sign-in uses Microsoft's official device code flow: the launcher shows you a verification URL and a short code, and you complete the sign-in in your own browser, on Microsoft's own page. Your password never passes through any field in the launcher.

After a successful sign-in, what the launcher stores are the tokens returned by the Microsoft and Minecraft services (refresh token, access token, expiry, Xbox user id), so that you do not have to sign in again next time. If any sign-in method requires you to type a password, that password is used only for that one request to the corresponding sign-in service and is cleared from memory and from stored data as soon as the request finishes. It is never persisted and never uploaded.

### Where tokens are stored

This differs by platform, and we state it plainly rather than generalising:

- **macOS, installed mode**: in the system Keychain, encrypted by the operating system.
- **Windows, Linux, and portable mode / a custom data directory on any platform**: in `accounts.json` inside the data directory, with file permissions restricted to the current user (0600), but **without additional encryption**. Integrating the Windows Credential Manager (DPAPI) is a known outstanding item.

> ⚠️ In other words: on Windows and Linux, or whenever you use the portable build, any program that can read your data directory can read those tokens. If you copy a portable folder onto a USB stick, the tokens travel with it. That is an inherent cost of portable mode rather than an oversight — but you should know about it.

In every case, these tokens are **never sent to our servers**. They only go to the official Microsoft, Xbox Live and Minecraft endpoints, to sign you in to the game itself.

## What we do not collect

- **No telemetry, analytics or usage statistics of any kind.** No such code exists in the launcher.
- **No automatic crash reporting.** When the game crashes, nothing is sent anywhere on its own.
- No passwords, tokens or credentials of any kind.
- No contents of your saves, worlds or mod files.
- No ads and no third-party tracking scripts. The website itself has zero JavaScript and makes no external requests.

## What the launcher asks our servers for

The launcher makes three kinds of request to `api.klp-launcher.com`. **All of them fetch content downward and carry no identifying information about you**:

- **Update checks**: the request path contains only two things — the operating system (`windows` / `darwin` / `linux`) and the CPU architecture (such as `x86_64` or `aarch64`). No current version number, no machine identifier, no account information.
- **News and server-directory content**: fetching lists and detail pages, the same as browsing a website.
- **The AI assistant's system prompt and skill manual**: text sent down to the launcher, cryptographically signed; if the signature does not verify, the launcher falls back to the copy built into the program. This channel only goes downward and uploads nothing.

As with any network request, our server sees your IP address while handling these. We do not use it for profiling and do not associate it with any account.

## The AI assistant

**The AI assistant does not go through our servers.** The launcher connects directly to the model service endpoint you enter in settings, using your own API key. Conversations, logs, mod lists — we never receive any of it, so there is nothing for us to retain.

The trade-off is that this content does go to the model provider you chose. How they handle and retain it is governed by your agreement with them and is outside our control. Please read the list below as a disclosure of what you are handing to a third party.

### What may be sent when you ask a question or ask it to diagnose a problem

- Your question itself and the context of the current conversation.
- Game logs (by default the tail of `latest.log`, distilled to the important lines; you can also ask it to read the full file).
- The full text of crash reports.
- The mod list of the instance, along with versions and loader information.
- Device information: CPU model and core count, machine model, architecture, memory size, operating system name and version, free disk space.
- File paths, including Java installation paths and instance paths.

> ⚠️ The launcher currently **performs no redaction on any of this**. Logs, crash reports and paths normally contain your home directory name (for example `C:\Users\YourName\…`), so if your system username is your real name, it will appear verbatim in what is sent to the model provider. This is what the current implementation does, and we would rather state it than gloss over it.

### Where conversations are stored

Only on your own computer, under `ai/sessions/` in the data directory, one file per conversation. There is no place on our servers where conversations are kept — **the server has no endpoint that receives them at all**.

### How to turn it off

The AI assistant only works once you have entered a model service endpoint, a model name and an API key in settings. Leave them empty and it cannot run, so nothing is sent. If you have already configured it and want to stop using it, clear those fields. The API key is stored in the same place as account tokens (the Keychain on macOS in installed mode, an 0600 local file otherwise); it is not written into the settings file and is not included when settings are exported.

## Third-party services

The launcher contacts the following services in response to what you do. Each has its own privacy policy, which we cannot make promises on behalf of.

- **Microsoft / Mojang**: authentication, and downloading the game itself, its assets and libraries.
- **Modrinth, CurseForge**: searching for and downloading mods, modpacks and resource packs.
- **Mirror nodes**: faster downloads of game files; switchable or disableable in settings.
- **The official Fabric, Forge, NeoForge and Quilt sources**: loader files.
- **Adoptium**: automatically downloading the Java runtime an instance needs.
- **Reference sites, video sites and search engines**: used by the AI assistant when it looks something up, only when it needs to.
- **Crafatar**: fetching your skin avatar by account UUID.

## Children's privacy

The launcher does not separately collect information from children and has no account system of its own. Game accounts are managed by Microsoft; parental controls and age-related rules are governed by Microsoft's policies.

## Changes to this policy

When features change and data flows change, this page changes with them and the date at the top is updated. If a change ever leaves this page out of date, that is an oversight on our part — please write in and point it out.

## Contact

For privacy questions, correction requests, or if you find a sentence on this page that does not match the actual implementation: write to **admin@klp-launcher.com**.
