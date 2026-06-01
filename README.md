# Why I Built This

During my internship at AIIMS, I spent some time observing work in the Cardiology Department. That experience made me curious about how much information is hidden inside ECG signals and how signal processing techniques can help expose patterns that may not be obvious in the raw waveform.

When I started exploring public ECG datasets, I noticed that many projects directly trained deep learning models on ECG values or pre-generated images. I wanted to understand the transformation itself.

Instead of treating the ECG as a machine learning problem from the beginning, I approached it as a signal processing problem first.

I began with raw heartbeat segments from the MIT-BIH Arrhythmia Dataset, applied bandpass filtering to reduce unwanted frequency components, and then used Continuous Wavelet Transform (CWT) to convert the signal into a time-frequency representation. These scalograms were then used to fine-tune a ResNet50 model for heartbeat classification.

The most interesting part of the project was seeing how a sequence of 187 ECG values could be transformed into a visual representation where different heartbeat patterns became much easier to distinguish.

To better understand what the model was learning, I also implemented Grad-CAM visualizations to highlight the regions of the scalogram that contributed most strongly to the final prediction.

This project helped me connect concepts from signal processing, biomedical data analysis, computer vision, and explainable AI into a single workflow.

## Dataset

The MIT-BIH Arrhythmia Dataset represents each heartbeat as 187 sampled ECG values followed by a class label.

<img src="./187%20values.png" width="800">

---

## Understanding the Signal

Before training any model, I explored how different heartbeat classes vary in morphology.

<img src="./ECG%20across%20class.png" width="800">

---

## Signal Preprocessing

Raw ECG signals often contain baseline drift and unwanted frequency components. To improve signal quality before feature extraction, a Butterworth bandpass filter was applied.
<img src="./ecg%20signal.png" width="800">

---

## Wavelet Exploration

I experimented with different wavelet families before selecting the final approach for scalogram generation.

<img src="./sym4%20wavelet.png" width="800">

---

## Continuous Wavelet Transform (CWT)

Instead of treating ECG as only a time-domain signal, Continuous Wavelet Transform was used to capture both temporal and frequency information.

<img src="./CWT%20Scalogram.png" width="800">

---

## Scalogram Generation

The generated wavelet coefficients were converted into RGB images so that transfer learning models could be applied.
<img src="./Scalogram%20to%20RGB.png" width="600">

---

## Model Training

A pretrained ResNet50 architecture was fine-tuned on the generated scalogram images. <br> <br>
<img src="./Training%20Loss.png" width="800">

Final Validation Accuracy: 90.17%

---

## Explainability

To better understand model predictions, Grad-CAM was used to visualize the regions that contributed most strongly to the final classification.

<img src="./XAI%20rep.png" width="800">

