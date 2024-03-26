## Project Description

This project is a sign language recognition system implemented using machine learning techniques. The system is designed to interpret and recognize hand gestures representing individual letters of the alphabet (A-Z) in American Sign Language (ASL).

### Key Features:

- **Real-time Gesture Recognition:** The system can recognize hand gestures captured in real-time through a webcam feed.
- **Multi-Gesture Support:** It supports recognition of multiple hand gestures corresponding to the letters A-Z.
- **Customizable Training:** Users can collect their own dataset of hand gestures and train the recognition model with their data.
- **MediaPipe Integration:** Utilizes MediaPipe, a popular framework for building cross-platform multimodal ML applications, for hand landmark detection.
- **Model Training and Evaluation:** The project provides scripts for training the recognition model and evaluating its performance on a given dataset.

### How It Works:

The system follows these general steps:

1. **Data Collection:** Users collect images of hand gestures for each letter of the alphabet using the provided `collectdata.py` script. These images are saved in the appropriate directory structure (`Images/A`, `Images/B`, ..., `Images/Z`).

2. **Dataset Generation:** The collected images are processed using the `data.py` script to extract keypoints using MediaPipe. These keypoints are then saved as numpy arrays (.npy files), creating a dataset for training the model.

3. **Model Training:** The `trainmodel.py` script is used to train the sign language recognition model using the generated dataset. The model architecture consists of LSTM layers for sequential data processing.

4. **Real-time Recognition:** Once trained, the model can be deployed to perform real-time recognition of hand gestures captured by a webcam. The system displays the recognized letters on the screen in response to detected gestures.

### Requirements:

- Python 3.x
- OpenCV
- NumPy
- TensorFlow
- Keras
- Mediapipe

### Usage:

Follow the instructions provided in the README to set up and run the project on your local machine.

1. Clone the project using git clone
2. install the requirements

   ```
   pip install -r requirements.txt
   ```

3. run the model
   ```
   python app.py
   ```

---

## How to Train the Model

## Collecting Data

To collect images for training, you can use the provided `collectdata.py` script. This script captures hand gestures from your webcam and saves them as images in the appropriate directory structure. Follow the steps below to collect data:

1. Ensure your webcam is connected and properly configured.
2. Run the `collectdata.py` script:

```

python collectdata.py

```

3. Perform hand gestures in front of your webcam and press the key in keyboard to capture it. Each gesture will be captured and saved in the corresponding directory (e.g., `Images/A`, `Images/B`, etc.).
4. For Capturing `A` sing perform `A` hand gesture and press `a` key on keyboard

5. Repeat the process for each gesture you want to include in your dataset.
6. For the current Model we are going with `no_sequences` as 15 and `sequence_length` as 15 ie 15 images for each gesture and 15 keypoints for each image

## Generating Dataset

Once you have collected the images for training, you can use the `data.py` script to generate a dataset from the collected images. This script reads the images, extracts keypoints using MediaPipe, and saves the keypoints as numpy arrays (.npy files) in the appropriate directory structure. Follow the steps below to generate the dataset:

it is very important to have correct proper ligiting if the hand is not recognised properly you will get `homogenous data` error in training

1. Ensure you have collected sufficient data for each gesture and organized it in the correct directory structure (as described in the Collecting Data section).

2. Run the `data.py` script:

```

python data.py

```

3. The script will process the collected images, extract keypoints, and save them as numpy arrays in the `Images` directory.

4. Once the dataset generation is complete, you can use the generated dataset to train your sign language recognition model.

## Training the Model

To train the sign language recognition model, follow these steps:

1. Ensure you have Generated Datasets and stored in `MP_Data` (as described in the generating Data Set section).

2. Run the `trainmodel.py` script to train the model:

```

python trainmodel.py

```

3. The script will load the dataset, preprocess the data, configure the model architecture, and start the training process.

4. During training, the model's performance metrics, such as loss and accuracy, will be displayed for each epoch. The training progress will be saved in the `Logs` directory.

5. Once the training is complete, the trained model will be saved as `model.json` and `model.h5` in the project directory. These files contain the model architecture and weights, respectively.

6. You can use the trained model for sign language recognition tasks by loading it in your application or script.

7. Feel free to adjust the hyperparameters, model architecture, or dataset size to optimize the performance of your model.

---
