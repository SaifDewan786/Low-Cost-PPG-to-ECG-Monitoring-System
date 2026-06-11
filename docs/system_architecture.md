# System Architecture

## Overview

The system is designed as an end-to-end pipeline for reconstructing ECG-like waveforms from PPG signals.

At a high level, the system contains five major parts:

1. PPG acquisition
2. Signal preprocessing
3. Multichannel input construction
4. TCN-based ECG-like waveform reconstruction
5. Visualization and warning-oriented interpretation

## High-Level Pipeline

```text
Low-cost PPG sensor
        ↓
ESP32-based acquisition device
        ↓
Continuous PPG signal recording
        ↓
Signal cleaning and normalization
        ↓
PPG + dPPG + ddPPG input construction
        ↓
TCN encoder-decoder reconstruction model
        ↓
ECG-like waveform output
        ↓
Postprocessing, BPM comparison, and visualization
        ↓
Web-based demonstration interface
```

## Mermaid Diagram

```mermaid
flowchart LR
    A[MAX30102 PPG Sensor] --> B[ESP32 Microcontroller]
    B --> C[Continuous PPG Acquisition]
    C --> D[Signal Cleaning and Normalization]
    D --> E[PPG + dPPG + ddPPG Input]
    E --> F[TCN Encoder-Decoder Model]
    F --> G[ECG-Like Waveform Reconstruction]
    G --> H[Postprocessing and BPM Comparison]
    H --> I[Web-Based Visualization Interface]
```

## Benchmark Branch

The benchmark branch uses paired PPG-ECG datasets for supervised training and evaluation.

Benchmark data is used for:

* Training the reconstruction model
* Validating the reconstruction model
* Testing waveform similarity
* Calculating reconstruction metrics
* Comparing reconstructed ECG with reference ECG

The project considered datasets such as:

* VitalDB
* PulseDB
* BIDMC

These datasets provide paired ECG and PPG signals and are useful for supervised reconstruction experiments.

## Custom Wearable Branch

The custom branch uses low-cost PPG recordings collected using the prototype device.

The custom branch is used for:

* Practical transfer testing
* Rhythm behavior observation
* BPM comparison
* Signal plausibility checking
* Wearable-device feasibility analysis

The custom branch does not currently include paired ECG ground truth. Therefore, it cannot be used for full morphology-level validation yet.

## Signal Flow

### 1. Acquisition

The wearable prototype collects PPG using a MAX30102 optical sensor and an ESP32 microcontroller.

### 2. Signal Preparation

The raw PPG signal is converted into structured numerical form and prepared for model input.

### 3. Preprocessing

The signal is normalized, clipped, mildly smoothed, and aligned to the expected model-ready sampling format.

### 4. Feature Construction

The model input is constructed using three signal channels:

* Original PPG
* First derivative PPG
* Second derivative PPG

### 5. Reconstruction

A TCN encoder-decoder model maps the multichannel PPG representation into a single-channel ECG-like waveform.

### 6. Postprocessing

The reconstructed signal is lightly postprocessed for visualization and rhythm-level comparison.

### 7. Interface

A web-based interface allows signal upload, reconstruction, waveform display, BPM comparison, warning-oriented interpretation, and output export.

## Design Philosophy

The architecture was designed to be:

* Low-cost
* Wearable-friendly
* Research-oriented
* Modular
* Explainable at system level
* Safe for demonstration
* Extendable for future paired-device validation

## Public Repository Boundary

This public repository only documents the architecture.

It does not include:

* Source code
* Firmware
* Model weights
* Dataset files
* Raw biosignal recordings
* Proprietary preprocessing logic
* Exact implementation parameters beyond high-level documentation
