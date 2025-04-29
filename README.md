# Sign Language Detection

A computer vision project that detects and classifies sign language gestures using OpenCV and MediaPipe.

## Overview

This project uses machine learning to recognize sign language gestures in real-time through a webcam. It captures hand landmarks using MediaPipe, processes them with a Random Forest classifier, and displays the predicted sign language gesture on screen.

## Features

- Real-time sign language detection through webcam
- Easy collection of custom training data
- Hand landmark detection using MediaPipe
- Classification using RandomForest algorithm
- Supports custom sign language gestures

## Requirements

- Python 3.6+
- OpenCV
- MediaPipe
- scikit-learn
- numpy
- matplotlib

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/sign-language-detection.git
   cd sign-language-detection
   ```

2. Create and activate a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   # On Windows
   venv\Scripts\activate
   # On macOS/Linux
   source venv/bin/activate
   ```

3. Install the required packages:
   ```bash
   pip install opencv-python mediapipe scikit-learn numpy matplotlib
   ```

## Project Structure

```
sign-language-detection/
├── collect_images.py       # Script to collect training images
├── create_dataset.py       # Process images and extract hand landmarks
├── train_classifier.py     # Train the RandomForest model
├── inference_classifier.py # Run real-time sign language detection
├── data/                   # Directory for storing training images
│   ├── 0/                  # Class 0 images (e.g., "I love you" sign)
│   ├── 1/                  # Class 1 images (e.g., "Thank you" sign)
│   └── 2/                  # Class 2 images (e.g., "No" sign)
├── data.pickle             # Processed landmark data
├── model.p                 # Trained model
└── README.md               # Project documentation
```

## Usage

### 1. Collect Training Images

First, collect images for each sign language gesture you want to detect:

```bash
python collect_images.py
```

By default, this will:
- Create a `data` directory if it doesn't exist
- Collect 100 images for each of 3 classes
- Open your webcam and start capturing when you press 'q'

You can modify `number_of_classes` and `dataset_size` in the script to adjust these parameters.

### 2. Create Dataset from Images

Process the collected images to extract hand landmarks:

```bash
python create_dataset.py
```

This will:
- Process all images in the `data` directory
- Extract hand landmarks using MediaPipe
- Save the processed data to `data.pickle`

### 3. Train the Classifier

Train the RandomForest model on the extracted hand landmarks:

```bash
python train_classifier.py
```

The script will:
- Load data from `data.pickle`
- Split data into training and testing sets
- Train a RandomForest classifier
- Display the accuracy score
- Save the trained model to `model.p`

### 4. Run Real-time Detection

Finally, run the inference script to detect sign language gestures in real-time:

```bash
python inference_classifier.py
```

This will:
- Open your webcam
- Detect hand landmarks using MediaPipe
- Classify the detected gesture using the trained model
- Display the prediction on screen

To exit the application, press 'q' or close the window.

## Customizing the Project

### Adding More Gestures

1. Modify the `number_of_classes` in `collect_images.py`
2. Run the collection process for each new class
3. Update the `labels_dict` in `inference_classifier.py` to include your new gestures:

```python
labels_dict = {0: 'i_love_you', 1: 'Thank_you', 2: 'No', 3: 'Your_New_Gesture'}
```

### Improving Model Accuracy

- Collect more training data for each class
- Ensure consistent lighting and background when collecting images
- Experiment with different machine learning models in `train_classifier.py`
- Adjust the `min_detection_confidence` parameter in MediaPipe setup

## Troubleshooting

- **No webcam detected**: Ensure your webcam is properly connected and not being used by another application
- **Poor detection accuracy**: Try collecting more training data in different positions and lighting conditions
- **MediaPipe not detecting hands**: Adjust the `min_detection_confidence` parameter to a lower value

## Acknowledgments

- [MediaPipe](https://mediapipe.dev/) for hand landmark detection
- [OpenCV](https://opencv.org/) for image processing
- [scikit-learn](https://scikit-learn.org/) for machine learning algorithms
