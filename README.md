
# Vehicle Tracking System using Arduino with GPS and GSM

## Overview
This project implements a **Vehicle Tracking System** using **Arduino** along with **GPS** and **GSM modules**. It allows tracking the vehicle's real-time location and sends this data to a web server for monitoring purposes. This system can be used for fleet management, theft prevention, or simply monitoring vehicle movement.

## Features
- **Real-time location tracking** using GPS data (latitude and longitude).
- **GSM-based communication** to send GPS coordinates to a remote server or via SMS.
- **Web-based monitoring** for real-time data visualization (via HTTP requests).
- **Portable system** that can be installed on any vehicle with minimal setup.

## Components Used
### Hardware:
- **Arduino Uno/Nano** (any Arduino board with multiple digital pins can be used).
- **GPS Module (e.g., NEO-6M)**: To acquire GPS coordinates (latitude and longitude).
- **GSM Module (SIM800L or SIM900A)**: To send data via SMS or to a web server over HTTP.
- **SIM card** with active data or SMS plan.
- **Power supply**: 9V battery or USB power source.

### Software:
- **Arduino IDE**: For programming the Arduino board.
- **TinyGPS++ Library**: For parsing GPS data.
- **SoftwareSerial Library**: To handle serial communication between Arduino and GPS/GSM modules.

## How It Works
- **GPS Module**: Continuously provides location data (latitude, longitude) from satellite signals.
- **GSM Module**: Sends this GPS data to a remote server through HTTP GET requests or sends SMS updates.
- **Arduino**: Serves as the core processor, managing GPS data acquisition and sending it via GSM.

## Installation

### 1. Hardware Connections
- **GPS Module**:
  - VCC → 5V (or 3.3V, depending on module).
  - GND → GND.
  - TX → Arduino Pin 4 (for receiving GPS data).
- **GSM Module**:
  - VCC → 5V (use a separate power supply if needed).
  - GND → GND.
  - TX → Arduino Pin 7.
  - RX → Arduino Pin 8.

### 2. Software Setup
- Install the necessary libraries in Arduino IDE.
  - **TinyGPS++ Library**: For GPS data parsing.
  - **SoftwareSerial Library**: To handle serial communication between GPS/GSM and Arduino.

#### Install Libraries:
Go to `Sketch > Include Library > Manage Libraries`, then search and install:
- **TinyGPS++**
- **SoftwareSerial** (already included in Arduino IDE)

### 3. Upload the Code
Clone this repository to your local system:
```bash
git clone https://github.com/your-username/vehicle-tracking-system.git
```
Open `vehicle_tracking.ino` in Arduino IDE, modify the server URL and API key as required, and upload the code to your Arduino board.

### 4. Web Server Setup (Optional)
For real-time data visualization, you need a web server to receive the GPS data and display it. You can use a simple PHP script to handle the HTTP requests from the GSM module.

#### Sample PHP Code:
```php
<?php
if (isset($_GET['lat']) && isset($_GET['lng'])) {
    $lat = $_GET['lat'];
    $lng = $_GET['lng'];
    // Save data or visualize
    echo "Location: Latitude: $lat, Longitude: $lng";
} else {
    echo "No GPS data received.";
}
?>
```

### 5. Running the Project
- Power up the Arduino and the modules.
- Monitor the vehicle's real-time GPS coordinates through the server or via SMS (based on your implementation).
- For HTTP tracking, open your browser and visit the web server to see live updates.

## Project Structure
```
|-- vehicle_tracking.ino   # Main Arduino sketch for GPS and GSM integration
|-- gps_data_receiver.php  # PHP script for receiving and visualizing GPS data
```

## Future Enhancements
- Implement geofencing to alert the owner if the vehicle crosses a specified boundary.
- Add an LCD or OLED display for local monitoring of the vehicle’s coordinates.
- Expand the functionality to send SOS alerts or emergency messages.

## Troubleshooting
- **GPS not fixing location**: Ensure the GPS module has a clear sky view.
- **GSM not sending data**: Verify that your SIM card has an active data/SMS plan, and check signal strength using `AT+CSQ`.
- **HTTP request not working**: Check the server URL and network connection.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
