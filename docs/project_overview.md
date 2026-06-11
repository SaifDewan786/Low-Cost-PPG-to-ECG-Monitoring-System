# Project Overview

## Project Title

Low-Cost PPG-to-ECG Reconstruction System Using a Temporal Convolutional Network

## Summary

This project is an ongoing proprietary research and development effort focused on reconstructing ECG-like waveforms from PPG signals using a low-cost wearable sensing system and a deep learning reconstruction model.

The system continuously records photoplethysmography (PPG) signals using a low-cost optical sensor-based device. The acquired PPG signal is then processed and passed through a Temporal Convolutional Network encoder-decoder model to generate an ECG-like waveform.

This repository is a documentation-only public portfolio version of the project. Source code, firmware, trained model weights, datasets, circuit-level implementation details, and proprietary training procedures are intentionally excluded due to intellectual property and startup confidentiality considerations.

## Problem Motivation

Electrocardiogram (ECG) is one of the most informative physiological signals for cardiac assessment. However, continuous ECG monitoring is not always practical for everyday use because it generally requires electrodes, controlled placement, dedicated hardware, and clinical-style acquisition conditions.

Photoplethysmography (PPG), on the other hand, is easier to collect using low-cost optical sensors. PPG is already common in smartwatches, fitness bands, pulse oximeters, and wearable health devices. However, PPG does not directly contain the same electrical information as ECG.

This project explores whether a deep learning model can learn the hidden relationship between PPG and ECG and reconstruct an ECG-like waveform from PPG input.

## Core Research Question

Can a low-cost wearable PPG device, combined with a deep learning reconstruction model, generate an ECG-like waveform that preserves useful rhythm information and supports accessible cardiac monitoring research?

## Project Scope

The project includes:

* Low-cost PPG acquisition using a wearable-style prototype
* Benchmark paired PPG-ECG dataset usage
* Signal preprocessing and normalization
* Multichannel PPG representation using:

  * PPG
  * First derivative PPG
  * Second derivative PPG
* Temporal Convolutional Network encoder-decoder reconstruction
* ECG-like waveform generation
* Benchmark reconstruction evaluation
* Custom-device transfer testing
* BPM comparison
* Warning-oriented interpretation
* Web-based visualization interface

## Current Project Status

This project is ongoing.

Completed work includes:

* Literature review on PPG-to-ECG reconstruction
* Benchmark dataset preparation
* TCN-based reconstruction model design
* Multichannel signal input strategy
* Low-cost MAX30102 and ESP32-based prototype development
* Custom PPG recording workflow
* Benchmark reconstruction experiments
* Custom-device transfer observation
* Web-based demonstration interface
* Documentation and result analysis

Ongoing or future work includes:

* Paired custom PPG-ECG data collection
* Device-specific fine-tuning
* Larger subject-level validation
* Improved wearable acquisition stability
* Clinical-grade evaluation design
* Real-time embedded deployment testing

## Important Disclaimer

This project is a research prototype.

It is not intended for:

* Medical diagnosis
* Clinical decision-making
* Emergency cardiac monitoring
* Replacement of directly measured ECG
* Regulatory or medical-device use

The generated ECG-like waveform should be treated as an experimental reconstruction output, not as a clinically validated ECG signal.

## Why This Project Matters

This work is important because it explores a more accessible direction for physiological monitoring. If PPG-based ECG-like reconstruction can be improved and validated, low-cost wearable devices may become more useful for rhythm awareness, early warning, and health-monitoring research.

The project is also significant because it does not stop at benchmark data. It also tests the transfer behavior of the reconstruction pipeline on custom PPG recordings from a low-cost wearable prototype. This helps expose the real gap between clean benchmark datasets and practical wearable signals.

## My Contribution Summary

Public-safe contribution areas include:

* Research pipeline development
* System-level documentation
* PPG-to-ECG reconstruction workflow design
* Low-cost hardware prototype involvement
* Signal preprocessing planning
* TCN model pipeline understanding and experimentation
* Evaluation strategy design
* Custom-device testing workflow
* Interface-level demonstration planning
* Result interpretation and limitation analysis

## What Is Withheld

The following are intentionally not included in this public repository:

* Source code
* Training notebooks
* Firmware
* Trained model weights
* Raw PPG or ECG signals
* Participant recordings
* Dataset files
* Circuit-level confidential details
* Full proprietary preprocessing implementation
* Exact model implementation
* Startup-related technical assets

This repository is meant to show the project concept, system architecture, methodology, and technical contribution without exposing intellectual property.
