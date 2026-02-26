# User Guide

This guide covers the core interface and workflow of RapidCull in detail: the grid view, viewer mode, labeling system, filtering, and project management.

---

## Table of Contents

- [The Labeling System](#the-labeling-system)
- [Grid View](#grid-view)
- [Viewer Mode](#viewer-mode)
- [Filtering](#filtering)
- [Burst Detection](#burst-detection)
- [Project Management](#project-management)
- [Settings](#settings)
  - [Integrations](#integrations)
- [Notifications](#notifications)

---

## The Labeling System

RapidCull uses a simple three-tier classification system to sort your images:

| Label | Color | Shortcut | Purpose |
|-------|-------|----------|---------|
| **Pick** | Green | `P` | Your best frames — the ones you will edit and deliver |
| **Candidate** | Yellow | `C` | Potential keepers — worth a second look |
| **Reject** | Red | `X` | Frames to discard — out of focus, duplicates, bad timing |
| **Unlabeled** | None | `U` | Default state — not yet reviewed |

Press `U` at any time to remove a label and return an image to the Unlabeled state.

### When to Use Each Label

- **Pick** — Use sparingly. These are the frames you're confident about. In a burst of 10 similar shots, there's usually 1-2 picks.
- **Candidate** — Use when you're unsure. Mark it as a candidate and come back later. Better to keep an image as a candidate than to accidentally reject a good frame.
- **Reject** — Use liberally. The faster you eliminate the clear rejects, the smaller your remaining set becomes.

Labels persist across sessions. When you reopen a project, all your labels are exactly where you left them.

---

## Grid View

The grid view is your primary workspace for browsing and organizing images.

### Layout

The grid automatically adjusts the number of columns based on your window width. Each cell is a fixed size with a small gap between thumbnails. Resizing your window immediately reflows the grid.

### Thumbnail Indicators

Each thumbnail can display:

- **Label dot** — A small colored dot indicating the image's current label (green, yellow, or red). Unlabeled images show no dot.
- **Burst badge** — A numbered badge (e.g., "3") appearing on images that are part of a burst group. The number indicates how many images are in that burst.

### Navigation

| Action | Input |
|--------|-------|
| Move selection | Arrow keys or `Tab` |
| Move selection backwards | `Shift+Tab` |
| Open selected image in viewer | `Enter` or double-click |

### Interactions

- **Single-click** on a thumbnail to select it. The selected image gets a visible border highlight.
- **Double-click** to open the image in the viewer.
- **Click a burst badge** to jump directly into burst comparison mode for that group.
- **Hover over a burst badge** to highlight all other images in the same burst group within the grid.

### Performance

RapidCull uses virtual scrolling to efficiently handle large projects. Only the visible rows (plus a small buffer) are rendered at any time. This means a project with 10,000+ images feels just as responsive as one with 100.

Thumbnails are generated in the background and cached to disk. The first time you open a project, you may see loading spinners as thumbnails are created. Subsequent opens are instant.

---

## Viewer Mode

The viewer provides a full-screen experience for examining individual images at full resolution.

### Opening and Closing

- Press `Enter` on a selected grid thumbnail, or double-click it
- Press `Escape` to return to the grid

### Navigation

| Action | Input |
|--------|-------|
| Next image | Right Arrow or `K` |
| Previous image | Left Arrow or `J` |
| Close viewer | `Escape` |

The viewer respects your current filter. If you're viewing only Picks, the next/previous navigation will only cycle through Pick images.

### Info Bar

The top of the viewer shows:
- The **filename** of the current image
- Your **position** in the sequence (e.g., "23 of 147")

### Bottom Bar

The bottom of the viewer shows:
- **Label buttons** — `P`, `C`, `X`, `U` buttons showing the current label state
- **Current label badge** — displays "Pick", "Candidate", "Reject", or "Unlabeled"
- **Zoom level** — shows "Fit" or the current zoom percentage (e.g., "142%")
- **Auto-Advance toggle** — checkbox to enable automatic advancement after labeling

### Labeling in the Viewer

Press `P`, `C`, `X`, or `U` to label the current image, or click the corresponding button in the bottom bar. The label is applied immediately and persisted.

### Auto-Advance

When enabled, labeling an image automatically advances to the next image in the sequence. This is extremely useful for rapid culling sessions — you can go through hundreds of images by repeatedly pressing `P`, `C`, or `X` without needing to navigate manually.

Toggle auto-advance using the checkbox in the viewer bottom bar.

### Zoom and Pan

The viewer starts in **Fit-to-Screen** mode, where the image is scaled to fill the available space.

| Action | Input |
|--------|-------|
| Zoom in | `+` or `=` |
| Zoom out | `-` or `_` |
| Reset to fit | `0` |
| Toggle fit / 100% | Double-click |
| Zoom toward cursor | Scroll wheel |
| Pan | Click and drag (when zoomed in) |

When zoomed in, the cursor changes to a grab icon. Click and drag to pan around the image. When you zoom close to the fit-to-screen scale, the viewer will snap back to fit mode automatically.

### Preloading

The viewer preloads the next and previous images in the background so that navigation feels instant. You won't notice any loading delay when moving through a sequence.

### Focus Assist

Focus Assist is a sharpness overlay you can invoke at any time in the viewer. Hold `F` (default, rebindable in Settings) to display it. Release the key to hide it.

While active, the overlay divides the image into a grid of regions. Low-sharpness areas are darkened, making soft focus immediately visible. A score badge in the corner shows an overall sharpness score from 0 to 100:

| Score range | Color | Meaning |
|-------------|-------|---------|
| 65–100 | Green | Sharp |
| 40–64 | Yellow | Moderate sharpness |
| 0–39 | Red | Soft or out of focus |

The grid detail level (coarse to fine) is adjustable in **Settings → Focus Assist**. Higher detail reveals smaller focus regions, useful for comparing fine differences between burst frames. Results are cached per image so re-invoking is instant.

### Photo Info Panel

Press `I` in the viewer to toggle the Photo Info panel — a sidebar showing the full EXIF metadata for the current image.

The panel displays:

| Field | Description |
|-------|-------------|
| **Camera** | Camera make and model |
| **Lens** | Lens name as recorded by the camera |
| **Shutter speed** | Exposure time (e.g., 1/500 s) |
| **Aperture** | f-number (e.g., f/2.8) |
| **ISO** | Sensor sensitivity |
| **Focal length** | As recorded in EXIF (not equivalent) |
| **Capture time** | Date and time the photo was taken |
| **File details** | Filename, format, and file size |

The panel sits alongside the image — the viewer canvas resizes to accommodate it so nothing is obscured. Press `I` again to close it.

### Missing Files

If an image file has been moved or deleted since the project was created, the viewer shows a folder icon with a "File not found" message. You can still navigate past missing files — the viewer won't crash.

---

## Filtering

The filter bar lets you focus on specific subsets of your images.

### Filter Options

| Filter | Shortcut | Shows |
|--------|----------|-------|
| All | `1` | Every image in the project |
| Picks | `2` | Only images labeled as Pick |
| Candidates | `3` | Only images labeled as Candidate |
| Rejects | `4` | Only images labeled as Reject |
| Unlabeled | `5` | Only images with no label |

### Live Counts

Each filter button displays the current count of images in that category. These counts update in real-time as you label images. This gives you a constant overview of your progress — you can see at a glance how many images you've reviewed and how many remain.

### Filter Persistence

The current filter affects:
- **Grid view** — only matching images are shown
- **Viewer navigation** — next/previous only cycles through matching images
- **Burst detection** — only bursts with 2+ visible members are shown

Switching filters is instant. There's no loading delay.

---

## Burst Detection

RapidCull automatically groups images into bursts based on capture time proximity.

### How It Works

When you open a project, RapidCull reads the capture timestamp from each image and groups images that were taken within a configurable time threshold of each other.

### Burst Threshold

The burst threshold determines how close in time two images must be to be considered part of the same burst. You can adjust this in the filter bar:

| Threshold | Best For |
|-----------|----------|
| 0.5s | Very fast continuous shooting (10+ fps) |
| 1.0s | Fast continuous shooting |
| **1.5s** (default) | Standard burst shooting |
| 2.0s | Moderate burst shooting |
| 3.0s | Loose grouping, slower sequences |

The threshold is saved and persists across sessions.

### Burst Badges

Images that belong to a burst show a numbered badge in the grid (e.g., "3" for a burst of three images). Click the badge or press `B` on a selected burst member to enter burst comparison mode.

For a complete guide on burst comparison, see [Burst Comparison](burst-comparison.md).

---

## Project Management

### Opening a Project

Click on any project in the home screen's project list to open it. RapidCull will:

1. Load the project database
2. Scan for any new or missing files
3. Generate thumbnails for new images
4. Display the grid view

### Missing File Detection

When you open a project, RapidCull checks that all indexed files still exist on disk. Files that have been moved or deleted are marked as "missing" — they show a distinct icon in the grid and a message in the viewer. Missing files are not deleted from the project database, so if you restore them, they'll work again.

### Deleting a Project

From the home screen, click the delete button next to a project to remove it from RapidCull. This removes the project from the registry. Your original image files are not affected.

### Project Data Storage

Each project stores its data in a `.rapidcull` folder inside the project directory. This folder contains your labels, cached thumbnails, and project settings. It is self-contained — you can safely move your project folder to a different location, just re-create the project in RapidCull pointing to the new path.

---

## Settings

The Settings dialog is accessible from the gear icon in the toolbar, available on both the Home screen and inside any open project. Settings are persisted across sessions.

### Appearance

Choose the application theme:

| Option | Behavior |
|--------|----------|
| **System** | Follows your operating system's dark/light preference (default) |
| **Dark** | Forces dark mode regardless of OS setting |
| **Light** | Forces light mode regardless of OS setting |

### Burst Comparison

| Setting | Default | Description |
|---------|---------|-------------|
| **Auto-apply winner label** | Off | When on, labels are applied immediately after each pick without a confirmation step |
| **Override existing labels on losers** | On | When off, already-labeled images keep their label; only unlabeled images receive the loser label |
| **Label losers as** | Reject | Choose whether losing images are labeled as Reject or left Unlabeled |

### Focus Assist

The **Analysis detail** slider controls the grid resolution used by Focus Assist (1 = Low, 5 = High). Higher detail divides the image into more regions, making it easier to pinpoint small areas of soft focus. The grid is orientation-aware — portrait images get taller grids.

### Integrations

Configure third-party application launch behavior.

| Setting | Description |
|---------|-------------|
| **Launch Lightroom Classic after export** | When enabled, RapidCull automatically opens Lightroom Classic once an export completes |
| **Lightroom Classic executable path** | Full path to the `Lightroom.exe` (Windows) or `Adobe Lightroom Classic.app` (macOS) executable |
| **Show launch option in export dialog** | When enabled, the export dialog shows a checkbox to trigger the launch; when disabled, the setting is hidden from the export dialog |

### Keyboard Shortcuts

Click any key badge to rebind that action. Press the desired key when prompted, or press `Escape` to cancel. Custom bindings are shown with a distinct style, with a **Reset** button to restore the default.

Rebindable actions:
- **Labeling** — Pick, Candidate, Reject, Remove label
- **Viewer** — Next image, Previous image, Focus Assist overlay
- **Burst Comparison** — Pick left, Pick right, Undo pick

Arrow keys always navigate in the viewer and burst comparison regardless of shortcut settings.

---

## Notifications

RapidCull uses toast notifications to communicate status:

- **Success** (green) — export complete, labels applied after burst comparison
- **Error** (red) — file not found, insufficient disk space
- **Warning** (yellow) — missing files detected on project open
- **Info** (blue) — informational messages (e.g., "No bursts available")

Notifications auto-dismiss after a few seconds.
