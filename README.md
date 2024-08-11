# Real-time Hand Tracking with OpenCV and cvzone Project

This project demonstrates a simple hand tracking application using OpenCV and the `cvzone` library. The application captures video from the webcam, detects hands in real-time, and displays the annotated video feed.

## Requirements

- Python 3
- OpenCV
- Cvzone

## Installation

To install the required libraries, please run:

```bash
pip install opencv-python cvzone
```

## Usage

1. **Initialize the Webcam**: The webcam is initialized using OpenCV's `VideoCapture` method.
2. **Initialize the Hand Tracker**: The hand tracker is initialized using `cvzone.HandDetector` with a detection confidence of 0.8 and a maximum of 2 hands.
3. **Capture and Process Frames**: The application continuously captures frames from the webcam, detects hands, and annotates the frames.
4. **Display the Annotated Frames**: The annotated frames are displayed in a window titled "Hand Tracking - AI".
5. **Exit the Application**: The application exits when any key is pressed.

## Code Explanation

```python
import cv2
from cvzone.HandTrackingModule import HandDetector

# Initialize the webcam
webcam = cv2.VideoCapture(0)

# Initialize the Hand Tracker
hand_detector = HandDetector(detectionCon=0.8, maxHands=2)

while True:
    # Capture the image from the webcam
    success, img = webcam.read()

    # Detect hands in the frame
    hands, img_hands = hand_detector.findHands(img)

    # Display the frame with annotations
    cv2.imshow("Hand Tracking - AI", img_hands)

    # Exit the application when any key is pressed
    if cv2.waitKey(1) != -1:
        break

# Release the webcam and close the windows
webcam.release()
cv2.destroyAllWindows()
```

## How It Works

1. **Webcam Initialization**: The webcam is accessed and initialized to capture video frames.
2. **Hand Detection**: The `HandDetector` from `cvzone` is used to detect hands in each frame with a specified confidence level.
3. **Frame Annotation**: Detected hands are annotated on the video frames.
4. **Display**: The annotated frames are displayed in a window.
5. **Exit Condition**: The application runs in a loop until any key is pressed, at which point it exits, releasing the webcam and closing all windows.

## Conclusion

This project provides a basic implementation of hand tracking using OpenCV and `cvzone`. It can be extended and customized for various applications such as gesture recognition, virtual controls, and more.
