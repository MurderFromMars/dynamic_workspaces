
# Kyanite | Smart Dynamic Workspace Management for Plasma 6

Kyanite is a dynamic workspace script for KDE Plasma 6 designed to create a clean, predictable, and truly adaptive workspace environment. It was built to complement Krohnkite and to push Plasma closer to the behavior of a real dynamic tiling window manager rather than a traditional desktop with automation layered on top.

The core idea is simple: workspaces should appear only when they are needed, disappear when they are no longer useful, and never break the user’s spatial or mental model in the process.

---

## Why Kyanite Exists

The original dynamic workspace script by Maurges introduced the concept of maintaining an empty desktop, but its behavior often conflicted with tiling workflows. Desktops could shift unexpectedly, cleanup routines sometimes moved the user to a different workspace, and Plasma frequently started with more desktops than necessary. There was no system for managing startup behavior, preserving indices, or ensuring a stable workspace model.

Kyanite was created to address these issues directly. It reimagines dynamic workspaces from a tiling‑first perspective, emphasizing index stability, minimalism, and continuous automatic cleanup. The result is a calmer, more intentional workflow that pairs naturally with Krohnkite.

---

## Design Philosophy

Kyanite is built around a few guiding principles:

- Workspaces should be created only in response to real usage, not preemptively.
- There should be exactly one empty workspace when expansion is needed, and none when it is not.
- Workspace indices should remain stable so muscle memory and spatial awareness are never disrupted.
- Automatic behavior should be invisible. The system should feel steady, not reactive.

These principles mirror the behavior of dedicated tiling window managers and form the foundation of Kyanite’s design.

---

## Key Improvements Over Upstream

### Plasma 6 Focused Architecture

Kyanite targets Plasma 6 exclusively. By removing Plasma 5 compatibility layers and legacy abstractions, the codebase becomes simpler, cleaner, and more reliable. This reduces edge cases and ensures behavior aligns with modern Plasma internals.

### True Dynamic Workspace Behavior

Workspaces are created only when a window actually occupies the last available desktop. Empty workspaces are removed automatically when they no longer serve a purpose. At most, one empty workspace is maintained at the end, and only when it is needed.

This creates a more natural, dynamic growth and culling system.

### Index Preserving Compaction

One of Kyanite’s most important features is index preserving compaction. When empty desktops are removed, the user’s current workspace index is preserved whenever possible. Cleanup never moves the user unexpectedly.

This is essential for tiling workflows where spatial consistency matters.

### Minimal Startup State

Kyanite allows Plasma to start with exactly one desktop. No additional workspaces are created unless they are actually needed. The second workspace appears only when the first window layout requires expansion.

This resolves Plasma’s messy startup behavior that the original script left untouched.

### Continuous Automatic Maintenance

Workspace compaction and correction happen continuously and automatically. Cleanup is triggered on window creation, window removal, desktop switches, and client desktop changes. The workspace layout remains accurate at all times without manual intervention.

### Animation Safe Desktop Removal

Kyanite includes safeguards to work around Plasma 6 animation quirks when removing desktops. This ensures workspace transitions remain smooth and visually consistent, avoiding broken or skipped animations.

### Designed for Krohnkite

Kyanite is built with Krohnkite in mind. Stable workspace indices integrate naturally with tiled layouts. Automatic expansion supports workspace‑per‑context workflows. Cleanup logic avoids disrupting tiling state.

Together, Kyanite and Krohnkite create a workflow that feels much closer to a true dynamic tiling window manager than Plasma’s default behavior.

---

## Manual Desktop Manipulation

Kyanite is designed to manage workspaces automatically. Manual creation or removal of desktops in Plasma behaves in ways that Kyanite cannot safely track or correct.

### Manual Desktop Removal
Removing a desktop manually causes Plasma to renumber desktops before Kyanite receives any signals. This can lead to:

- Incorrect desktop numbering  
- Unexpected compaction behavior  

Kyanite will continue running, but the layout may become temporarily inconsistent.

### Manual Desktop Addition
Adding desktops manually is even more disruptive. Plasma may insert new desktops at unpredictable positions, and when Kyanite later compacts or when you switch desktops:

- KWin can crash due to mismatched internal indices  
- The desktop list may become unstable until Plasma restarts  

Manual addition is strongly discouraged.

### No Interception Possible
KWin scripting cannot block or override manual desktop creation or removal. If users manipulate desktops themselves, Kyanite cannot guarantee correct behavior.

### No Workarounds
Any workaround for these issues would be hack like in nature and would come at a high cost to stability and functionality. After extensive investigation, there is simply no way to fix manual desktop manipulation without making the script objectively worse. For this reason, any issues opened about problems caused by manual desktop manipulation will be ignored and closed.

---

## Summary

Kyanite is not a cosmetic fork or a minor tweak. It is a behavioral rewrite focused on delivering a cohesive, predictable dynamic workspace model for Plasma 6.

It provides stable index preserving behavior, minimal startup state, continuous automatic cleanup, and seamless integration with Krohnkite. For users who treat Plasma as a tiling environment rather than a traditional desktop, Kyanite offers a cleaner, more intentional way to manage workspaces.

---

## Credits

Kyanite began as a fork of the original dynamic workspace script by Maurges. Their work laid the foundation for dynamic workspaces in Plasma. Over time, Kyanite diverged so significantly that remaining a fork no longer made sense, and it is now maintained as a standalone project.

## License (GPL 3.0)

Kyanite is distributed under the GNU General Public License v3.0.
