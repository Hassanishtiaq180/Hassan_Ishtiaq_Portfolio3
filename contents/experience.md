
# 🧪 Detailed Engineering & Project Experience

I focus on high-density power converter topologies, advanced motor control algorithms, industrial IoT master architectures, and robust multi-board product engineering.

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

```text
[ Incoming AC / Sagging Rail ] ---> [ WMZ11A PTC ] ---> [ 1N4752A Zener (33V) ] ---> [ PC817C Optocoupler Loop ] ---> [ Rx/Tx UART ]

```

> **Engineering Deep-Dive:** Under peak compressor draw, severe voltage sags triggered a thermal cascade inside the **WMZ11A** loop protection PTC thermistor, dramatically driving up its resistance. This resistance spike choked the current loop, starving the **PC817C** optocoupler's internal LED and corrupting the UART data stream.
> By recalculating the dynamic current budget, the circuit was optimized by adjusting the series resistance network and sizing a **1N4752A (33V, 1W)** Zener regulator to clamp loop voltages safely above the saturation threshold. This modification maintained an optimal collector saturation current ($I_{C(\text{sat})}$) through the optocoupler's photo-transistor, ensuring clean, jitter-free logic-level transitions even during continuous 198V AC voltage sags.

![Description of the hardware or PCB layout](/static/assets/img/Test_Bench.jpeg)
---

### 2. 🔥 Industrial Heat Pump Drive & Safety Control Infrastructure

* **Company:** Enertia Pvt Ltd
* **Timeline:** 10/05/2025 – 05/12/2025
* **Role:** Lead Electronics Engineer
* **Status:** Commercialized & Deployed at Scale into the Industrial Market

#### A. High-Reliability Power Distribution & Layout Hardening

* Designed a ruggedized power management layer capable of stepping down volatile industrial mains supplies into tightly regulated control rails.
* Implemented robust hardware-level protection networks featuring Metal Oxide Varistors (MOVs) and Transient Voltage Suppressors (TVS) rated to absorb massive inductive line kicks.
* Programmed analog comparator interrupt service routines (ISRs) on the host microcontroller to achieve sub-millisecond trip times for hardware-level **Overcurrent (OC), Overvoltage (OV), and Undervoltage (UV)** state monitoring, immediately disabling gate drivers during overload or brownout states to protect sensitive switching topologies under load-stall conditions.

#### B. Gas & Ignition Management

* Developed a complete, software-governed automatic gas control manifold matrix featuring integrated digital solenoid valve drivers.
* Designed an automatic multi-strike high-voltage electronic sparking ignition module utilizing zero-cross ignition timing.
* Implemented localized magnetic and optical isolation barriers to completely decouple thousands of volts of high-frequency spark noise from sensitive low-voltage logic traces while incorporating optical/thermal flame rectification monitoring to safely verify ignition states.

#### C. Failsafe Operations & "No Gas" Vacuum Protection

* Developed a firmware-level fault handler designed to calculate real-time thermodynamic efficiency trends across distributed sensor nodes.
* Authored a hardware-software **"No Gas Protection"** interlock protocol: if the fuel manifold pressure or temperature changes reveal a lack of gas supply during an active ignition command (such as fuel exhaustion), the firmware executes a priority shutdown sequence. This protocol immediately cuts drive current to the compressor and isolates the fuel supply line, preventing a destructive high-vacuum state from compromising mechanical seals.
![Description of the hardware or PCB layout](/static/assets/img/Heat_Pumo_table.jpeg)
---

### 3. 💧 Touch-Interactive Smart Water Dispenser Platform

* **Company:** Enertia Pvt Ltd
* **Timeline:** 05/02/2025 – 07/08/2025
* **Role:** Lead Electronics Engineer
* **Architecture:** Multi-Layered Commercial-Grade Infrastructure

#### A. Concurrence & Core Control

* Utilized an ESP32-S3 running FreeRTOS to manage asynchronous tasks across capacitive touch UI inputs, multi-pump bottom-bottle automated extraction loops, and rapid cooling/heating thermal cycles.
* Developed modular software routines to balance real-time user input responses against precision thermal metrics, ensuring zero display lag while regulating high-power inductive heating coils.

#### B. Fluidics & EMI Mitigation

* Integrated high-precision hall-effect flow meters for closed-loop volumetric control alongside anti-scald digital locks.
* Designed a multi-source automated extraction fluidics manifold with integrated carbonation capabilities.
* Implemented distributed RC snubbers, freewheeling flyback diodes, and specialized PCB layout isolation routing to completely mitigate high-frequency electromagnetic interference (EMI) generated by inductive pump switching near the capacitive touch sensor plane.
![Description of the hardware or PCB layout](/static/assets/img/Dispenser_PCB.png)
---

### 4. ⚡ Custom HVAC Control Board & Inverter Stage

* **Company:** Sabro Technologies
* **Role:** Electronics Engineer
* **Technology Stack:** Infineon IMC102T, ESP32, PFC, Single-Shunt Topology
* **System Design:** Designed and developed a comprehensive 220VAC HVAC control system integrating active Power Factor Correction (PFC) boost infrastructure and a single-shunt current feedback loop for phase current reconstruction.
* **Component Coordination:** Configured an Infineon IMC102T motor controller to operate as a dedicated real-time motor drive co-processor, pairing it with an ESP32 master microcontroller that coordinates electronic expansion valve (EEV) stepper motor control, system-wide diagnostics, and communication routing.

