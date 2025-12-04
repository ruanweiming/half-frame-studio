**[English](README.md) | [中文](README.zh.md)**

---

# 📸 Half-Frame Studio

**Automatic Half-Frame Splitter & Stitcher**

**[🌐 Live Demo: https://half.wayming.xyz/](https://half.wayming.xyz/)**

---

## 📖 Project Introduction

Half-Frame Studio is a pure front-end web application designed for half-frame film photographers. It automatically detects the dark center strip (gap) in scanned negatives, performs precise splitting, correction, and stitching—all processed **locally** in your browser. Images never leave your device.

**Use Cases:**
- Film shot with half-frame cameras (e.g., Ricoh Auto Half EF2)
- Batch processing of entire roll scans
- Creating long-format stitched compositions from multiple half-frames

---

## ✨ Key Features

### 🔒 Privacy & Security
- **100% Local Processing**: All image processing happens in your browser, no network required
- **No Server Interaction**: Image data never leaves your device
- **Offline Capable**: Works offline after initial page load

### 🤖 Smart Detection
- **Auto Gap Detection**: Automatically identifies the dark center strip using brightness analysis
- **Batch Processing**: Import entire rolls at once with automatic detection
- **Anomaly Flagging**: Automatically flags frames with detection issues (night shots, uneven exposure, etc.)

### 🎯 AI Auto Fix
- **Smart Calibration**: Calculates median gap width across the roll to auto-correct anomalies
- **Exposure Compensation**: Automatically corrects detection bias caused by uneven exposure
- **Adjustable Sensitivity**: Fine-tune detection sensitivity for different shooting scenarios

### 🎨 Fine Editing
- **Pixel-Level Adjustment**: Click to enter edit mode, drag the divider for precise fine-tuning
- **Independent Rotation**: Rotate left and right frames separately (90°, 180°, 270°)
- **Live Preview**: Real-time preview of crop results while editing
- **Reset Function**: One-click reset to auto-detection results

### 🖼️ Stitch Workshop
- **Dual Mode Support**:
  - **Synthetic Mode**: Generate clean gaps with customizable width and noise level
  - **Natural Mode**: Preserve real film gap texture (light leaks, dust, grain) for authentic film look
- **Drag to Reorder**: Drag and drop on timeline to adjust image order
- **Unlimited Stitching**: Stitch any number of images into long-format compositions

### 📊 Management Features
- **Smart Sorting**: Sort by filename or date (ascending/descending)
- **Batch Selection**: Checkbox selection, Ctrl+A select all, ESC deselect
- **Filter Views**: Filter by All/Alerts/Selected
- **View Size**: Adjust thumbnail size to fit different screens

### ⚡ Performance Optimization
- **Web Worker**: Multi-threaded processing without blocking the main thread
- **Concurrent Export**: Smart chunking to prevent memory overflow
- **Thumbnail Pipeline**: Generates downscaled thumbnails for grid view and stitch assets to significantly reduce memory usage (configurable via `THUMBNAIL_MAX_WIDTH`)
- **Original Mode Toggle**: Optional “Original Mode” switch intended for desktop use; mobile devices default to thumbnail mode for better stability
- **Mobile-Safe Concurrency**: Device-aware worker concurrency limits (e.g. fewer parallel tasks on phones) to avoid Safari memory crashes when importing large batches
- **Memory Management**: Aggressive release of `ImageBitmap` objects and Blob URLs after analysis/export to keep long sessions stable

---

## 🚀 Quick Start

### Usage Steps

1. **Import Images**
   - Click "Add Images" or drag entire roll scans onto the page
   - Supports batch import with automatic detection

2. **Adjust Settings**
   - **Cutting Mode**:
     - Auto Crop: Directly outputs two half-frame images
     - Keep Gap: Preserves full strip with divider indicator (ideal for stitching)
   - **Sensitivity**: Adjust detection strictness (Low=strict, High=loose)
   - **AI Auto Fix**: Automatically corrects anomaly frames when enabled

3. **Edit & Correct**
   - Click an image to enter edit mode
   - Drag the red divider to fine-tune cut position
   - Use bottom buttons to rotate left/right frames
   - Press ESC to exit editor

4. **Select & Export**
   - Check the circle on top-left to select images
   - Use Ctrl+A to select all, ESC to deselect
   - Click "Export Selected" or "Export All" for batch export
   - Exports as ZIP archive containing all cropped images

5. **Stitch Creation**
   - Select multiple images and click "Stitch"
   - Add assets to timeline in Stitch Workshop
   - Drag to reorder, choose gap mode
   - Save the stitched result

### Keyboard Shortcuts

- `←` / `→`: Navigate frames in edit mode
- `ESC`: Exit editor / Deselect all
- `Ctrl + A` / `Cmd + A`: Select all filtered images

---

## 🛠️ Tech Stack

- **Pure Frontend**: HTML5 + CSS3 + Vanilla JavaScript
- **Canvas API**: Image processing and rendering
- **Web Worker**: Multi-threaded image analysis and export
- **File API**: Local file reading and processing
- **JSZip**: ZIP compression and packaging
- **Responsive Design**: Desktop and mobile support

---

## 🏗️ Deployment Guide

This project consists of pure static files and can be deployed on any server capable of hosting HTML/CSS/JS.

### Method 1: Docker Deployment (Recommended)

1. **Prepare Files**
   ```bash
   # Ensure project files are in server directory
/root/var/www/half-frame-studio/
   ```

2. **Start Nginx Container**
```bash
sudo docker run --name half-frame-web \
--restart unless-stopped \
-p 8000:80 \
-v /root/var/www/half-frame-studio:/usr/share/nginx/html:ro \
-d nginx:alpine
   ```

3. **Configure Reverse Proxy (Nginx Proxy Manager)**
   
   Set up forwarding in NPM:
   
   | Setting | Value |
   | :--- | :--- |
   | Domain Name(s) | half.wayming.xyz |
   | Scheme | http |
   | Forward Hostname / IP | 127.0.0.1 |
   | Forward Port | 8000 |

### Method 2: Direct Deployment

Upload project files to any web server (Apache, Nginx, GitHub Pages, Netlify, Vercel, etc.).

---

## 📝 Usage Tips

- **Best Experience**: Recommended to use on desktop for better screen space and mouse control
- **Mobile Support**: Works on mobile devices; drag divider lines directly on images
- **Original Mode**: On desktop you can enable **Original Mode** for maximum image quality in grid and editor; on mobile it’s recommended to keep it off so the app uses thumbnails and stays stable even with many high‑res scans
- **Data Safety**: Refreshing or closing the page will lose data; export results promptly
- **File Formats**: Supports common image formats (JPEG, PNG, WebP, etc.)
- **Duplicate Detection**: Automatically detects and skips duplicate files

---

## 📜 License

This project is licensed under **CC BY-NC-SA 4.0**.

**CC BY-NC-SA 4.0 (Attribution-NonCommercial-ShareAlike 4.0 International)**

This license allows you to:
- ✅ Share and adapt this work
- ❌ Strictly prohibits commercial use (NC)
- ✅ Requires distribution of derivatives under the same license (SA)

---

## 🙏 Acknowledgments

Thanks to all half-frame film photographers for their support and feedback!

---

**Made with ❤️ for the half-frame photography community**
