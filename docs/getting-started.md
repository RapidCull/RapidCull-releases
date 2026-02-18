# Getting Started

This guide walks you through installing RapidCull, creating your first project, and completing your first culling session.

---

## Installation

### Windows

1. Download the latest `.exe` installer from the [Releases](../../../releases) page
2. Run the installer and follow the on-screen prompts
3. Launch RapidCull from the Start Menu or desktop shortcut

### macOS

1. Download the latest `.dmg` file from the [Releases](../../../releases) page
2. Open the `.dmg` and drag RapidCull to your Applications folder
3. Launch RapidCull from Applications

> **Note:** On macOS, you may need to right-click and select "Open" the first time to bypass Gatekeeper. RapidCull is a legitimate application — this prompt appears for all newly downloaded apps.

---

## Home Screen

When you launch RapidCull, you'll see the home screen with:

- A **New Project** button to create or import a project
- A **Projects list** showing your recent projects with timestamps
- Quick access to open or delete existing projects

If this is your first time, the projects list will be empty — let's create one.

---

## Creating a Project

RapidCull offers two ways to start a project:

### Option 1: Direct Mode (Recommended)

Use this when your images are already organized in a folder and you want to work with them in place.

1. Click **New Project**
2. Select **Direct** mode
3. Browse to the folder containing your images
4. Click **Create**

RapidCull will scan the folder (including subfolders) and index all supported image files. Your original files are never moved or modified.

### Option 2: Import Mode

Use this when you want to copy images from a source (like a memory card) into a managed project folder.

1. Click **New Project**
2. Select **Import** mode
3. Browse to the **source folder** containing your images
4. Choose a **destination parent folder** where the project will be created
5. Enter a **project name** (defaults to today's date)
6. Click **Create**

RapidCull will copy all supported images from the source to a new project folder, showing progress as it goes. You can cancel the import at any time.

> **Tip:** Import mode checks available disk space before copying and handles filename collisions automatically.

---

## Understanding the Interface

Once your project opens, you'll see the main workspace:

### Top Bar

- **Project name** displayed at the top
- **Keyboard shortcuts help** — press `?` or click the help icon to see all shortcuts
- **Export button** — export your labeled images when you're done

### Filter Bar

- **Filter buttons**: All | Picks | Candidates | Rejects | Unlabeled
- Each button shows a **live count** of images in that category
- Use keyboard shortcuts `1` through `5` to switch filters quickly
- **Burst threshold** selector for adjusting burst detection sensitivity

### Grid View

- **Thumbnail grid** showing all images matching your current filter
- Each thumbnail shows a **label indicator** (green dot for Pick, yellow for Candidate, red for Reject)
- Images in bursts show a **burst badge** with the group count
- Click to select, double-click or press `Enter` to open the viewer

---

## Your First Culling Session

Here's a recommended workflow for culling a shoot:

### Step 1: Quick Scan

Browse through the grid to get an overview of the shoot. Use the arrow keys or click to navigate. Press `Enter` to open the viewer for any image that catches your eye.

### Step 2: Label Obvious Picks and Rejects

Start by identifying the clear winners and clear rejects:

- Press `P` to mark an image as a **Pick** (best frames)
- Press `X` to mark an image as a **Reject** (frames to discard)
- Press `C` to mark uncertain frames as **Candidates** (review later)

In the viewer, you can enable **Auto-Advance** to automatically move to the next image after labeling — this speeds up the workflow significantly.

### Step 3: Compare Bursts

For burst sequences (groups of rapid-fire shots), use burst comparison mode:

1. Select any image that shows a **burst badge** in the grid
2. Press `B` to enter burst comparison mode
3. Two images appear side by side — press `1` (or Left Arrow) to pick the left image, or `2` (or Right Arrow) to pick the right one
4. The winner advances, a new challenger appears
5. After all comparisons, the winner is labeled as Pick and losers as Reject

See the [Burst Comparison guide](burst-comparison.md) for a full explanation.

### Step 4: Review Candidates

Switch to the **Candidates** filter (press `3`) and make final decisions:

- Promote the best candidates to Picks (`P`)
- Demote the rest to Rejects (`X`)

### Step 5: Export

When you're satisfied with your selections:

1. Click the **Export** button
2. Choose a destination folder
3. Select which labels to include (Picks and Candidates are on by default)
4. Click **Export**

RapidCull copies your selected images to the destination and generates XMP sidecar files for Lightroom Classic compatibility.

See the [Export & XMP guide](export-and-xmp.md) for details.

---

## What's Next

- [User Guide](user-guide.md) — deep dive into the grid, viewer, and labeling system
- [Keyboard Shortcuts](keyboard-shortcuts.md) — full shortcut reference
- [Burst Comparison](burst-comparison.md) — master the knockout comparison workflow
- [Export & XMP](export-and-xmp.md) — understand export options and Lightroom integration
