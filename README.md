# COSC 111 - Laboratory Activities Portfolio

This repository contains all laboratory activities and examinations completed for COSC 111. Each activity demonstrates various concepts in embedded systems programming, sensor interfacing, serial communication, and Arduino-Python integration.

---

## 📁 Repository Structure

```
PERALTA_PORTFOLIO_COSC111B/
├── Laboratory_1/
├── Laboratory_2/
├── Laboratory_3/
├── Laboratory_4/
├── Laboratory_5/
├── Laboratory_6/
├── Laboratory_7/
├── LabExam_Midterms/
└── LabExam_Finals/
```

---

## 🛠️ General Requirements

### Software Requirements
- **Arduino IDE** (version 1.8.x or later)
- **Python 3.x**
- **Required Python Libraries:**
  - `pyserial` - Serial communication
  - `fastapi` - Web API framework (Lab 7)
  - `uvicorn` - ASGI server (Lab 7)
  - `requests` - HTTP requests (Final Exam)

### Hardware Requirements
- **Arduino Uno** (or compatible board)
- **Breadboard** and jumper wires
- **LEDs** (various colors)
- **Resistors** (220Ω for LEDs, 10kΩ for sensors)
- **Sensors:**
  - Thermistor (Lab 3)
  - Photoresistor (Labs 3, 4, Midterm Exam)
- **Push Buttons** (Labs 6, 7, Final Exam)

### Installation

