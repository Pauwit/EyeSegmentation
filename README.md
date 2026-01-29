# Eye Segmentation & Classification

[![button](https://img.shields.io/badge/Hugging_Face-YOLO__EyeDiaphragm-blue?style=plastic&logo=huggingface&logoColor=yellow)](https://huggingface.co/DigitalHolography/YOLO_EyeDiaphragm)
[![button](https://img.shields.io/badge/Hugging_Face-YOLO__EyeSide-teal?style=plastic&logo=huggingface&logoColor=yellow)](https://huggingface.co/DigitalHolography/YOLO_EyeSide)
[![button](https://img.shields.io/badge/Hugging_Face-YOLO__OpticDisk-blue?style=plastic&logo=huggingface&logoColor=yellow)](https://huggingface.co/DigitalHolography/YOLO_OpticDisk)
[![button](https://img.shields.io/badge/Hugging_Face-UResNet__OpticDisk-darkred?style=plastic&logo=huggingface&logoColor=yellow)](https://huggingface.co/DigitalHolography/UResNet_OpticDisk)

> Part of the [Digital Holography Project](https://github.com/DigitalHolography)

## Description

This repository provides a complete pipeline for semantic segmentation/classification of optic disks, eye diaphragms and eye side from medical **M0** images generated from the [HoloDoppler application](https://github.com/DigitalHolography/HoloDoppler).

This project heavily uses the Ultralytics' YOLO library. Their links can be found in the yolo.ipynb notebook.

Pretrained models are available for download on the Hugging Face links above to run the prediction locally.

## Repository Structure

```
├── dataset.ipynb      # (EXPERIMENTAL) Notebook for dataset creation/preparation and manipulation
├── detector.ipynb     # (DEPRECATED) Notebook for running predictions on U-ResNet models
├── eye.ipynb          # Notebook for eye diaphragm prediction and vizualisation
├── eye_side.ipynb     # Notebook for eye side prediction and vizualisation
├── optic_disk.ipynb   # Notebook for optic disk prediction and vizualisation
├── pngs.txt           # (INFORAMTION) List of image paths used for dataset creation
├── unet.ipynb         # (DEPRECATED) Self made U-Net training with PyTorch
├── uresnet.ipynb      # (DEPRECATED) Self made U-ResNet training with PyTorch
└── yolo.ipynb         # Notebook for Ultralytics' YOLO information and training
```

The important notebooks for predictions :
- **`eye.ipynb`**: Eye diaphragm segmentation
- **`eye_side.ipynb`**: Eye side classification
- **`optic_disk.ipynb`**: Optic disk segmentation
