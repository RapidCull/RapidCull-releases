# Burst Detection & Comparison

Burst comparison is RapidCull's signature feature. It formalizes the process photographers already use — comparing similar frames side by side — into a structured knockout tournament that guarantees convergence in the minimum number of decisions.

---

## Table of Contents

- [How Burst Detection Works](#how-burst-detection-works)
- [Entering Burst Comparison](#entering-burst-comparison)
- [The Knockout Tournament](#the-knockout-tournament)
- [Controls](#controls)
- [Marking Candidates During a Round](#marking-candidates-during-a-round)
- [Layout Options](#layout-options)
- [Zoom and Pan](#zoom-and-pan)
- [Undo](#undo)
- [Results](#results)
- [Tips for Effective Burst Comparison](#tips-for-effective-burst-comparison)

---

## How Burst Detection Works

When you open a project, RapidCull reads the capture timestamp from each image's metadata and groups images that were shot within a configurable time window.

### Burst Threshold

The burst threshold determines the maximum time gap between consecutive images for them to be considered part of the same burst.

| Threshold          | Use Case                                                   |
| ------------------ | ---------------------------------------------------------- |
| 0.5s               | Sports, wildlife — very fast continuous shooting (10+ fps) |
| 1.0s               | Action photography, fast continuous mode                   |
| **1.5s** (default) | General burst shooting, portraits, events                  |
| 2.0s               | Moderate-speed sequences                                   |
| 3.0s               | Loose grouping, bracketed exposures, slower sequences      |

You can change the threshold at any time using the dropdown in the filter bar. The threshold is saved and persists across sessions. Changing it triggers an immediate re-detection — burst groups update in the grid instantly.

### Filter-Aware Bursts

Burst detection respects your current filter. If you're viewing only Picks, a burst will only appear if it contains 2 or more Pick images. This prevents showing burst badges for groups where only one member is visible.

---

## Entering Burst Comparison

There are two ways to enter burst comparison mode:

1. **Select a burst member in the grid and press `B`**
2. **Click the burst badge** on any thumbnail in the grid

If the selected image is not part of a burst (or the burst has fewer than 2 visible members), RapidCull shows an informational notification.

---

## The Knockout Tournament

Burst comparison uses a sequential knockout format, similar to a single-elimination tournament:

### How It Works

1. The first image in the burst is loaded as the **champion** (left/top pane)
2. The second image is loaded as the **challenger** (right/bottom pane)
3. You compare the two and pick the stronger frame
4. The **winner becomes the new champion** and stays in place
5. The **next image in the burst** becomes the new challenger
6. Repeat until all images have been compared

### Why This Works

For a burst of _n_ images, this approach requires exactly **n - 1** decisions to find the best frame. There's no going back and forth, no re-comparing, no unresolved state. Every decision is final (though you can undo with `Z`).

Compare this to manually flipping through a burst:

- A 5-image burst requires 4 decisions (not 10+ comparisons)
- A 10-image burst requires 9 decisions (not dozens of back-and-forth flips)
- A 20-image burst requires 19 decisions (still tractable)

### Progress Indicator

During comparison, a progress indicator shows your position: e.g., "Round 3 of 7". This tells you exactly how many decisions remain.

---

## Controls

| Shortcut                   | Action                                            |
| -------------------------- | ------------------------------------------------- |
| `1` or Left Arrow          | Pick the **left/top** image (champion)            |
| `2` or Right Arrow         | Pick the **right/bottom** image (challenger)      |
| `Shift+1` or `Shift+Left`  | Pick left and mark right as **Candidate**         |
| `Shift+2` or `Shift+Right` | Pick right and mark left as **Candidate**         |
| `Z`                        | Undo the last decision                            |
| `V`                        | Toggle between side-by-side and top-bottom layout |
| `L`                        | Toggle linked zoom                                |
| `?`                        | Show/hide keyboard shortcuts overlay              |
| `Escape`                   | Exit burst comparison                             |

### RAW vs. Preview Toggle

When the burst group contains at least one RAW file, an image icon button appears in the top bar. Click it to toggle between **RAW** mode (decode full-size RAW after the initial embedded JPEG loads) and **Preview** mode (stay on the embedded JPEG only). The active state is indicated by an accent highlight on the button.

This toggle is shared with the single-image viewer — changing it in burst comparison also affects the viewer and vice versa. The setting persists across sessions.

---

## Marking Candidates During a Round

A burst of 8–15 images often contains a second or third strong frame. RapidCull gives you two ways to rescue runner-up images as **Candidates** without disrupting the tournament's pace.

### Option A — Shift modifier (inline, during rounds)

Hold **Shift** while picking to mark the losing image as Candidate instead of giving it the default loser label:

- `Shift+Left Arrow` or `Shift+1` — pick the left image; the right (losing) image is marked as Candidate
- `Shift+Right Arrow` or `Shift+2` — pick the right image; the left (losing) image is marked as Candidate

When Shift is held both panes gain a subtle amber tint to confirm candidate-marking mode is active. After the pick, the losing pane flashes amber rather than the usual grey dim.

This is additive — if you never use Shift, nothing changes.

**First-run hint:** A dismissible banner appears at the bottom of the burst overlay the first time you open burst comparison, reminding you that Shift is available. It disappears after you dismiss it and never reappears.

### Option B — Confirmation filmstrip (after all rounds)

When the tournament finishes and `Auto Apply` is off, the confirmation screen shows a horizontal filmstrip of all loser images below the winner preview. Any image you Shift-marked during the rounds appears pre-selected (amber border + checkmark badge).

You can also toggle any loser to Candidate here by:
- **Clicking** a thumbnail
- **Pressing the number key** shown on the thumbnail (`1`–`9`)

Thumbnails you leave unselected receive the default loser label (Reject or Unlabeled, per your Settings). `Enter` applies all selections; `Escape` cancels and returns to the last round.

> **Note:** When `Auto Apply` is enabled in Settings, the confirmation screen is skipped entirely. Option A candidate marks are still applied — the filmstrip is simply not shown.

---

## Layout Options

Toggle between two layouts with `V`:

### Side-by-Side (default)

Images are displayed next to each other horizontally. This works well on wide monitors and is the most natural layout for landscape-oriented images.

```
+-------------------+-------------------+
|                   |                   |
|    Champion       |    Challenger     |
|    (Left)         |    (Right)        |
|                   |                   |
+-------------------+-------------------+
```

### Top-Bottom

Images are stacked vertically. This can be useful for portrait-oriented images or when you want to see more vertical detail.

```
+---------------------------------------+
|              Champion                  |
|              (Top)                     |
+---------------------------------------+
|              Challenger                |
|              (Bottom)                  |
+---------------------------------------+
```

---

## Zoom and Pan

Each pane in burst comparison is a full-featured viewer with independent zoom and pan.

| Action | Input                           |
| ------ | ------------------------------- |
| Zoom   | Scroll wheel on the target pane |
| Pan    | Click and drag within a pane    |
| Fit    | Double-click to reset           |

### Linked Zoom

Press `L` to toggle **linked zoom**. When enabled:

- Zooming in one pane zooms the other to the same level
- Panning in one pane pans the other to match

This is useful for comparing fine details (sharpness, focus point, expressions) at the same position and magnification in both images.

---

## Undo

Press `Z` to undo the last decision. The previous challenger returns, and the tournament state rewinds by one step — including any candidate mark that was applied during that pick. You can undo multiple times to go back several rounds.

---

## Results

When the tournament completes (all challengers have been compared):

- The **winner** is labeled as **Pick** (green)
- Images you marked as **Candidate** (via Shift or the filmstrip) are labeled as **Candidate** (amber)
- Remaining losers receive the default loser label — **Reject** or **Unlabeled** — based on your Settings
- A success notification confirms the labels applied, including a candidate count when applicable
- Burst comparison mode closes automatically

These labels are immediately visible in the grid and the filter counts update in real-time.

> **Note:** By default, burst results overwrite any existing labels on the burst images. If you enable the "Only label unlabeled losers" option in Settings, only unlabeled images receive the loser label — Candidate-marked images and the winner are always written regardless.

---

## Tips for Effective Burst Comparison

### Adjust Your Threshold

If your bursts are too large (combining unrelated sequences), reduce the threshold. If bursts are splitting sequences that belong together, increase it. Start with 1.5s and adjust from there.

### Use Linked Zoom for Sharpness

When comparing similar frames, enable linked zoom (`L`) and zoom in to the subject's eyes or the primary focus point. Slight differences in sharpness become obvious at 100% zoom.

### Trust Your First Instinct

The knockout format works best when you make quick, intuitive decisions. Don't overthink each comparison — you're looking for the _better_ frame, not the _perfect_ frame. The entire point is to converge quickly.

### Work Through All Bursts in Sequence

After completing a burst comparison, select the next burst in the grid and press `B` again. Working through all bursts systematically is the fastest way to cull a burst-heavy shoot.

### Rescuing a Runner-Up

If a frame was strong but lost to an even better one, hold Shift while picking the winner — the loser becomes a Candidate instead of being rejected. You can also use the filmstrip on the confirmation screen to promote losers after the tournament if you realize one was worth keeping.

### Combine with Manual Labeling

Burst comparison handles burst groups. For standalone images (not in bursts), use the standard labeling workflow in the grid or viewer. The two approaches complement each other:

1. **Burst comparison** — rapidly find the best frame in each group
2. **Manual labeling** — review remaining non-burst images individually
