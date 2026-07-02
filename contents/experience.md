# 🧪 Detailed Engineering & Project Experience

I focus on high-density power converter topologies, advanced motor control algorithms, industrial IoT master architectures, and robust multi-board product engineering. Over 15 multidisciplinary projects delivered across industrial HVAC, fuel monitoring, consumer electronics, and smart automation.

---

### 1. ❄️ Commercial Split-System Inverter Air Conditioner (1.5 Tonne / 2HP)

* **Company:** Sabro Technologies
* **Timeline:** 01/02/2026 – Present
* **Role:** Lead Electronics Engineer
* **Architecture:** Dual-Board Distributed Topology (Indoor Master Control + Outdoor Power Drive Stage)

#### A. Indoor Unit (IDU) Mainboard Control Card

* **Hardware Infrastructure:** Designed and optimized a multi-layer control card centered around a high-performance master microcontroller. Built local power management layers leveraging a step-down Buck converter topology to derive stable 12V (relays/fans), 5V (sensors), and 3.3V (logic) rails directly from rectified AC mains.
* **Peripherals & Sensing:** Interfaced high-speed capacitive zero-crossing detection circuits to drive the indoor AC fan motor speed via triac phase-angle control. Integrated a multi-channel precision NTC thermistor biasing network to continuously map room ambient and evaporator coil temperatures. Designed multi-phase stepper motor drive stages for automated horizontal and vertical louver positioning.
* **Isolated Communication Sub-Circuit:** Engineered a high-voltage, single-wire current loop communication physical layer to safely negotiate bidirectional UART data packets across long field interconnect wiring between the indoor and outdoor environments.

#### B. Outdoor Unit (ODU) Inverter & Power Stage

* **Dual-Processor Orchestration:** Developed a synchronized processing core utilizing an **ESP32 Master** handling high-level state machine routines, external peripherals, and protective monitoring, paired with an **Infineon iMOTION IMC102T** dedicated Motion Control Engine (MCE) configured for low-latency space vector field-oriented motor control (FOC).
* **Power Electronics & Motor Drive:** Laid out a high-current power stage integration leveraging Intelligent Power Modules (IPMs) for variable-speed three-phase compressor commutation. Integrated an active Power Factor Correction (PFC) boost converter topology utilizing high-voltage power MOSFETs to maximize grid efficiency, eliminate total harmonic distortion (THD), and maintain DC bus stiffness.
* **Peripherals & Safety:** Designed driver stages for an electronic expansion valve (EEV) stepper motor for variable refrigerant metering, four-way reversing valves for heat/cool cycle shifting, and a high-current outdoor BLDC fan motor. Engineered an 8-channel analog telemetry front-end tracking compressor discharge, ambient air, condenser coils, and heat-sink temperatures.
* **Deep Circuit Troubleshooting:** Successfully diagnosed and resolved an intermittent field issue where the system experienced communication frame errors and drops down to 198V AC under full 8.5A compressor load over low-quality field wires.

![Test bench hardware](/static/assets/img/Test_Bench.jpeg)

---

### 2. 🔥 Industrial Heat Pump Drive & Safety Control Infrastructure

* **Company:** Enertia Pvt Ltd
* **Timeline:** 10/05/2025 – 05/12/2025
* **Role:** Lead Electronics Engineer
* **Status:** Commercialized & Deployed at Scale

#### A. High-Reliability Power Distribution & Layout Hardening

* Designed a ruggedized power management layer capable of stepping down volatile industrial mains supplies into tightly regulated control rails.
* Implemented robust hardware-level protection networks featuring Metal Oxide Varistors (MOVs) and Transient Voltage Suppressors (TVS) rated to absorb massive inductive line kicks.
* Programmed analog comparator ISRs to achieve sub-millisecond trip times for **Overcurrent (OC), Overvoltage (OV), and Undervoltage (UV)** state monitoring, immediately disabling gate drivers during overload or brownout states.

#### B. Gas & Ignition Management

