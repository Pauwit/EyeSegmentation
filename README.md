# Papillae Detection
![Static Badge](https://img.shields.io/badge/Hugging_Face-UResNet__OpticDisk__V1-blue?style=plastic&logo=huggingface&logoColor=yellow&link=https%3A%2F%2Fhuggingface.co%2FDigitalHolography%2FUResNet_OpticDisk_V1%2Ftree%2Fmain)


This repository provides a complete pipeline for semantic segmentation of eye papillae from medical M0 images using a U-Res-Net convolutional neural network. The project includes scripts for dataset preparation, data augmentation, model training, and inference.

The core of this project is a U-Net-based architecture with residual blocks (U-Res-Net) implemented in PyTorch. The model is trained to generate binary masks that accurately outline the papillae region in grayscale eye images.

A pretrained model is available for download on the Hugging Face link above to run the inference locally.

## Repository Structure

```
├── create_dataset.ipynb  # Notebook for dataset preparation
├── detector.ipynb        # Notebook for running inference on an image
├── eye.ipynb             # Main notebook for U-Res-Net training and evaluation
├── unet.ipynb            # (Experimental) U-Net training on Carvana dataset
└── pngs.txt              # List of image paths for dataset creation
```

- **`eye.ipynb`**: The primary notebook for this project. It contains the code for defining the U-Res-Net, setting up the dataset and dataloaders, running the training and validation loops, and visualizing results.
- **`detector.ipynb`**: A streamlined notebook for detecting papillae in a single image using a pre-trained model.
- **`create_dataset.ipynb`**: Provides functions to extract frames from video files and organize them into a dataset suitable for training.
- **`states/`**: This directory should store the saved model weights (`.pth` files).

## Usage

### Prerequisites

You need a Python environment with the following libraries installed. A GPU with CUDA is highly recommended for training.

- `torch` & `torchvision`
- `opencv-python`
- `scikit-image`
- `numpy`
- `matplotlib`
- `Pillow (PIL)`
- `tqdm`

### 1. Dataset Preparation

1.  Place your training images in the `data/eye/train/` directory.
2.  Place the corresponding binary masks in the `data/eye/train_masks/` directory. Ensure that image and mask filenames match.

### 2. Training the Model

1.  Open the `eye.ipynb` notebook.
2.  Configure the training parameters in the first few cells, such as `DATASET_DIR`, `IMAGE_SIZE`, `LEARNING_RATE`, `BATCH_SIZE`, and `EPOCHS`.
3.  Execute all cells in the notebook to start the training process.
4.  The training loop will save the best model weights (based on validation Dice score) to the path specified by the `path` argument in the `train_uresnet` function (e.g., `models/eye.pth`).
5.  Training progress, including loss and Dice scores for both training and validation sets, will be plotted at the end.

### 3. Running Inference

1.  If you didn't train a model yourself, download it from the hugging face link above (e.g., in `"models/eye.pth"`)
2.  Open the `detector.ipynb` notebook.
3.  Set the `MODEL_PATH` variable to the location of your trained model file (e.g., `"models/eye.pth"`).
4.  Set the `IMAGE_PATH` variable to the path of the M0 image you want to process.
5.  (Optional) Set the `SAVE_PATH` variable to a file path if you wish to save the resulting mask as a PNG image. Set it to `None` to disable saving.
6.  Run all the cells in the notebook. A plot will be displayed showing the original image and the predicted mask side-by-side.

## Results

The U-Res-Net model is trained using a combined loss function (BCEWithLogitsLoss + Dice Loss) and achieves a high segmentation performance, with a **Dice coefficient of approximately 0.94** on the validation set.

The inference script (`detector.ipynb`) applies a post-processing step that isolates the largest connected object in the predicted mask. This effectively removes any small, spurious detections and produces a clean, single-region segmentation of the papilla, which is useful for subsequent analysis. The final output is a binary mask highlighting the detected papilla region.