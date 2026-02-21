# Frequently Asked Questions

---

## General

### What is RapidCull?

RapidCull is a desktop application built specifically for photo culling — the process of reviewing large sets of images and selecting the best frames. It is not an editor, not a DAM (digital asset manager), and not an AI auto-selector. It helps you make fast, structured decisions about which images to keep.

### What platforms does RapidCull support?

RapidCull is available for **Windows** and **macOS**.

### Does RapidCull require an internet connection?

No. RapidCull is fully local-first. All data is stored on your machine. No cloud services, no accounts, no internet connection needed.

### Is RapidCull free?

RapidCull is currently in beta and free to use. Check the [Releases](../../../releases) page for the latest version. See the [License Agreement](../LICENSE.md) for full terms.

---

## Projects & Files

### Does RapidCull modify my original files?

No. RapidCull never modifies, moves, or deletes your original image files. Labels and metadata are stored in a separate `.rapidcull` database inside the project folder. Export creates copies — your originals remain untouched.

### What's the difference between Direct and Import mode?

- **Direct mode** points RapidCull at an existing folder. Your files stay where they are.
- **Import mode** copies files from a source (like a memory card) into a new project folder.

Most users working with files already on their computer should use Direct mode. Import mode is useful when ingesting directly from a camera card.

### Can I move my project folder to a different location?

The project's `.rapidcull` folder is self-contained within your project directory. If you move the entire project folder, you'll need to create a new project in RapidCull pointing to the new location. Your original labels won't carry over automatically since they're stored in the database at the original path.

### What happens if I delete an image file after creating a project?

RapidCull detects missing files when you open a project. Missing files are marked with a distinct icon in the grid and a "File not found" message in the viewer. They don't cause crashes — you can still navigate past them. The label data for missing files is preserved in case the files are restored.

### How many images can RapidCull handle?

RapidCull is designed for large projects and can handle 10,000+ images without performance issues. The limiting factor is typically disk space for cached previews, not application performance.

### Does RapidCull scan subfolders?

Yes. When you create a project, RapidCull recursively scans the entire directory tree. All supported image files in all subfolders are included in the project.

---

## Labeling

### What do the labels mean?

| Label         | Purpose                                             |
| ------------- | --------------------------------------------------- |
| **Pick**      | Your best frames — the ones you'll edit and deliver |
| **Candidate** | Potential keepers — worth a second look             |
| **Reject**    | Frames to discard                                   |
| **Unlabeled** | Not yet reviewed                                    |

### Are labels saved automatically?

Yes. Every label change is saved immediately to the project database. There's no "save" button — your work is always preserved.

### Can I change a label after it's been set?

Yes. Simply press a different label key (`P`, `C`, `X`, or `U`) on any image to change its label. There's no undo for individual label changes in the grid/viewer, but the burst comparison mode has a dedicated undo (`Z`).

---

## Burst Comparison

### How does burst detection work?

RapidCull reads the capture timestamp from each image's metadata and groups images that were shot within a configurable time window of each other. The default threshold is 1.5 seconds.

### My bursts are too large / too small. What should I do?

Adjust the burst threshold in the filter bar. Lower values (0.5s, 1.0s) create smaller, tighter groups. Higher values (2.0s, 3.0s) create larger, looser groups. The threshold is saved across sessions.

### What happens to labels after burst comparison?

The winner is automatically labeled as **Pick** and all losers are labeled as **Reject**. If any of those images had existing labels, they will be overwritten.

### Can I skip burst comparison and label manually instead?

Absolutely. Burst comparison is optional. You can label any image manually using `P`, `C`, `X`, or `U` in the grid or viewer, regardless of whether it's part of a burst.

### What if I disagree with a burst comparison result?

After burst comparison completes, you can change any label manually. Just select the image in the grid and press a different label key.

---

## Export & Lightroom

### What gets exported?

RapidCull copies the original image files (not thumbnails or previews) along with an XMP sidecar file for each image. You choose which labels to include in the export.

