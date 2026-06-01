# Why I Built This

During my internship at AIIMS, I spent some time observing work in the Cardiology Department. That experience made me curious about how much information is hidden inside ECG signals and how signal processing techniques can help expose patterns that may not be obvious in the raw waveform.

When I started exploring public ECG datasets, I noticed that many projects directly trained deep learning models on ECG values or pre-generated images. I wanted to understand the transformation itself.

Instead of treating the ECG as a machine learning problem from the beginning, I approached it as a signal processing problem first.

I began with raw heartbeat segments from the MIT-BIH Arrhythmia Dataset, applied bandpass filtering to reduce unwanted frequency components, and then used Continuous Wavelet Transform (CWT) to convert the signal into a time-frequency representation. These scalograms were then used to fine-tune a ResNet50 model for heartbeat classification.

The most interesting part of the project was seeing how a sequence of 187 ECG values could be transformed into a visual representation where different heartbeat patterns became much easier to distinguish.

To better understand what the model was learning, I also implemented Grad-CAM visualizations to highlight the regions of the scalogram that contributed most strongly to the final prediction.

This project helped me connect concepts from signal processing, biomedical data analysis, computer vision, and explainable AI into a single workflow.
