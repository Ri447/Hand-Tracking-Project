# Hand Tracking using Python, OpenCV & MediaPipe

A real-time hand-tracking project built using **Python, OpenCV, and MediaPipe**. The application uses a webcam to detect hands, track 21 hand landmarks, visualize their connections, and retrieve the pixel coordinates of individual landmarks.

This project explores computer vision fundamentals, real-time image processing, and hand landmark detection.

## Features

- **Real-time Hand Detection:** Detects hands using MediaPipe Hands.
- **21 Hand Landmarks:** Identifies and tracks 21 landmarks on each detected hand.
- **Landmark Visualization:** Draws connections between hand landmarks using OpenCV and MediaPipe.
- **Coordinate Extraction:** Retrieves the X and Y pixel coordinates of individual landmarks.
- **Custom Landmark Markers:** Displays filled circular markers on detected hand landmarks.
- **FPS Counter:** Displays the real-time processing frame rate.
- **Reusable Hand Detector:** Implements a Python class to organize hand detection and landmark tracking.

## Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| OpenCV | Webcam access, image processing and visualization |
| MediaPipe | Hand detection and landmark tracking |
| NumPy | Numerical operations |
| uv | Python dependency and environment management |

## Project Structure

```text
Hand-Tracking-Project/
│
├── HandTrackingMin.py       # Initial hand tracking implementation
│
├── HandTrackingModule.py   # Reusable hand detector class
│
├── main.py                 # Project entry point (to be updated)
│
├── pyproject.toml           # Project dependencies
│
├── uv.lock                  # Locked dependency versions
│
├── .gitignore
│
└── README.md
```

## How It Works

### 1. Hand Detection

MediaPipe Hands processes webcam frames and detects the presence of hands.

```python
imgRGB = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
self.results = self.hands.process(imgRGB)
```

OpenCV captures images in BGR format, so the image is converted to RGB before being passed to MediaPipe.

### 2. Landmark Detection

MediaPipe identifies 21 landmarks on each detected hand.

Each landmark has:
- An ID (0–20)
- An X coordinate
- A Y coordinate
- A normalized position in the image

### 3. Landmark Coordinate Extraction

The `findPosition()` method converts normalized landmark coordinates into pixel coordinates.

```python
cx, cy = int(lm.x * w), int(lm.y * h)
lmList.append([id, cx, cy])
```

The resulting list stores the landmark ID and its corresponding pixel coordinates.

### 4. Visualization

OpenCV draws circular markers on detected landmarks, while MediaPipe draws the connections between them.

## MediaPipe Hand Landmark Reference

MediaPipe detects 21 landmarks for each hand:

| Landmark ID | Hand Part |
|---|---|
| 0 | Wrist |
| 1–4 | Thumb |
| 5–8 | Index Finger |
| 9–12 | Middle Finger |
| 13–16 | Ring Finger |
| 17–20 | Pinky Finger |

These landmarks can be used to calculate finger positions, recognize gestures, and build interactive computer vision applications.

## Future Improvements

- [ ] Finger counting and gesture recognition
- [ ] Hand gesture classification
- [ ] Gesture-controlled virtual mouse
- [ ] Mouse movement using index finger tracking
- [ ] Click detection using thumb and index finger
- [ ] Improved tracking performance and visualization

## Learning Outcomes

Through this project, I explored:

- Computer vision fundamentals
- Real-time webcam processing
- MediaPipe hand landmark detection
- OpenCV image processing
- Object-Oriented Programming in Python
- Coordinate extraction and tracking
- Real-time FPS calculation