* Developed a complete, software-governed automatic gas control manifold matrix featuring integrated digital solenoid valve drivers.
* Designed an automatic multi-strike high-voltage electronic sparking ignition module utilizing zero-cross ignition timing.
* Implemented localized magnetic and optical isolation barriers to decouple high-frequency spark noise from sensitive low-voltage logic traces.

#### C. Failsafe Operations & "No Gas" Vacuum Protection

* Authored a hardware-software **"No Gas Protection"** interlock protocol that immediately cuts drive current to the compressor and isolates the fuel supply line upon detecting fuel exhaustion during an active ignition command, preventing a destructive high-vacuum state.

![Heat pump hardware](/static/assets/img/Heat_Pumo_table.jpeg)

---

### 3. 💧 Touch-Interactive Smart Water Dispenser Platform

* **Company:** Enertia Pvt Ltd
* **Timeline:** 05/02/2025 – 07/08/2025
* **Role:** Lead Electronics Engineer
* **Architecture:** Multi-Layered Commercial-Grade Infrastructure

* **Concurrence & Core Control:** Utilized an ESP32-S3 running FreeRTOS to manage asynchronous tasks across capacitive touch UI inputs, multi-pump extraction loops, and rapid cooling/heating thermal cycles.
* **Sensor Integration:** Integrated hall-effect flow sensors for accurate volume measurement, float switches for water level detection, and temperature sensors with hot-water safety locks to prevent scalding.
* **Fluidics & EMI Mitigation:** Designed a multi-source automated extraction fluidics manifold with integrated carbonation capabilities. Implemented distributed RC snubbers and flyback diodes to suppress EMI generated by inductive pump switching near the capacitive touch sensor plane.
* **Outcome:** Prototype passed rigorous safety and performance tests and is currently in pilot production.

![Dispenser PCB](/static/assets/img/Dispenser_PCB.png)

---

### 4. ⚡ Custom HVAC Control Board & Inverter Stage

* **Company:** Sabro Technologies
* **Role:** Electronics Engineer
* **Technology Stack:** Infineon IMC102T, ESP32, PFC, Single-Shunt Topology

* **System Design:** Designed and developed a comprehensive 220VAC HVAC control system integrating active PFC boost infrastructure and a single-shunt current feedback loop for phase current reconstruction.
* **Component Coordination:** Configured an Infineon IMC102T motor controller as a dedicated real-time motor drive co-processor, paired with an ESP32 master microcontroller that coordinates EEV stepper motor control, system-wide diagnostics, and communication routing.

![IPM drive hardware](/static/assets/img/IPM_drive_new.jpeg)

---

### 5. 🏎️ Field-Oriented Control (FOC) & Motor Drivers

* **Company:** Sabro Technologies
* **Role:** Electronics Engineer
* **Technology Stack:** Infineon iMOTION, MCEWizard, MCEDesigner, Space Vector PWM (SVPWM)

* **Algorithm Optimization:** Configured and tuned FOC algorithms for permanent magnet synchronous motors (PMSM) using Infineon iMOTION hardware. Developed single-shunt current reconstruction topologies to map rotor position accurately without external hall sensors.
* **Control Loop Tuning:** Specialized in analyzing and tuning current regulator bandwidth, optimizing proportional-integral ($K_p/K_i$) loop gains, and establishing robust UART/Modbus communications with real-time Motion Control Engines (MCE).

![Inverter hardware](/static/assets/img/Inverter.png)

---

### 6. 🌐 Industrial IoT & Robust Embedded Firmware

* **Company:** Sabro Technologies
* **Role:** Electronics Engineer
* **Technology Stack:** ESP32-S3, STM32, C/C++, Secure Boot, OTA Pipelines

* **Firmware Pipelines:** Developed robust, field-deployable firmware pipelines utilizing ESP32-S3 and STM32 platforms.
* **Reliability Implementations:** Implemented custom dual-stage bootloaders, secure OTA firmware update structures with fallback partition redundancy, and advanced low-power state management utilizing hardware watchdog timers.

![Dubai taxi PCB](/static/assets/img/Dubai_taxi_PCB.png)
![Dubai taxi PCB Proteus](/static/assets/img/Dubai_taxi_PCB_proteus.png)

---

### 7. 🔬 Heterogeneous Power Stage R&D

