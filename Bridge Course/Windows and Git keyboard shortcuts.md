# 🖥️ Windows, Git, & Keyboard Shortcuts Reference

An ultra-clean, comprehensive cheat sheet optimized for high-readability on GitHub. This document consolidates all essential system commands, terminal workflows, and recording guides into a single file.

---

## 📌 Quick Navigation
* [Method 1: Snipping Tool (Screenshots)](#1-snipping-tool-screenshots)
* [Method 2: Keyboard Shortcuts (Screenshots)](#2-keyboard-shortcuts-screenshots)
* [Method 3: Snipping Tool (Screen Recording)](#3-snipping-tool-screen-recording)
* [Method 4: Xbox Game Bar (Screen Recording)](#4-xbox-game-bar-screen-recording)
* [Method 5: Navigation & Tab Management](#5-navigation--tab-management)
* [Method 6: Core System Actions](#6-core-system-actions)
* [Method 7: Essential Git Terminal Shortcuts](#7-essential-git-terminal-shortcuts)
* [Method 8: Terminal Interface Shortcuts](#8-terminal-interface-shortcuts)

---

## 1. Snipping Tool (Screenshots)
Ideal for capturing specific, precise portions of your screen.

### 🚀 How to Use
1. Press `Win + Shift + S` (or search for **Snipping Tool** in the Start menu).
2. Drag a box over the exact area you want to capture.
3. The image is instantly saved to your clipboard.

### 🌟 Pro-Tips
* **Delayed Snipping:** Open the full app to set a 3, 5, or 10-second capture delay for open menus.
* **Text Extraction:** Click the **Text Actions** button in the app to copy text directly out of your screenshot.

---

## 2. Keyboard Shortcuts (Screenshots)
The fastest way to capture images without opening an app interface.



| Shortcut | Action | Save Location |
| :--- | :--- | :--- |
| `PrtScn` | Captures entire screen | Clipboard |
| `Alt + PrtScn` | Captures active window only | Clipboard |
| `Win + PrtScn` | Captures entire screen | `Pictures > Screenshots` |

> 💡 **Note:** On some keyboards, you may need to hold down the `Fn` key to activate the `PrtScn` functions.
> ⚙️ **Customization:** Go to `Settings > Accessibility > Keyboard` to make the `PrtScn` key launch the snipping overlay automatically.

---

## 3. Snipping Tool (Screen Recording)
Great for quick, flexible video clips of a specific desktop area.

### 🚀 How to Use
1. Open the **Snipping Tool**.
2. Click the **Recording (Camera)** icon.
3. Click **New** and draw a boundary around the area to record.
4. Toggle audio settings on the bar, then click **Start**.

### ⚙️ Video Settings
* **Audio Inputs:** Independent toggle switches control both your **Microphone** and **System Audio**.
* **Output Format:** Videos save automatically to `Videos > Screen Recordings` as `.mp4` files.
* **Quick Editing:** Click the post-capture notification to open and trim your video in **Clipchamp**.

---

## 4. Xbox Game Bar (Screen Recording)
Designed for high-performance, single-app, or gameplay recording. 

### 🚀 Essential Shortcuts
* `Win + G` — Toggle the main control dashboard overlay.
* `Win + Alt + R` — Instantly start or stop recording the active window.
* `Win + Alt + PrtScn` — Take a screenshot of the active window only.
* `Win + Alt + M` — Toggle your microphone on/off while recording.

### ⚠️ Limitations & Rules
* **App Lock:** It records only **one active application window** at a time. It cannot record the Windows Desktop or File Explorer.
* **Storage Location:** Clips save automatically to `This PC > Videos > Captures`.

---

## 5. Navigation & Tab Management
* **`Alt + Tab`** ─── Switch between open application windows
* **`Ctrl + Tab`** ─── Cycle forward through active browser tabs
* **`Ctrl + T`** ───── Open a brand new browser tab
* **`Ctrl + Shift + T`** ─ Reopen the last closed browser tab

---

## 6. Core System Actions



| Key Combination | Targeted Action |
| :--- | :--- |
| `Ctrl + F` | **Find** specific text on a page |
| `Ctrl + S` | **Save** the current file |
| `Ctrl + Shift + S` | **Save As** a new file/format |
| `Ctrl + P` | **Print** the active document |
| `Ctrl + Z` | **Undo** your last mistake |

---

## 7. Essential Git Terminal Shortcuts

### 🛠️ Working Directory & Staging
* **`git status`** ─── View modified, staged, and untracked files
* **`git add .`** ──── Stage all current changes for the next commit
* **`git add -p`** ─── Interactively review and stage changes line-by-line

### 💾 Committing & History
* **`git commit -m "msg"`** ─ Commit staged changes with a quick message
* **`git commit --amend`** ── Edit your very last local commit message
* **`git log --oneline`** ─── View a compact, single-line history of commits

### 🌿 Branches & Syncing
* **`git switch -c <name>`** ─ Create and instantly swap to a new branch
* **`git pull origin <name>`** ─ Fetch and merge updates from the remote repository
* **`git push origin <name>`** ─ Upload your local commits to the remote server

---

## 8. Terminal Interface Shortcuts
* **`Ctrl + C`** ─── Abort, kill, or stop the currently running command
* **`Ctrl + L`** ─── Clear the entire terminal screen instantly
* **`Tab`** ──────── Auto-complete directory names, file paths, or Git branches
* **`Up Arrow`** ─── Cycle backward through your previously entered commands

---

> 💡 **Pro-Tip:** Keep this markdown file in your root repository folder as `README.md` or inside a `.github/` folder for rapid team deployment.
