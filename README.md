# PuzzleBooth 

A hand-gesture controlled photo booth app that runs entirely in your browser. It requires zero installation, no backend, and no dependencies for the app itself to be installed and run.

---

## **Description**

PuzzleBooth captures a photo using your index fingers to set up a "frame" or variable size, turns it into a 3x3 puzzle with a many different kinds of photo booth effects, and lets you assemble it using pinching gestures. Once completed, it allows you to save the images as a downloadable photo collage strip.

---

## **System Requirements**

- **Browser:** Chrome or Edge (recommended), Firefox
- **Hardware:** Webcamera or a phone camera set up to be used as a webcamera
- **Internet Connection:** Required to load the MediaPipe model (~10 MB, first time only)
- **Local Server:** Required to run the app (cannot be opened directly as a local file)

---

## **Installation & Setup**

### 1. Clone the repository

```bash
git clone https://github.com/KomradeKrusader/PuzzleBooth.git
cd PuzzleBooth
```

### 2. Start a local server

The app uses ES Modules and requires camera access, so it must be served over HTTP.

Install the [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension in VS Code -> navigate to the **app.js** file in PuzzleBooth folder -> click **Go Live** button (usually on the bottom right of your screen).

### 3. Open in your browser

Upon pressing the "Go Live" button, a browser window should open automatically, but if that doesn't happen, open a web browser and type in:
```
http://localhost:5500
```

It is necessary to allow camera access when prompted by your browser.

---

## **Project Structure**

```
Puzzle/
├── index.html        # App entry point
├── app.js            # Core logic (tracking, puzzle, gallery)
├── css/
│   └── styles.css    # Styles and layout
└── .gitignore
```

---

## **Control Gestures**

| Gesture | Action |
|---|---|
| Pinch with both hands | Lock photo frame and start countdown |
| Pinch with one hand over a piece | Drag puzzle piece |
| Closed fist (hold) | Save completed puzzle / Reset current puzzle |

---

## **Application Logic**

1. Show both hands (index fingers) to the camera and pinch to define the capture frame.
2. Hold the pinch gesture till the countdown starts. The photo will be taken automatically.
3. The photo is split into a 3x3 puzzle with a photo booth filter of the users' choice.
4. Rearrange the pieces using pinch gestures. The puzzle pieces will snap in place once they're in their correct location.
5. Once completed, make a fist to save it to the photo strip with a shatter animation. (You can also show a thumbs up!)
6. Download the photo collage strip once you have completed 3 puzzles.

---

## **Upcoming features**

1. A way to increase countdown timer.
2. More filters.
3. Proper phone compatibility.
4. UI overhaul once I figure out how css works.

## **Tech Used**

- **[MediaPipe Tasks Vision](https://developers.google.com/mediapipe)** `v0.10.14` — Hand landmark detection
- **Canvas 2D API** — Rendering the live feed, jumbling the puzzle pieces, applying photo booth effects
- **JavaScript (ES Modules)** — Framework-free (vanilla JS)
- **CSS Custom Properties** — Theming and layout

All external dependencies are loaded via CDN. No additional installation is required.

---

## **Troubleshooting**

### **The camera does not turn on**

Verify that no other application (Teams, Zoom, Discord, etc.) is using the camera in the background.

### **The app does not load the model**

Check your internet connection. The MediaPipe model (~10 MB) is downloaded from `storage.googleapis.com` and the runtime from `cdn.jsdelivr.net`. If either of these domains is blocked on your network, the app will not be able to start.

### **The app shows a black screen**

Make sure you are serving the app from a local HTTP server, not opening it directly as a file from your file explorer (`file://`).

### **The pinch gesture is not detected**

Ensure you have good lighting and that both hands are clearly visible to the camera. Bring your index finger and thumb closer together until the yellow indicator on the screen activates. Make sure your thumb is not obstructing the view of the index finger and vice-versa.

---

## **Browser Compatibility**

| Browser | Support |
|---|---|
| Chrome / Edge | Recommended |
| Firefox | Supported |
| Safari | Limited (may require additional permissions) |
| Mobile | Limited (I recommended using desktop) |

---

## **Liscense**

MIT — Free to use, modify, and share. Please give credit :)
