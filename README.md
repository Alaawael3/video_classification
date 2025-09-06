# video_classification
This project implements a video classification pipeline from scratch using a combination of Convolutional Neural Networks (CNNs) for spatial feature extraction and LSTMs for temporal sequence modeling. The goal is to detect and classify activities (binary theft/no-theft in this case) from raw video input.

## Features
- Extract frames efficiently from .mp4 videos with padding & normalization.

- Custom FrameGenerator for streaming frame sequences + labels.

- Robust train/val/test split that ensures no data leakage across subsets.

- End-to-end CNN + LSTM pipeline for spatiotemporal learning.

- Modular code with custom residual layers for experimentation.

- Deployed as a Django web app for real-world usage.

## Dataset Preparation
Videos are first organized by class (theft/ and no_theft/).
I implemented a safe manual split to avoid data leakage:

### Techniques to Prevent Data Leakage

- Strict split by video file: same video never appears in multiple subsets.

- Shuffling applied only to training to preserve evaluation integrity.

- Frame padding ensures temporal consistency without introducing bias.

- Resizing with padding avoids distorting motion patterns.

## Model Architecture

- TimeDistributed CNN layers handle each frame individually.

- LSTM layer captures sequential motion patterns.

- Dropout helps prevent overfitting.

- Binary classification with sigmoid activation.

## Deployment with Django
### Prediction Results
<p align="center">
  <img src="https://github.com/Alaawael3/video_classification/blob/7488a008e578bf7d1eab27765c7469b168419f5f/shop_lifter_prediction.jpg?raw=true" alt="Prediction Result" width="700"/>
</p>

<p align="center">
  <img src="https://github.com/Alaawael3/video_classification/blob/1995e4cca7e011b69f47915fbcbf472efc71ffd5/non_shop_lifting.jpg?raw=true" alt="Prediction Result" width="700"/>
</p>
