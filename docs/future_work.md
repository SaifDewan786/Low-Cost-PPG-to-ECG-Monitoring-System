# Future Work

## Overview

The current system demonstrates a promising research framework for reconstructing ECG-like waveforms from PPG using a low-cost wearable prototype and a TCN-based deep learning model.

The next stage should focus on improving validation, device-specific performance, robustness, and real-world usability.

## 1. Collect Paired Custom PPG-ECG Data

The most important future step is to collect simultaneous custom PPG and ECG recordings.

This would allow the reconstructed ECG-like output to be compared directly against real ECG from the same person and same time window.

Future paired data should include:

* Custom PPG from the low-cost device
* Simultaneous ECG reference
* Resting recordings
* Faster-heartbeat recordings
* Motion-sensitive recordings
* Multiple subjects
* Multiple sessions per subject
* Different sensor placements

## 2. Device-Specific Fine-Tuning

The current reconstruction model is trained primarily using benchmark data.

Future work should fine-tune the model using paired custom PPG-ECG recordings from the actual device.

This can help reduce domain mismatch caused by:

* MAX30102 sensor characteristics
* ESP32 acquisition behavior
* Finger placement variation
* Low-cost sensor noise
* Sampling differences
* Real-world signal artifacts

## 3. Subject-Wise Evaluation

Future experiments should use subject-wise or patient-wise splits.

This is important because random or index-based splits may overestimate model performance if similar samples from the same subject appear in both training and test sets.

Recommended split strategy:

```text
Training subjects ≠ Validation subjects ≠ Test subjects
```

## 4. Larger and More Diverse Dataset

Future custom data collection should include:

* More participants
* Different age groups
* Different physiological states
* Multiple recording durations
* Different room lighting conditions
* Controlled and uncontrolled posture
* Motion artifact conditions
* Different sensor pressure levels
* Different skin tones and peripheral perfusion conditions

A larger dataset will make the model more reliable and generalizable.

## 5. Improved Hardware Design

The low-cost prototype can be improved by adding:

* Better sensor enclosure
* Stable finger placement support
* Better ambient light shielding
* Improved cable management
* Battery support
* Wireless data transfer
* Real-time streaming
* Better sampling-rate control
* More reliable signal-quality indicators

## 6. Signal Quality Index

A signal quality index should be added before reconstruction.

The system should detect whether the input PPG is good enough for reconstruction.

Possible quality indicators:

* Signal amplitude stability
* Baseline drift level
* Peak regularity
* Noise level
* Motion artifact estimate
* Saturation detection
* Missing sample detection

If the signal quality is poor, the system should warn the user instead of generating misleading output.

## 7. Better Postprocessing

Future postprocessing improvements may include:

* Baseline correction
* Peak smoothing
* Adaptive filtering
* Rhythm consistency checking
* Outlier removal
* Segment-level confidence scoring
* Beat-level quality estimation

Postprocessing should improve visualization without hiding model failure.

## 8. Improved Model Variants

Future model experiments may include:

* Larger TCN models
* Lightweight TCN models
* TCN with attention
* U-Net-style 1D convolutional models
* Transformer-based reconstruction models
* Diffusion-based waveform generation
* Hybrid TCN-transformer architecture
* Uncertainty-aware reconstruction

The goal should not only be lower error, but also better morphology reliability and practical robustness.

## 9. Real-Time Reconstruction

The current system should be extended toward real-time or near-real-time processing.

Important deployment questions:

* Can the model process continuous PPG windows fast enough?
* What is the inference latency?
* Can the model run on a laptop, phone, or edge board?
* Can the system update ECG-like output continuously?
* Can poor-quality input be rejected automatically?

## 10. Mobile or Web Dashboard Improvement

The demonstration interface can be improved with:

* Better waveform visualization
* Live signal streaming
* BPM trend chart
* Reconstruction confidence display
* Signal-quality warnings
* Exportable PDF report
* User session history
* Clear medical disclaimer
* Better UI for non-technical users

## 11. Clinical and Ethical Validation

Before any medical use, the system would require:

* Clinical-grade paired validation
* Institutional approval where necessary
* Larger participant studies
* Comparison with medical ECG devices
* Bias and subgroup analysis
* Safety analysis
* Regulatory review
* Strong privacy protection

## 12. Startup-Oriented Product Direction

If developed as a startup product, the project should move carefully through:

1. Research prototype
2. Lab validation
3. Paired custom data collection
4. Improved hardware prototype
5. Device-specific model training
6. Safety-focused testing
7. Medical advisor review
8. Regulatory planning
9. User-facing pilot
10. Clinical validation

## Summary

The most important next step is paired custom PPG-ECG data collection. Without paired custom ECG ground truth, the system can show rhythm-level feasibility but cannot prove morphology-level ECG reconstruction accuracy.

The long-term goal is to develop a robust, low-cost, wearable-friendly cardiac monitoring research platform that can reconstruct ECG-like waveforms from PPG while remaining transparent about limitations, uncertainty, and safety.

