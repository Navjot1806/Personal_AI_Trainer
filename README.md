# Digital Personal Trainer

## Description

Your Digital Personal Trainer is an advanced fitness application designed to track your body movements throughout a workout, helping you correct your posture, keep track of your reps, and ensure you get fit the right way. Utilizing the Pose Detection API from Google's AI framework, MediaPipe, this app performs keypoint detection, pose classification, and pose correction to provide real-time feedback during your workouts.

## Features

1. **Keypoint Detection**
   - Utilizes a pre-trained MediaPipe landmark model, a Convolutional Neural Network, to detect 33 keypoints from a video feed.
   - Processes input from a webcam with an image size of [1,256,256,3] and outputs coordinates and visibility factors for each keypoint.

2. **Pose Classification**
   - Employs 18 of the detected keypoints to classify the workout being performed.
   - Uses the MMFit dataset to train the classifier on various exercises.

3. **Pose Correction**
   - Identifies incorrect postures by calculating angles between limbs and comparing them against benchmarks.
   - Counts the number of reps performed correctly for each workout.

## Implementation

### Dataset

- Utilizes the MMFit dataset, which includes inertial sensor data and synchronized multi-viewpoint RGB-D video with 2D and 3D pose estimates.
- The data is divided into training, testing, and validation sets, with 375,753 frames retained after filtering out noise.

### Input Normalization

- Normalizes keypoints around the center of gravity to account for variables like distance from the camera, height, and camera angle.

### Model Architecture

- **Input Shape:** (36,) representing the X and Y coordinates of 18 keypoints.
- **Output:** Probability of the input falling under one of 10 exercise classes.
- **Sequential Model:** Consists of 2 hidden layers and a dropout of 0.5 to prevent overfitting.
- **Loss Function:** sparse_categorical_crossentropy with a learning rate of 0.01.
- **Training:** Achieved a final validation accuracy of 96% over 20 epochs.

## Getting Started

1. **Clone the Repository:**
   ```sh
   git clone https://github.com/Meet19aug/digital-personal-trainer.git
   cd digital-personal-trainer
   ```

2. **Install Dependencies:**
   ```sh
   npm install
   ```

3. **Run the Application:**
   ```sh
   npm start
   ```

## Usage

- Ensure your webcam is enabled and positioned to capture your full body.
- Start the application and follow the on-screen instructions for various workouts.
- Receive real-time feedback on your posture and rep count.

## Contributing

We welcome contributions to enhance the functionality and features of this application. Please follow the standard [contribution guidelines](CONTRIBUTING.md).
