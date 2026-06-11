# Benchmark Result Summary

## Overview

The benchmark phase evaluated whether the TCN encoder-decoder model could reconstruct ECG-like waveforms from paired PPG input under supervised conditions.

The benchmark data provided both:

* PPG input signal
* Reference ECG target signal

This allowed formal waveform-level comparison between the reconstructed ECG-like output and the reference ECG.

## Evaluation Metrics

The benchmark reconstruction was evaluated using the following metrics.

### Mean Absolute Error

Mean Absolute Error measures the average absolute difference between the reconstructed ECG-like waveform and the reference ECG waveform.

Lower MAE indicates better reconstruction.

### Root Mean Square Error

Root Mean Square Error gives stronger penalty to larger errors.

Lower RMSE indicates better reconstruction.

### Pearson Correlation

Pearson Correlation measures waveform similarity between the reconstructed ECG-like output and the reference ECG.

Higher Pearson correlation indicates stronger structural similarity.

## Public-Safe Benchmark Results

| Metric                 |  Value |
| ---------------------- | -----: |
| Mean Absolute Error    | 0.3566 |
| Root Mean Square Error | 0.6417 |
| Pearson Correlation    |  0.884 |

## Interpretation

The benchmark results show promising ECG-like waveform reconstruction under paired-data conditions.

The Pearson correlation value suggests that the reconstructed waveform preserved meaningful structural similarity with the reference ECG in the benchmark setting.

The MAE and RMSE values indicate that measurable reconstruction error remained, which is expected because PPG and ECG are physiologically related but not identical signals.

## Training Behavior

The model showed stable learning behavior during benchmark training.

The training and validation loss curves showed a decreasing trend, indicating that the model learned the supervised reconstruction task.

## What Is Not Included

The following are intentionally excluded:

* Raw benchmark signal files
* Processed dataset files
* Training notebooks
* Model source code
* Model weights
* Training logs
* Generated ECG waveform files
* Full hyperparameter record
* Proprietary evaluation scripts

## Caution

Benchmark performance does not guarantee equally reliable performance on low-cost wearable PPG recordings.

Benchmark datasets are generally cleaner and more controlled than custom-device signals. Therefore, custom-device testing and paired real-device validation are necessary before stronger practical claims can be made.
