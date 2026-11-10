# Smart Helmet — Drowsy Driving Detection via Sensor Fusion

Undergraduate thesis project (BS Computer Engineering, University of San Carlos). A wearable helmet system that detects driver drowsiness by fusing **three independent signals**:

| Module | Signal | What it measures |
|---|---|---|
| **EEG** | Brainwave band power | Alertness level from EEG frequency bands |
| **CV** | Camera + Haar cascade (OpenCV) | Eye closure, via PERCLOS |
| **IMU** | Inertial sensor + Kalman filter | Head movement and nodding |

Each module produces its own classification (Keras models in `machineLeaningModels/`); a second-level model then fuses them into a final drowsiness decision.

## Repository layout

```
main.cpp                 Entry point; runs the three modules together
eeg.cpp / eeg.h          EEG acquisition and processing
cv.cpp / cv.h            Eye detection and PERCLOS computation (OpenCV)
imu.cpp / imu.h          IMU processing
kalmanFilter.*           Kalman filter for IMU data
Parser_Filter.*          Serial data parsing and filtering
machineLeaningModels/    Trained models (EEG, IMU, PERCLOS, 2nd-level fusion)
plot*.plot               gnuplot scripts for visualising raw/EEG/IMU/PERCLOS data
```

## Results

<!-- TODO: add accuracy/precision/recall for single-modality vs. fused model -->

## Hardware

<!-- TODO: EEG headset model, IMU sensor, camera, host board -->

## Build

```bash
make
```

<!-- TODO: dependencies (OpenCV version, gnuplot, serial port setup) -->

## Related repositories

- [opencv-test](https://github.com/jammiguelyfish/opencv-test) — CV module
- [Drowsiness-Detection-System](https://github.com/jammiguelyfish/Drowsiness-Detection-System) — fused system
