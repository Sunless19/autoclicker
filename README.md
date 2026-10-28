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
- Macros on a hotkey that mix keys, mouse clicks at fixed positions and pauses, e.g. `F7` → `V E L`, or `F8` → `V Click(500,300) {200} E`. Play them once, N times or on a loop.
- Name your macros, e.g. "open spotify automated"
- Global hotkeys (default **F6**) that work in any window
- Runs in the background from the system tray
- **Idle mode**: one switch (in the window or the tray menu) that turns everything off: hotkeys, clicking and macros
- Updates itself: click **Yes** on the update prompt and it installs the new version and restarts
- Never starts by itself with Windows or Linux

### Macro syntax

📖 **[Read the Macro Guide](MACROS.md)**: a step-by-step walkthrough, every step type, examples and troubleshooting.

| Step | Example | What it does |
|------|---------|--------------|
| Key | `V`, `Enter`, `Space`, `Up`, `F5` | Press and release the key |
| Combo | `Ctrl+C`, `Shift+Alt+F2` | Hold modifiers while pressing the key |
| Pause | `{500}` | Wait 500 ms |
| Text | `"gg wp"` | Type the text exactly as written |
| Click | `left-click`, `left-click(500,300)` | Click where the pointer is, or at a position |
| Other clicks | `right-click(x,y)`, `double-click(x,y)`, `middle-click(x,y)` | Same, with other buttons |
| Move | `Move(500,300)` | Move the pointer without clicking |

## Note

Many online games and services prohibit automated input, so check the rules before using it there.
