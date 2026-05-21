# Real-Time ASL Fingerspelling Recognition

The program is a real-time American Sign Language (ASL) recognition system focused on fingerspelling (spelling words letter by letter with hand shapes) and converting it to written text.


# 🚀 Features

**Real-Time Hand Detection:** Uses MediaPipe Hands (from Google) to detect 21 hand landmarks accurately and quickly in live video.
* **High Accuracy:** Trained for about 10-15 minutes on a GPU in Google Colab, achieving up to 99% accuracy on test data.
**Smart Word Building:** Uses a "majority voting" system over the last 8 frames to avoid random false predictions. If confidence is high (>90%) and prediction is stable, adds the letter to the current word.
**Dynamic Spacing & Clearing:** Short pause (no hand for 2-3 seconds) adds a space, while a long pause (>5 seconds) clears the word.
**User Interface:** Built using Gradio to provide a simple web interface that runs directly from Google Colab with a public shareable link.


# 🧠 Technical Implementation

**Dataset:** The model was trained on the popular Sign Language MNIST dataset, containing over 27,000 images of hands forming ASL letters from A to Y (J and Z are excluded as they require motion).
**Model Architecture:** A Convolutional Neural Network (CNN) was built using TensorFlow/Keras. It consists of feature extraction layers (Conv2D + MaxPooling) and classification layers (Dense).
**Frame Processing Pipeline:**
  1. MediaPipe detects the hand and draws landmarks.
  2. Crops only the hand region.
  3. Converts it to grayscale, resizes to 28×28 pixels (same as training data).
  4. Feeds it into the CNN model to predict the letter with confidence score.

**Result:** A complete AI system that converts finger-spelled signs into written text in real-time with high accuracy!
