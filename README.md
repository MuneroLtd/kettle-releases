# Kettle

A macOS menu bar traffic light for every Claude Code session on your Mac — green, amber or red at a
glance — and a nudge that keeps coming back until you deal with the session that is waiting on you.

This repository holds Kettle's signed, notarised downloads. The source is private.

## Requirements

- macOS 14 Sonoma or later, Apple silicon
- Claude Code installed

## Install

**With Homebrew** (recommended — `brew upgrade` keeps it current):

```sh
brew install --cask muneroltd/tap/kettle
```

**Or download it:** open the [latest release](https://github.com/MuneroLtd/kettle-releases/releases/latest),
download `Kettle-<version>.zip`, double-click it, and drag **Kettle.app** into **Applications**.
Each release lists the zip's SHA-256 so you can check it with `shasum -a 256 Kettle-<version>.zip`.

Every build is signed with Munero Limited's Developer ID and notarised by Apple, so it opens with a
normal double-click — no right-click or security override needed.

## First run

1. Open Kettle from Applications. It lives in the menu bar; there is no Dock icon.
2. **Set Up Kettle** opens on its own and walks you through connecting it to Claude Code. Kettle backs
   up your Claude Code `settings.json` before adding its hooks, and merges rather than overwriting.
   Every step except the final checks can be skipped and revisited later from
   **Settings → General → Set Up Kettle…**
3. Sessions you start (or resume) in Claude Code from then on appear in the menu bar.

**Permissions.** Kettle needs none to track sessions and alert you. Clicking a session to jump to its
terminal asks for **Automation** for that terminal (Ghostty 1.3+, Terminal, iTerm2) the first time, and
older Ghostty needs **Accessibility**. Decline either and everything else keeps working.

Kettle makes no network connections and sends nothing off your Mac.

## Uninstall

First remove Kettle's hooks, which restores your earlier Claude Code settings:

```sh
/Applications/Kettle.app/Contents/MacOS/Kettle --uninstall-hooks
```

Then either `brew uninstall --zap --cask kettle` (which also removes Kettle's preferences and data), or
quit Kettle, drag it to the Bin, and delete `~/Library/Application Support/Kettle`.

## Problems

Check which version you have in **Settings → General → About**, and include it when you report an issue.

**Kettle is running but there is no menu bar icon.** On a MacBook with a notch, macOS hides menu bar items that do not fit beside it. Quit Kettle and open it again, or quit another menu bar app to make room. On macOS 26, also check that Kettle is on under **System Settings → Menu Bar → Allow in the Menu Bar**.
