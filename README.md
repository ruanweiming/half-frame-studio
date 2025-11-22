# 📸 Half-Frame Studio

**自动半格胶片切割与拼图工具 | Automatic Half-Frame Splitter & Stitcher**

**[🌐 Live Demo: https://half.wayming.xyz/](https://half.wayming.xyz/)**

<style>
.lang-toggle { display: inline-block; margin: 10px 0; }
.lang-toggle input[type="checkbox"] { display: none; }
.lang-toggle label { 
    display: inline-block; 
    padding: 6px 12px; 
    background: #2a2a2a; 
    color: #e5e5e5; 
    border: 1px solid #333; 
    border-radius: 6px; 
    cursor: pointer; 
    font-size: 13px;
    transition: all 0.2s;
}
.lang-toggle label:hover { background: #383838; border-color: #555; }
.lang-toggle input:checked + label { background: #0a84ff; border-color: #0a84ff; }
.lang-zh { display: none; }
.lang-en { display: block; }
.lang-toggle input:checked ~ .lang-zh { display: block; }
.lang-toggle input:checked ~ .lang-en { display: none; }
</style>

<div class="lang-toggle">
<input type="checkbox" id="lang-switch">
<label for="lang-switch">中文 / English</label>
</div>

<div class="lang-en">

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
- **Memory Management**: Automatic resource cleanup for extended use

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

</div>

<div class="lang-zh">

## 📖 项目简介

Half-Frame Studio 是一个专为半格胶片摄影玩家设计的纯前端 Web 应用。它能在浏览器本地自动识别底片扫描件中的中缝黑条，进行精确切割、修正和拼图，所有处理过程完全在本地完成，图片**绝不会**上传到任何服务器。

**适用场景：**
- 使用半格相机（如 Ricoh Auto Half EF2）拍摄的胶片
- 需要批量处理整卷底片扫描件
- 希望将多张半格照片拼接成长条作品

---

## ✨ 核心特性

### 🔒 隐私与安全
- **100% 本地处理**：所有图片处理均在浏览器本地完成，无需网络连接
- **无服务器交互**：图片数据不会上传到任何服务器
- **离线可用**：支持离线使用（需先加载页面）

### 🤖 智能识别
- **自动检测中缝**：基于亮度分析算法，自动识别底片中的黑条位置
- **批量处理**：支持一次性导入整卷底片，自动识别所有图片
- **异常标记**：自动标记识别异常的图片（如夜景、曝光不均等）

### 🎯 AI 修正
- **智能校准**：计算整卷胶片的平均间距，自动校准偏差较大的切割
- **曝光补偿**：针对曝光不均导致的识别偏差进行自动修正
- **可调灵敏度**：支持调整识别灵敏度，适应不同拍摄场景

### 🎨 精细编辑
- **像素级调整**：单击图片进入编辑模式，拖动分割线进行精确微调
- **独立旋转**：可分别旋转左右两侧的画面（90°、180°、270°）
- **实时预览**：编辑时实时预览切割效果
- **重置功能**：一键重置为自动识别结果

### 🖼️ 拼图工坊
- **双模式支持**：
  - **人工模拟模式**：生成标准黑条，可自定义宽度、噪点强度
  - **原始底片模式**：保留底片真实区域（含漏光/灰尘/纹理），还原胶片质感
- **拖拽排序**：在时间轴上拖拽调整图片顺序
- **无限拼接**：支持将任意数量的图片拼接成长条

### 📊 管理功能
- **智能排序**：按文件名或日期排序（升序/降序）
- **批量选择**：支持复选框选择、Ctrl+A 全选、ESC 取消选择
- **筛选视图**：按全部/异常/已选筛选图片
- **视图大小**：可调整缩略图大小，适应不同屏幕

### ⚡ 性能优化
- **Web Worker**：使用多线程处理，不阻塞主线程
- **并发导出**：智能分块处理，避免内存溢出
- **内存管理**：自动释放资源，优化长时间使用体验

---

## 🚀 快速开始

### 使用步骤

1. **导入图片**
   - 点击 "添加图片" 按钮或直接拖拽整卷底片到页面
   - 支持批量导入，系统会自动识别所有图片

2. **调整设置**
   - **切割模式**：
     - 自动去黑边：直接输出左右两张半格照片
     - 保留黑边：保留整张底片，仅用分割线指示（适合后续拼图）
   - **识别灵敏度**：调整识别严格程度（低=严格，高=宽松）
   - **AI 修正**：开启后自动校准异常帧

3. **编辑与修正**
   - 单击图片进入编辑模式
   - 拖动红色分割线微调切割位置
   - 使用底部按钮旋转左右画面
   - 按 ESC 退出编辑

4. **选择与导出**
   - 勾选左上角圆圈选择图片
   - 使用 Ctrl+A 全选，ESC 取消选择
   - 点击 "导出选中" 或 "导出全部" 批量导出
   - 导出为 ZIP 压缩包，包含所有切割后的图片

5. **拼图创作**
   - 选择多张图片，点击 "拼图"
   - 在拼图工坊中将素材添加到时间轴
   - 拖拽调整顺序，选择黑条模式
   - 保存拼接结果

### 快捷键

- `←` / `→`：在编辑模式下切换图片
- `ESC`：退出编辑 / 取消全选
- `Ctrl + A` / `Cmd + A`：全选当前筛选的图片

---

## 🛠️ 技术栈

- **纯前端**：HTML5 + CSS3 + Vanilla JavaScript
- **Canvas API**：图片处理和渲染
- **Web Worker**：多线程图片分析和导出
- **File API**：本地文件读取和处理
- **JSZip**：ZIP 压缩打包
- **响应式设计**：支持桌面和移动端

---

## 🏗️ 部署指南

本项目是纯静态文件，可部署在任何能够托管 HTML/CSS/JS 的服务器上。

### 方式一：Docker 部署（推荐）

1. **准备文件**
   ```bash
   # 确保项目文件位于服务器目录
   /root/var/www/half-frame-studio/
   ```

2. **启动 Nginx 容器**
   ```bash
   sudo docker run --name half-frame-web \
     --restart unless-stopped \
     -p 8000:80 \
     -v /root/var/www/half-frame-studio:/usr/share/nginx/html:ro \
     -d nginx:alpine
   ```

3. **配置反向代理（Nginx Proxy Manager）**
   
   在 NPM 中设置转发：
   
   | 配置项 | 值 |
   | :--- | :--- |
   | Domain Name(s) | half.wayming.xyz |
   | Scheme | http |
   | Forward Hostname / IP | 127.0.0.1 |
   | Forward Port | 8000 |

### 方式二：直接部署

将项目文件上传到任何 Web 服务器（Apache、Nginx、GitHub Pages、Netlify、Vercel 等）即可。

---

## 📝 使用提示

- **最佳体验**：建议使用电脑访问，大屏幕和鼠标操作更便捷
- **移动端**：支持移动端使用，可直接拖动图片上的分割线进行调整
- **数据安全**：刷新或关闭页面会导致数据丢失，请及时导出结果
- **文件格式**：支持常见图片格式（JPEG、PNG、WebP 等）
- **重复检测**：系统会自动检测并跳过重复导入的文件

---

## 📜 许可证

本项目采用 **CC BY-NC-SA 4.0** 许可证。

**CC BY-NC-SA 4.0 (Attribution-NonCommercial-ShareAlike 4.0 International)**

**知识共享 署名-非商业性使用-相同方式共享 4.0 国际**

该许可证允许您：
- ✅ 共享和改编本项目
- ❌ 严格禁止用于商业目的 (NC)
- ✅ 必须在相同的许可证下发布衍生作品 (SA)

---

## 🙏 致谢

感谢所有半格胶片摄影玩家的支持与反馈！

---

**Made with ❤️ for the half-frame photography community**

</div>
