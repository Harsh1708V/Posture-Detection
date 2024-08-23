This GitHub repository contains a posture detection program that utilizes [YOLOv5](https://github.com/ultralytics/yolov5), an advanced object detection algorithm, to detect and predict lateral sitting postures. The program is designed to analyze the user's sitting posture in real-time and provide feedback on whether the posture is good or bad based on predefined criteria. The goal of this project is to promote healthy sitting habits and prevent potential health issues associated with poor posture.

Key Features:

* YOLOv5: The program leverages the power of YOLOv5, which is an object detection algorithm, to
  accurately detect the user's sitting posture from a webcam.
* Real-time Posture Detection: The program provides real-time feedback on the user's sitting posture, making it suitable
  for use in applications such as office ergonomics, fitness, and health monitoring.
* Good vs. Bad Posture Classification: The program uses a pre-trained model to classify the detected posture as good or
  bad, enabling users to improve their posture and prevent potential health issues associated with poor sitting habits.
* Open-source: The program is released under an open-source license, allowing users to access the source code, modify
  it, and contribute to the project.

### Built With

![Python]

# Getting Started

### Prerequisites

* Python 3.12.x

### Installation  
If you have an NVIDIA graphics processor, you can activate GPU acceleration by installing the GPU requirements. Note that without GPU acceleration, the inference will run on the CPU, which can be very slow.  
#### Windows  
  
1. `git clone https://github.com/itakurah/SittingPostureDetection.git`  
2. `python -m venv venv`  
3. `.\venv\scripts\activate.bat`  
##### Default/NVIDIA GPU support:  
4.  `pip install -r ./requirements_windows.txt` **OR** `pip install -r ./requirements_windows_gpu.txt`

### Run the program

`python application.py <optional: model_file.pt>`
The default model is loaded if no model file is specified.

# Model
The program uses a custom trained [YOLOv5s](https://github.com/ultralytics/yolov5/blob/79af1144c270ac7169553d450b9170f9c60f92e4/models/yolov5s.yaml) model that is trained on about 160 images per class for 146 epochs. The model has two classes: sitting_good and sitting_bad to give feedback about the current sitting posture.
## Architecture
The architecture that is used for the model is the standard YOLOv5 architecture:

*Fig. 1: The architecture of the YOLOv5 model, which consists of three parts: (i) Backbone: CSPDarknet, (ii) Neck: PANet, and (iii) Head: YOLO Layer. The data are initially input to CSPDarknet for feature extraction and subsequently fed to PANet for feature fusion. Lastly, the YOLO Layer outputs the object detection results (i.e., class, score, location, size)*

## Model Results
The validation set contains 80 images (40 sitting_good, 40 sitting_bad). The results are as follows:
|Class|Images|Instances|Precision|Recall|mAP50|mAP50-95|
|--|--|--|--|--|--|--|
|all| 80 | 80 | 0.87 | 0.939 | 0.931 | 0.734 |
|sitting_good| 40 |  40| 0.884 | 0.954 | 0.908 |0.744  |
|sitting_bad| 80 | 40 | 0.855 | 0.925 | 0.953 | 0.724 |

Detailed graphs:

F1-Confidence Curve:

<img src = "https://github.com/user-attachments/assets/955f3b41-c49a-463a-a6d9-88ee1e547851" width=50% height=50%>

Precision-Confidence Curve:

![P_curve](https://github.com/user-attachments/assets/e2049240-c4b1-4c0a-900e-b636b88f4699)

Recall-Confidence Curve:

![R_curve](https://github.com/user-attachments/assets/d7e53659-8321-411e-9de3-cb246fe91666)

Precision-Recall Curve:

![PR_curve](https://github.com/user-attachments/assets/b5ed840e-eb63-4036-8f6f-f9c3aeb900ad)

Confusion Matrix:

![confusion_matrix](https://github.com/user-attachments/assets/a970f4ef-3b0f-42cf-a19d-4e6589d771e9)

# Sources

 - Jocher, G. (2020). YOLOv5 by Ultralytics (Version 7.0) [Computer software]. https://doi.org/10.5281/zenodo.3908559
 - Fig. 1: TraCon: A novel dataset for real-time traffic cones detection using deep learning - Scientific Figure on ResearchGate. Available from: https://www.researchgate.net/figure/The-architecture-of-the-YOLOv5-model-which-consists-of-three-parts-i-Backbone_fig1_360834230 [accessed 24 Jun, 2023]

# License

This project is licensed under the MIT License. See the LICENSE file for details.

<!-- MARKDOWN LINKS & IMAGES -->

[Python]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
