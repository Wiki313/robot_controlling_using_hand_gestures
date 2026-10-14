# Robot Controlling Using Hand Gestures 🤖✋

Control a simulated robot hands-free using real-time hand gesture recognition.

The system captures hand movements from a webcam, classifies gestures with a Keras deep learning model, and drives a robot in a PyBullet simulation.

## Features

- Real-time hand gesture recognition with MediaPipe Holistic and OpenCV
- Gesture classification with a Keras model (`model.h5` + `labels.npy`)
- Robot simulation in PyBullet with `hrobot.urdf` on `plane.urdf`
- Live prediction overlay on the camera feed
- Easy-to-run Python code

## Gestures

| Gesture | Robot Movement |
|---------|----------------|
| MoveForward | Move forward |
| MoveBackWard | Move backward |
| Move Right | Move right |
| Move Left | Move left |

Predictions below the 0.5 confidence threshold are ignored and shown as `None`.

## Requirements

- Python 3.8+
- Webcam

Install dependencies:

```bash
pip install opencv-python mediapipe keras numpy pybullet
```

## How to Run

```bash
python robot.py
```

1. Ensure `model.h5`, `labels.npy`, `hrobot.urdf`, and `plane.urdf` are in the project directory.
2. Run `robot.py`. A PyBullet simulation window and a camera window will open.
3. Show a gesture to the webcam to move the simulated robot.
4. Press `Esc` in the camera window to quit.

## Project Structure

```text
.
├── robot.py      # Main script: gesture recognition and robot control
├── hrobot.urdf   # Robot model for PyBullet simulation
├── plane.urdf    # Ground plane for PyBullet simulation
├── model.h5      # Trained Keras gesture classification model
├── labels.npy    # Gesture labels for the model
└── README.md     # Project documentation
```

## How It Works

1. OpenCV captures frames from the webcam.
2. MediaPipe Holistic detects left- and right-hand landmarks.
3. Hand landmarks are normalized and passed to the Keras model for gesture classification.
4. The predicted gesture is mapped to a movement command (`dx`, `dy`).
5. PyBullet moves the simulated robot accordingly.
6. The current prediction is shown as an overlay on the camera feed.

## Future Improvements

- Support for controlling a real hardware robot (via Arduino / Raspberry Pi)
- Train on a larger custom dataset for more gestures
- Improve gesture accuracy with advanced deep learning models

## Author

Muhammad Waqar — [LinkedIn](https://www.linkedin.com/in/mwaqar-ai/)
