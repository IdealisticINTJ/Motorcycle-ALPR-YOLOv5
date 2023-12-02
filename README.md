### To be updated. Code refactored. 
---

# Part 1 

## 1. Motorcycle Helmet Detection 

### Introduction
This methodology outlines the approach and techniques used to develop a real-time end-to-end motorcycle helmet detection system based on the YOLOv5 algorithm. The system aims to automatically detect motorcycles in images or videos and determine whether the riders are wearing helmets. The methodology is divided into two stages: Motorcycle Detection (YOLOv5-MD) and Helmet Detection (YOLOv5-HD). To validate the system's effectiveness, a new dataset called HFUT-MH was created, incorporating various real-world traffic scenarios.

### Dataset
The HFUT-MH dataset consists of two subsets:
1. HFUT-MH1: Used for motorcycle detection, containing 28,634 images with three categories (motorcycles, bicycles, tricycles).
2. HFUT-MH2: Used for helmet detection, containing 24,492 images with two categories (helmets and no_helmets).

#### Dataset Preparation
- Remove repeated images.
- Exclude non-riding vehicles, highly blurred objects, and irrelevant vehicles.

### 1.1 Motorcycle Detection (YOLOv5-MD)
#### Model Configuration
- YOLOv5 architecture.
- Depth_multiple: 0.33.
- Width_multiple: 0.5.
- Input size: 640x640.
- Two detection categories: motorcycles, bicycles, and tricycles.
- K-means++ algorithm for anchor clustering.

#### Training
- Stochastic Gradient Descent (SGD) optimizer with momentum (0.937) and weight decay (0.0005).
- Training for 300 epochs.
- HFUT-MH1 dataset split into training and test sets (70:30).

#### Evaluation Metrics
- Precision (P), Recall (R), F1-score, and Average Precision (AP).

#### Results
- Achieved mAP of 98.5% and FPS of 126.
- Outperformed state-of-the-art methods in both accuracy and real-time detection.

### 1.2 Helmet Detection (YOLOv5-HD)
#### Model Configuration
- YOLOv5 architecture.
- Depth_multiple: 0.33.
- Width_multiple: 0.5.
- Input size: 320x320.
- Two detection categories: helmet and no_helmet.
- K-means++ algorithm for anchor clustering.

#### Training
- Stochastic Gradient Descent (SGD) optimizer with momentum (0.937) and weight decay (0.0005).
- Training for 300 epochs.
- HFUT-MH2 dataset split into training and test sets (70:30).

#### Evaluation Metrics
- Precision (P), Recall (R), F1-score, and Average Precision (AP).

#### Results
- Achieved mAP of 99.2% and FPS of 135.
- Outperformed state-of-the-art methods in both accuracy and real-time detection.

### Integration
- Combine the results from both stages to determine whether a motorcycle rider is wearing a helmet.
- Evaluate and optimize the integration for real-time processing.

### Detection in Crowded Scenes
- Introduced Soft-NMS post-processing to improve detection in congested traffic scenarios.
- Adjusted the σ value for optimal mAP.

### Final End-to-End Detection Results
- Achieved end-to-end mAP of 97.7%, F1-score of 92.7%, and FPS of 63.
- Successfully detected overloaded motorcycles based on the number of helmets detected.

### Conclusion
The proposed methodology presents a highly accurate and real-time end-to-end motorcycle helmet detection system based on YOLOv5. The HFUT-MH dataset, developed for this purpose, provides a diverse and challenging dataset for training and validation. The system outperforms state-of-the-art methods in terms of both accuracy and real-time detection. Future work may include object tracking to reduce redundant detection and improve system efficiency for traffic video surveillance.
