# video_classification
This project implements a video classification pipeline from scratch using a combination of Convolutional Neural Networks (CNNs) for spatial feature extraction and LSTMs for temporal sequence modeling. The goal is to detect and classify activities (binary theft/no-theft in this case) from raw video input.

## Features
Extract frames efficiently from .mp4 videos with padding & normalization.

Custom FrameGenerator for streaming frame sequences + labels.

Robust train/val/test split that ensures no data leakage across subsets.

End-to-end CNN + LSTM pipeline for spatiotemporal learning.

Modular code with custom residual layers for experimentation.

Deployed as a Django web app for real-world usage.

## Dataset Preparation
Videos are first organized by class (e.g., theft/ and no_theft/).
We implemented a safe manual split to avoid data leakage:

def prepare_split(source_dir, split_dir, splits=(0.7, 0.2, 0.1)):
    # Creates train/val/test splits by copying videos into new dirs


Ensures same video never appears in multiple splits.

Uses stratified shuffling within each class.

Results in:

dataset_split/
├── train/
│   ├── theft/
│   └── no_theft/
├── val/
│   ├── theft/
│   └── no_theft/
└── test/
    ├── theft/
    └── no_theft/

## Model Architecture
TimeDistributed CNN layers handle each frame individually.

LSTM layer captures sequential motion patterns.

Dropout helps prevent overfitting.

Binary classification with sigmoid activation.

## Deployment with Django
