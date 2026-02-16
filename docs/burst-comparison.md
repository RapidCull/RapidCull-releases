# Burst Detection & Comparison

Burst comparison is RapidCull's signature feature. It formalizes the process photographers already use — comparing similar frames side by side — into a structured knockout tournament that guarantees convergence in the minimum number of decisions.

---

## Table of Contents

- [How Burst Detection Works](#how-burst-detection-works)
- [Entering Burst Comparison](#entering-burst-comparison)
- [The Knockout Tournament](#the-knockout-tournament)
- [Controls](#controls)
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

| Shortcut           | Action                                            |
| ------------------ | ------------------------------------------------- |
| `1` or Left Arrow  | Pick the **left/top** image (champion)            |
| `2` or Right Arrow | Pick the **right/bottom** image (challenger)      |
| `Z`                | Undo the last decision                            |
| `V`                | Toggle between side-by-side and top-bottom layout |
| `L`                | Toggle linked zoom                                |
| `?`                | Show/hide keyboard shortcuts overlay              |
| `Escape`           | Exit burst comparison                             |

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

Press `Z` to undo the last decision. The previous challenger returns, and the tournament state rewinds by one step. You can undo multiple times to go back several rounds.

---

## Results

When the tournament completes (all challengers have been compared):

- The **winner** is automatically labeled as **Pick** (green)
- All **losers** are automatically labeled as **Reject** (red)
- A success notification confirms the labels were applied
- Burst comparison mode closes automatically

These labels are immediately visible in the grid and the filter counts update in real-time.

> **Note:** If any of the burst images already had labels before entering comparison, those labels will be overwritten by the tournament results.

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

### Combine with Manual Labeling

Burst comparison handles burst groups. For standalone images (not in bursts), use the standard labeling workflow in the grid or viewer. The two approaches complement each other:

1. **Burst comparison** — rapidly find the best frame in each group
2. **Manual labeling** — review remaining non-burst images individually
