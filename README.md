Here is the updated `README.md` in Markdown format, now including information about the best-performing models and their evaluation metrics:

---

# Aerial Image Segmentation for Buildings and Roads

This repository contains a suite of deep learning models tailored for segmenting **buildings** and **roads** from high-resolution satellite imagery. Each model explores different techniques, from classical unsupervised methods to attention-based CNN architectures, to improve segmentation quality.

## 📁 Repository Structure

* [`K-Means-Clustering/`](./K-Means-Clustering)
  Unsupervised clustering-based segmentation.

* [`Patched-Based CNN/`](./Patched-Based%20CNN)
  Supervised CNN trained on localized patches from satellite images.

* [`Res2UNet/`](./Res2UNet)
  A deep residual variant of U-Net designed for enhanced feature learning.

* [`Stacked-UNet-Building-Extraction/`](./Stacked-UNet-Building-Extraction)
  Multi-stage refinement using stacked U-Nets for building extraction.

* [`UNet_ECBA/`](./UNet_ECBA)
  U-Net augmented with Efficient Channel and Batch Attention modules.

* `README.md`
  Repository overview and documentation (this file).

---

## Model Descriptions

### K-Means Clustering

A baseline unsupervised segmentation model using K-means clustering on pixel intensity. Quick to set up, but lacks spatial awareness or learning capability.

---

### Patch-Based CNN

Divides large satellite images into patches (e.g., 224×224) and trains a CNN to classify each pixel in the patch. Offers localized learning, useful for areas with fine-grained structure or inconsistent textures.

---

### Res2UNet — Top Performer

Integrates ResNet-style residual blocks into the U-Net architecture, enabling better gradient flow and multi-scale feature learning.

* **Mean IoU Score**: `0.7138`
* **Mean Dice Loss**: `0.3820`

Excels at extracting both road and building structures due to its strong representation capacity.

---

### Stacked U-Net for Building Extraction

Uses a cascade of U-Net models where each stage refines the output of the previous one. Particularly useful in accurately delineating dense building clusters. It also has a single UNet implementation too.

### Single UNet
* **Mean IoU Score**: `0.6658`
* **Mean Dice Loss**: `0.6948`

### Stacked UNet
* **Mean IoU Score**: `0.4876`
* **Mean Dice Loss**: `-0.3937`

---

### U-Net with ECBA Attention — Best Performer

Combines U-Net with ECBA (Efficient Channel and Batch Attention) modules. These attention mechanisms allow the model to focus on the most informative spatial and channel features.

* **Mean IoU Score**: `0.7866`
* **Mean Dice Loss**: `0.4683`

Outperformed all other models in this repository on test data, offering a powerful balance between precision and generalization.

---

## Evaluation Metrics

All models are evaluated using:

* **Intersection over Union (IoU)**: Measures overlap between prediction and ground truth.
* **Dice Loss**: A loss function derived from the Dice coefficient (1 - Dice Score), emphasizing segmentation accuracy of foreground objects.

---

## Dataset

Each model is trained and tested on aerial imagery datasets containing ground-truth masks for buildings and roads. Details on preprocessing, splits, and dataset structures are available within each model directory.

---

## Getting Started

1. **Clone the repository:**

   ```bash
   git clone https://github.com/nathanmathewv/Aerial-Image-Segmentation-PE.git
   cd Aerial-Image-Segmentation-PE
   ```

2. **Navigate to a model directory:**

   ```bash
   cd Res2UNet
   ```

3. **Train/Evaluate** the model by following the instructions in the corresponding folder.
