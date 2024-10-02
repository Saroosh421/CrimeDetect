# Assault Detection System using Video Frames and CNN

This project is designed to detect assaults in video frames using a lightweight Convolutional Neural Network (CNN) model. The system extracts frames from video files, processes them, and classifies them as either "Assault" or "Normal." The results are aggregated for a complete video-level prediction. It also includes an alert system that logs the detection results and sends an email if an assault is detected.

## Table of Contents
1. [Project Overview](#project-overview)
2. [Features](#features)
3. [Requirements](#requirements)
4. [Installation](#installation)
5. [Usage](#usage)
6. [Model Architecture](#model-architecture)
7. [Data Processing](#data-processing)
8. [Results](#results)
9. [Alerts and Logging](#alerts-and-logging)

## Project Overview
The project uses the Raspberry Pi camera to record a video, extract frames, and apply a custom-trained CNN model to predict whether the video contains assault incidents. Predictions are made on each frame, and the final decision is based on the aggregate score. If an assault is detected, the system logs the event and sends an alert email with the relevant details.

## Features
- **Frame extraction** from videos using OpenCV.
- **Custom CNN model** built using PyTorch to classify frames.
- **Data augmentation** using various transformations.
- **Training and evaluation loop** to monitor model performance.
- **Logging and email alerts** for detected assault events.

## Requirements
The project requires the following Python libraries, which are specified in the `requirements.txt` file:
- `matplotlib`
- `numpy`
- `opencv-python`
- `Pillow`
- `torch`
- `torchvision`
- `requests`
- `scipy`
- `tensorboard`
- `pandas`
- `seaborn`

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/assault-detection-system.git
   cd assault-detection-system

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt

3. Set up the environment variables:
   ```bash
   export EMAIL_PASSWORD=yourpassword

## Usage
1. Recording and Extracting Frames
- `Record a video for 30 seconds using the Raspberry Pi camera`
- `Extract frames from the video`
2. Training the Model
- `Organize frames into Assault_Frames and Normal_Frames directories inside Train_Data` 
3. Predicting on New Videos
- `Extract frames from the video`
- `Run the inference script to classify the frames`
4. Email Alerts
- `Logs the detection details`
- `Sends an email alert with the log file attached`

## Model Architecture
The CNN model architecture used is lightweight and designed for frame classification. It has the following layers:

- `3 convolutional layers`
- `Max pooling layers`
- `Global average pooling layer`
- `Fully connected layer with a sigmoid activation function for binary classification`

## Data Processing
The system processes videos by extracting frames at a rate of 5 frames per second. Images are then preprocessed using the following transformations:

- `Resizing to (128x128)`
- `Random horizontal flipping`
- `Random rotation`
- `Normalization`

## Results
- `The system trains on the frame dataset and evaluates performance by tracking training and test accuracy, along with loss values`
- `Results are visualized using Matplotlib at the end of training, displaying accuracy and loss curves for both the training and testing phases`

## Alerts and Logging
When the model detects an assault event:

- `A log file is created with details about the video, prediction score, date, and time`
- `An email alert is sent with the log file attached to the predefined email addresses`
