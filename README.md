📸 Minimalist Web Photo Editor

A lightweight, single-page web application that embeds a full-featured image editor into the browser. It allows users to modify a default image or dynamically pass any image URL via a query parameter.

✨ Features
🎛️ Full-Screen Editor: Automatically scales to fit any screen size (desktop or mobile).
🔗 Dynamic Loading: Pass any web image to the editor dynamically using URL query parameters.
💾 Callback System: Logs the modified image data directly to the browser console upon saving.
📦 Filerobot Integration: Powered by the lightweight Scaleflex Filerobot Image Editor CDN.

🚀 Getting Started
Prerequisites
You only need a modern web browser (Chrome, Firefox, Edge, or Safari). No installation or local server configuration is required.

Quick Start
1. Copy the HTML code into a local file named `index.html`.
2. Double-click `index.html` to open it directly in your web browser.

🛠️ Usage & Query Parameters
By default, the application loads a placeholder image. You can pass your own custom image URL using the `?img=` query parameter.

Example URL Syntax:
```text
file:///path/to/your/index.html?img=https://example.com
```
Default Image: `https://cloudimg.io` (used if no parameter is provided).
Dynamic Image: Automatically decodes and loads any properly formatted, hotlinkable image URL passed to the browser address bar.

🏗️ Built With
HTML5 & CSS3: For the structural workspace layout.
JavaScript (Vanilla): For URL parameter parsing and state management.
[Filerobot Image Editor](https://github.com): Provides the UI core for cropping, filtering, and exporting images.
