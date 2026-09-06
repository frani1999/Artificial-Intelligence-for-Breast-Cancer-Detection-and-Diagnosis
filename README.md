# 1. Artificial Intelligence for Breast Cancer Detection and Diagnosis

This thesis explores different techniques for detecting and diagnosing breast cancer using artificial intelligence algorithms based on **machine learning** and **deep learning**. Labelled mammography images serve as the data source and are processed differently depending on the technique applied.

The results are compared to identify the best combination of techniques to integrate into a CADx or CADe system.

# 2. Repository Contents

This repository contains four folders:

* **Data** → contains CSV and XLSX files used to assign labels to images or extract subsets of images. The dataset images can be downloaded from [Kaggle - CBIS-DDSM: Breast Cancer Image Dataset](https://www.kaggle.com/datasets/awsaf49/cbis-ddsm-breast-cancer-image-dataset).
* **Code** → contains the Python code developed for each experiment, organised into the following folders:
  * **Detection** → contains the code for the detection part of the project.
  * **Diagnosis** → contains the code for the diagnosis part of the project.
  * **Others** → contains additional scripts relevant to the project. The **MIAS** subfolder contains code used at the beginning of the project to explore Python functions with the **MIAS** database, which is smaller than the **CBIS-DDSM** database. The **Obsolete** subfolder contains code for techniques that were later discarded.
* **Results** → contains the results of the detection and diagnosis experiments, including graphs and execution logs in TXT files. The YOLOv5 detection results include separate folders for training and testing outputs.
* **Resources** → contains images used in the project documentation.

# 3. Techniques Used

The following **deep learning** techniques were used:

- A custom convolutional neural network (CNN) with the following architecture:

<p align="center">
  <img src="Resources/My_CNN.png" alt="My CNN architecture" width="650">
</p>

- The VGG16 network, with the following architecture:

<p align="center">
  <img src="Resources/Net_VGG16.png" alt="VGG16 network architecture" width="650">
</p>

- **YOLOv5 retraining**: The object detection algorithm was adapted to detect tumours in mammography images. A subset of mammograms from CBIS-DDSM was manually labelled in **YOLOv5** format for training.
  - [YOLOv5 repository](https://github.com/ultralytics/yolov5)
  - [YOLOv5 retraining tutorial](https://colab.research.google.com/github/roboflow-ai/yolov5-custom-training-tutorial/blob/main/yolov5-custom-training.ipynb#scrollTo=X7yAi9hd-T4B)

The following **machine learning** techniques were used:

- *K-Nearest Neighbours (KNN)*
- *Logistic Regression*
- *Support Vector Machine (SVM)*
- *Random Forest*
- *Decision Tree Classifier*
- *Gaussian Naive Bayes Classifier (GaussianNB)*

# 4. Results

## 4.1. Detection Results

### 4.1.1. Custom CNN

<p align="center">
  <img src="Results/Detection/My_CNN_and_VGG16/Detection%20Result%20-%20My%20CNN.png" alt="Detection Result - My CNN" width="600">
</p>

<h3 align="center"><strong>Test accuracy: 0.84</strong></h3>

### 4.1.2. VGG16 Network

<p align="center">
  <img src="Results/Detection/My_CNN_and_VGG16/Detection%20Result%20-%20VGG16.png" alt="Detection Result - VGG16" width="600">
</p>

<h3 align="center"><strong>Test accuracy: 0.87</strong></h3>

### 4.1.3. YOLOv5

#### 4.1.3.1. Confusion Matrix

<p align="center">
  <img src="Results/Detection/YOLOv5/Train/confusion_matrix.png" alt="YOLOv5 confusion matrix" width="600">
</p>

#### 4.1.3.2. Metrics

<p align="center">
  <img src="Results/Detection/YOLOv5/Train/results.png" alt="YOLOv5 training metrics" width="800">
</p>

#### 4.1.3.3. Sample Results

<table align="center">
  <tr>
    <td align="center"><img src="Results/Detection/YOLOv5/Test/test1.jpg" alt="YOLOv5 detection sample 1" width="350"></td>
    <td align="center"><img src="Results/Detection/YOLOv5/Test/test11.jpg" alt="YOLOv5 detection sample 11" width="350"></td>
  </tr>
  <tr>
    <td align="center"><img src="Results/Detection/YOLOv5/Test/test19.jpg" alt="YOLOv5 detection sample 19" width="350"></td>
    <td align="center"><img src="Results/Detection/YOLOv5/Test/test22.jpg" alt="YOLOv5 detection sample 22" width="350"></td>
  </tr>
  <tr>
    <td align="center"><img src="Results/Detection/YOLOv5/Test/test33.jpg" alt="YOLOv5 detection sample 33" width="350"></td>
    <td align="center"><img src="Results/Detection/YOLOv5/Test/test5.jpg" alt="YOLOv5 detection sample 5" width="350"></td>
  </tr>
</table>

## 4.2. Diagnosis Results

### 4.2.1. Calcifications - Custom CNN

<p align="center">
  <img src="Results/Diagnosis/My_CNN_and_VGG16/Calcifications/Calc_Diagnosis_My_CNN.png" alt="Calcification diagnosis results for the custom CNN" width="600">
</p>

<h3 align="center"><strong>Test accuracy: 0.6</strong></h3>

### 4.2.2. Calcifications - VGG16 Network

<p align="center">
  <img src="Results/Diagnosis/My_CNN_and_VGG16/Calcifications/Calc_Diagnosis_VGG16.png" alt="Calcification diagnosis results for VGG16" width="600">
</p>

<h3 align="center"><strong>Test accuracy: 0.57</strong></h3>

### 4.2.3. Masses - Custom CNN

<p align="center">
  <img src="Results/Diagnosis/My_CNN_and_VGG16/Masses/Diagnosis_My_CNN_masses.png" alt="Mass diagnosis results for the custom CNN" width="600">
</p>

<h3 align="center"><strong>Test accuracy: 0.54</strong></h3>

### 4.2.4. Masses - VGG16 Network

<p align="center">
  <img src="Results/Diagnosis/My_CNN_and_VGG16/Masses/Diagnosis_VGG16_masses.png" alt="Mass diagnosis results for VGG16" width="600">
</p>

<h3 align="center"><strong>Test accuracy: 0.62</strong></h3>

## 4.3. Diagnosis Results Using Machine Learning Techniques

**Sensitivity formula:**

$$
\text{Sensitivity} = \frac{\text{Correctly classified benign cases}}{\text{Total benign cases}} \times 100\%
$$

**Specificity formula:**

$$
\text{Specificity} = \frac{\text{Correctly classified malignant cases}}{\text{Total malignant cases}} \times 100\%
$$

**Sensitivity:**

| Technique                | Feature extraction (%) | Bounded feature extraction (%) |
| ------------------------ | ---------------------- | ------------------------------ |
| KNN                      | 36.57                  | 37.09                          |
| Logistic Regression      | 54.24                  | 53.56                          |
| SVC                      | 55.88                  | 55.88                          |
| Random Forest            | 44.80                  | 45.36                          |
| Decision Tree Classifier | 45.60                  | 39.66                          |
| GaussianNB               | 57.68                  | 57.39                          |

**Specificity:**

| Technique                | Feature extraction (%) | Bounded feature extraction (%) |
| ------------------------ | ---------------------- | ------------------------------ |
| KNN                      | 26.04                  | 25.86                          |
| Logistic Regression      | 33.96                  | 26.83                          |
| SVC                      | 20.21                  | 20.21                          |
| Random Forest            | 28.29                  | 30.13                          |
| Decision Tree Classifier | 30.86                  | 26.74                          |
| GaussianNB               | 18.44                  | 18.33                          |

Both tasks use binary classification. The following tables show the complementary percentages (100% minus each value above):

**Sensitivity:**

| Technique                | Feature extraction (%) | Bounded feature extraction (%) |
| ------------------------ | ---------------------- | ------------------------------ |
| KNN                      | 63.43                  | 62.91                          |
| Logistic Regression      | 45.76                  | 46.44                          |
| SVC                      | 44.12                  | 44.12                          |
| Random Forest            | 55.20                  | 54.64                          |
| Decision Tree Classifier | 54.40                  | 60.34                          |
| GaussianNB               | 42.32                  | 42.61                          |

**Specificity:**

| Technique                | Feature extraction (%) | Bounded feature extraction (%) |
| ------------------------ | ---------------------- | ------------------------------ |
| KNN                      | 73.96                  | 74.14                          |
| Logistic Regression      | 66.04                  | 73.17                          |
| SVC                      | 79.79                  | 79.79                          |
| Random Forest            | 71.71                  | 69.87                          |
| Decision Tree Classifier | 69.14                  | 73.26                          |
| GaussianNB               | 81.56                  | 81.67                          |
