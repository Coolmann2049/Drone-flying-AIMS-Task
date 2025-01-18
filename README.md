This repository is a task given by AIMS-DTU to control a drone based on Hand-gesture classification and Voice control. 

For hand gesture recognition, a pre-made repository [hand-gesture-recognition-using-mediapipe]([url](https://github.com/kinivi/hand-gesture-recognition-mediapipe/blob/main/README.md)) was used.
(Note the linked repository is translated version by [kinivi](https://github.com/kinivi). Original can be found [here](https://github.com/Kazuhito00/hand-gesture-recognition-using-mediapipe/blob/main/README_EN.md) by [Kazuhito00](https://github.com/Kazuhito00).

Changes made to original repository:
- Removed "point_history_classifier" model and it's usage in app.py
- Removed pre-existing gesture-classifiers (open, close, pointer, ok)
- Removed pre-existing training-data
- Added new gesture-classifiers (up, down, left, right, forward, backward, stop, wiggle)
- Added new training data to all gesture-classifiers
- Removed FPS measure.

**model/keypoint_classifier**

This directory stores files related to hand sign recognition.
The following files are stored.

- Training data(keypoint.csv)
- Trained model(keypoint_classifier.tflite)
- Label data(keypoint_classifier_label.csv)
- Inference module(keypoint_classifier.py)

The original repository can be referenced on how the model was trained and how to train it further
Point gesture collection and training is currently out of scope but is the future of the project.

**Model structure**
for the model prepared in keypoint_classification.ipynb
![image](https://github.com/user-attachments/assets/840e7c70-5828-4ac4-8552-89996d4a8a55)

How the model works? 
The model is a neural network that uses hand-landmarks on the cropped region after normalization to classify it into the given categories.
The hand-landmark was taken from google's [mediapipe hands](https://ai.google.dev/edge/mediapipe/solutions/vision/hand_landmarker#models) model. 

The mediapipe hands model card can be found [here](https://storage.googleapis.com/mediapipe-assets/Model%20Card%20Hand%20Tracking%20(Lite_Full)%20with%20Fairness%20Oct%202021.pdf). It was trained on a downsized [HaGRID Database](https://www.kaggle.com/datasets/innominate817/hagrid-sample-30k-384p/data)
The original HaGRID database can be found [here](https://github.com/hukenovs/hagrid). 
The mediapipe hands model bases it's predictions off the [GHUM Hand Model](https://openaccess.thecvf.com/content_CVPR_2020/papers/Xu_GHUM__GHUML_Generative_3D_Human_Shape_and_Articulated_Pose_CVPR_2020_paper.pdf).

