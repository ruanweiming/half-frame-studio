# 📸 Half-Frame Studio: 自动半格胶片切割与拼图工具

**[Demo / Live Application: https://half.wayming.xyz/](https://half.wayming.xyz/)**

这是一个纯前端、在浏览器本地运行的 Web Application，专为半格胶片摄影玩家设计。它能自动识别底片扫描件中的中缝黑条，并精确切割、修正和拼图。

---

# 📸 Half-Frame Studio: Automatic Half-Frame Splitter & Stitcher

**[Demo / Live Application: https://half.wayming.xyz/](https://half.wayming.xyz/)**

This is a pure front-end, browser-local Web Application designed for half-frame film photographers. It automatically detects the dark strip (gap) in scanned negatives for precise splitting, correction, and stitching.

## 💡 核心特性 (Key Features)

| Feature | 中文描述 | English Description |
| :--- | :--- | :--- |
| **纯本地处理** | 所有图片处理均在您的浏览器本地完成，图片**绝不会**上传到任何服务器。 | All image processing happens **locally** in your browser; images never leave your device. |
| **自动识别** | 自动分析底片亮度分布，识别并定位中缝黑条，支持批量导入。 | Automatically analyzes film strip brightness to locate and identify the dark center gap. |
| **AI 修正** | 计算整卷胶片的平均间距，对曝光不均导致的切割偏差进行自动校准。 | Calculates the median gap width of the roll to automatically correct anomalies caused by uneven exposure. |
| **拼图工坊** | 支持将任意数量的切割图片拼成长条，可选择**人工模拟**或**原始底片**模式创建缝隙。 | Allows stitching any number of cropped frames. Features **Synthetic** (clean, customizable gap) and **Natural** (preserving the real film gap texture) modes. |
| **精细编辑** | 双击图片进入编辑器，支持像素级拖动切割线微调，并可独立旋转左右两侧的画面。 | Double-click to enter the editor for pixel-level line adjustments and independent rotation of the left and right frames. |

---

## 🏗️ 部署指南 (Deployment Guide)

本项目是纯静态文件，可部署在任何能够托管 HTML/CSS/JS 的服务上。

### 1. File Location / 文件位置

Ensure your files are placed in the server's directory, for example:
确保项目文件位于服务器的以下路径：
/root/var/www/half-frame-studio/
### 2. Docker Deployment / Docker 部署 (Recommended)

Use the following command to run a persistent Nginx container serving the application on port **8000**:
使用以下命令启动一个持久运行的 Nginx 容器，将应用部署在 **8000 端口**：

```bash
sudo docker run --name half-frame-web \
--restart unless-stopped \
-p 8000:80 \
-v /root/var/www/half-frame-studio:/usr/share/nginx/html:ro \
-d nginx:alpine
3. Proxy Configuration (NPM) / 反向代理配置To access the app via HTTPS at https://half.wayming.xyz/, configure your Nginx Proxy Manager (NPM) as follows:为了通过 HTTPS 域名访问，请在 NPM 中设置转发：Setting / 配置项Value / 值Domain Name(s)half.wayming.xyzSchemehttpForward Hostname / IP127.0.0.1 (or your Docker internal gateway IP)Forward Port8000📜 许可证 (License)本项目采用 CC BY-NC-SA 4.0 许可证。CC BY-NC-SA 4.0 (Attribution-NonCommercial-ShareAlike 4.0 International)知识共享 署名-非商业性使用-相同方式共享 4.0 国际This license allows you to share and adapt the work, but strictly prohibits commercial use (NC) and requires you to distribute derivatives under the same license (SA).该许可证允许您共享和改编本项目，但严格禁止用于商业目的 (NC)，且要求您在相同的许可证下发布衍生作品 (SA)。
