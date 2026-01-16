# STRIX
##Stabilized Rocket Information Exchange
Embedded navigation and telemetry code for a guidance system prototype. The repository includes an extended Kalman filter (EKF) for attitude estimation, matrix utilities, and Arduino sketches for encrypted RF24 communications.

## Contents
- `EKF.hpp`, `EKF.cpp`: EKF state, predict/update, and quaternion handling.
- `matrixUtils.hpp`: Quaternion, rotation, and small-matrix helpers used by the EKF.
- `fastmatrix.hpp`: Third-party header-only matrix expression library (not authored in this project).
- `KF_test.ino`: Arduino-based EKF simulation and serial plotter output.
- `GCS_MASTER.ino`: Ground station sketch for encrypted RF24 link.
- `MSL_SLAVE.ino`: Remote node sketch for encrypted RF24 link.
- `Makefile`: Build rules for the C++ sources.
- `Interface Control Document, STRIX.pdf`: System interface reference.

## Build (C++)
The `Makefile` compiles the C++ sources into a `guidance_system` target:

```bash
make
```

Note: the C++ sources implement library components only; there is no `main()` entry point in this repository.

## Arduino sketches
Open the sketches with the Arduino IDE or compatible tooling.

- `KF_test.ino` simulates a pitch maneuver, runs the EKF at 100 Hz, and prints roll/pitch/yaw to the Serial Plotter.
- `GCS_MASTER.ino` and `MSL_SLAVE.ino` implement an AES-CBC encrypted 32-byte payload exchange over nRF24L01+ radios.

### Dependencies (Arduino)
- RF24 / nRF24L01+ driver library
- AES and AESLib
- Base64 (used by `GCS_MASTER.ino`)
    
