# Evaluation Strategy

## Overview

The project uses two complementary evaluation paths:

1. Benchmark evaluation using paired PPG-ECG datasets
2. Custom-device transfer evaluation using low-cost wearable PPG recordings

The benchmark path provides formal waveform comparison because both PPG input and ECG target are available.

The custom-device path evaluates practical transfer behavior because the custom prototype provides PPG-only recordings without paired ECG ground truth in the current stage.

## Benchmark Evaluation

Benchmark evaluation measures how well the model reconstructs ECG from paired PPG-ECG data.

The reconstructed ECG is compared with the reference ECG using waveform-similarity metrics.

## Main Benchmark Metrics

### Mean Absolute Error

Mean Absolute Error measures average absolute difference between the reconstructed ECG and the reference ECG.

```text
MAE = mean(|reference ECG - reconstructed ECG|)
```

Lower MAE is better.

### Root Mean Square Error

Root Mean Square Error gives more weight to larger reconstruction errors.

```text
RMSE = sqrt(mean((reference ECG - reconstructed ECG)^2))
```

Lower RMSE is better.

### Pearson Correlation Coefficient

Pearson Correlation Coefficient measures structural similarity between the reconstructed and reference waveform.

Higher correlation is better.

```text
PCC = correlation(reference ECG, reconstructed ECG)
```

## Public-Safe Benchmark Summary

The final selected TCN encoder-decoder model produced the following benchmark-level reconstruction summary:

| Metric              |  Value |
| ------------------- | -----: |
| MAE                 | 0.3566 |
| RMSE                | 0.6417 |
| Pearson Correlation |  0.884 |

These values are included as a public-safe summary. Raw logs, model files, waveform files, and full implementation details are not included in this repository.

## Visual Evaluation

In addition to numerical metrics, waveform visualization is important.

The benchmark branch can be inspected visually by plotting:

* Input PPG
* Reference ECG
* Reconstructed ECG-like waveform

Visual comparison helps determine whether the generated waveform preserves useful rhythm and morphology patterns.

## Training Behavior

Training and validation loss curves are useful for checking whether the model converged properly.

A stable decrease in training and validation loss suggests that the model learned the reconstruction task under benchmark conditions.

## Custom Device Evaluation

The custom-device branch is different from benchmark evaluation because paired custom ECG ground truth is not currently available.

Therefore, custom-device evaluation focuses on:

* Rhythm consistency
* BPM comparison
* Waveform plausibility
* Signal stability
* Preprocessing sensitivity
* Practical transfer behavior

## Custom Wearable BPM Summary

The public-safe custom-device rhythm summary is:

| Condition                  | Input PPG BPM | Reconstructed ECG BPM | Estimated Gap |
| -------------------------- | ------------: | --------------------: | ------------: |
| Resting condition          |         65–80 |                 65–80 |         0%–1% |
| Faster-heartbeat condition |         75–95 |                75–100 |         0%–3% |

This suggests that rhythm-level transfer was more reliable than full morphology-level transfer.

## Important Interpretation

The custom-device results should be interpreted carefully.

The current system can show:

* Whether rhythm trends are preserved
* Whether reconstructed output behaves plausibly
* Whether the model responds to low-cost PPG input
* Whether BPM estimates are broadly consistent

But it cannot yet prove:

* Clinical ECG accuracy
* Diagnostic reliability
* Full morphology correctness
* Arrhythmia detection reliability
* Replacement of direct ECG

## Why Custom Morphology Validation Is Limited

The custom acquisition branch collected PPG-only recordings. Without simultaneously measured custom ECG, the reconstructed output cannot be compared with a true ECG target.

Therefore, custom-device output must be treated as feasibility evidence, not clinical validation.

## Future Evaluation Improvements

Future evaluation should include:

* Simultaneous custom PPG and ECG recording
* Subject-wise train/validation/test split
* More subjects
* More recording conditions
* Motion artifact testing
* Device-specific fine-tuning
* Clinical-quality reference ECG
* Beat-level morphology analysis
* R-peak and rhythm consistency analysis
* External validation dataset testing

## Summary

The evaluation strategy separates benchmark reconstruction performance from custom-device feasibility.

Benchmark results show supervised reconstruction capability. Custom-device results show practical transfer behavior and reveal the need for paired real-device validation.

