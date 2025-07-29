# volume_control_python
🖐️ Hand Gesture-Based Volume Control using Python
This project uses hand gestures to control system volume. By recognizing the distance between your thumb and index finger, it increases or decreases the system volume using pyautogui, MediaPipe, and OpenCV.

📌 Features
📷 Real-time hand tracking using webcam

🎯 Tracks thumb and index finger

🔊 Increases volume when the distance is greater than 40 pixels

🔉 Decreases volume when the distance is less than or equal to 40 pixels

💻 Cross-platform (depends on pyautogui support)

🔧 Requirements
Install the required libraries using pip:



MediaPipe detects landmarks (21 key points)

Thumb tip (landmark 4) and Index finger tip (landmark 8) positions are used

The Euclidean distance between them is calculated

If the distance:

> 40 → pyautogui.press("volumeup")

<= 40 → pyautogui.press("volumedown")

A red line is drawn between the fingers for visual feedback

A label appears showing "Volume Up" or "Volume Down"

🖼️ Demo
<img src="demo_image.png" width="400"/>
🧠 Key Code Snippets
Draw only valid hand landmarks and highlight tips:

python
Copy
Edit
drawing_utils.draw_landmarks(image, hand, mp.solutions.hands.HAND_CONNECTIONS)
if nu == 8:  # Index finger tip
    cv2.circle(image, (x, y), 10, (255, 0, 0), 3)
if nu == 4:  # Thumb tip
    cv2.circle(image, (x, y), 10, (0, 255, 0), 3)
Distance-based volume control:

dist = ((x2 - x1)**2 + (y2 - y1)**2)**0.5 // 4
if dist > 40:
    pyautogui.press("volumeup")
else:
    pyautogui.press("volumedown")
