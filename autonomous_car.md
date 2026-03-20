# Autonomous Car

## Motivation

The main goal of this project is to extend human scope to spaces where direct intervention is too dangerous or physically inaccessible. For example, rescue operations, space exploration, reconnaissance missions, disaster responses could be examples of usage of these cars. 

## Idea

The idea is to make an autonomous car that enters the space, maps it, *(optionally)* identifies objects requested by a mission and puts then on the map, sends it to the station then awaiting for new commands which includes navigation, path traversing, recording of some audio or taking photos which sends it back to the station for the analysis. On command, it can return back and finish the mission.   

The system will **process data**, create a **map** using **sensor fusion**, avoiding obstacles and processing some audio using AI to improve mapping, and send the data to the station, which will output it to humans which will order new commands.

---

## Sensors

- **Sonar** -> HC-SR04 (8-16 of them or turn it into a radar)
- **Gyroscope** -> MPU-6050
- (*Optionally*) **Camera** -> not decided yet
- **Microphone** -> not decided yet
  
There are other sensors that can be used for gathering information about the whole space like **temperature**, **humidity** sensors, etc.
---

## Board

For the microcontroller, we can make use of an **ESP32** because of its efficient energy use or **Raspberry Pi Pico 2** which could gather the sensor data, process it and reduce noise, filter audio and send data to the PC.

For the **AI**, SLAM, navigation, audio analysis we can use a **PC** (not decided on the AI acceleration). The communication between PC and microcontroller will be done through **serial** connection, with the chip on the **ESP32** or **Raspberry Pi Pico 2W** acting as the access point.

---

## Stack

We will mainly use:

- **MicroPython** / **Embassy (Rust)** for the microcontroller
- **ROS2**
- **Python** / **PyTorch** (not sure) for neural networks

---

## Implementation

The system implies a three-stage pipeline: data acquisition, signal processing, and AI-driven decision making.

All the sensors are connected to the **ESP32**, which performs:

- Noise filtering for sonar sensors
- Filtering for audio (probably on microcontroller, not decided yet)
- IMU data preprocessing
- Wheel encoder data gathering for velocity estimation

Once filtered, through the **serial**, the ESP32 will send the sampled data to the computer. Based on this data and continously evolving map, the system will perform:

- Extended Kalman filter for sensor fusion and navigation
- Autonomous planning for object avoidance
- Neural network inference for object/entity detection by sensors

All this processed information (map, current position, detected points of interest) will be sent to the station. Optionally, the new commands will be sent to adjust car's mission.

P.S. The idea needs more development and needs more discussion with the professor.