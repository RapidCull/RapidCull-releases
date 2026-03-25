# Keyboard Shortcuts

RapidCull is designed for keyboard-first interaction. Every core action has a keyboard shortcut so you can cull efficiently without reaching for the mouse.

Press `?` at any time to open the in-app shortcuts overlay.

---

## Labeling

These shortcuts work in both the grid view and the viewer.

| Shortcut | Action |
|----------|--------|
| `P` | Label as **Pick** |
| `C` | Label as **Candidate** |
| `X` | Label as **Reject** |
| `U` | Remove label (**Unlabeled**) |

---

## Grid Navigation

| Shortcut | Action |
|----------|--------|
| Arrow keys | Move selection through the grid |
| `Tab` | Move to next image |
| `Shift+Tab` | Move to previous image |
| `Enter` | Open selected image in the viewer |

---

## Viewer Navigation

| Shortcut | Action |
|----------|--------|
| Left Arrow / `J` | Previous image |
| Right Arrow / `K` | Next image |
| `Escape` | Close viewer and return to grid |
| `F` (hold) | Show Focus Assist overlay (release to hide) |
| `I` | Toggle Photo Info panel |
| `B` | Toggle subject bounding box overlay (only active when detection data exists) |

---

## Viewer Zoom

| Shortcut | Action |
|----------|--------|
| `+` or `=` | Zoom in |
| `-` or `_` | Zoom out |
| `0` | Reset to fit-to-screen |
| Double-click | Toggle between fit and 100% zoom |
| Scroll wheel | Zoom toward cursor position |
| Click + drag | Pan when zoomed in |

---

## Filtering

| Shortcut | Action |
|----------|--------|
| `1` | Show **all** images |
| `2` | Show **Picks** only |
| `3` | Show **Candidates** only |
| `4` | Show **Rejects** only |
| `5` | Show **Unlabeled** only |

---

## Burst Comparison

`B` in the grid enters burst comparison mode for the selected image. This is a separate context from the viewer `B` shortcut above — both use the same key but in different screens.

| Shortcut | Action |
|----------|--------|
| `B` | Enter burst comparison mode (when a burst member is selected in the grid) |
| `1` or Left Arrow | Pick the **left** image (champion) |
| `2` or Right Arrow | Pick the **right** image (challenger) |
| `Shift+1` or `Shift+Left` | Pick left; mark right as **Candidate** |
| `Shift+2` or `Shift+Right` | Pick right; mark left as **Candidate** |
| `1`–`9` _(confirmation screen)_ | Toggle the corresponding loser thumbnail as Candidate |
| `Enter` _(confirmation screen)_ | Apply labels |
| `Z` | Undo last pick (also reverts any candidate mark from that pick) |
| `V` | Toggle layout (side-by-side / top-bottom) |
| `L` | Toggle linked zoom between both panes |
| `?` | Show/hide shortcuts help overlay |
| `Escape` | Exit burst comparison / cancel confirmation |

---

## General

| Shortcut | Action |
|----------|--------|
| `?` | Toggle keyboard shortcuts help overlay |
| `Escape` | Close current overlay / return to previous view |

---

## Quick Reference Card

```
LABELING          GRID              VIEWER            FILTERING
P  Pick           Arrows  Move      J/Left   Prev     1  All
C  Candidate      Tab     Next      K/Right  Next     2  Picks
X  Reject         S-Tab   Prev      Esc      Close    3  Candidates
U  Unlabeled      Enter   Open      +/-      Zoom     4  Rejects
                                    0        Fit      5  Unlabeled
                                    F(hold)  Focus Assist
                                    I        Photo Info
                                    B        Bbox overlay*

BURST COMPARISON                    ZOOM
B         Enter burst mode          +/=      Zoom in
1/Left    Pick left (champion)      -/_      Zoom out
2/Right   Pick right (challenger)   0        Reset fit
S+1/Left  Pick left, mark right     Dbl-clk  Fit/100%
S+2/Right Pick right, mark left     Scroll   Zoom to cursor
1-9       Toggle candidate (confirm) Drag    Pan
Enter     Apply (confirm screen)
Z         Undo
V         Toggle layout
L         Linked zoom
Esc       Exit

* Viewer B: toggle subject bounding box; only active when AI detection data exists.
  Grid B: enter burst comparison for the selected image. Same key, different context.
```
