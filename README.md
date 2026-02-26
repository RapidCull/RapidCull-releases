# RapidCull

A small desktop tool for fast photo selection.

RapidCull is a local-first application focused on one part of the photography workflow: going through large image sets and deciding which shots to keep. It is designed around quick keyboard interaction and simple labels, with export options that fit into existing editing workflows.

The idea is straightforward: review quickly, decide clearly, and continue editing in the tools you already use.

---

## What it does

RapidCull helps with:

- browsing large image folders efficiently
- marking images as keep / maybe / reject
- comparing similar shots in burst sequences
- exporting decisions as XMP sidecars for compatibility with Lightroom Classic and similar tools

It intentionally stays focused on selection rather than editing or heavy automation.

---

## Features

### Grid overview

Browse large shoots with smooth scrolling and clear visual labels.

### Keyboard-driven workflow

Navigate and label images without leaving the keyboard. Auto-advance helps maintain flow during large culling sessions.

### Burst comparison

Group images captured close together and quickly narrow them down to a preferred frame.

### XMP export

Save decisions as standard sidecar metadata so your ratings transfer cleanly into other software.

### Local storage

Projects stay on your machine. No cloud services, accounts, or uploads.

### Focus Assist

Hold `F` in the viewer to overlay a sharpness map on the current image. Low-sharpness regions are darkened and an overall score (0–100) is displayed, making it easy to spot focus differences between similar frames.

### Photo Info Panel

Press `I` in the viewer to open a sidebar showing full EXIF metadata for the current image — camera, lens, shutter speed, aperture, ISO, focal length, capture time, and file details.

### Lightroom Classic Integration

Optionally configure RapidCull to launch Lightroom Classic automatically after an export. Set the executable path once in **Settings → Integrations** and enable the toggle.

### Settings

Customizable theme (dark, light, or system), burst comparison behavior, Focus Assist detail level, rebindable keyboard shortcuts, and third-party integrations — all persisted across sessions.

### RAW + standard formats

Supports common RAW formats alongside JPEG, PNG, TIFF, BMP, and others.

---

## Quick start

1. Download RapidCull for your platform.
2. Create a project from a folder of images.
3. Browse and label images using `P`, `C`, and `X`.
4. Use burst comparison where helpful.
5. Export XMP metadata and continue editing in your preferred editor.

See [Getting Started](docs/getting-started.md) for more detail.

---

## Documentation

- [Getting Started](docs/getting-started.md)
- [User Guide](docs/user-guide.md)
- [Keyboard Shortcuts](docs/keyboard-shortcuts.md)
- [Burst Comparison](docs/)