![Description of the hardware or PCB layout](/static/assets/img/IPM_drive_new.jpeg)

---

### 5. 🏎️ Field-Oriented Control (FOC) & Motor Drivers

* **Company:** Sabro Technologies
* **Role:** Electronics Engineer
* **Technology Stack:** Infineon iMOTION, MCEWizard, MCEDesigner, Space Vector PWM (SVPWM)
* **Algorithm Optimization:** Configured and tuned Field-Oriented Control (FOC) algorithms for permanent magnet synchronous motors (PMSM) using Infineon iMOTION hardware. Developed single-shunt current reconstruction topologies to map rotor position accurately without external hall sensors.
* **Control Loop Tuning:** Specialized in analyzing and tuning current regulator bandwidth, optimizing proportional-integral ($K_p/K_i$) loop gains, and establishing robust UART/Modbus communications with real-time Motion Control Engines (MCE) to guarantee stable torque generation under highly dynamic load steps.
![Description of the hardware or PCB layout](/static/assets/img/Inverter.png)
---

### 6. 🌐 Industrial IoT & Robust Embedded Firmware

* **Company:** Sabro Technologies
* **Role:** Electronics Engineer
* **Technology Stack:** ESP32-S3, STM32, C/C++, Secure Boot, OTA Pipelines
* **Firmware Pipelines:** Developed robust, field-deployable firmware pipelines utilizing ESP32-S3 and STM32 platforms.
* **Reliability Implementations:** Implemented custom dual-stage bootloaders, secure over-the-air (OTA) firmware update structures with fallback partition redundancy, and advanced low-power state management utilizing hardware watchdog timers to ensure seamless remote telemetry recovery during field brownout scenarios.
![Description of the hardware or PCB layout](/static/assets/img/Dubai_taxi_PCB.png) 
![Description of the hardware or PCB layout](/static/assets/img/Dubai_taxi_PCB_proteus.png) 
![Description of the hardware or PCB layout](/static/assets/img/Dubai_taxi_PCB_proteus_PS.png) 

---

### 7. 🔬 Heterogeneous Power Stage R&D

* **Company:**  Sabro Technologies  R&D Lab
* **Role:** Electronics Engineer
* **Technology Stack:** Wide-Bandgap Semiconductors (GaN & SiC), Altium Designer, Thermal Modeling
* **Next-Gen Topologies:** Researched and drafted advanced architectures for heterogeneous power stages using next-generation wide-bandgap semiconductors (Gallium Nitride and Silicon Carbide) targeted for 400V-class high-efficiency inverters.
* **Dynamic Balancing:** Focused on balancing gate-drive timing dynamics, parasitic loop inductance reduction, and asymmetric thermal distribution across mixed-device legs to bypass the silicon efficiency plateau.
![Description of the hardware or PCB layout](/static/assets/img/Power_Supply.jpg)
---

### 8. ⛽ Real-Time Secure Fuel Telemetry & Theft Prevention Node

* **Company:** Sabro Technologies (Industrial Automation Division)
* **Role:** Electronics Engineer
* **Technology Stack:** Ultra-Low-Power ESP32, Encrypted MQTT, Cellular Telemetry
* **Telemetry Processing:** Implemented ultra-low-power ESP32 sensor nodes driven by high-accuracy pulse-output flow calculation algorithms to monitor fuel levels and prevent transport tampering.
* **Encrypted Communication:** Structured an edge-to-cloud telemetry infrastructure utilizing hardware-accelerated encrypted MQTT packets over cellular/Wi-Fi links to transmit secure volume logs, executing deep sleep profiles and hardware watchdog timers to handle sustained brownout scenarios.
![Description of the hardware or PCB layout](/static/assets/img/Fuel.png)
![Description of the hardware or PCB layout](/static/assets/img/Carbon.png)
---

### 9. 🚖 Automotive Ruggedized Power Supply & Signage Controller

* **Company:** Sabro Technologies
* **Role:** Electronics Engineer
* **Technology Stack:** DC-DC Buck Topologies, Thermal Management, ISO 16750 Standards
* **DC-DC Buck Architecture:** Engineered a high-efficiency DC-DC buck converter topology stepping down highly noisy 12V automotive battery lines to highly regulated 5V and 3.3V logic rails, sustaining continuous 3A+ loads.
* **Environmental Hardening:** Applied stringent thermal mapping to sustain prolonged 85°C ambient operational thresholds and engineered trace spacing and vibration dampening layouts satisfying ISO 16750 standards.

---

### 10. 🛰️ Adaptive Network Optimization via Reinforcement Learning

* **Company:** National University of Sciences and Technology (NUST)
* **Role:** Research Engineer & Master's Scholar
* **Technology Stack:** MATLAB, Simulink, Machine Learning, Q-Learning
* **Adaptive Intelligence:** Designed a custom network routing protocol integrated with a localized Q-learning reinforcement framework.
* **Autonomous Decisions:** Enabled network nodes to make adaptive, self-healing routing decisions based on dynamic traffic topology shifts and link quality metrics, validating performance increases through comprehensive MATLAB/Simulink modeling environments.
* **International Publication:** This research was peer-reviewed and officially published in MDPI Sensors. Read the full paper here: [MDPI Sensors Journal Paper](https://www.google.com/search?q=https://www.mdpi.com/1424-8220/21/12/4121/html).
