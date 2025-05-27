ABSTRACT

Solar-powered intelligent Microgrid combines smart load management with renewable energy to manage power distribution based on batteries' SoC. Two ESP32 devices communicating through RS-485 (MAX485) are included in the system: one master that tracks battery voltage and calculates SoC, and one slave that manages loads (fan and light) through relays.

A load control mechanism based on priority ensures effective utilization of energy: all loads run at high SoC, critical loads are at medium SoC, and non-critical loads are switched off at low SoC. Remote monitoring and control are facilitated using Blynk IoT, while ThingSpeak is used for real-time data logging and email notification for SoC status.

This microgrid provides a cost-effective and stable energy solution for off-grid sites, disaster relief camps, and remote hospitals, providing continuous power supply where electricity is scarce

Key Features:

1. Dual ESP32 microcontrollers (Master-Slave) using RS-485 (MAX485) for robust communication

2. Real-time battery SoC monitoring and priority-based load management

3. Remote monitoring and control via Blynk IoT

4. Data logging and email alerts using ThingSpeak

5. Smart switching of fan and light based on battery charge levels

Technologies Used:

1. ESP32, MAX485, Voltage & Current Sensors, Relay Module

2. Blynk IoT, ThingSpeak

3. RS-485 Serial Communication 
