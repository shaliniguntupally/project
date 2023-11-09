Driver fatigue and drowsiness are significant factors contributing to car accidents. When drivers become exhausted, their reflexes slow down, and there's a risk of them dozing off while driving, creating hazardous situations. This problem leads to a substantial increase in global road fatalities.
To tackle this issue, a real-time system for detecting driver drowsiness can be implemented using a camera like the Raspberry Pi camera, capturing the driver's facial images. By analyzing these images in real-time, the system can determine if the driver is fatigued or drowsy. This analysis typically involves identifying facial features like eyes and mouth to recognize signs of drowsiness, such as drooping eyelids or yawning.
Once the system identifies signs of driver fatigue, it can activate alerts for both the driver and concerned parties, such as authorities or family members, using sound signals or other alert methods. These alerts act as warnings, prompting the driver to take necessary actions, such as stopping for rest or allowing another person to drive.
By employing real-time image analysis and timely alerts, this system aims to improve road safety by preventing accidents caused by drowsy driving, ultimately saving lives and reducing the overall number of road fatalities.

The following formula is used for calculation of EAR:
 
Below is a breakdown of the code's components:

Imports:
cv2: This library, OpenCV, is utilized for computer vision tasks.
dlib: This library, Dlib, is employed for face detection and predicting facial landmarks.
distance from scipy.spatial: This module is used to compute the Euclidean distance between specific facial landmarks.
Eye Aspect Ratio Calculation:
The function calculate_eye_aspect_ratio(eye) evaluates the Eye Aspect Ratio (EAR) for a given eye, a measure used to discern if the eyes are open or closed.
EAR is computed with the formula: EAR = (A + B) / (2 * C), where A, B, and C represent distances between specific facial landmarks.

Initialization:
detector: This object, from Dlib, is a face detector used to identify faces within video frames.
predictor: This object, also from Dlib, is a facial landmark predictor loaded with a pre-trained model file ("shape_predictor_68_face_landmarks.dat").
video_capture: This connection is established to the default camera (index 0) for capturing video frames.
Constants:
EYE_AR_THRESHOLD: This is a predefined threshold value for the Eye Aspect Ratio. If the calculated EAR falls below this threshold, it indicates drowsiness.
FRAME_COUNT: This variable specifies the number of consecutive frames below the threshold necessary to classify the driver as drowsy.
Main Loop:
The code operates within an infinite loop, continuously capturing video frames from the camera.
For each frame, it is converted to grayscale, and faces are detected using the detector.
For each identified face, facial landmarks are predicted using the predictor.
The EAR is calculated for both eyes, and if it falls below the threshold, a frame counter (frame_counter) is incremented. If this counter surpasses FRAME_COUNT, indicating drowsiness, the text "Drowsy" is displayed on the frame.
If the EAR is above the threshold, the frame counter is reset to 0.
Convex hulls are drawn around the left and right eyes for visualization.
The processed frame, indicating the driver's drowsiness status, is displayed in a window titled "Driver Drowsiness Detection."
The loop can be terminated by pressing the 'q' key, closing the video window.
In summary, this code continuously captures video frames, detects faces and facial landmarks, calculates the Eye Aspect Ratio for drowsiness detection, and displays the video frames with an alert message if the driver is deemed drowsy. It provides a real-time indication of the driver's drowsiness status based on their eye movements.
Drowsiness Detection System for Enhanced Road Safety
Background
Drowsy driving poses a significant threat to road safety, contributing to a substantial number of accidents, injuries, and fatalities worldwide. To address this issue, implementing a real-time driver drowsiness detection system can effectively monitor driver behavior and provide timely alerts to both the driver and concerned authorities when fatigue is detected.
System Overview
The proposed system utilizes a Raspberry Pi camera mounted within the vehicle to capture real-time images of the driver's face and eyes. These images are then processed using advanced computer vision techniques to extract relevant features, such as eye blinking rate, perclos (percentage of eyelid closure), and facial expressions. These extracted features are then analyzed using a trained machine learning model that has been meticulously trained on a comprehensive dataset of labeled images. This model effectively classifies the driver's state as either alert or fatigued.
Key Components
Raspberry Pi: The Raspberry Pi serves as the processing unit for the system, leveraging its low-cost and single-board design for efficient operation.
Raspberry Pi Camera: A high-resolution camera captures real-time images of the driver's face and eyes, providing the necessary data for drowsiness detection.
Computer Vision Algorithms: Sophisticated computer vision algorithms extract critical features from the captured images, such as eye blinking rate, perclos, and facial expressions.
Machine Learning Model: A trained machine learning model, carefully trained on a dataset of labeled images, analyzes the extracted features and classifies the driver's state as either alert or fatigued.
Notification Mechanism: An effective notification mechanism alerts the driver and concerned authorities, such as family members or emergency responders, when fatigue is detected. This notification can be implemented through sound signals, email, or SMS.
Working Principle
Real-time Image Capture: The Raspberry Pi camera continuously captures real-time images of the driver's face and eyes.
Feature Extraction: Computer vision algorithms process the captured images to extract relevant features, such as eye blinking rate, perclos, and facial expressions.
Fatigue Classification: The extracted features are fed into the trained machine learning model, which accurately classifies the driver's state as either alert or fatigued.
Alert Triggering: Upon detection of fatigue, an alert is triggered to warn both the driver and concerned authorities.
Driver Notification: The driver is notified through a sound signal, such as a beep or a voice message, to encourage corrective measures.
Authority Notification: Concerned authorities, such as family members or emergency responders, are notified via email or SMS to ensure timely intervention if necessary.

Benefits
Real-time Monitoring: Continuous monitoring of the driver's state enables prompt intervention and accident prevention.
Non-intrusive Detection: The system operates without requiring additional driver input, ensuring distraction-free driving.
Early Warning: Early detection of fatigue allows drivers to take precautionary measures, such as pulling over to rest or seeking assistance.
Enhanced Road Safety: By reducing the risk of fatigue-related accidents, the system significantly improves road safety.
Implementation Steps
Data Collection: Gather a comprehensive dataset of images representing various levels of driver fatigue.
Feature Extraction: Develop robust computer vision algorithms to extract relevant features from the collected images.
Model Training: Train a machine learning model using the labeled dataset to effectively classify driver fatigue.
System Integration: Integrate the camera, computer vision algorithms, machine learning model, and notification mechanism into the Raspberry Pi platform.
Testing and Evaluation: Conduct thorough testing and evaluation to ensure accurate fatigue detection and system performance in real-world driving scenarios.