1. **Arduino Setup:**
   - Install Arduino IDE from [arduino.cc](https://www.arduino.cc/en/software)
   - Connect Arduino Uno via USB
   - Select board: Tools → Board → Arduino Uno
   - Select port: Tools → Port → (your COM port)

2. **Python Setup:**
   ```bash
   pip install pyserial fastapi uvicorn requests
   ```

3. **Uploading Code:**
   - Open `.ino` file in Arduino IDE
   - Click Upload button
   - Wait for "Done uploading" message

4. **Running Python Scripts:**
   - Ensure Arduino is connected and code is uploaded
   - Update COM port in Python scripts if needed
   - Run: `python <script_name>.py`

---

## 🔬 Laboratory Activities

### Laboratory 1: Basic LED Sequential Control

**Description:**  
A fundamental Arduino program that demonstrates sequential LED control using digital output pins. Five LEDs are connected to pins 12, 11, 10, 9, and 8, and are turned on and off in sequence.

**Components:**
- 5 LEDs
- 5 Resistors (220Ω recommended)
- Arduino Uno

**Features:**
- Sequential LED activation (one at a time)
- 1-second delay between each LED state change
- Simple for-loop implementation for LED control

**Code Structure:**
- Uses an array to store LED pin numbers
- `setup()`: Initializes all LED pins as OUTPUT
- `loop()`: Turns LEDs ON sequentially, then OFF sequentially

**Files:**
- `Laboratory_1.ino` - Main Arduino sketch

---

### Laboratory 2: LED Control with PWM Brightness

**Description:**  
An advanced LED control system that demonstrates both digital and PWM (Pulse Width Modulation) control. Non-PWM pins use standard digital control, while PWM-capable pins (9, 10, 11) use analog brightness control to create a smooth fade effect.

**Components:**
- 5 LEDs (connected to pins 12, 11, 10, 9, 8)
- 5 Resistors (220Ω recommended)
- Arduino Uno

**Features:**
- Conditional LED control based on pin capabilities
- PWM brightness fade-in and fade-out for pins 9, 10, 11
- Sequential forward and reverse LED activation
- Brightness control from 0 to 255 (PWM range)

**Code Structure:**
- Checks if pin is PWM-capable before applying control
- Uses `analogWrite()` for PWM pins
- Uses `digitalWrite()` for standard digital pins
- Implements while loops for sequential control

**Files:**
- `Laboratory_2.ino` - Main Arduino sketch

---

### Laboratory 3: Fire Detection System

**Description:**  
A sensor-based fire detection system that monitors temperature using a thermistor and light intensity using a photoresistor. The system triggers an alert (LED/buzzer) when both temperature and brightness exceed predefined thresholds, indicating a potential fire condition.

**Components:**
- Thermistor (connected to A0)
- Photoresistor (connected to A2)
- 10kΩ resistor (for thermistor voltage divider)
- Alert LED/Buzzer (connected to pin 12)
- Arduino Uno

**Features:**
- Temperature reading in Celsius using Steinhart-Hart equation
- Light intensity/brightness measurement
- Fire detection logic: Temperature ≥ 40°C AND Brightness ≥ 220
- Serial monitoring of sensor values
- Alert system with blinking LED/buzzer

**Code Structure:**
- `readTemperature()`: Converts analog reading to Celsius
- `readBrightness()`: Reads and scales photoresistor value
- `loop()`: Continuously monitors sensors and triggers alerts

**Thresholds:**
- Temperature Threshold: 40°C
- Light Threshold: 220 (scaled value)

**Files:**
- `LabAct_3_CODE.ino` - Main Arduino sketch

---

### Laboratory 4: Light Detection Alert with Serial Control

**Description:**  
A light detection system that monitors ambient light levels using a photoresistor. When brightness exceeds a threshold, an alert LED begins blinking. The system can be controlled via serial commands, allowing users to stop the blinking alert remotely.

**Components:**
- Photoresistor (connected to A0)
- Alert LED (connected to pin 8)
- Arduino Uno

**Features:**
- Continuous brightness monitoring
- Threshold-based alert activation (≥ 220)
- Serial command interface ("stop" command)
- Real-time brightness value display via Serial Monitor
- Fast blinking alert (100ms intervals)

**Code Structure:**
- `readBrightness()`: Reads and scales photoresistor value
- Serial command parsing for user control
- State management for alert system

**Serial Commands:**
- `stop` - Stops the blinking alert

**Files:**
- `Laboratory_4.ino` - Main Arduino sketch

---

### Laboratory 5: RGB LED Control via Serial Communication

**Description:**  
A bi-directional communication system between Arduino and Python. The Arduino controls RGB LEDs based on serial commands sent from a Python script. This demonstrates serial communication, command parsing, and modular code organization using header files.

**Components:**
- RGB LED (Red: pin 8, Green: pin 9, Blue: pin 10)
- 3 Resistors (220Ω recommended)
- Arduino Uno

**Features:**
- Serial command interface (R, G, B, A, O, V)
- Individual LED toggle control
- All LEDs ON/OFF commands
- Special "Violet" mode (Red + Blue)
- Python GUI menu for easy control
- Modular code structure with header file

**Code Structure:**
- `ledheader.h`: Contains LED pin definitions and control functions
- `Laboratory_5.ino`: Main sketch with serial command parsing
- `Laboratory_5.py`: Python script for user interface

**Serial Commands:**
- `R` - Toggle Red LED
- `G` - Toggle Green LED
- `B` - Toggle Blue LED
- `A` - Turn All LEDs ON
- `O` - Turn All LEDs OFF
- `V` - Turn on Violet (Red + Blue)

**Python Features:**
- Interactive menu system
- Serial port configuration (COM6 default)
- Real-time command feedback
- Error handling for serial communication

**Files:**
- `Laboratory_5.ino` - Main Arduino sketch
- `Laboratory_5.py` - Python control script
- `ledheader.h` - LED control header file

**Setup Instructions:**
1. Upload `Laboratory_5.ino` to Arduino
2. Install Python dependencies: `pip install pyserial`
3. Update COM port in `Laboratory_5.py` if needed
4. Run: `python Laboratory_5.py`

---

### Laboratory 6: Bi-directional Serial Communication

**Description:**  
An advanced serial communication system demonstrating two-way data exchange between Arduino and Python. Physical buttons on the Arduino send data to Python, and Python sends commands back to control LEDs. This demonstrates edge detection, button debouncing, and real-time serial communication.

**Components:**
- RGB LED (Red: pin 7, Green: pin 6, Blue: pin 5)
- 3 Push buttons (connected to pins 12, 11, 10 with pull-up resistors)
- 3 Resistors (220Ω for LEDs)
- Arduino Uno

**Features:**
- **Arduino → Python**: Button presses send character codes (R, G, B)
- **Python → Arduino**: Python receives button data and sends LED control commands (1, 2, 3)
- Edge detection for button presses (detects button press, not hold)
- LED toggle control based on Python commands
- Real-time serial monitoring

**Code Structure:**
- `ledheader.h`: LED pin definitions and toggle function
- `Laboratory_6.ino`: Button reading and serial communication
- `Laboratory_6.py`: Python listener and command sender

**Communication Flow:**
1. Button pressed on Arduino → Sends 'R', 'G', or 'B' to Python
2. Python receives character → Sends corresponding '1', '2', or '3' back
3. Arduino receives command → Toggles corresponding LED

**Files:**
- `Laboratory_6.ino` - Main Arduino sketch
- `Laboratory_6.py` - Python serial listener
- `ledheader.h` - LED control header file

**Setup Instructions:**
1. Upload `Laboratory_6.ino` to Arduino
2. Install Python dependencies: `pip install pyserial`
3. Update COM port in `Laboratory_6.py` (default: COM5)
4. Run: `python Laboratory_6.py`

---

### Laboratory 7: Web API Integration with FastAPI

**Description:**  
A web-based control system using FastAPI to create RESTful endpoints for controlling Arduino LEDs. This demonstrates modern web API development, HTTP requests, and integration between web services and embedded systems.

**Components:**
- RGB LED (Red: pin 7, Green: pin 6, Blue: pin 10)
- 3 Push buttons (connected to pins 12, 11, 10)
- 3 Resistors (220Ω for LEDs)
- Arduino Uno

**Features:**
- RESTful API endpoints for LED control
- HTTP GET requests to control LEDs
- Individual LED toggle (Red, Green, Blue)
- All LEDs ON/OFF commands
- Button press detection and serial output
- FastAPI web server with automatic serial connection management

**API Endpoints:**
- `GET /` - API status check
- `GET /led/on` - Turn all LEDs ON
- `GET /led/off` - Turn all LEDs OFF
- `GET /led/{color}` - Toggle specific LED (red, green, blue)

**Code Structure:**
- `ledheader.h`: LED control functions and pin definitions
- `Laboratory_7.ino`: Serial command handler and button detection
- `Laboratory_7.py`: FastAPI server with serial communication

**Files:**
- `Laboratory_7.ino` - Main Arduino sketch
- `Laboratory_7.py` - FastAPI web server
- `ledheader.h` - LED control header file

**Setup Instructions:**
1. Upload `Laboratory_7.ino` to Arduino
2. Install Python dependencies: `pip install fastapi uvicorn pyserial`
3. Update COM port in `Laboratory_7.py` (default: COM5)
4. Run: `uvicorn Laboratory_7:app --reload` or `python Laboratory_7.py`
5. Access API at: `http://localhost:8000`
6. Test endpoints: `http://localhost:8000/led/red`, `/led/green`, `/led/blue`, `/led/on`, `/led/off`

---

## 📝 Examinations

### Lab Exam - Midterms: Light Intensity Monitoring System

**Description:**  
A sophisticated light intensity monitoring system with dual operating modes (Automatic and Manual). The system uses a photoresistor to measure ambient light and displays the status using three colored LEDs (Green, Yellow, Red). In Automatic mode, it also determines the environment condition (Cloudy/Clear).

**Components:**
- Photoresistor (connected to A0)
- 3 LEDs: Green (pin 11), Yellow (pin 12), Red (pin 13)
- 3 Resistors (220Ω recommended)
- Arduino Uno

**Features:**
- **Automatic Mode**: Uses default thresholds (LOW = 40%, HIGH = 70%)
  - Displays environment status (Cloudy/Clear)
  - Automatic threshold management
- **Manual Mode**: User-configurable thresholds
  - Custom LOW threshold setting
  - Custom HIGH threshold setting
  - Threshold validation (LOW < HIGH, HIGH ≤ 100)
- Real-time light intensity percentage display (0-100%)
- Three-tier LED indication system:
  - Green LED: Light intensity ≤ LOW threshold
  - Yellow LED: LOW threshold < Intensity < HIGH threshold
  - Red LED: Intensity ≥ HIGH threshold

**Serial Commands:**
- `MODE AUTO` - Switch to Automatic mode (reverts to default thresholds)
- `MODE MANUAL` - Switch to Manual mode
- `SET LOW <value>` - Set LOW threshold (Manual mode only, 0 ≤ value < HIGH)
- `SET HIGH <value>` - Set HIGH threshold (Manual mode only, LOW < value ≤ 100)

**Code Structure:**
- Mode management system
- Threshold validation and storage
- Light intensity mapping (0-1023 → 0-100%)
- LED control logic based on thresholds
- Environment detection (Automatic mode only)

**Files:**
- `LabExam_Midterms.ino` - Main Arduino sketch

**Usage Example:**
```
Serial Input: MODE MANUAL
Serial Input: SET LOW 30
Serial Input: SET HIGH 80
```

---

### Lab Exam - Finals: Button Press Detection with API Integration

**Description:**  
A system that detects button presses on an Arduino and sends HTTP requests to an external API endpoint. This demonstrates integration between embedded systems and web services, serial communication, and API interaction.

**Components:**
- Push button (connected to pin 12 with pull-up resistor)
- Arduino Uno

**Features:**
- Button press detection with edge detection
- Serial communication to Python script
- HTTP GET request to external API
- API endpoint: `/led/group/{GROUP_NUMBER}/toggle`
- Error handling for serial and API communication
- Configurable API base URL and group number

**Code Structure:**
- `LabExam_Finals.ino`: Button detection and serial output
- `LabExam_Finals.py`: Serial listener and API request handler

**Communication Flow:**
1. Button pressed on Arduino
2. Arduino sends "Button 1 Pressed" via Serial
3. Python script receives message
4. Python sends HTTP GET request to API endpoint
5. API response is displayed

**Configuration:**
- `SERIAL_PORT`: Arduino COM port (default: COM5)
- `BAUD_RATE`: Serial communication speed (9600)
- `API_BASE_URL`: Base URL of the API server
- `GROUP_NUMBER`: Group identifier for API endpoint (default: "1")

**Files:**
- `LabExam_Finals.ino` - Main Arduino sketch
- `LabExam_Finals.py` - Python API integration script

**Setup Instructions:**
1. Upload `LabExam_Finals.ino` to Arduino
2. Install Python dependencies: `pip install pyserial requests`
3. Configure `API_BASE_URL` and `GROUP_NUMBER` in `LabExam_Finals.py`
4. Update `SERIAL_PORT` if needed
5. Run: `python LabExam_Finals.py`

**API Endpoint Format:**
```
GET {API_BASE_URL}/led/group/{GROUP_NUMBER}/toggle
```

---

## 📊 Activity Summary

| Activity | Focus Area | Key Concepts |
|----------|-----------|--------------|
| Lab 1 | Basic I/O | Digital output, loops, arrays |
| Lab 2 | PWM Control | Analog output, PWM, brightness control |
| Lab 3 | Sensors | Analog input, thermistor, photoresistor, fire detection |
| Lab 4 | Serial I/O | Serial communication, command parsing |
| Lab 5 | Arduino-Python | Serial communication, modular code, command interface |
| Lab 6 | Bi-directional Comm | Two-way serial, edge detection, button debouncing |
| Lab 7 | Web Integration | RESTful API, FastAPI, HTTP requests |
| Midterm Exam | Advanced Sensors | Mode switching, threshold management, environment detection |
| Final Exam | API Integration | HTTP requests, external API communication |