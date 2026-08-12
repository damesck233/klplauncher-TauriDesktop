# Changelog

User-facing release notes. Dates are release dates. 中文版：[CHANGELOG.zh-CN.md](CHANGELOG.zh-CN.md)

> The launcher is in **closed beta**, so version numbers move quickly — and a few of them
> (0.1.94, 0.1.96, 0.1.99) were test builds burned while debugging the update pipeline
> itself. They carried no user-facing changes and are not listed separately.

---

## 0.1.100 — 2026-08-11

**Fixed**

- On the portable build, self-update showed no download progress and sat at `0.0 MB`, which looked like a hang. It now reports the downloaded size as it goes.
- Added an overall timeout to the update download. Previously a stalled connection looked exactly like a slow download, leaving nothing to do but wait.

## 0.1.98 — 2026-08-11

**Fixed**

- Self-update on the portable build failed with a signature verification error.
- Update failures reported a single generic line ("failed to download the update"); the message now names the layer that actually failed.

## 0.1.97 — 2026-08-11

**Changed**

- **The portable build now updates by replacing the program in place.** It previously went through the installer, which put the new version in a different directory — so after updating you were still opening the old copy, and your instances appeared to have vanished.
- **Portable is now the default data mode.** Only a copy put there by the installer uses the system user directory, which means the portable build can ship as a single executable with no accompanying files.
- Removed the rule that switched back to installed mode whenever the system directory already held data — it made updated portable builds flip modes for no visible reason. Instances left behind in the system directory are now surfaced as a notice in settings.

**Improved**

- Settings now states **why the current data mode is what it is**, instead of leaving you to guess.

## 0.1.95 — 2026-08-11

**Added**

- **Third-party authentication** (authlib-injector / third-party Yggdrasil): sign-in wizard, launch-time injection, and account management UI.
- **Game directory migration**: a card in settings that lays out every "from → to" pair, requires two-step confirmation, and can be rolled back.
- Isolated instances now keep their game directory **inside your own game folder** (`<game folder>/versions/<version id>`) instead of the launcher's private data directory, with collision detection.

**Improved**

- AI chat: two adjacent reasoning blocks are merged into one; while thinking, only a green dot remains instead of extra text.

## 0.1.93 — 2026-08-11

**Fixed**

- When Java was explicitly requested for download, an existing system installation no longer silently substitutes for it — fixing "I clicked download and nothing was installed".

**Improved**

- The download pill at the bottom now yields space while the AI is streaming, so the two no longer overlap.

## 0.1.92 — 2026-08-11

**Fixed**

- Blank forced-update screen on Windows.
- The portable build failed to start at all from read-only media; it now falls back to storing data the way the installed build does.
- Paging through news on the home screen no longer sends stable releases to the download page.

---

Earlier versions were early closed-beta builds with no public release record.

Questions or suggestions: open an [issue](https://github.com/damesck233/klplauncher-TauriDesktop/issues/new/choose) or write to admin@klp-launcher.com.
