# Macro Guide

A **macro** is a list of steps (key presses, mouse clicks, pauses, typed text) that AutoClicker plays when you press its hotkey. This guide shows how to write the **Steps** box in the **Macros** tab, starting from a real example.

> **Quickest start: record it.** Click **Record** in the Macros tab, do the actions yourself (press keys, click, scroll), then press **Esc**. AutoClicker writes the steps for you, pauses included. See [Recording a macro](#recording-a-macro).

## The basics

- **Separate steps with spaces.** Each word is one step, played left to right.
- **Upper or lower case doesn't matter.** `space`, `Space` and `SPACE` are the same.
- **Letters press the key.** `V` presses the V key, which types a lowercase `v` in a text box. For a capital letter, write `Shift+V` or `"V"`.
- Between steps, AutoClicker waits the **Delay** you set (50 ms by default).

## Walkthrough: `V E L space F12 P left-click right-click 1 H`

Here's what each step does, in order:

| Step | What happens |
|------|--------------|
| `V` | Presses and releases **V** |
| `E` | Presses **E** |
| `L` | Presses **L** |
| `space` | Presses the **Space** bar |
| `F12` | Presses **F12** |
| `P` | Presses **P** |
| `left-click` | Left-clicks **wherever the mouse pointer is right now** |
| `right-click` | Right-clicks wherever the pointer is |
| `1` | Presses the **1** key (the one above the letters, not the number pad) |
| `H` | Presses **H** |

With the default settings (50 ms between steps, keys held for 30 ms), the whole macro takes under a second.

### Making it more reliable

That macro works as written, but real apps often need a moment to react. Three common tweaks:

1. **Add pauses where something has to open or load.** If F12 opens a menu, give it time before pressing P:
   `V E L space F12 {300} P left-click right-click 1 H`
   `{300}` waits 300 milliseconds (0.3 s).
2. **Click at a fixed spot instead of wherever the mouse happens to be.** Put the screen position in brackets:
   `... P left-click(960,540) right-click(960,540) 1 H`
   You don't have to work out the numbers yourself: click **Add click…**, then click the spot on screen, and `Click(x,y)` is added to the end of your steps.
3. **Avoid hotkeys inside macros.** If F12 is also the hotkey for another macro (or for the clicker), pressing F12 inside this macro triggers that one too. Use keys that aren't hotkeys, or change the other hotkey.

## Everything you can write

### Keys

| Write | Key |
|-------|-----|
| `A` … `Z` | Letter keys |
| `0` … `9` | Number keys above the letters |
| `Num0` … `Num9` | Number pad keys |
| `F1` … `F24` | Function keys |
| `Enter` (or `Return`), `Tab`, `Space`, `Esc` (or `Escape`), `Backspace` | |
| `Delete` (`Del`), `Insert` (`Ins`), `Home`, `End`, `PageUp` (`PgUp`), `PageDown` (`PgDn`) | |
| `Up`, `Down`, `Left`, `Right` | Arrow keys |
| `Shift`, `Ctrl`, `Alt`, `Win`, `CapsLock`, `Pause` | Pressed on their own |
| `-` `.` `,` `/` `;` `'` `[` `]` `=` … | Punctuation: write the character itself |

### Key combos

Join keys with `+` to hold modifiers while pressing a key:

| Write | Does |
|-------|------|
| `Ctrl+C` | Copy |
| `Ctrl+Shift+Esc` | Open Task Manager (Windows) |
| `Alt+Tab` | Switch window |
| `Shift+V` | Capital V |

Modifiers are `Ctrl`, `Alt`, `Shift` and `Win`.

### Pauses

| Write | Does |
|-------|------|
| `{500}` | Wait 500 ms (half a second) |
| `{2000}` | Wait 2 seconds |

### Typing text

Put text in double quotes to type it exactly, spaces included: `"gg wp"`, `"hello@example.com"`. Text can't contain a `"` itself.

On Linux under Wayland, only characters on a US keyboard can be typed this way.

### Mouse

| Write | Does |
|-------|------|
| `left-click` or `Click` | Left-click where the pointer is |
| `left-click(500,300)` or `Click(500,300)` | Move to x=500, y=300 and left-click |
| `right-click`, `right-click(x,y)` (or `RClick`) | Right-click |
| `middle-click`, `middle-click(x,y)` (or `MClick`) | Middle-click (wheel button) |
| `double-click`, `double-click(x,y)` (or `DClick`) | Double-click |
| `Move(500,300)` | Move the pointer without clicking |
| `Ctrl+Click(500,300)` | Hold Ctrl while clicking (any modifier works) |

Positions are screen pixels: `(0,0)` is the top-left corner of your main screen, x grows to the right and y grows downward. With several monitors, screens to the left or above can have negative positions.

### Advanced steps

These are also listed in the **Advanced** tab, where **Insert** adds one to your macro.

| Write | Does |
|-------|------|
| `Scroll(-3)` | Scroll the mouse wheel: negative scrolls down, positive up (in notches) |
| `HScroll(2)` | Scroll sideways: positive right, negative left |
| `Hold(Shift)` | Press a key and keep it held during the following steps |
| `Release(Shift)` | Let go of a key held with **Hold** |
| `MouseDown(500,300)` or `MouseDown` | Press the left mouse button (at a position, or where the pointer is) and keep it held |
| `MouseUp(700,300)` or `MouseUp` | Let go of the left mouse button |
| `Drag(500,300,700,300)` | Press at the first position, move smoothly to the second, and let go |

Anything still held when a macro ends or is stopped is let go automatically, so a key or button can never stay stuck.

Example, select several files with Shift held: `Click(400,300) Hold(Shift) Click(400,500) Release(Shift)`

## Recording a macro

1. In the **Macros** tab, click **Record**. Your hotkeys pause while recording, so pressing them gets recorded instead of triggering.
2. Do what you want the macro to do: press keys and combos, click, double-click, drag, scroll.
3. Press **Esc** (or click **Stop**). The steps appear in the Steps box, added after anything already there.
4. Check them, adjust if you like, then click **Add** or **Save changes**.

Pauses longer than about 0.15 s are kept as `{…}` steps, so the macro plays back at your pace; delete them to make it faster. Clicks are recorded at their exact screen positions. Clicks on AutoClicker's own window (like the Stop button) are left out.

On Linux with Wayland, clicks are recorded without a position (Wayland hides where the mouse is). On X11 the mouse wheel isn't recorded.

## Only in a specific app

Tick **Only in app** on a macro (or on the clicker, in the Clicker tab) and choose the app: pick it from the list of open apps, type its name (like "spotify"), or type part of its window title. Untick it to run in any app again; the app you chose is remembered.

- A macro only starts while that app is focused, and stops if you switch away.
- The clicker pauses while another app is focused and continues when you come back.
- On Linux with Wayland, the focused app can't be detected, so limited macros won't run there.

## Emergency stop

Press **Ctrl+Alt+P** (change it in **Settings**) to stop clicking and every macro at once. AutoClicker also switches on **Idle mode**, so nothing starts again until you untick it. The emergency stop key works even in Idle mode.

You can also push the mouse into **any corner of the screen** while something runs, which does the same. Corners that a macro or the clicker moves to itself don't count. This can be turned off in Settings, and isn't available on Wayland.

## The other settings

| Setting | What it does |
|---------|--------------|
| **Name** | Your label for the macro, e.g. "open spotify automated". To rename, double-click the name in the list. |
| **Hotkey** | The key that starts the macro, e.g. `F8` or `Ctrl+F8`. Press it again to stop a running macro. Can be left empty to keep a macro without a hotkey for now. |
| **Only in app** | Tick it and choose an app to limit the macro to that app (see above). Unticked, it runs in any app. |
| **Mode** | **Play once**, **Repeat N times** (set **Times**), or **Loop until stopped** (until you press the hotkey again). |
| **Delay (ms)** | Wait between steps. Raise it if an app misses steps. |
| **Hold (ms)** | How long each key stays pressed. Some games ignore very short presses; try 50–100 ms. |

After editing, click **Add** for a new macro, or select one in the list and click **Save changes**.

## Examples

| Name | Steps | Mode |
|------|-------|------|
| open spotify automated (Windows) | `Win {500} "spotify" {700} Enter` | Play once |
| copy line to next line | `Home Shift+End Ctrl+C Down Ctrl+V` | Play once |
| fill a form | `Click(700,400) "John" Tab "Smith" Tab "john@example.com" Enter` | Play once |
| refresh every 10 s | `F5 {10000}` | Loop until stopped |
| click two buttons | `Click(400,300) {250} Click(400,360)` | Repeat N times |

## Troubleshooting

| Problem | Try |
|---------|-----|
| Nothing happens at all, hotkeys do nothing | **Idle mode** is on (the title bar says "Idle"), for example after an emergency stop. Untick it at the bottom of the window or in the tray menu. |
| A macro does nothing when you press its hotkey | It's limited to an app (**Only in app**) that isn't focused, or it has no hotkey. The status bar says which. |
| Everything stopped by itself | The mouse touched a corner of the screen (emergency stop). Turn that off in Settings if it gets in the way. |
| "Unknown key …" when saving | Check the spelling against the tables above. Steps are separated by spaces, so `left click` is two steps; write `left-click`. |
| Some keys are skipped | Raise **Delay**, or add `{200}` pauses where the app is busy. |
| A game ignores the keys | Raise **Hold** to 50–100 ms. Some games block simulated input entirely. |
| Clicks land in the wrong place | The window moved, or the click was picked on another monitor. Use **Add click…** again with the window where it will be. |
| Nothing happens in an app running as administrator (Windows) | Click **Run as admin** at the bottom of AutoClicker. |
| The macro starts another macro | One of its steps is another macro's hotkey. Change that hotkey or remove the step. |

> Many online games and services don't allow automated input. Check their rules before using macros there.
