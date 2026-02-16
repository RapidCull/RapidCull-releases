# Supported Formats

RapidCull supports a wide range of standard image formats and RAW camera formats. All supported formats can be browsed in the grid, viewed at full resolution, labeled, and exported with XMP sidecars.

---

## Standard Formats

| Format | Extensions | Notes |
|--------|-----------|-------|
| JPEG | `.jpg`, `.jpeg` | Full support. Displayed directly in the viewer. |
| PNG | `.png` | Full support. Displayed directly in the viewer. |
| TIFF | `.tiff`, `.tif` | Full support including multi-page TIFF (first page used). |
| BMP | `.bmp` | Basic support. |

---

## RAW Camera Formats

| Manufacturer | Format | Extension | Notes |
|-------------|--------|-----------|-------|
| Canon | CR2 | `.cr2` | Full support. |
| Canon | CR3 | `.cr3` | Full support. Newer Canon mirrorless format. |
| Nikon | NEF | `.nef` | Full support. |
| Sony | ARW | `.arw` | Full support. Alpha series RAW format. |
| Fujifilm | RAF | `.raf` | Full support. X-series RAW format. |
| Olympus / OM System | ORF | `.orf` | Full support. |
| Adobe | DNG | `.dng` | Full support. Universal RAW format. |
| Panasonic | RW2 | `.rw2` | Full support. Lumix series RAW format. |
| Generic | RAW | `.raw` | Basic support for generic RAW files. |

---

## How RAW Files Are Handled

RAW files are not fully decoded — that would be slow and is the job of your editing software. Instead, RapidCull extracts the preview image embedded in each RAW file for fast viewing. Most modern cameras embed high-resolution previews (often full-resolution) in their RAW files, which is more than sufficient for culling decisions — evaluating composition, sharpness, expression, and timing.

Previews and thumbnails are generated in the background and cached when you first open a project. You may see loading indicators briefly as they're created. Subsequent opens are instant.

---

## Recursive Directory Scanning

When you create a project, RapidCull scans the entire directory tree recursively. This means images in subfolders are included automatically. The `.rapidcull` cache directory is excluded from scanning.

For example, this structure:
```
my-shoot/
  day-1/
    IMG_0001.CR2
    IMG_0002.CR2
  day-2/
    IMG_0100.CR2
    IMG_0101.CR2
```

...would result in all four images being indexed in a single project.

---

## Unsupported Formats

RapidCull does not currently support:
- Video files (MP4, MOV, etc.)
- HEIF / HEIC images
- WebP images
- PSD / PSB (Photoshop) files
- Layered TIFF files (only the first page is used)

If RapidCull encounters unsupported files during scanning, they are silently skipped. Only files with recognized extensions are indexed.