### What is an XMP sidecar file?

An XMP sidecar is a small XML file that sits alongside your image file and contains metadata. RapidCull generates XMP sidecars with color labels and star ratings that are readable by Lightroom Classic and other Adobe applications.

### How do labels map to Lightroom?

| RapidCull Label | Lightroom Color | Lightroom Stars |
| --------------- | --------------- | --------------- |
| Pick            | Green           | 5 stars         |
| Candidate       | Yellow          | 3 stars         |
| Reject          | Red             | 1 star          |

### Can I export to Lightroom directly?

RapidCull doesn't integrate directly with Lightroom's catalog. Instead, you export files with XMP sidecars and then import the exported folder into Lightroom. Lightroom reads the XMP files automatically during import.

### What happens if I cancel an export?

The export is safely cancelled. No partial files are left in the destination — RapidCull uses a staging directory and only moves files to the final destination when the export is complete.

### Can I export to an external drive?

Yes. You can select any writable location as the export destination, including external drives, network drives, or cloud-synced folders.

---

## RAW Files

### Does RapidCull develop RAW files?

No. RapidCull extracts a preview from RAW files for fast viewing. Full RAW development is the job of your editing software (Lightroom, Capture One, etc.).

### Why do some RAW files look different in RapidCull vs. my editor?

RapidCull shows the preview image embedded in the RAW file by your camera, which uses the camera's default processing. Your editor applies its own processing, which may look different. For culling purposes — evaluating sharpness, composition, timing, and expression — the preview is sufficient.

### My camera's RAW format isn't listed. Will it work?

If your camera outputs files with one of the [supported extensions](supported-formats.md), RapidCull will attempt to read them. Most modern cameras use one of the supported formats. If your format isn't supported, you can convert to DNG using Adobe's free DNG Converter, which RapidCull fully supports.

---

## Performance

### Why are thumbnails slow to load the first time?

When you first open a project, RapidCull needs to generate thumbnails for all your images. This is a one-time process — the results are cached. Subsequent opens are instant.

### The grid feels slow with a very large project. What can I do?

RapidCull should handle 10,000+ images smoothly. If you're experiencing slowness, try:

- Ensuring your project folder is on an SSD (not a mechanical hard drive)
- Closing other memory-intensive applications
- Waiting for initial thumbnail generation to complete

---

## Troubleshooting

### Some images show an error icon in the grid

This means RapidCull couldn't generate a preview for that file. The file may be corrupted, or the embedded preview may be missing. You can still label the image, but it won't display a visual preview.

### I see a "File not found" message in the viewer

The original image file has been moved or deleted since the project was created. RapidCull tracks this state but doesn't prevent you from navigating. If you restore the file to its original location, it will appear again.

### The burst threshold doesn't seem to detect my bursts correctly

Some images may have inaccurate or missing capture timestamps in their metadata. Images without valid timestamps cannot be grouped into bursts. Ensure your camera's date/time is set correctly.

### Does RapidCull support dark mode?

Yes. Open Settings (gear icon in the toolbar) and choose **Dark**, **Light**, or **System** (follows your OS preference) under Appearance. The default is Dark.

### Can I customize keyboard shortcuts?

Yes. Open Settings and scroll to **Keyboard Shortcuts**. Click any key badge to rebind it, then press the desired key. Arrow keys always navigate in the viewer and burst comparison regardless of custom bindings.

### What does the Focus Assist score mean?

The score (0–100) represents the relative sharpness of the image. 65 or above (green) indicates a sharp image. 40–64 (yellow) is moderate. Below 40 (red) suggests soft or out-of-focus. Use it as a guide alongside your own visual judgment — the score is based on the embedded preview, not a full RAW decode.

### How do I report a bug or request a feature?

Please [open an issue](../../../issues) on this repository. Include:

- Your operating system and version
- The version of RapidCull you're using
- Steps to reproduce the problem
- Any error messages you saw
