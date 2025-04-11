# 🐵🐵 Primate Nasal Tracking in Thermal Imaging Despite Fence Occlusion 🐵🐵

This repository contains all the main source code used for my final year dissertation project on: **Primate Nasal Tracking in Thermal Imaging Despite Fence Occlusion**.
(See report write up for explanation).

Below is an overview of each file in this repository: what is contained and how to run it.

## Fence Mitigation

All notebooks in this section were run on **Google Colab** but can be compatible with **Jupyter Notebook**.

### 1) All Fence Detection  
This file contains 6 methods for qualitative fence detection:
- Edge detection (Sobel filter, morphological operations)  
- Hough Line Transforms (Standard and Probabilistic)  
- Temperature thresholding  
- Hybrid approach: temperature thresholding followed by standard Hough Transform

### 2) Best Fence Detection  
This file is a quantitative evaluation of the best previous fence detection methods: Standard Hough, Probabilistic Hough, temperature thresholding, and hybrid approach.
Quantitative evaluation is possible thanks to 4 manually annotated ground-truth images located in the Ground truth masks folder. Their respective thermal images are also in that folder. Image number matches ground truth fence label e.g. 1.csv frame will match mask_1.tif labelling.

### 3) All Inpainting  
Qualitative comparison of 4 inpainting techniques:
- Navier-Stokes  
- Telea  
- Biharmonic  
- SIREN (neural implicit inpainting)

### 4) Best Inpainting Compared  
Using the best inpainting methods, SIREN and Biharmonic inpainting where tested quantitatively using an artificial fence frame.
Images to test inpainting and fence detection (as well as the artificial fence mask) are in "Sample Images" folder.
Performs a **quantitative comparison** of SIREN vs. Biharmonic inpainting using artificial fence mask.  

## Labelling Process
The process of semi-manually labelling the primates nose for U-Net training is in this file: Semi-automatic Labelling. Example data to test out how the labels are generates is in the zip file: labelling.zip. 


## Tracking
The rest of the files were written in vscode using a Jupter notebook and virtual environments. These files cannot be run in google colab as they require `tkinter` library for GUI-based user interaction. Zip file called: "test_sequence_for_tracking.zip" contains a primate video sequence, in the form of individual csv raw temperature frames. The sequence chosen was not the only one tested, but it is a good test because it is a difficult clip due to primate moving, camera moving, and the lighting changing. 

### 5) Lucas-Kanade Tracking  
Notebook shows different implementations of Lucas-Kanade-based tracking:
- Standard Lucas-Kanade (only click at the start what feature to track)
- Lucas-Kanade with Kalman filter  
- Lucas-Kanade with manual re-detection as a fallback

### 6) U-Net Tracking  
File showing how to use a trained U-Net to detect primates nose and track it across frames.
Please note, the final model's weights have been uploaded to Canvas source code only. In canvas source code it can be found in the folder Tracking code, the file is called "Model_best.pth".

### 7) U-Net Training  
This notebook shows how the U-Net model used for nose detecting was trained. Note, Kaggle was used for implementing this notebook as it offer's GPU acceleration. For training the U-Net GPU acceleration is recommended. 

## Video Examples
This folder contains mp4 videos that show the performance of different methods:
- **Lucas-Kanade fallback on U-Net**: First tries Lucas-Kanade, then U-Net, then manual correction if both fail.
- **Lucas-Kanade and Kalman Filter**: Combines both techniques to attempt smoother tracking.
- **U-Net Only**: Uses only the U-Net for nose detection and tracking.
- **Only Lucas-Kanade**: Shows how different fence segmentation methods (listed above), combined with biharmonic inpainting, affect Lucas-Kanade tracking. Temperature thresholding had the best performance. 

