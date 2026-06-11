# Model Overview

## Model Type

The reconstruction model is based on a Temporal Convolutional Network encoder-decoder architecture.

The model performs sequence-to-sequence waveform reconstruction:

```text
Input:  PPG-based multichannel signal window
Output: ECG-like waveform window
```

## Input and Output

The model input contains three channels:

1. Original PPG
2. First derivative PPG
3. Second derivative PPG

The model output is a single-channel ECG-like waveform.

General input-output format:

```text
Input shape:  3 × 1024
Output shape: 1 × 1024
```

## Why TCN?

A Temporal Convolutional Network is suitable for this problem because PPG and ECG are time-series signals.

TCN-style models are useful because they can:

* Model local waveform patterns
* Capture longer-range temporal dependencies
* Use dilated convolutions to expand receptive field
* Avoid recurrent computation
* Train efficiently
* Preserve temporal structure
* Support sequence-to-sequence reconstruction

## Encoder-Decoder Design

The model follows an encoder-decoder design.

The encoder compresses and extracts temporal features from the multichannel PPG input.

The bottleneck captures wider temporal context using dilated temporal convolution.

The decoder reconstructs the output waveform from the learned representation.

## High-Level Architecture

```text
PPG + dPPG + ddPPG input
        ↓
Conv1D stem
        ↓
Encoder block 1
        ↓
Downsampling
        ↓
Encoder block 2
        ↓
Downsampling
        ↓
Dilated TCN bottleneck
        ↓
Decoder block 2
        ↓
Upsampling and skip fusion
        ↓
Decoder block 1
        ↓
1×1 Conv1D output head
        ↓
Reconstructed ECG-like waveform
```

## Main Architectural Components

### Conv1D Stem

The initial stem projects the three-channel input into a higher-dimensional feature representation.

It preserves temporal resolution while preparing the signal for deeper temporal modeling.

### Encoder Blocks

The encoder extracts local and mid-range temporal patterns from the input signal.

Encoder blocks help the model learn:

* Pulse shape
* Slope behavior
* Repeating rhythm patterns
* Short-range waveform dependencies

### Downsampling

Downsampling compresses the temporal representation and allows the model to learn more abstract signal features.

### Dilated TCN Bottleneck

The bottleneck uses dilated temporal convolutions.

Dilated convolutions allow the model to observe a wider time range without making the model extremely deep.

This is useful because ECG reconstruction requires both:

* Local waveform morphology
* Broader rhythm context

### Decoder Blocks

The decoder reconstructs the ECG-like waveform from compressed temporal features.

Skip connections help preserve detailed temporal information from encoder stages.

### Output Head

The final output layer maps the decoder features into one ECG-like waveform channel.

The output is a continuous waveform, not a class label.

## Loss Strategy

The full proprietary implementation is not included.

At a high level, the model was trained using a reconstruction-oriented objective designed to balance:

* Point-wise waveform similarity
* Morphological consistency
* Temporal smoothness
* Peak-sensitive reconstruction behavior
* Rhythm preservation

## Public Repository Boundary

This repository does not include:

* Exact model code
* Training code
* Trained model weights
* Full loss implementation
* Dataset files
* Hyperparameter logs
* Proprietary optimization details

The goal is to document the model concept without exposing implementation assets.

## Summary

The model is a TCN encoder-decoder for ECG-like waveform reconstruction from PPG. It uses derivative-enhanced input and temporal convolutional modeling to learn a mapping from wearable-friendly optical pulse signals to ECG-like waveform structure.
