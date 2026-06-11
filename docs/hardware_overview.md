# Hardware Overview

## Purpose

The hardware part of the project was developed to collect PPG signals using a low-cost wearable-style setup. The goal was to test whether a benchmark-trained PPG-to-ECG reconstruction system could process signals collected from a practical, low-cost sensing device.

The custom acquisition setup was intentionally simple and accessible. It was designed as a research prototype rather than a finished medical device.

## Hardware Components

| Component                      | Function                               | Reason for Use                                                       |
| ------------------------------ | -------------------------------------- | -------------------------------------------------------------------- |
| MAX30102 sensor module         | Optical PPG acquisition                | Low-cost, compact, widely used in wearable pulse-monitoring projects |
| ESP32 DevKit / microcontroller | Sensor reading and data transfer       | Affordable, programmable, supports embedded prototyping              |
| Fingertip pulse oximeter       | Practical reference during acquisition | Helps observe rhythm stability and signal quality during testing     |
| Breadboard and jumper wires    | Prototype connection                   | Enables fast hardware iteration                                      |
| USB connection                 | Power and data transfer                | Simple development and recording workflow                            |
| Enclosure / physical support   | Finger and sensor positioning          | Improves signal stability during recording                           |

## MAX30102 Sensor

The MAX30102 is an optical biosensing module commonly used for PPG and pulse-monitoring applications.

It was selected because:

* It is low-cost
* It is widely available
* It is compact
* It supports wearable-style optical sensing
* It can be interfaced with microcontrollers
* It is suitable for proof-of-concept physiological monitoring

## ESP32 Microcontroller

The ESP32 was used as the embedded platform for reading sensor data and transferring it to the software pipeline.

It was selected because:

* It is affordable
* It is easy to program
* It has enough capability for prototype biosignal acquisition
* It supports serial communication
* It is commonly used in student and hobbyist embedded projects
* It allows fast iteration during hardware testing

## Fingertip Pulse Oximeter

A fingertip pulse oximeter was used during acquisition as a practical reference.

It helped with:

* Observing approximate heart-rate behavior
* Checking whether the subject was in a stable condition
* Identifying poor acquisition conditions
* Comparing rough BPM behavior with reconstructed output
* Supporting practical testing without clinical equipment

The pulse oximeter was not used as a clinical-grade ECG reference.

## Acquisition Setup

The custom PPG acquisition was performed in a quiet environment to reduce motion and environmental disturbances.

During data collection:

1. The finger was placed on the sensing setup.
2. The subject remained as still as possible.
3. PPG was recorded using the custom device.
4. A pulse oximeter was used alongside the setup for practical rhythm observation.
5. The recorded PPG signal was saved as text data.
6. The signal was later parsed and prepared for the reconstruction pipeline.

## Practical Issues Observed

Low-cost PPG acquisition is sensitive to:

* Finger movement
* Sensor pressure variation
* Loose contact
* Ambient light disturbance
* Finger placement changes
* Motion artifacts
* Baseline drift
* Sampling interpretation errors
* Device-specific noise

These issues are important because they explain why benchmark-trained models may not transfer perfectly to real-device signals.

## Public-Safe Hardware Documentation

This repository intentionally avoids sharing:

* Full circuit schematic
* PCB files
* Firmware
* Exact wiring implementation if proprietary
* Device calibration details
* Raw hardware data
* Startup-sensitive design decisions

The goal is to document the system concept and engineering contribution without exposing confidential implementation details.

## Future Hardware Improvements

Future hardware improvements may include:

* Better sensor enclosure
* More stable finger placement
* Improved ambient light shielding
* Motion artifact reduction
* Integrated battery support
* Wireless data transfer
* Real-time streaming
* Better sampling-rate control
* Simultaneous paired ECG acquisition for validation
* More robust wearable form factor

## Summary

The hardware prototype demonstrates that low-cost optical sensing can be integrated into a PPG-to-ECG reconstruction workflow. While the setup is not a medical device, it provides a practical research platform for testing wearable-style PPG acquisition and deep-learning-based ECG-like waveform reconstruction.

