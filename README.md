# ASCII Cam 95

A mobile-first web page that turns your phone's camera feed into live ASCII art, inside a Windows 95-style window.

All processing happens in your browser. No video is uploaded anywhere.

## Features
- Front and rear camera switching, with mirroring
- Detail and contrast sliders, auto levels, and invert
- Character sets: Classic, Detailed, Blocks, Bubbles, Binary, Dots
- Color themes: DOS Gray, Green, Amber, Paper
- Freeze a frame (or double-tap the screen), then save it as `.txt` (uses the phone's share sheet when available) or copy it to the clipboard

## Hosting
It's a single static `index.html`. Enable GitHub Pages under **Settings → Pages → Deploy from a branch → `main` / root**.
Camera access needs HTTPS, which GitHub Pages provides.
