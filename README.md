# jRN - JS Renamer - JavaScript Renamer

**Free, portable bulk file renamer for Windows, with JavaScript renaming.**

Made by **Stefan Karlsson** · *Gazeomatic*

[![Download](https://img.shields.io/github/v/release/Siba79/jRN?label=Download&color=2563eb)](https://github.com/Siba79/jRN/releases/latest)\
[![Donate with PayPal](https://img.shields.io/badge/Donate-PayPal-FFC439?logo=paypal&logoColor=003087)](https://paypal.me/gazeomatic)\
![Windows 10/11](https://img.shields.io/badge/Windows-10%20%7C%2011-0d9488)\
![Freeware](https://img.shields.io/badge/License-Freeware-6b7280)

![jRN main window](docs/jrn_main.png)

## Download & start
1. Download `jRN_v<version>_Windows_x64_portable.zip` from [Releases](https://github.com/Siba79/jRN/releases).
2. Unzip it anywhere, for example `D:\Programs\jRN`.
3. Run `jRN.exe`. There's no installer.

Or install it with winget:  `winget install Gazeomatic.jRN`

**Portable:** jRN keeps its settings, scripts and undo log in a `jRN_data` folder next to `jRN.exe`.
Nothing is copied to Windows. To remove jRN, delete the folder.
The only optional system change is the Explorer menu (see below), and you can remove it again from the app.

## Features
- **Rules:** RegEx, Name, Replace, Case, Remove, Add, Append folder name, Numbering, Extension.
- **Rename files or folders:** tick *Rename folders* to rename folders (with all subfolders if you like).
- **Browse in the list:** Back, Forward and Up buttons, double-click a folder to open it.
- **JavaScript renaming** in the same style as Bulk Rename Utility: `fileProperty()`, `filePropertyNum()`, `counter`, `newName`, `object("folder")`, `padNum()` and more.
- Reads any Windows file property: image width/height, date taken, camera, music tags and more.
- Live preview. Red rows show problems such as duplicate names, files that already exist or invalid characters.
- Safe, all-or-nothing renaming, and **Undo** that works even after a restart.
- **Options > Show 'Open in jRN' in Explorer right-click menu** (optional, on/off). On Windows 11 it's under *Show more options*.

## Example script
```js
// HDR_<folder>_001_<longest side>px.jpg   e.g. HDR_Beard_001_4096px.jpg
var w = filePropertyNum('System.Image.HorizontalSize');
var h = filePropertyNum('System.Image.VerticalSize');
newName = "HDR_" + folderName + "_" + padNum(counter, 3) + "_" + Math.max(w, h) + "px";
```

## Support
jRN is freeware. If it saves you time, a donation is much appreciated:
**[paypal.me/gazeomatic](https://paypal.me/gazeomatic)**

See `LICENSE.txt` for the terms.

## Version history

### 1.2.2
- New default script: `HDR_<folder>_<number>_<longest side>px`, e.g. `HDR_Beard_001_4096px.jpg`

### 1.2.1
- Fixed: JavaScript renaming in the compiled release (a dukpy runtime file was missing)
- Wider Modified column

### 1.2.0
- **Rename folders** mode: a checkbox that switches the list from files to folders.
  All rules and JavaScript work on folder names, and a folder plus its subfolders can be renamed in one go
- Navigation in the file list: Back, Forward and Up buttons, double-click a folder to open it
  (Alt+Left / Alt+Right / Backspace)
- Undo also works for folder renames

### 1.1.3
- Fixed: 'Open in jRN' in the Explorer right-click menu now starts jRN (the menu pointed to a wrong path)
- The window always ends above the taskbar
- Help > Open log file

### 1.1.2
- 'Open in jRN' from Explorer always opens jRN, even if an old jRN process is stuck in the background
- An already open jRN window now comes to the front reliably
- Problems are written to `jRN_data\jrn.log`

### 1.1.1
- The jRN icon now shows next to 'Open in jRN' in the Explorer right-click menu

### 1.1.0
- Freeware release: compiled, portable build (settings stay in `jRN_data` next to `jRN.exe`)
- PayPal donate button and a new About window
- Settings from earlier versions are imported automatically

### 1.0.2
- Sharp jRN icon in the title bar and taskbar
- The window always fits on the screen

### 1.0.1
- Release zips with version numbers, and Windows file details in jRN.exe

### 1.0.0
- First version: rename rules, JavaScript renaming, file properties, live preview, undo
  and the Explorer right-click menu
