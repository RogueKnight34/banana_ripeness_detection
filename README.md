# Banna Detection and Ripeness Classification using YOLOv11 and MobileNetV2

## Group memebers 
- [Maria Roman]
- [Jeremy Kulisek]

## Project Overview 
This project presents a two-stage computer vision pipeline for banana detection and ripeness classification. The system first detects bananas in an image using YOLOv11 obeject detection model, then classifies the detected banana regions into one of four ripeness categories: uripe, ripe, overripe, or rotten using a MobileNetV2-based classifier.

The goal for this project is to demonstrate an automated approach to fruit quality assessment that could support future applications in agricultural monitoring, fruit sorting, and waste reduction.

## Objectives
- Detect bananas within an image using object detection
- Classify detected bananas by ripeness level
- Combine both models into a single end-to-end pipeline
- Evaluate the strengths and limitations of the two-stage approach

## Tools and Technologies
- Python
- YOLOv11
- Ultralytics
- TensorFlow / Keras
- MobileNetV2
- OpenCV
- NumPy
- Matplotlib
- Roboflow
- Kaggle
- Google Colab

## Project Pipeline
Our system uses a two-stage workflow: 

1. **Object Detection Stage**
   - A YOLOv11 model is trained to detect and localize bananas in a given image.
   - The detector produces bounding boxes around the banana regions.
  
2. **Ripeness Classification Stage**
   - Each detected banana crop is resized and passed to a MobileNetV2-based classifier.
   - The classifier predicts one of four ripeness labels:
     -Unripe
     -Ripe
     -Overripe
     -Rotten

3. **Final Output**
   - The original image is displayed with bounding boxes and predicted ripeness labels.

## Datasets
For this project we utilized the following datasets:
- open-source banana ripeness dataset for the classification stage
- a custom Roboflow-prepared dataset for the banana object detection stage
- additional custom test images for qualitative evaluation 


## Models Information

### YOLOv11 Detector
The YOLOv11 model was used to detect bananas in an image, it was trained in Google Colab using Ultralytics framework after exporting the dataset from Roboflow.

**Detection Metrics**
- Precision: 55.1%
- Recall: 57.4%
- F1-score: 0.562
- mAP@50: 0.501 
- mAP@50-95: 0.294

### MobileNetV2 Classifier
The ripeness classifier was built using transfer learning with MobileNetV2 in TensorFlow/ Keras, it predicts the following four classes:
- Unripe
- Ripe
- Overripe
- Rotten

## Results Summary
The integrated pipeline successfully detected bananas and classified ripeness in many test images, especially when the banana were clearly visible and separated from the backgound.

### Strengths 
- Works well on clear single-banana images
- Can handle some multi-banana scenes
- Successfully combines detection and classification into one pipeline from using two separate models

### Limitations 
- YOLO had more difficulty with rotten or darker bananas
- The classifier had more difficuolty with unripe bananas, especially green-yellow transition cases
- Some final errors were caused by interaction between the two models, since incorrector loose crops from the detector can reduce classification accuracy



## How to Use
1. Clone this repository or download the project files. 
2. Open Google Colab notebook which contains the merged pipeline.
3. Install the required libraries.
4. Upload the classifier model file and a banana test image.

## Option A: Use the Included Trained YOLO Model
5. Uisng the 'best.pt' file, upload it to Colab when prompted or place it in the expected working path.
6. Load both models.
7. Run the final test cell to generate the detection and ripeness classification output.
   
## Option B: Reproduce the YOLO Model by Retraining 
5. Open the Roboflow project / version used for this project:
   https://universe.roboflow.com/marias-workspace-nru3u/banana-finder-faan5
7. Go to **Version**.
8. Select **Dowload Dataset** or **Export**
9. Choose **YOLOv11** format.
10. Select **Show download code**
11. Paste that code into the provided Colab notebook.
12. Run the Roboflow dataset download cell.
13. Run the YOLO training cell to generate wa new 'best.pt' file in Colab.
14. Load both models.
15. Run the final test cell to generate the detection and ripeness classification output. 



