* **Company:** Sabro Technologies R&D Lab
* **Role:** Electronics Engineer
* **Technology Stack:** Wide-Bandgap Semiconductors (GaN & SiC), Altium Designer, Thermal Modeling

* **Next-Gen Topologies:** Researched and drafted advanced architectures for heterogeneous power stages using GaN and SiC semiconductors targeted for 400V-class high-efficiency inverters.
* **Dynamic Balancing:** Focused on balancing gate-drive timing dynamics, parasitic loop inductance reduction, and asymmetric thermal distribution across mixed-device legs.

![Power supply hardware](/static/assets/img/Power_Supply.jpg)

---

### 8. ⛽ Real-Time Secure Fuel Telemetry & Theft Prevention Node

* **Company:** Sabro Technologies (Industrial Automation Division)
* **Role:** Electronics Engineer
* **Technology Stack:** Ultra-Low-Power ESP32, Encrypted MQTT, Cellular Telemetry

* **Telemetry Processing:** Implemented ultra-low-power ESP32 sensor nodes with high-accuracy pulse-output flow calculation algorithms to monitor fuel levels and prevent transport tampering.
* **Encrypted Communication:** Structured an edge-to-cloud telemetry infrastructure utilizing hardware-accelerated encrypted MQTT packets over cellular/Wi-Fi links. Executing deep sleep profiles and hardware watchdog timers for sustained brownout scenarios.
* **Outcome:** Reduced fuel theft incidents by over 30% in pilot stations.

![Fuel monitoring](/static/assets/img/Fuel.png)


---

### 9. 🚖 Automotive Ruggedized Power Supply & Signage Controller

* **Company:** Sabro Technologies
* **Role:** Electronics Engineer
* **Technology Stack:** DC-DC Buck Topologies, Thermal Management, ISO 16750 Standards

* **DC-DC Buck Architecture:** Engineered a high-efficiency DC-DC buck converter stepping down noisy 12V automotive battery lines to regulated 5V and 3.3V logic rails, sustaining continuous 3A+ loads.
* **Environmental Hardening:** Applied stringent thermal mapping to sustain prolonged 85°C ambient operational thresholds and engineered trace spacing and vibration dampening layouts satisfying ISO 16750 standards.
![Dubai taxi PCB Proteus PS](/static/assets/img/Dubai_taxi_PCB_proteus_PS.png)

---

### 10. 🌿 Carbon Emission Monitoring System

* **Company:** Sabro Technologies
* **Role:** Electronics Engineer
* **Technology Stack:** ESP32, MQTT, Gas & Particulate Sensors

* **Sensor Node Design:** Created ESP32-based sensor nodes equipped with calibrated CO2 gas sensors and PM2.5 particulate matter detectors for continuous industrial environmental monitoring.
* **Wireless Communication:** Integrated MQTT-based telemetry with onboard data filtering and averaging algorithms to reduce noise and improve measurement accuracy.
* **Outcome:** Enabled real-time environmental monitoring with actionable insights, helping clients meet stringent environmental compliance standards.
![Carbon sensor](/static/assets/img/Carbon.png)
---

### 11. ⚙️ Split Capacitor Motor (SCM) Driver Design

* **Company:** Sabro Technologies
* **Role:** Electronics Engineer
* **Technology Stack:** ESP32, PWM Generation, Full Bridge Module

* Learned fundamental techniques for driving and controlling Split Capacitor Motors (SCM).
* Explored one-leg, two-leg, three-leg, and four-leg drive configurations — selected three-leg as optimal for the application.
* Utilized ESP32 to generate six PWM signals for driving the three-leg configuration.
* Conducted market research and identified an appropriate Full Bridge module; designed the PCB control board.

---

### 12. 📡 ESP32-S2 Voltage & Current Sensor Design

* **Technology Stack:** ESP32-S2, Proteus PCB Design, Analog Sensing

* Studied the fundamental hardware design requirements of the ESP32-S2 chip including flash and current specifications.
* Evaluated voltage and current sensor options for compatibility with ESP32-S2 ADC inputs.
* Created the full PCB layout in Proteus integrating the ESP32-S2 with voltage and current sensing circuits.
* Successfully assembled and tested the board, validating accurate sensor readings.

