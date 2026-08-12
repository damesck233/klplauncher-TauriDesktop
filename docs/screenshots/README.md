# Screenshots

**This directory is still empty.** Screenshots have to come from a launcher running real
data — mocking them up would be pointless — so this is waiting on captures from an actual
install.

## What is needed

In order of importance. The first four are the ones the README and the CurseForge
application actually need:

| Filename | What to capture | Notes |
|---|---|---|
| `home.png` | Home screen: the continue-playing card plus recent instances | The single best "this is a real launcher" shot |
| `instances.png` | Instance list with several instances on different loaders | Shows instance isolation |
| `download-mods.png` | Mod browsing on the Downloads page | **Key shot for the CurseForge application** — shows the content sources are wired up |
| `ai-confirm.png` | The AI assistant with a confirmation card open | Shows "nothing runs until you approve it" |
| `tasks.png` | Task centre with a few downloads in progress | |
| `servers.png` | Server directory with player counts and latency | |
| `settings.png` | Settings | |

## Before capturing

- **Use one window size throughout** — 1280×800 or 1440×900 — and pick one theme, light or
  dark. Do not mix.
- **Redact personal information**: account names, skin avatars, real home directory paths
  (`C:\Users\YourName\…`), server IPs. These images are public.
- Real instance names and real mods are fine and make it look less like a demo.
- PNG, unscaled, no added borders or drop shadows (GitHub handles that).

## Once they are here

Add a section to the repository's `README.md` referencing them, for example:

```markdown
## Screenshots

| Home | Instances |
|---|---|
| ![Home](docs/screenshots/home.png) | ![Instances](docs/screenshots/instances.png) |
```
