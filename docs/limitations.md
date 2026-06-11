# Limitations

## Overview

This project is a research prototype for ECG-like waveform reconstruction from PPG. It is not a medical device and is not intended for diagnosis.

The limitations are important because ECG reconstruction from PPG is a difficult physiological and machine learning problem. Public benchmark success does not guarantee reliable performance on low-cost wearable signals.

## 1. Not a Clinical System

The reconstructed ECG-like waveform should not be interpreted as a clinical ECG.

The system is not intended for:

* Diagnosis
* Emergency detection
* Medical decision-making
* ECG replacement
* Patient monitoring in clinical settings
* Regulatory medical-device use

The output is experimental and should be treated as research-only.

## 2. ECG and PPG Are Not Perfectly Aligned

ECG measures the electrical activity of the heart.

PPG measures the peripheral blood-volume response after cardiac contraction.

Because of this, PPG appears after a physiological delay. This delay is related to pulse arrival time and can vary across people and conditions.

Therefore, PPG-to-ECG reconstruction is not a simple one-to-one waveform translation problem.

## 3. Pulse Arrival Time Variation

Pulse arrival time can vary due to:

* Subject physiology
* Blood pressure
* Vascular condition
* Measurement site
* Sensor placement
* Signal quality
* Motion
* Physiological state

This makes temporal alignment between ECG and PPG challenging.

## 4. Benchmark-to-Device Domain Mismatch

Benchmark datasets are usually cleaner and more controlled than low-cost wearable recordings.

Custom-device PPG can contain:

* Motion artifact
* Baseline drift
* Pressure variation
* Finger placement variation
* Sampling irregularity
* Sensor-specific noise
* Ambient light disturbance

This domain mismatch can reduce reconstruction reliability.

## 5. No Paired Custom ECG Ground Truth Yet

The custom-device branch currently uses PPG-only recordings.

Because simultaneous custom ECG was not available in the current stage, full morphology-level validation on real-device data is not possible yet.

The custom-device evaluation can support rhythm-level feasibility, but not clinical waveform validation.

## 6. Morphology Reliability Is Limited on Custom Device Data

The reconstructed waveform may preserve broad rhythm behavior, but detailed morphology may be less reliable when the input comes from low-cost custom PPG.

This means the model may generate plausible ECG-like shapes without guaranteeing true ECG morphology.

## 7. Dataset Split Limitation

Benchmark experiments may be affected by split strategy.

Index-based splits can be more optimistic than strict subject-wise splits. Future work should use subject-wise or patient-wise splitting whenever possible.

## 8. Limited Subject Diversity in Custom Testing

The custom-device testing stage needs more participants and recording sessions before stronger claims can be made.

Future validation should include:

* More subjects
* Different ages
* Different resting states
* Motion conditions
* Different finger placements
* Multiple recording environments
* Paired reference ECG

## 9. Hardware Prototype Limitations

The hardware is a low-cost research prototype.

Possible limitations include:

* Sensor instability
* Inconsistent finger pressure
* Motion sensitivity
* Noise from ambient light
* Prototype wiring limitations
* Lack of medical-grade calibration
* Limited physical robustness

## 10. Web Interface Is Demonstration-Oriented

The web interface supports visualization and warning-oriented interpretation, but it is not a certified clinical interface.

It should be treated as a research demonstration tool.

## 11. IP and Confidentiality Limitations

Because this project may be used for startup purposes, some information is intentionally withheld.

Not included publicly:

* Source code
* Firmware
* Model weights
* Dataset files
* Raw biosignal recordings
* Exact preprocessing implementation
* Exact training pipeline
* Circuit-level confidential details

## Summary

The project demonstrates a promising direction for low-cost PPG-based ECG-like waveform reconstruction, but it remains a research prototype. Stronger validation requires paired custom PPG-ECG data, subject-wise evaluation, device-specific fine-tuning, and real-world clinical testing.

