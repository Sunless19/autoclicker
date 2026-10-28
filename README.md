# AutoClicker

<img src="assets/icon.png" width="96" alt="AutoClicker icon">

A small, configurable autoclicker and key-macro player for **Windows and Linux**.

## Download

Get the latest version from the [Releases page](../../releases/latest):

- **Windows:** `AutoClicker.exe`. Just run it, no installer. If SmartScreen warns about an unsigned app, choose **More info → Run anyway**.
- **Linux:** `AutoClicker-linux-x86_64.tar.gz`. Extract it and run `./AutoClicker`. On **Wayland** (the default on recent Ubuntu and Fedora), run `./setup-permissions.sh` once, then log out and back in.

The app tells you when a new version is available.

## Features

- Click interval from milliseconds to hours; left, right or middle button; single or double click
- Repeat a set number of times or until stopped
- Click at the cursor or at a fixed position, with **Pick location**
- Key macros on a hotkey, e.g. `F7` → `V E L`, played once, N times or on a loop
- Global hotkeys (default **F6**) that work in any window

### Macro syntax

| Step | Example | What it does |
|------|---------|--------------|
| Key | `V`, `Enter`, `Space`, `Up`, `F5` | Press and release the key |
| Combo | `Ctrl+C`, `Shift+Alt+F2` | Hold modifiers while pressing the key |
| Pause | `{500}` | Wait 500 ms |
| Text | `"gg wp"` | Type the text exactly as written |

## Note

Many online games and services prohibit automated input, so check the rules before using it there.
