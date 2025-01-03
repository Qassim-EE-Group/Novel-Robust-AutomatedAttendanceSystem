# Novel-Robust-AutomatedAttendanceSystem

This repository contains the codebase for an automated attendance system built with Python and Flask. The system leverages face recognition and advanced image processing techniques to capture, analyze, and record attendance for classroom sessions. It includes features for instructor and student roles, allowing instructors to manage courses, enroll students, and review attendance logs, while students can upload their images for recognition. The project integrates a MySQL database for storing attendance records, course details, and user data. Additionally, the system employs YOLO-based object detection and RetinaFace for face detection, ESRGAN for image enhancement, and advanced algorithms for classifying student attendance dynamically across multiple session images. This repository serves as a robust solution for streamlining attendance management in academic or professional environments.


## Requirements

First of all, you need a camera to connect it with the code, so that the code can take the input image from it.

Secondly, you have to install the following libraries:

- Python v3.9

- io (from BytesIO)

- Flask

- flask_socketio

- mysql.connector.python

- werkzeug.security

- werkzeug.utils

- opencv-python

- numpy

- insightface (Microsoft C++ Build Tools is needed)

- torch

- ultralytics

- pandas

- ESRGAN model

- onnxruntime


## Codes explanation

Now we will explain each code. What is the purpose of it and what is the key lines yo have to modify, so the code work properly in your computer.

### AAS_Program.py


### aasfinal7.py

The *`aasfinal7.py`* script facilitates automated image capture during a session using a network camera. It controls the camera's flashlight via an API and captures three images at predefined intervals: the first after a fixed time, the second after an additional interval, and the third at a random time before the session ends. The script uses OpenCV to stream video from the camera and save captured frames as images, ensuring proper lighting by activating the flashlight before each capture. This script is a critical component for gathering visual data in the automated attendance system.

### CoursesEmb3.py

The *`CoursesEmb3.py`* script manages the creation, updating, and storage of facial embeddings for students in specific courses. It uses the InsightFace library to extract normalized facial embeddings from student images and averages them to represent each student. The embeddings are stored both in a `.pkl` file (named after the course ID) and in a MySQL database. The script ensures embeddings are updated when new student images are added, making it a critical part of maintaining accurate and efficient facial recognition for course attendance systems.

### db_operations12.py

The *`db_operations12.py`* script is a comprehensive utility for managing database operations in the automated attendance system. It establishes a connection with a MySQL database and provides functions for handling instructors, students, courses, and attendance records. Key functionalities include adding and retrieving instructors and students, managing course enrollments, storing and fetching facial embeddings, and inserting and updating attendance data. The script also supports saving and retrieving session images and embeddings, ensuring smooth interaction between the application and the database. It is integral to maintaining the system's data integrity and operational efficiency.

### v18.py

The *`v18.py`* script is a key component of the automated attendance system, responsible for facial recognition and classification. It uses InsightFace to analyze images, extract embeddings, and match them with pre-stored course-specific embeddings. The script classifies students into categories like attended, late, absent, and out-of-class based on their presence across three images taken during a session. It includes preprocessing methods such as CLAHE for image enhancement and duplicate detection to avoid redundant processing. Additionally, it supports dynamic updates for face recognition thresholds and saves recognized faces with bounding boxes drawn for visual validation.

### yolo_detect5.py

The *`yolo_detect5.py`* script integrates YOLOv8 for detecting persons in an image and RetinaFace for detecting faces within those regions. It processes images in multiple steps, starting with detecting persons, followed by cropping and refining face regions. The script also uses ESRGAN for super-resolution to enhance the quality of cropped face images. It supports GPU acceleration for faster processing and outputs enhanced face images for further analysis or recognition, making it a vital preprocessing module for high-accuracy face detection and recognition in the attendance system.

### HTML folder

It consists of 5 html codes each one of them plays an important role in shaping the friendly user-interface and enhancing the overall user experience.

## Database

By using MySQL library, we created a database to save the images of each student, and they can upload an image by entering the student user-interface and upload the desire images. These images are saved in a pkl-file folder, also the results of the attendance process is saved in pkl-file folder and on the user-interface.  
