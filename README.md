# Eye Segmentation & Classification
<a href="https://huggingface.co/DigitalHolography/YOLO_EyeDiaphragm" target="_blank" style="text-underline: none">
    <img src="https://img.shields.io/badge/Hugging_Face-YOLO__EyeDiaphragm-blue?style=plastic&logo=huggingface&logoColor=yellow" alt="Hugging Face link">
</a>
<a href="https://huggingface.co/DigitalHolography/YOLO_EyeSide" target="_blank" style="text-underline: none">
    <img src="https://img.shields.io/badge/Hugging_Face-YOLO__EyeSide-teal?style=plastic&logo=huggingface&logoColor=yellow" alt="Hugging Face link">
</a>
<a href="https://huggingface.co/DigitalHolography/YOLO_OpticDisk" target="_blank" style="text-underline: none">
    <img src="https://img.shields.io/badge/Hugging_Face-YOLO__OpticDisk-blue?style=plastic&logo=huggingface&logoColor=yellow" alt="Hugging Face link">
</a>
<a href="https://huggingface.co/DigitalHolography/UResNet_OpticDisk" target="_blank" style="text-underline: none">
    <img src="https://img.shields.io/badge/Hugging_Face-UResNet__OpticDisk-darkred?style=plastic&logo=huggingface&logoColor=yellow" alt="Hugging Face link">
</a>

> Part of the [HoloVibes Project](https://github.com/DigitalHolography/Holovibes)

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
├── unet.ipynb         # (DEPRECATED) Self made U-Net training with PyTorch
├── uresnet.ipynb      # (DEPRECATED) Self made U-ResNet training with PyTorch
├── pngs.txt           # (INFORAMTION) List of image paths used for dataset creation
└── yolo.ipynb         # Notebook for Ultralytics' YOLO information and training
```

The important notebooks for predictions :
- **`eye.ipynb`**: Eye diaphragm segmentation
- **`eye_side.ipynb`**: Eye side classification
- **`optic_disk.ipynb`**: Optic disk segmentation