---

### 13. 🔧 Motor Driving Using STM32

* **Technology Stack:** STM32, STEVAL-IPM20B, Motor Control Workbench

* Gained working knowledge of STM32 communication methods, timers, and chip-specific commands.
* Identified and selected the STEVAL-IPM20B Intelligent Power Module for motor control application.
* Utilized Motor Control Workbench to conduct real-time tests on the compressor.
* Calibrated the compressor motor using STM32 for optimal performance across load ranges.
![STM32](/static/assets/img/stm32.jpg)

---

### 14. 🔋 PFC-Based Power Supply for 2KVA Inverters

* **Technology Stack:** PFC Circuit Design, PCB Layout, Power Quality

* Prioritized signal integrity and effective thermal management in PCB layouts for high-power inverter applications.
* Designed an advanced Power Factor Correction (PFC) circuit to elevate power quality within 2kVA inverters.
* Demonstrated proficiency in diagnosing and repairing faulty PCBs to ensure optimal functionality.
* Integrated optimized PCB designs, expert repair skills, and advanced PFC techniques, significantly improving inverter efficiency and reliability.

---

### 15. 🤖 MOSFET-Based H-Bridge Motor Driver

* **Technology Stack:** MOSFET H-Bridge, High-Power PCB Design

* Designed and developed high-power motor drivers utilizing MOSFETs for efficient and robust motor operation in electric vehicles, industrial machinery, and robotics.
* Selected MOSFETs as primary switching devices for their high switching speed, low on-resistance, and high current handling capability.
* Engineered circuits capable of handling high power levels while maximizing efficiency and minimizing switching losses.

---

### 16. 🎓 Electronic Attendance System with NFC ID Cards

* **Institution:** HITEC University (Final Year Project)
* **Technology Stack:** NFC, Microcontroller, Database Integration

* Developed an electronic attendance system incorporating NFC ID cards for efficient and precise tracking in schools, offices, and events.
* Implemented NFC technology for wireless communication between ID cards and the attendance reader, enabling seamless attendance recording.
* Programmed the system to read NFC cards, record attendance data, and store it in a dedicated database for processing and analysis.
* Covered hardware design, firmware development, and database integration.
![Attendance](/static/assets/img/Attendance.jpg)

---

### 17. 🤸 Two-Wheels Self-Balancing Robot

* **Technology Stack:** Gyroscope, Accelerometer, PID Control, Kalman Filter

* Developed a two-wheeled self-balancing robot capable of maintaining upright balance using sensor feedback and control algorithms.
* Utilized gyroscopes and accelerometers to detect tilt, adjusting motor speeds accordingly in real time.
* Implemented PID control and Kalman filter algorithms for stable and precise balancing.
* Covered mechanical design, electronics integration, software development, and control parameter tuning.

---

### 18. 🌱 Greenhouse Monitoring System

* **Technology Stack:** Multi-Sensor Array, Embedded Control, Automation

* Designed a real-time monitoring and control system for environmental parameters within a greenhouse.
* Utilized sensors to measure temperature, humidity, light intensity, soil moisture, and CO2 levels.
* Processed and analyzed data to maintain optimal plant growth conditions, triggering automated actions for ventilation, irrigation, or lighting as needed.

---

### 19. 🛰️ Adaptive Network Optimization via Reinforcement Learning

* **Company:** National University of Sciences and Technology (NUST)
* **Role:** Research Engineer & Master's Scholar
* **Technology Stack:** MATLAB, Simulink, Machine Learning, Q-Learning

* **Adaptive Intelligence:** Designed a custom network routing protocol integrated with a localized Q-learning reinforcement framework.
* **Autonomous Decisions:** Enabled network nodes to make adaptive, self-healing routing decisions based on dynamic traffic topology shifts and link quality metrics, validating performance increases through comprehensive MATLAB/Simulink modeling.
* **International Publication:** Peer-reviewed and officially published in MDPI Sensors. [Read the full paper](https://www.mdpi.com/1424-8220/21/12/4121/html).
