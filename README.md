

# Better Dynamic Workspaces

*A Plasma‑6‑native reimagining of the original **dynamic_workspaces** script created by **maurges**.*

This fork modernizes the original concept for Plasma 6, delivering predictable desktop ordering, GNOME‑like dynamic workspace behavior, and a clean, maintainable codebase.

---

# Why This Fork Exists ⚙️

The original dynamic_workspaces pioneered dynamic workspaces on KDE.  
However, it was designed for Plasma 5, and Plasma 6 introduced new APIs and behaviors that made certain patterns harder to maintain.

Under Plasma 6, the original script could encounter:

- Inconsistent desktop numbering after repeated add/remove cycles  
- All previous session desktops being restored on startup  
- The user starting on an arbitrary desktop  
- Increased complexity from supporting both Plasma 5 and 6  

This fork rebuilds the idea with a Plasma‑6‑first approach, producing a cleaner, more predictable, and more GNOME‑accurate experience.

---

# Key Features ✨

## Plasma 6‑Native Codebase
This fork uses Plasma 6’s virtual desktop API directly, resulting in:

- Cleaner, more maintainable logic  
- More reliable multi‑desktop window handling  
- No legacy compatibility layers  

---

## GNOME‑Style Dynamic Workspace Model 🖥️

The workspace lifecycle now mirrors GNOME’s behavior:

- Always start with **two** desktops  
- Always begin on **Desktop 1**  
- A new desktop is created only when a window occupies the last one  
- Empty desktops are removed automatically  
- The last desktop is always kept empty  

This ensures a minimal, self‑maintaining workspace layout.

---

# Unified Cleanup System

The original project relied on a **direction‑based “shift‑left” cleanup behavior**, where empty desktops were removed only when switching left, and windows were shifted to earlier desktop indices to maintain order.  
While clever, this approach became brittle under Plasma 6 and introduced unnecessary complexity.

This fork replaces that system with a **single GNOME‑accurate cleanup pass** that is:

- **Direction agnostic** — cleanup runs regardless of navigation direction  
- **Append only** — no shifting windows left, no index rewrites  
- **Gap free** — all empty desktops except the last are removed  
- **Stable** — the last desktop is always kept empty  
- **Consistent** — cleanup runs after every structural change  

By removing the shift left logic entirely, the workspace lifecycle becomes deterministic, predictable, and far easier to maintain.

---

## Consistent Desktop Renumbering 🔢
Desktops are always sequential:

**Desktop 1 → Desktop 2 → Desktop 3 → …**

Renumbering is automatic, robust, and keeps the pager and internal ordering consistent.

---

## Predictable Startup Behavior
The script ensures a clean and consistent session start:

- Always begins on Desktop 1  
- Always starts with exactly two desktops  
- Avoids Plasma’s default session‑restore clutter  

---

## Modernized Logic and Structure 🧹

The codebase removes:

- Deprecated APIs  
- Plasma 5 compatibility logic  
- Direction‑dependent cleanup  
- Middle‑desktop deletion rules  
- Index‑shifting window movement  

Replaced with:

- Direct Plasma 6 desktop objects  
- A unified cleanup pass  
- Clear add/remove rules  
- Reliable animation guarding  
- A simple, append‑only workspace lifecycle  

---

# Comparison With the Original Project 📊

| Feature | Original Project (maurges) | This Fork |
|--------|-----------------------------|-----------|
| Plasma 5 support | Yes | No |
| Plasma 6 support | Partial | Full, native |
| Startup desktops | Restores all from last session | Always 2 |
| Startup focus | Last used desktop | Always Desktop 1 |
| Desktop renumbering | No | Yes, always sequential |
| Dynamic behavior | Basic | GNOME‑like |
| Cleanup model | Direction‑based, shift‑left logic | Unified GNOME‑style cleanup |
| Workspace lifecycle | Mixed rules | Strictly append‑only |
| Code complexity | Higher | Reduced, Plasma 6 only |
| Window shifting | Required | Removed |
| Session consistency | Variable | Deterministic |

---

# License (MIT) 📄

This fork uses the MIT License — simple, permissive, and contributor‑friendly.

---

# Credits 🙏

This project is inspired by and builds upon the original **dynamic_workspaces** script created by **maurges**.  
Their work established the foundation for dynamic workspaces on KDE, and this fork continues that vision with a Plasma‑6‑native, GNOME‑accurate approach.
