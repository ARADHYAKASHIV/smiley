# Smile Detection Program

This Python program uses OpenCV, a popular computer vision library, to detect smiles in real-time video captured from the default camera.

## Dependencies
- OpenCV

## Code Explanation

1. `smile_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + 'haarcascade_smile.xml')`: This line loads the Haar cascade file for smile detection.

2. `open_camera()`: This function opens the default camera and starts capturing video.

3. `cap = cv2.VideoCapture(0)`: This line initializes the video capture object for the default camera.

4. The `while True:` loop continuously captures frames from the camera.

5. `ret, frame = cap.read()`: This line captures a frame from the video.

6. `gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)`: This line converts the captured frame to grayscale.

7. `faces = face_cascade.detectMultiScale(gray, 1.1, 4)`: This line detects faces in the grayscale frame.

8. The `for (x, y, w, h) in faces:` loop iterates over each detected face.

9. `cv2.rectangle(frame, (x, y), (x+w, y+h), (255, 0, 0), 2)`: This line draws a rectangle around the detected face.

10. `smiles = smile_cascade.detectMultiScale(face_roi, 1.8, 20)`: This line detects smiles within the region of interest in the face.

11. The `for (sx, sy, sw, sh) in smiles:` loop iterates over each detected smile.

12. `cv2.rectangle(frame, (x+sx, y+sy), (x+sx+sw, y+sy+sh), (0, 255, 0), 2)`: This line draws a rectangle around the detected smile.

13. `smile_percentage = sw / w * 100`: This line calculates the smile percentage.

14. `cv2.putText(frame, f'Smile: {smile_percentage:.2f}%', (x, y - 10), cv2.FONT_HERSHEY_SIMPLEX, 0.9, (0, 255, 0), 2)`: This line puts the smile percentage text on the frame.

15. `cv2.imshow('Camera', frame)`: This line displays the frame with the detected faces and smiles.

The loop breaks if 'q' is pressed.

## Usage
Run the `open_camera()` function to start the smile detection program.
