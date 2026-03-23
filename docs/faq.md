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

## AI Analysis

### What is the AI Score?

The AI Score is a 0–100 composite quality number assigned to each image during analysis. Higher is better. It combines three signals: subject-region sharpness (55%), BRISQUE perceptual quality (35%), and subject detection confidence (10%, only applied when a subject is found). Color coding: green (≥70 = High), yellow (40–69 = Mid), red (<40 = Low).

### How do I run AI analysis?

Click the **Analyze** button in the project header toolbar. A progress bar appears below the toolbar while analysis runs. The button is only shown when the AI model is available — if you don't see it, see the next question.

### What if the Analyze button doesn't appear?

The Analyze button is hidden when the AI model is not loaded. This happens when the bundled `yolo11n.onnx` model file is missing from the application resources. In a standard RapidCull installation the model is included automatically. If you built the app from source, see the ONNX Runtime model setup section in the developer documentation.

All other features — labeling, burst comparison, export, Focus Assist — work normally without the AI model.

### What is subject detection?

During analysis, a YOLO model scans each image for recognizable subjects: people, birds, cats, dogs, horses, elephants, bears, zebras, and giraffes. When a subject is found, RapidCull records the subject class (e.g., "person"), detection confidence, and the bounding box coordinates. This information appears in the Photo Info panel (`I`) and can be visualized as a bounding box overlay in the viewer (`B`).

### What does the sharpness rating in the Photo Info panel mean?

The sharpness value is the Laplacian variance computed on the detected subject's bounding box region. If no subject was detected, it is computed on the full image. It is shown as Low (below 100), Med (100–499), or High (500 and above). This is a measure of local texture detail — a higher value generally corresponds to sharper focus in that region. The label reads "Subject sharpness" when a bbox is present, "Image sharpness" otherwise.

### Does AI analysis modify my image files?

No. All scores and detection results are stored in the project's `.rapidcull` database. Your original files are never touched.

### Can I re-run analysis after adding new images?

Yes. Clicking Analyze again will process any images that do not yet have a composite score. Already-analyzed images are not re-processed.

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

### What is the AI Score badge on thumbnails and in the viewer?

The AI Score (0–100, higher is better) is a composite quality score computed during AI analysis. It combines three signals:

- **Subject-region sharpness** — Laplacian variance measured on the detected subject bounding box, or the full image if no subject was detected (weight: 55%)
- **BRISQUE quality** — a perceptual no-reference image quality measure (weight: 35%)
- **Subject detection confidence** — a small bonus when a recognized subject (person, animal, etc.) is detected with confidence above 50% (weight: 10%)

Color coding: green (70–100) = high quality, yellow (40–69) = moderate, red (0–39) = low. The badge only appears after AI analysis has been run. Images that have not been analyzed show no badge.

### How do I report a bug or request a feature?

Please [open an issue](../../../issues) on this repository. Include:

- Your operating system and version
- The version of RapidCull you're using
- Steps to reproduce the problem
- Any error messages you saw
