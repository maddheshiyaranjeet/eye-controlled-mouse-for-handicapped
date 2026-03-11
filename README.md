 # eye-controlled-mouse-for-handicapped
In conclusion, the eye-controlled mouse is a powerful and innovative tool that enables handicapped individuals to interact with computers without physical touch. By using only eye movements, it opens new opportunities for education, communication, and digital participation, helping create a more inclusive technological environment. 👁️💻






## ✨ Key Highlights

* **♿ Accessibility First:** Designed specifically for people with ALS, quadriplegia, or advanced motor disabilities.
* **🎯 Sub-Pixel Precision:** Uses **MediaPipe’s Refined Iris Landmarks** (474–478) for stable cursor positioning.
* **⚡ Zero-Latency Control:** Optimized Python loop for real-time processing without the need for external GPU acceleration.
* **💻 Hardware Agnostic:** Works on any standard 720p/1080p webcam; no expensive infrared eye-trackers required.
* **🖱️ Natural Interaction:** Integrated "Blink-to-Click" logic with adjustable sensitivity thresholds.

---

## 🧠 Core Features

### 👁️ Precision Eye Tracking

* **Iris Centroid Mapping:** Isolates the iris landmarks to calculate the gaze vector.
* **Resolution Scaling:** Automatically maps camera coordinates ($640 \times 480$) to system resolution (e.g., $1920 \times 1080$) using dynamic scaling factors.

### 🖱️ Gesture-Based Interaction

* **Blink Detection:** Monitors the Euclidean distance between the upper and lower eyelids (Landmarks 145 & 159).
* **Automated Clicking:** Triggers `pyautogui.click()` when the eyelid distance falls below the **0.004** threshold.
* **Visual Feedback:** Real-time GUI overlay showing tracked points and "Click" status for user calibration.

### 🛡️ System Safety

* **Fail-Safe Mechanism:** Inherits PyAutoGUI’s fail-safe (slamming the mouse to a corner kills the script).
* **Environment Adaptation:** Mirrored frame processing (`cv2.flip`) to ensure intuitive "natural" movement.

---

## 🛠️ Tech Stack

| Layer | Technologies |
| --- | --- |
| **Language** | Python 3.9+ |
| **Computer Vision** | OpenCV (Open Source Computer Vision Library) |
| **AI Inference** | MediaPipe (Face Mesh + Iris Refinement) |
| **Automation** | PyAutoGUI (System-level Mouse/Keyboard Control) |
| **Mathematics** | NumPy / Coordinate Geometry |

---

## 📁 Project Structure

```text
OcularLink/
│
├── core/
│   ├── tracker.py       # Main Eye-Tracking logic
│   ├── gestures.py      # Blink & Gesture detection algorithms
│   └── utils.py         # Coordinate scaling & screen mapping
│
├── assets/
│   ├── demo.mp4         # Presentation video
│   └── landmarks.png    # MediaPipe reference guide
│
├── requirements.txt     # Dependency list
├── main.py              # Application entry point
└── README.md            # Project documentation

```

---

## 🚀 Getting Started

### 1️⃣ Installation

Ensure you have a working Python environment, then install the core dependencies:

```bash
pip install opencv-python mediapipe pyautogui

```

### 2️⃣ Configuration

Adjust the sensitivity in `main.py` based on your webcam's distance:

```python
# Adjust this threshold for blink sensitivity
if (left[0].y - left[1].y) < 0.004:
    pyautogui.click()

```

### 3️⃣ Run the Application

```bash
python main.py

```

---

## 🧪 Technical Logic Summary

The system calculates the **Aspect Ratio** of the eye landmarks. When the user blinks, the vertical distance between points 145 and 159 converges toward zero.

$$Distance = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$$

The cursor position is determined by the **Normalized Iris Center**, which is then multiplied by the `screen_width` and `screen_height` to translate "Eye-Space" into "Desktop-Space."

---

## 🔮 Future Enhancements

* **Dwell-Time Clicking:** Implement a "stare-to-click" feature for users who cannot blink voluntarily.
* **Kalman Filtering:** Add a mathematical smoothing filter to eliminate cursor "jitter" caused by natural eye micro-movements (saccades).
* **Voice-Overlays:** Integrate a speech-to-text engine for typing while moving the mouse with eyes.

---
