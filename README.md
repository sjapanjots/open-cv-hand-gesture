# Virtual Mouse Using Hand Gesture Recognition: The AI Mouse! ✨

Welcome to the repository for a super fun and practical project that brings your hand gestures to life on your computer screen! This Virtual Mouse project allows you to control your cursor and execute standard mouse functions (and even take screenshots!) using only your hand, powered by the magic of computer vision.

Say goodbye to wrist strain and hello to hands-free control! 👋

---

## 🌟 Features

This project utilizes advanced computer vision techniques to enable full mouse functionality via simple hand gestures:

*   **Mouse Movement:** Control the cursor position dynamically by moving your hand.
*   **Left Click:** Perform precise left-click actions.
*   **Right Click:** Execute precise right-click actions.
*   **Double Click:** Quickly open folders or files with a specific two-finger bend gesture.
*   **Screenshot Utility:** Capture your screen instantly with a simple "all closed" hand configuration.

## 💻 Technical Deep Dive

This project relies on powerful Python libraries:

| Library | Role |
| :--- | :--- |
| **OpenCV (CV2)** | Handles the video feed, capturing frames from the camera, displaying the output (`IM show`), and flipping the frame for a mirrored view. |
| **MediaPipe (MB)** | Essential for hand tracking. It detects and tracks **21 key landmarks** (points) on the hand, which are used to calculate angles and distances for gesture recognition. |
| **NumPy (NB)** | Used for calculating geometric properties like the **angle** between lines and the **Euclidean distance** between points, crucial for determining finger bends and closure. |
| **PyAutoGUI** | Used to retrieve system information (screen width and height), map the index finger tip position to the cursor movement, and perform the highly precise **double click** action. |
| **Pynput.mouse** | Found to be better suited and more precise for performing quick **left click** and **right click** actions. |

## 🚀 Use Cases and Applications

This AI Mouse goes beyond novelty. Here are some proper use cases:

*   **Accessibility:** This system provides a non-traditional input method, which can be highly beneficial for users who may have difficulty operating a standard physical mouse.
*   **Hands-Free Operation:** Control your computer while your hands are otherwise occupied or when a traditional mouse setup is inconvenient.
*   **Presentations/Kiosks:** Use natural gestures to interact with displays or slides from a distance.
*   **Demonstration:** It's an excellent showcase of the power and reliability of computer vision and gesture recognition for translating physical actions into digital commands.

The demonstration successfully showed core tasks like **creating and deleting a folder**, and **opening a drive and subsequent folders** using only the configured gestures.

---

## 🛠️ Installation and Setup

### Prerequisites

Before you start, make sure you have Python installed. You will also need to install the following libraries.

1.  **Install OpenCV:**
    ```bash
    pip install opencv-python
    ```
    (Note: This is referred to as `pip install open CV` in the source).

2.  **Install PyAutoGUI:**
    ```bash
    pip install pyautogui
    ```
    (Note: This is referred to as `pip install by Auto GUI` in the source).

3.  **Install Pynput:**
    ```bash
    pip install pynput
    ```
    (Note: This is referred to as `pip install p inbut` in the source).

You will also need **MediaPipe** and **NumPy** which are used extensively throughout the project.

### Project Structure

Ensure your repository contains:

1.  **Main Python File:** (e.g., `virtual_mouse.py`) where the video capture, gesture detection, and mouse actions are defined.
2.  **Utility File (`util.py`):** This file must contain the helper functions: `get_angle` and `get_distance`.

## ▶️ How to Run the Project

1.  **Ensure Camera Connection:** The project captures the video feed frame by frame from your camera. If you have a single primary camera, the index passed to `CV2.VideoCapture` should be `0`.
2.  **Execute the Script:** Run your main Python file.
3.  **Close the Window:** If you need to stop the video feed and close the window, **press the `Q` key**.

---

## ✋ Gesture Guide: Controlling the Mouse

The system uses specific landmarks and geometric calculations (angles and distances) to interpret your hand position.

| Mouse Action | Required Hand Gesture (Conditions) | Technical Criteria |
| :--- | :--- | :--- |
| **Mouse Movement** | Thumb closed **AND** Index and Middle fingers upright. | **Thumb Closed:** Distance between thumb tip (L4) and index base (L5) is **less than 50**. **Index Upright:** Angle of index finger is **greater than 90**. The cursor is mapped to the index finger tip's XY coordinate. |
| **Stop Movement** | Thumb is open/straight. | **Thumb Open:** Distance between thumb tip (L4) and index base (L5) is **greater than 50**. |
| **Left Click** | Thumb straight, Index finger bent, Middle finger straight. | **Thumb Straight** (Distance > 50), **Index Bent** (Angle < 50), **Middle Straight** (Angle > 90). |
| **Right Click** | Thumb straight, Index finger straight, Middle finger bent. | **Thumb Straight** (Distance > 50), **Index Straight** (Angle > 90), **Middle Bent** (Angle < 50). |
| **Double Click** | Thumb straight, Index finger bent, Middle finger bent. | **Thumb Straight** (Distance > 50), **Index Bent** (Angle < 50), **Middle Bent** (Angle < 50). |
| **Screenshot** | Thumb, Index, and Middle fingers are all closed. | All relevant distances and angles (for Thumb, Index, Middle) are **less than 50**. |

Happy coding and gesturing! If you enjoyed this project, don't forget to star the repo! ⭐