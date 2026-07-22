# Adjustable CC/CV Buck Converter

An open-source, high-efficiency DC-DC step-down buck converter schematic designed in KiCad. It features **Constant Voltage (CV)** and **Constant Current (CC)** control, making it ideal for battery charging, LED driving, and benchtop power supply projects.

---

## ⚡ Key Features

* **Core IC:** XL4015 Step-Down DC-DC Converter (180 kHz PWM).
* **Control Modes:**
  * **Constant Voltage (CV):** Precision output voltage regulation using `RV2`.
  * **Constant Current (CC):** Adjustable current limit control using `RV1`.
* **Precision Voltage Reference:** Built-in `L78L05` + `TL431` voltage reference circuit for stable current limit thresholds.
* **Low-side Current Sensing:** Precision $0.05\ \Omega$ sense resistor monitored via an `LM358` dual op-amp.
* **Status Indicators:** Integrated onboard LEDs for CC/CV active state indication.
* **Protection:** Screw terminal connectors and input fuse protection.
* **Wattage:**  75W with heatsinks and airflow.
---

## Working Principle

### 1. Main Switching Regulator Stage XL4015 (U2): 
A 180 kHz fixed-frequency step-down PWM DC/DC converter capable of driving up to a 5A load.
  #### ● L1 (40uH) & D1 (Schottky Diode): 
  Standard buck topology output LC filtering network and freewheeling diode.
  #### ● C2, C5, C6: 
  Input and output bulk decoupling capacitors to smooth out ripple voltage.
  ### 2. Voltage Regulation (CV Mode)
  The FB (Feedback, Pin 2) pin of the XL4015 expects a reference voltage (typically around 1.25 V).
  #### ● RV2 (10k) & R4/R5:
  RV2 acts as a feedback potentiometer tied to the output line, allowing you to manually adjust and set the target output voltage.
### 3. Current Control & Sensing Stage (CC Mode)
  #### ● Current Sense Resistor (R6 - 0.05ohm): 
  Connected in series with the low-side return ground, generating a small proportional voltage drop based on load current (Vsense = Iout X   0.05ohm).
  ### 4. Precision Reference (U1, U3, RV1):
   #### ● U1 (L78L05): 
   Standard linear regulator generating a clean 5V rail.
   #### ● U3 (TL431): 
   Precision adjustable reference IC producing a ultra-stable voltage.
   #### ● RV1 (10k Potentiometer): 
   Sets the current limit reference threshold for the operational amplifier.
   ### ● Op-Amp Control (U4 - LM358): 
   #### ● U4A : 
   Compares current sense voltage against current reference set by RV1. When current exceeds the threshold, U4A pulls down the feedback pin via D2, forcing the XL4015 to dial back output duty cycle (Constant Current limiting mode).
   #### ● U4B:
   Drives indicator LEDs (D3 / D4) to visually indicate status (e.g., Constant Voltage mode vs. Constant Current/Charging mode).

 ## ● Here is a well labeled diagram of the circuit schematic:
 
<img width="2311" height="1270" alt="image" src="https://github.com/user-attachments/assets/3d25254c-aefd-4925-bf51-2ecaeffdcef6" />

## ● PCB(First Copper Layer):

<img width="1200" height="1138" alt="image" src="https://github.com/user-attachments/assets/439b3304-a946-438d-a78f-92be4ca103df" />

## ● PCB(Second Copper Layer):

<img width="1108" height="1112" alt="image" src="https://github.com/user-attachments/assets/9cd5587f-c5c7-47e8-97d5-40ad53769707" />

## ● Rendered 3D Model(Angled View):

<img width="2464" height="1600" alt="image" src="https://github.com/user-attachments/assets/31e6aacb-f1a0-4482-8129-a25e4bda3b89" />

## ● Rendered 3D Model(Top View):

<img width="2464" height="1600" alt="image" src="https://github.com/user-attachments/assets/fbabffb7-ec2f-457e-a284-3257a5ea5f68" />

## ● Rendered PCB(Front):

<img width="1444" height="1459" alt="image" src="https://github.com/user-attachments/assets/4aa2bf4e-bc8b-4b34-8f63-a6ebae07a0e4" />

## ● Rendered PCB(Back):

<img width="1535" height="1459" alt="image" src="https://github.com/user-attachments/assets/b715ab25-dbf9-4971-9ea9-699260a69441" />

### ● Repository Structure

```
├── docs/                   # Datasheet of ICs used
├── manufacturing/          # Gerbers & BOM
│   ├── gerbers/            # Gerber and drill files for PCB fabrication
│   ├── bom/                # Bill of Materials (.csv )
├── ZVS.kicad_pcb  # KiCad PCB Layout file
├── ZVS.kicad_sch  # KiCad Schematic file
├── ZVS.kicad_pro  # KiCad Project file
└── README.md               # This file
 #Adjustable CC/CV buck converter
```

### ● Authored by:

#### ---------------------------------------------------------Bharat Sati----------------------------------------------------------------------------

### ● License:

####
