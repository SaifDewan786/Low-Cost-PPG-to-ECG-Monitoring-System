# Results

This folder contains public-safe result summaries for the low-cost PPG-to-ECG reconstruction project.

The full source code, raw biosignal data, trained model weights, waveform output files, firmware, participant recordings, and detailed proprietary evaluation logs are intentionally excluded due to intellectual property and privacy considerations.

## Result Categories

The project has two main result categories:

1. Benchmark reconstruction evaluation
2. Custom wearable transfer observation

## Benchmark Evaluation

The benchmark phase uses paired PPG-ECG datasets. Since both input PPG and reference ECG are available, the reconstructed ECG-like waveform can be compared against the reference ECG.

Main benchmark indicators:

* Mean Absolute Error
* Root Mean Square Error
* Pearson Correlation
* Visual waveform similarity
* Training and validation loss behavior

## Custom Wearable Observation

The custom-device phase uses PPG collected from a low-cost wearable-style prototype.

The custom device branch is not a full morphology-level validation because paired custom ECG ground truth was not available in the current stage.

Custom-device observations focus on:

* Rhythm consistency
* BPM comparison
* Waveform plausibility
* Transfer behavior
* Sensitivity to preprocessing and acquisition quality

## Important Disclaimer

These results are for research documentation only.

They do not prove clinical validity and should not be used for medical diagnosis, treatment, or emergency monitoring.

The generated ECG-like waveform is experimental and should not be treated as a replacement for directly measured ECG.



