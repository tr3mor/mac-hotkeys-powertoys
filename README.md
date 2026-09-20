# mac-hotkeys-powertoys

PowerToys Keyboard Manager config that remaps Windows hotkeys to their macOS equivalents.

`default.json` is a [PowerToys Keyboard Manager](https://learn.microsoft.com/en-us/windows/powertoys/keyboard-manager) settings file. It remaps modifier keys and a set of shortcuts so that muscle memory built on macOS (Command/Option-based editing, navigation, and window shortcuts) carries over to Windows.

## Installation

1. Install [PowerToys](https://learn.microsoft.com/en-us/windows/powertoys/install) and enable the **Keyboard Manager** module.
2. Close PowerToys.
3. Copy `default.json` to:
   ```
   %LOCALAPPDATA%\Microsoft\PowerToys\Keyboard Manager\default.json
   ```
   (back up your existing file first if you have custom remaps already).
4. Restart PowerToys.
5. Open **Keyboard Manager** settings to confirm the remaps show up under "Remap a key" / "Remap a shortcut".

Key codes below are Windows virtual-key (VK) codes, e.g. `162` = Left Ctrl, `164` = Left Alt, `91` = Left Windows/Command, `160` = Left Shift.

## Modifier key rotation

Three modifier keys are rotated so that pressing Ctrl behaves as Win, Win behaves as Alt, and Alt behaves as Ctrl. This lines up the physical position of the keys on a Mac-style keyboard (Control, Option, Command) with how those positions are used on macOS:

| Key pressed | VK | Becomes | VK |
|---|---|---|---|
| Left Ctrl | 162 | Left Win | 91 |
| Left Win | 91 | Left Alt | 164 |
| Left Alt | 164 | Left Ctrl | 162 |

Additionally:

| Key pressed | Sends |
|---|---|
| Caps Lock (20) | Win + Space (91;32) — switches the keyboard input language, Windows' built-in shortcut for cycling input languages |

## Shortcut remaps

PowerToys matches the exact original key combination before applying the single-key rotation above, so these overrides fire even though the individual keys involved are also remapped:

### Text editing / navigation

| Shortcut pressed | Becomes | Action |
|---|---|---|
| Alt + Backspace | Ctrl + Backspace | Delete previous word |
| Alt + ← | Ctrl + ← | Move one word left |
| Alt + → | Ctrl + → | Move one word right |
| Alt + Shift + ← | Ctrl + Shift + ← | Select one word left |
| Alt + Shift + → | Ctrl + Shift + → | Select one word right |
| Ctrl + ← | Home | Move to start of line |
| Ctrl + → | End | Move to end of line |
| Ctrl + ↑ | Ctrl + Home | Move to start of document |
| Ctrl + ↓ | Ctrl + End | Move to end of document |
| Ctrl + Shift + ← | Shift + Home | Select to start of line |
| Ctrl + Shift + ↑ | Ctrl + Shift + Home | Select to start of document |

### Window / app management

| Shortcut pressed | Becomes | Action |
|---|---|---|
| Alt + W | Ctrl + W | Close tab/window |
| Ctrl + Tab | Alt + Tab | Switch windows (task switcher) |
| Ctrl + Space | Alt + Space | Open PowerToys Run / launcher |
| Ctrl + M | Win + ↓ | Minimize window |

### Browser shortcuts

| Shortcut pressed | Becomes | Action |
|---|---|---|
| Ctrl + [ | Ctrl + L | Focus address bar |
| Ctrl + \\ | Ctrl + E | Focus search bar |
| Ctrl + ] | Ctrl + R | Refresh page |
| Ctrl + Shift + \\ | Ctrl + J | Open downloads |

### Undo/redo & misc

| Shortcut pressed | Becomes | Action |
|---|---|---|
| Ctrl + Shift + Z | Ctrl + Y | Redo |
| Ctrl + Shift + S | F12 | Custom (e.g. trigger a tool bound to F12) |
| Ctrl + = | Ctrl + Shift | Custom modifier combo |

## Notes

- `appSpecific` shortcut lists are empty; all remaps here are global (apply in every application).
- Edit `default.json` directly, or use the PowerToys Keyboard Manager UI, which will rewrite this file for you.
