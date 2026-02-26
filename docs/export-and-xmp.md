# Export & XMP Integration

RapidCull's export system copies your selected images to a destination folder and generates XMP sidecar files that are fully compatible with Adobe Lightroom Classic. This lets you cull in RapidCull and seamlessly continue your workflow in your editor of choice.

---

## Table of Contents

- [Starting an Export](#starting-an-export)
- [Export Options](#export-options)
- [The Export Process](#the-export-process)
- [XMP Sidecar Files](#xmp-sidecar-files)
- [Lightroom Classic Integration](#lightroom-classic-integration)
  - [Auto-launch After Export](#auto-launch-after-export)
  - [Importing into Lightroom](#importing-into-lightroom)
- [Cancellation and Safety](#cancellation-and-safety)

---

## Starting an Export

1. Click the **Export** button in the top bar of the project view
2. The export dialog opens with configuration options
3. Configure your settings and click **Export**

---

## Export Options

### Destination Folder

Browse your filesystem to select where exported files should be placed. The destination must be:
- A valid, existing directory
- Writable by the current user
- On a drive with sufficient free space

RapidCull checks disk space before starting and will warn you if there isn't enough room.

### Label Selection

Choose which labeled images to include in the export:

| Option | Default | Description |
|--------|---------|-------------|
| **Include Picks** | On | Export images labeled as Pick |
| **Include Candidates** | On | Export images labeled as Candidate |
| **Include Rejects** | Off | Export images labeled as Reject |

A live count at the bottom of the dialog shows exactly how many files will be exported based on your current selection. This count excludes any files that have been marked as missing.

---

## The Export Process

RapidCull exports your files safely:

- Missing files (deleted or moved since import) are automatically excluded
- Disk space is checked before starting
- Files only appear in the destination once the entire export succeeds — if cancelled or interrupted, your destination folder is not left in a partial state
- For each exported image, an XMP sidecar file is generated with your label

During export, a progress dialog shows the number of files copied, the current file name, and a **Cancel** button to abort.

---

## XMP Sidecar Files

For each exported image, RapidCull generates a companion `.xmp` file with the same base name.

### Example

Exporting `IMG_0042.CR2` with a Pick label produces:
```
IMG_0042.CR2
IMG_0042.xmp
```

### Label Mapping

| RapidCull Label | XMP Color Label | XMP Star Rating |
|-----------------|-----------------|-----------------|
| Pick | Green | 5 stars |
| Candidate | Yellow | 3 stars |
| Reject | Red | 1 star |

---

## Lightroom Classic Integration

RapidCull's XMP output is designed to integrate seamlessly with Adobe Lightroom Classic.

### Auto-launch After Export

RapidCull can open Lightroom Classic automatically once an export completes.

To configure this, open **Settings → Integrations** and:

1. Set the **Lightroom Classic executable path** to the full path of your Lightroom installation
2. Enable **Launch Lightroom Classic after export**
3. Optionally enable **Show launch option in export dialog** — this adds a checkbox in the export dialog so you can decide per-export whether to launch Lightroom

When the option is hidden from the export dialog, the setting acts as a global toggle.

### Importing into Lightroom

1. **Export from RapidCull** to a destination folder
2. **Open Lightroom Classic**
3. **Import** the destination folder (File > Import Photos and Video)
4. Lightroom will automatically read the XMP sidecar files
5. Your **color labels** and **star ratings** appear immediately in Lightroom's Library module

### What You'll See in Lightroom

- **Picks** show up with a green color label and 5 stars
- **Candidates** show up with a yellow color label and 3 stars
- **Rejects** show up with a red color label and 1 star

You can use Lightroom's built-in filter bar to sort by color label or star rating, continuing the organization that you started in RapidCull.

### Working with Existing Lightroom Catalogs

If you're importing into an existing catalog, the XMP sidecars will be read during import. The labels and ratings will appear alongside any other metadata Lightroom extracts from the files.

---

## Cancellation and Safety

### Cancelling an Export

You can cancel an in-progress export at any time using the **Cancel** button in the progress dialog. When you cancel:

- The staging directory is cleaned up
- No files are left in a partial state in the destination
- Your project labels are unaffected

### Safe Exports

Your destination folder is never left in an incomplete state. If the export completes, all files are there. If it's cancelled or fails, the destination is untouched.
