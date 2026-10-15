# ASCII Cam 95

A mobile-first web page that turns your phone's camera feed into live ASCII art, inside a Windows 95-style window.

All processing happens in your browser. No video is uploaded anywhere.

## Features
- Front and rear camera switching, with mirroring
- Detail and contrast sliders, auto levels, and invert
- Character sets: Classic, Detailed, Blocks, Bubbles, Binary, Dots
- Color themes: DOS Gray, Green, Amber, Paper
- Freeze a frame (or double-tap the screen), then save it as `.txt` (uses the phone's share sheet when available) or copy it to the clipboard

## Tracker Cam (`tracker.html`)
Point the camera at an object, press **Track object** (or tap the object on screen), and a red line follows it as it moves or as you move the camera.
- Tracking runs in the browser using normalized cross-correlation template matching on a downscaled grayscale frame, with slow template adaptation and box-size adjustment so it handles lighting and distance changes.
- If the object is lost, the box turns yellow and the tracker searches a wider area until it finds the object again.
- **Clear line**, **Flip camera**, and **Save image** (PNG with the line drawn on it) buttons.
- Works best on objects with visible texture or edges. Plain, single-color objects are harder to lock on to.

## Hosting
It's a single static `index.html`. Enable GitHub Pages under **Settings → Pages → Deploy from a branch → `main` / root**.
Camera access needs HTTPS, which GitHub Pages provides.
