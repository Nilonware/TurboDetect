# TurboDetect V3.2
### Track without payment. Detect without limits.

<img width="7680" height="4320" alt="TurboDetect Thumbnail" src="https://github.com/user-attachments/assets/e36caf23-a3a1-4f6c-920f-f20c6c92cb33" />

## 🚀 Overview
**TurboDetect V3.2** is a lightweight, fast, and flexible face-detection engine designed for creators, developers, and hobbyists who want **reliable face sensing without subscriptions, trackers, or bloat**.

Unlike the generic copy-paste engines found everywhere, TurboDetect uses its **own custom detection logic** — no paywalls, no cloud processing, no hidden dependencies.

*Not a fan of AI?*  
We also include a **non-AI detection mode** powered by classic computer-vision techniques.

---

## ✨ Features
- ⚡ Real-time detection  
- 🤖 AI-powered **or** non-AI mode  
- 🔒 Fully offline — no data leaves your device  
- 🎯 Accurate and fast  
- 🧩 Easy to integrate into Python projects  
- 🎨 Supports blur, pixelation, masking, and custom censor effects  

---

# 🧪 Code Samples (Face Censoring)

Below are working examples using standard OpenCV face detection.  
You can replace these detectors with your own TurboDetect engine.

---

## **1. Blur Censor (Gaussian Blur)**

```python
import cv2

# Load a face detector (Haar cascade)
face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + "haarcascade_frontalface_default.xml")

# Start webcam
cap = cv2.VideoCapture(0)

while True:
    ret, frame = cap.read()
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)

    faces = face_cascade.detectMultiScale(gray, 1.3, 5)

    for (x, y, w, h) in faces:
        face = frame[y:y+h, x:x+w]
        blurred = cv2.GaussianBlur(face, (45, 45), 30)
        frame[y:y+h, x:x+w] = blurred

    cv2.imshow("TurboDetect Censor Mode", frame)

    if cv2.waitKey(1) & 0xFF == 27:  # ESC key
        break

cap.release()
cv2.destroyAllWindows()
