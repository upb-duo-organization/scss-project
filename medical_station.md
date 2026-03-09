# Home Medical Station

## Motivation

The main goal of this project is to democratize healthcare monitoring, making vital health data accessible to everyone regardless of location or resources. This solution brings decent health monitoring into homes and underserved communities potentially improving health outcomes for those with limited access to regular medical care.

## Idea

Our project will show the implementation of a **home medical station** that will measure vital signs:

- Pulse
- Blood oxygen levels
- Respiratory rate
- Temperature
- ECG

The system will **filter the noise** and send the data to a **main processing unit**, which will run a **neural network** in order to analyse the data and give the best advice or make predictions based on it.

---

## Sensors

- **Pulse** → MAX30102  
- **Blood oxygen levels** → MAX30102  
- **Respiratory rate** → Turbine with hall effect sensor to measure it  
- **Temperature** → MLX90614ESF
- **ECG** → AD8232

---

## Board

For the microcontroller, we can make use of an **ESP32** capable of SPI and I2C communication, and analog-to-digital converion, if needed, an **ADC module** for additional pins (e.g. another ESP32).

For the **neural network** that will run to analyse the data, we can use a **PC**, and then send back the data to the microcontroller to display it on a screen or generate a PDF report for a user.

The communication between the station and the main processing unit will be done through **Wi-Fi**, with the chip on the **ESP32 acting as the access point**.

---

## Stack

We will mainly use:

- **MicroPython** / **Embassy** for the microcontroller
- **Python** / **Rust** for the design and implementation of the neural network and for communication between microcontroller and PC

---

## Implementation

The system implies a three-stage pipeline: data acquisition, signal processing, and AI analysis.

All the sensors will be connected to the **ESP32**, which will perform:

- Noise filtering
- Peak detection algorithms (e.g. Heart rate variability)
- Analog-to-digital conversion

Once filtered, through the **Wi-Fi chip**, the ESP32 will send the sampled serialized data to the computer. Based on this data and previously collected data, the system will:

- Compute different parameters
- Detect possible health problems
- Provide a diagnostic
- Suggest prevention methods
- Make predictions
- Prepare a report

All this processed information will then be **sent back to the ESP32**, which will display the results on a **screen for the user of the station to see** OR, for instance, sent **a PDF report** to user's email so that he/she can share that with his/her doctor.
