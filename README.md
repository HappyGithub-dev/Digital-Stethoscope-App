# EchoChest: Dual-Modality Digital Stethoscope

## Overview
EchoChest is a clinical research framework designed to evaluate the efficacy of native smartphone sensors for non-invasive cardiac monitoring, comparing acoustic and kinetic modalities.

## Data Acquisition
*   **iOS Application:** A custom Swift application engineered for synchronous, dual-modality sensor recording.
*   **Acoustic Sensing:** Phonocardiogram (PCG) data captured via the internal microphone.
*   **Kinetic Sensing:** Seismocardiogram (SCG) data captured via the internal accelerometer.
*   **Clinical Cohort:** 40 human subjects recorded in a resting state, accompanied by clinical pulse meter ground truth data.

## Processing Pipeline
*   **Filtering:** Applied Second-Order Sections (SOS) Butterworth bandpass filters (20–150 Hz for PCG; 1–20 Hz for SCG).
*   **Mathematical Stability:** Downsampled high-resolution acoustic files to 2 kHz to prevent numerical underflow during extraction.
*   **Feature Extraction:** Utilized Hilbert transforms and dynamic peak-detection to compute Heart Rate (BPM) and Signal-to-Noise Ratio (SNR).
*   **Machine Learning:** Deployed a Random Forest Regressor to map the extracted DSP features to the clinical ground truth.

## Clinical Results
*   **Kinetic Supremacy:** The SCG modality demonstrated high clinical reliability with a Bland-Altman mean bias of just 1.41 BPM.
*   **Acoustic Limitations:** The PCG modality exhibited a 40.72 BPM mean bias, struggling heavily with ambient noise interference.
*   **Model Accuracy:** The Random Forest ensemble model achieved an R² score of 0.872.
*   **Feature Importance:** The ML algorithm assigned the highest predictive weight (51.4%) to the SCG heart rate, confirming the accelerometer as the optimal monitoring sensor.
