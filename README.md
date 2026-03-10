# Machine Monitoring System (MQTT + ESP32 + Flask)

An Industrial IoT machine monitoring system that measures machine vibration using an **ESP32 + ADXL345 sensor**, sends data via **MQTT**, and processes it using a **Python backend** with a **Flask dashboard, Telegram alerts, downtime analytics, and Excel logging**.

This system is designed for **factory machines, predictive maintenance, and production monitoring**.

---

# System Architecture


ESP32 + ADXL345 Sensor
│
▼
MQTT Broker
│
▼
Python Monitoring Backend
│
├── Flask Dashboard
├── Downtime Analytics
├── Telegram Alerts
├── Excel Logging
└── Daily Machine Reports


---

# Project Features

### Sensor Firmware (ESP32)

- ADXL345 accelerometer vibration sensing
- RMS vibration calculation
- MQTT publishing
- WiFi auto reconnect
- MQTT auto reconnect
- Watchdog reset protection
- Local WebSocket vibration monitor
- Built-in web interface for debugging

---

### Backend Monitoring System

- MQTT vibration monitoring
- Machine state detection
  - Working
  - Idle
  - Off / Sensor Off
- Automatic uptime / downtime calculation
- Downtime reason tracking
- Flask web dashboard
- Excel downtime logging
- JSON state persistence
- Daily summary reports
- Machine utilization analytics
- MTBF calculation
- Telegram alert system
- Telegram command interface

---

### Telegram Bot Features

Commands supported:


/status
/logs
/download
/summary


Examples:

**/status**


Machine Status
Vibration: 1.34 m/s²
Status: Machine Working


**/download**

Downloads the Excel downtime report.

---

# Dashboard Features

The web dashboard displays:

- Live vibration value
- Machine state
- Total uptime
- Total downtime
- Utilization %
- MTBF
- Average downtime
- Longest downtime
- Reason completion rate
- Status breakdown

Tabs include:


Home
Downtime Logs
History


---

# Project Structure


machine-monitoring-system
│
├── backend/
│ ├── app.py
│ ├── config.py
│ ├── monitoring.py
│ ├── mqtt_client.py
│ ├── telegram_service.py
│ ├── excel_logger.py
│ ├── state_manager.py
│ ├── watchdog.py
│ ├── requirements.txt
│ │
│ ├── templates/
│ │ └── dashboard.html
│ │
│ ├── data/
│ │ ├── state.json
│ │ └── history.json
│ │
│ └── logs/
│
├── firmware/
│ └── esp32-vibration-sensor
│ └── esp32-vibration-sensor.ino
│
├── hardware/
│ └── wiring-diagram.png (optional)
│
└── README.md


---

# Hardware Requirements

- ESP32
- ADXL345 Accelerometer
- Jumper wires
- Power supply

### Wiring

| ADXL345 | ESP32 |
|-------|------|
| VCC | 3.3V |
| GND | GND |
| SDA | GPIO21 |
| SCL | GPIO22 |

---

# MQTT Configuration

Broker example:


z9fe19ea.ala.asia-southeast1.emqxsl.com
port: 8883
TLS enabled


Topic used:


vibration/rms


---

# Backend Installation

### Clone the repository


git clone https://github.com/ronitzhah/machine-monitoring-system.git


Enter directory


cd machine-monitoring-system/backend


Install dependencies


pip install -r requirements.txt


---

# Run the Monitoring Server


python app.py


Dashboard available at:


http://localhost:5000


---

# ESP32 Firmware Setup

Open the firmware in **Arduino IDE**:


firmware/esp32-vibration-sensor/esp32-vibration-sensor.ino


Install required libraries:

- Adafruit ADXL345
- Adafruit Unified Sensor
- PubSubClient
- ESPAsyncWebServer
- AsyncTCP

Upload firmware to ESP32.

---

# Excel Logging

Downtime logs are automatically saved in:


backend/logs/


Example:


downtime_2026-03-10.xlsx


---

# Daily Analytics

Every day the system generates:

- Daily machine utilization
- MTBF
- Average downtime
- Longest downtime
- Most common downtime reason

And sends a **Telegram summary message**.

---

# Watchdog Protection

System includes:

### ESP32 Watchdog

Automatically resets the ESP32 if firmware freezes.

### Backend Watchdog

Restarts the backend if MQTT data becomes stale.

---

# Security Notes

Before making this repository public:

Remove or replace:


WiFi credentials
MQTT credentials
Telegram bot token


Use environment variables instead.

---

# Possible Future Improvements

- OTA firmware updates
- Docker deployment
- Grafana vibration dashboard
- Prometheus metrics
- Multi-machine monitoring
- Cloud deployment
- Predictive maintenance ML models

---

# License

MIT License

---

# Author

Developed for Industrial Machine Monitoring using IoT technologies.
