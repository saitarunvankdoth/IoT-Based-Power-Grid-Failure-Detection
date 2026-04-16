# IoT-Based-Power-Grid-Failure-Detection
# Power Grid Failure Detection using IoT

A microcontroller-based system that monitors power grid voltage and frequency in real-time and automatically disconnects the load when values fall outside acceptable limits — helping prevent blackouts and equipment damage.

> Final Year Project — B.E. in Electrical and Electronics Engineering  
> MVSR Engineering College, Hyderabad (2024)

---

## Overview

Power grid synchronization failure can cause complete blackouts. This project addresses that by continuously sensing voltage and frequency from the supply and triggering a relay to disconnect the feeder whenever the readings deviate beyond safe thresholds. Live data is visualized remotely via ThingSpeak (IoT platform).

---

## Features

- Real-time voltage and frequency monitoring
- Automatic load disconnection on fault detection
- LCD display showing live readings and alert messages
- IoT integration via ESP8266 Wi-Fi module and ThingSpeak
- LED and relay-based visual/physical fault indicators
- Microcontroller health check on startup

---

## Acceptable Operating Ranges

| Parameter | Safe Range |
|-----------|------------|
| Voltage   | 210V – 245V |
| Frequency | 49Hz – 51Hz |

The system trips the relay and turns off the load if values go outside these ranges.

---

## Hardware Components

| Component | Purpose |
|-----------|---------|
| PIC16F73 Microcontroller | Core processing unit |
| Potentiometer | Voltage level simulation/adjustment |
| Opto-coupler | Frequency sensing |
| Relay | Load disconnection |
| LCD (16x2) | Display voltage, frequency, and alerts |
| ESP8266 Wi-Fi Module | IoT connectivity |
| Crystal Oscillator (20MHz) | Clock source for MCU |
| Regulated Power Supply (5V) | Powers the circuit |
| LED Indicators | Status indicators |

---

## Software & Tools

- **PIC C Compiler (CCS)** — for writing and compiling embedded C code
- **Express PCB / Proteus 7** — for circuit design and simulation
- **PICkit 2 Programmer** — for dumping the hex file to the microcontroller
- **ThingSpeak** — for IoT-based real-time data visualization

---

## How It Works

1. The PIC16F73 reads voltage via ADC (from potentiometer) and frequency via Timer0.
2. Values are displayed on the LCD every cycle.
3. If voltage exceeds 245V or drops below 210V → relay trips, load disconnects, alert shown.
4. If frequency goes above 51Hz or below 49Hz → same protective action.
5. Data is sent to ThingSpeak via the ESP8266 module for remote monitoring.

---

## Project Structure

```
├── code.c          # Main embedded C source code
├── README.md       # Project documentation
```

---

## Circuit Overview

The system takes 230V AC mains → step-down transformer → bridge rectifier → filter → 5V regulated DC for the MCU. The relay is connected in series with the bulb (load), controlled by the microcontroller output pin.

---

## Results

| Condition | Voltage | Frequency | Load Status |
|-----------|---------|-----------|-------------|
| Normal | 229V | 50Hz | ON |
| Low Voltage | 183V | 50Hz | OFF |
| High Voltage | 252V | 50Hz | OFF |
| High Frequency | 230V | 58Hz | OFF |
| Low Frequency | 230V | 42Hz | OFF |

---

## Team

- Thodupunuri Saneeth (2451-20-734-006)
- Vankdoth Sai Tarun (2451-20-734-019)
- Mohammed Abdul Raheem Saad (2451-20-734-034)

**Guide:** S. Shyam Mohan, Assistant Professor, Dept. of EEE, MVSR Engineering College

---

## References

- [Wikipedia](https://www.wikipedia.com)
- [All About Circuits](https://www.allaboutcircuits.com)
- [Microchip Technology](https://www.microchip.com)
- Raj Kamal — *Microcontrollers: Architecture, Programming, Interfacing and System Design*
- Mazidi & Mazidi — *Embedded Systems*
- PIC Microcontroller Manual — Microchip
