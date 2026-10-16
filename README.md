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

## Blink Counter (`blink.html`)
Uses the front camera to count how many times you blink, and shows blinks per minute, time since your last blink, and a live graph of how open your eyes are.
- Face landmarks come from [MediaPipe Face Landmarker](https://ai.google.dev/edge/mediapipe/solutions/vision/face_landmarker), which runs on-device in the browser. The library loads from jsDelivr and the ~4 MB model from Google's storage the first time you press Start. There's no backend, and video never leaves the device.
- A blink is counted when the eye aspect ratio drops below a set fraction of your normal open-eye level (which it learns automatically) and comes back within 40–800 ms. Longer closures aren't counted.
- Use the **Sensitivity** slider if it misses blinks (raise it) or counts extra ones (lower it).

## Toon Booth (`toon.html`)
Take a photo with the front camera (or upload one) and it gets redrawn as a yellow, Simpsons-style cartoon: flat colors, thick black outlines, big round eyes, an outlined nose and mouth, and optional stubble. Choose a cartoon sky background or a cartoonized version of the original, and press and hold the picture to compare with the photo.
- Runs entirely in the browser with no backend. MediaPipe's face landmarker finds the eyes, nose, mouth and brows, and its selfie multiclass segmenter separates hair, skin, clothes and background. The models (~20 MB) download once and are cached.
- This is a stylized filter, not a generative AI redraw, so the result keeps your hair, clothes and face shape rather than inventing a new character.

## Hosting
It's a single static `index.html`. Enable GitHub Pages under **Settings → Pages → Deploy from a branch → `main` / root**.
Camera access needs HTTPS, which GitHub Pages provides.
