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

METHODOLOGY

1.	System Architecture:

The intelligent microgrid solar powered unites smart load management and renewable energy with remote monitoring. The system's primary components are:

•	Solar Power Source – Supplies energy to the system.
•	Battery Storage Unit (12V, 7.2Ah Lead-Acid Battery) – Sells over excess solar energy and provides power in the event of solar input shortfalls.
•	ESP32 Microcontrollers – Two ESP32 modules talk through RS-485 (MAX485), with one being the master and one slave for control and data exchange.
•	RS-485 Communication (MAX485 Module) – Allows reliable long-distance communications between the ESP32 modules.
•	Voltage & Current Sensors – Monitor battery voltage and current to calculate State of Charge (SoC) and available energy.
•	Relay Module – Switches loads (light and fan) based on SoC levels.
•	Blynk IoT & ThingSpeak – Employed for remote switching, data plotting, and emailing.


2.	Hardware Implementation:

ESP32 Modules (Master & Slave)

Master ESP32:
•	Monitors the battery voltage from a 25V voltage sensor and estimates SoC.
•	Reports voltage and SoC data to the Slave ESP32 over RS-485 (MAX485 module).
Slave ESP32:
•	It accepts SoC and voltage information from the slave.
•	Enforces relay-controlled switching of the load based on given SoC ranges.
•	Post the data to ThingSpeak for logging and real-time visualization.
•	Allows remote load control through Blynk IoT.

Sensors & Modules Utilized
•	Voltage Sensor (0-25V) – Used to measure battery voltage for SoC calculation.
•	Current Sensor (ACS712, 20A) – Used to measure battery current flow.
•	2-Channel Relay Module – Used to control light and fan according to SoC status.
•	MAX485 Module – Allows RS-485 communication between ESP32 modules.

3.	Communication & Data Flow:

•	Master ESP32 reads the battery voltage and computes SoC.
•	The Master ESP32 sends SoC and voltage data to the Master ESP32 through RS-485.
•	The Slave ESP32:
-	Uses SoC information to decide optimal load running.
-	Manages relay states accordingly.
-	Transmits data to ThingSpeak to store and visualize in the cloud.

4.	Load Management Strategy:

A priority scheme of relay control manages load running according to battery SoC levels:
	SoC > 75% → Light and Fan ON.
	50% < SoC ≤ 75% → Only Light ON.
	SoC ≤ 50% → All non-essential loads OFF to save battery energy.

The relay switching cycle is automated and executed every 20 minutes to guarantee effective load allocation according to available battery energy.

5.	Remote Monitoring & Data Analysis:

•	Blynk IoT provides real-time remote load control through a smartphone app.
•	ThingSpeak Cloud retains voltage and SoC readings so users can see trends and maximize load scheduling.
•	Email alerts are sent through ThingSpeak to notify users of low SoC levels.


RESULTS
•	The table (Fig.01) presents real-time solar panel readings, showing the relationship between irradiance, battery voltage, and SoC.

Location: AB2, third floor
Time: 12.00 PM TO 03.00 PM 
*Irradiance is read by using the app “Solar Radiation.

![image](https://github.com/user-attachments/assets/40b9f5b8-2ba6-4add-befe-fff87a68c5ab)

Table 01. Solar Panel Readings

 ![image](https://github.com/user-attachments/assets/ee056dc6-26ce-4107-a40a-386711ef96f6)
 
Fig.01. Charge Controller and Battery Voltage Sensor


•	When the battery gets drained or disconnected.

 ![image](https://github.com/user-attachments/assets/fe939279-7aec-4219-86df-ee5cc065908a)
 
 
Fig.02. The Thingspeak website gets information and analyzes 

 ![image](https://github.com/user-attachments/assets/b3878405-5d15-4ed5-a4f2-bbf12e3b05fa)
 
Fig.03. User gets the mail regarding the alert

•	When during the normal condition of the battery

![image](https://github.com/user-attachments/assets/b8e21cc0-63c8-4bf9-a3d0-ed7e862d0dc7)

Fig.04. The Thingspeak website gets information and analyzes

 ![image](https://github.com/user-attachments/assets/158c0ff8-5282-47f2-a511-14bd71cd3ab0)
 
Fig.05.Load Prioritizing with the Soc Value at the standalone state

 ![image](https://github.com/user-attachments/assets/4daf0349-fa33-4cae-8f4c-6930844b3545)
 
Fig.06. The serial communication between two ESP32s successfully transfers SoC data via RS-485. 

 ![image](https://github.com/user-attachments/assets/60655eb5-6b28-4751-b618-61f4cd6d4b65)
 
Fig.07. The Serial  Data Transmission between two Esp32 successfully transfers SoC data via RS-485 and load prioritizing 

 ![image](https://github.com/user-attachments/assets/8d4e454d-b30e-4e61-92b1-572f7654a02e)
 
Fig.08. Remote Controlling using Bylnk Iot

CONCLUSIONS:


The solar-powered intelligent microgrid showcased in this work is a vital step toward distributed, sustainable, and autonomous power management. Leveraging real-time load prioritization according to the State of Charge of the battery enables the system to optimize power utilization even during stressed energy conditions. The integration of ESP32 microcontrollers with the RS-485 communication protocol, without any bottlenecks in data exchange across modules, comprised the backbone of an intelligent control network. The addition of IoT platforms such as Blynk and ThingSpeak augmented the system's ability to monitor remotely, have user-configurable alerts, and view historical data, giving users visibility and control.
This project is not only affordable and environmentally friendly but also tackles a pressing worldwide demand—access to energy in rural and underdeveloped areas. From lighting rural homes and medical camps to powering emergency shelters during natural disasters, the portability and scalability of this system make it an invaluable asset in disaster resilience and rural electrification. The load-priority mechanism makes certain that mission-critical devices stay on in low-resource conditions, ultimately maximizing energy efficiency, cutting down waste, and extending battery life.
In the future, the project will provide a solid foundation for the integration of next-generation technologies like AI-based load forecasting, MPPT controllers, and hybrid renewable sources. With additional developments, it has the potential to transform into a fully autonomous, self-healing microgrid—able to adapt to shifting conditions in real time while providing power with no disruptions. In a sense, this project represents the future of smart energy systems: green, intelligent, and resilient.
