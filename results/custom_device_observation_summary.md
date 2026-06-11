# Custom Device Observation Summary

## Overview

The custom-device phase tested whether the benchmark-trained PPG-to-ECG reconstruction framework could process PPG collected from a low-cost wearable-style prototype.

The custom setup used:

* MAX30102 optical PPG sensor
* ESP32 microcontroller
* Basic low-cost prototyping components
* Fingertip pulse oximeter as a practical rhythm reference during acquisition

## Custom Testing Goal

The goal was not to prove clinical ECG accuracy.

The goal was to observe whether the reconstruction pipeline remained behaviorally meaningful when the input came from a low-cost real-device PPG signal rather than a clean benchmark dataset.

## Custom Workflow

```text
Custom PPG recording
        ↓
Text-data import
        ↓
Numerical parsing
        ↓
125 Hz model-ready preparation
        ↓
Preprocessing
        ↓
PPG + dPPG + ddPPG construction
        ↓
TCN-ED inference
        ↓
ECG-like waveform output
        ↓
BPM comparison and visual inspection
```

## Public-Safe BPM Summary

| Condition                  | Input PPG BPM | Reconstructed ECG BPM | Estimated Gap |
| -------------------------- | ------------: | --------------------: | ------------: |
| Resting condition          |         65–80 |                 65–80 |         0%–1% |
| Faster-heartbeat condition |         75–95 |                75–100 |         0%–3% |

## Main Observation

The custom-device phase suggested that rhythm-level transfer was more reliable than full morphology-level transfer.

The reconstructed ECG-like output generally followed broad rhythm behavior, but detailed morphology was less stable than benchmark reconstruction.

## Positive Observations

* The system could process custom low-cost PPG recordings.
* BPM-level rhythm behavior was broadly preserved.
* The reconstructed output showed meaningful repeated waveform patterns.
* The system demonstrated practical feasibility beyond benchmark-only testing.
* The custom workflow helped expose real-device transfer issues.

## Limitations Observed

Custom-device signals were more sensitive to:

* Motion
* Finger placement
* Finger pressure
* Sensor contact quality
* Ambient noise
* Sampling-rate interpretation
* Device-specific signal distortion

## Morphology Caution

Because paired custom ECG ground truth was not available, morphology-level validation could not be performed.

Therefore, the custom-device output should be interpreted as:

```text
feasibility-level reconstruction behavior
```

not as:

```text
clinically validated ECG reconstruction
```

## Key Finding

The custom-device result supports the main conclusion of the project:

Benchmark reconstruction success is promising, but real-device deployment requires paired custom PPG-ECG data, device-specific fine-tuning, stronger signal-quality control, and larger validation.

## Future Result Improvements

Future result files should include:

* Paired custom PPG-ECG evaluation
* Subject-wise benchmark testing
* Device-specific fine-tuning results
* Signal-quality analysis
* Real-time inference latency
* Motion artifact robustness testing
* Beat-level morphology comparison
* Confidence or uncertainty analysis

## Public Repository Boundary

No raw custom recordings, generated waveform files, participant data, model outputs, or confidential evaluation logs are included in this public repository.


