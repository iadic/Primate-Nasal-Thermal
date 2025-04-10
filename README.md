# 🐵🐵 Primate Nasal Tracking in Thermal Imaging Despite Fence Occlusion 🐵🐵

This repository contains all the main source code used for my final year dissertation project on: **Primate Nasal Tracking in Thermal Imaging Despite Fence Occlusion**.
(See report write up for explaination).

Below is an overview of each file in this repository: what is contained and how to run it.

## Fence Mitigation

> All notebooks in this section were run on **Google Colab** (also compatible with **Jupyter Notebook**).

### 1) All Fence Detection  
Demonstrates six visual methods for qualitative fence detection:
- Edge detection (Sobel filter, morphological operations)  
- Hough Line Transforms (Standard and Probabilistic)  
- Temperature thresholding  
- Hybrid approach: temperature thresholding followed by standard Hough Transform

### 2) Best Fence Detection  
Quantitatively compares four methods (Standard Hough, Probabilistic Hough, temperature thresholding, and hybrid) using four annotated ground-truth images.  
📂 Ground truth masks and images are located in the `Ground Truth Fence Masks` folder.

### 3) All Inpainting  
Shows a **qualitative comparison** of different inpainting techniques:
- Navier-Stokes  
- Telea  
- Biharmonic  
- SIREN (neural implicit inpainting)

### 4) Best Inpainting Compared  
Performs a **quantitative comparison** of SIREN vs. Biharmonic inpainting using artificial fence masks.  
📂 Sample images for testing inpainting methods are located in the `Sample Images` folder.

---

## ✏️ Labelling Process

These notebooks create a custom dataset for **U-Net-based nose segmentation**.

- `Semi-automatic Labelling`: Allows user input to select the nose point and generate a binary mask (used when Lucas-Kanade fails).
- `Example data for labelling.zip`: Contains a sample video sequence to demonstrate the labeling process.

> **Note:** Some files require `tkinter` for GUI-based user interaction, so must be run in a local Jupyter Notebook environment (not Colab).

---

## 🧠 Tracking

### 5) Lucas-Kanade Tracking  
Explores different Lucas-Kanade-based methods:
- Plain Lucas-Kanade  
- Lucas-Kanade with Kalman filter  
- Lucas-Kanade with manual re-detection fallback

### 6) U-Net Tracking  
Uses a trained U-Net to detect and track the nose region frame-by-frame.  
🔗 **Model weights download link:** [Insert your Google Drive or Hugging Face link here]

### 7) U-Net Training  
Notebook used to train the U-Net segmentation model, run on **Kaggle** with GPU acceleration. Shows the full training pipeline and preprocessing for primate nose segmentation.

📂 `test_sequence_for_tracking.zip`: A difficult, unseen test sequence (in CSV format) used to evaluate how well various tracking methods perform.

---

## 🎥 Video Examples

These `.mp4` videos demonstrate the performance of different methods:

- **Lucas-Kanade fallback on U-Net**: First tries Lucas-Kanade, then U-Net, then manual correction if both fail.
- **Lucas-Kanade + Kalman Filter**: Combines both techniques for smoother tracking.
- **U-Net Only**: Uses only the U-Net for detection and tracking.
- **Lucas-Kanade + Inpainting**: Shows how different fence segmentation methods, combined with biharmonic inpainting and Lucas-Kanade tracking, affect overall performance.

---

## 📁 Folder Summary (Optional)
> _Add this if you'd like a quick map of the folder layout_

```bash
Primate-Nasal-Thermal/
├── Fence Mitigation/
├── Labeling Process/
├── Tracking/
├── Sample Images/
├── Ground Truth Fence Masks/
├── test_sequence_for_tracking.zip
├── videos/
├── README.md
