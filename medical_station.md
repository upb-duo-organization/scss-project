# Home Medical Station

## Idea

Our project will show the implementation of a **home medical station** that will measure:

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
- **Temperature** → `//roy again add sensor, u said u have something`  
- **ECG** → `//roy add ur sensor`

---

## Board

For the microcontroller, we can make use of an **ESP32**, and if needed, an **ADC module** for additional pins.

For the **neural network** that will run to analyse the data, we can use a **laptop**, and then send back the data to the microcontroller to display it on a screen.

The communication between the station and the main processing unit will be done through **Wi-Fi**, with the chip on the **ESP32 acting as the access point**.

---

## Language

We will mainly use:

- **MicroPython** for the microcontroller
- **Python** for the design and implementation of the neural network

---

## Implementation

`//add more here roy please, my scientific language does not work with me rn :(`

All the sensors will be connected to the **ESP32**, which will perform:

- Noise filtering
- Analog-to-digital conversion

Then, through the **Wi-Fi chip**, the ESP32 will send the sampled data to the computer. Based on this data and previously collected data, the system will:

- Compute different parameters
- Detect possible health problems
- Provide a diagnostic
- Suggest prevention methods
- Make predictions

All this processed information will then be **sent back to the ESP32**, which will display the results on a **screen for the user of the station to see**.

`//this needs much much more work, I m sorry, my mind rly doesn t work rn`