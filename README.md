# Face-Recognition-Based-Hotel-Check-In-Check-Out-System
A Python-based Face Recognition System designed to simplify and automate hotel guest check-in and check-out processes using real-time facial recognition technology.
# Face Recognition-Based Hotel Check-In & Check-Out System

A Python-based Face Recognition System designed to simplify and automate hotel guest check-in and check-out processes using real-time facial recognition technology.

The system uses **OpenCV** and the **face_recognition** library to identify registered individuals through a webcam, helping reduce manual identity verification and making the hotel registration experience faster and more convenient.

### Key Features
- Real-time face detection using a webcam.
- Facial recognition of registered individuals.
- Automatic identification using stored facial encodings.
- Displays the recognized person's name on the screen.
- Identifies unregistered individuals as unknown persons.

### Technologies Used
- Python
- OpenCV
- Face Recognition
- NumPy

### Project Objective
To explore how AI-powered facial recognition can improve hotel operations by making guest identification easier, reducing manual check-in procedures, and creating a smoother check-in and check-out experience.

### Future Enhancements
- Automated guest check-in and check-out.
- Guest database integration.
- Check-in and check-out timestamp recording.
- Automated billing and room allocation.
- Web-based hotel management dashboard.

**Note:** This is a prototype demonstrating facial recognition. Actual hotel deployment would require secure identity verification, guest consent, data protection, and integration with a hotel management system.



Bro, I've checked your complete code. Your overall logic is good! The main issue is the image-loading path. I also spotted a couple of things that we can improve to make your face recognition project more reliable.

I'll retain your original functionality and all six people.

## 1. Complete corrected code

Replace your existing `main.py` with this:

```
    ("messi.jpeg", "messi"),        print(f"Image not found: {image_path}")        face_locations, face_encodings    ):        # Compare detected face with known faces        face_distances = face_recognition.face_distance(            known_face_encodings, face_encoding        )        name = "unknown_person"        if len(face_distances) > 0:            best_match_index = face_distances.argmin()            if face_distances[best_match_index] < 0.6:                name = known_face_names[best_match_index]        # Draw rectangle        cv2.rectangle(            frame,            (left, top),            (right, bottom),            (0, 0, 255),            2        )        # Display name        cv2.putText(            frame,            name,            (left, top - 10),            cv2.FONT_HERSHEY_SIMPLEX,            0.9,            (0, 0, 255),            2        )    cv2.imshow("Face Recognition System", frame)    # Press Q to exit    if cv2.waitKey(1) & 0xFF == ord('q'):        break# Release resourcesvideo_capture.release()cv2.destroyAllWindows()
```

## 2. What did I change?

| Your original code                    | Improvement                            |
| ------------------------------------- | -------------------------------------- |
| Relative image paths                  | Uses `BASE_DIR` to locate images       |
| Six separate image-loading statements | Uses a loop                            |
| Direct `[0]` encoding access          | Checks whether a face exists           |
| First matching face wins              | Finds the closest face match           |
| No RGB conversion                     | Converts webcam frames from BGR to RGB |
| No webcam validation                  | Checks camera availability             |

## 3. How to run it

1. Save the code using `Ctrl + S`.
2. Make sure all six images are inside `face_rec`.
3. Run the following in your VS Code terminal:

```
python main.py
```

4. Your webcam should open.
5. Press `Q` to close the webcam window.

Expected result

Your webcam should identify the six registered people and display their names. Anyone who doesn't match should appear as `unknown_person`.

## 4. Something important to understand

Your code uses:

```
if face_distances[best_match_index] < 0.6:
```

Here, `0.6` is the face-matching threshold. Lower values generally make matching stricter, while higher values make it more lenient. You may need to tune this based on your images and lighting.
