# Traffic Light Controller using FSM

## Overview
This project implements a **Traffic Light Controller** using a **Finite State Machine (FSM)** in Verilog. The controller manages traffic signals for a **highway** and a **small road**, using a sensor input to detect vehicle presence on the small road. The FSM ensures smooth transitions between the different traffic light states while adhering to real-world traffic rules.

## Features
- **Two traffic signals:** One for the **highway** and one for the **small road**.
- **FSM-based control:** Ensures proper sequencing of green, yellow, and red signals.
- **Sensor-based operation:** The small road signal turns green only if a vehicle is detected.
- **State transition delays:** Implements realistic delays for transitioning from **Green → Yellow → Red**.

## FSM States
The FSM consists of **five states:**

| State | Description |
|-------|------------|
| S0 | Highway: Green, Small Road: Red (Default state) |
| S1 | Highway: Yellow, Small Road: Red |
| S2 | Highway: Red, Small Road: Red |
| S3 | Highway: Red, Small Road: Green (If a vehicle is detected) |
| S4 | Highway: Red, Small Road: Yellow |

## State Transitions
1. **S0 → S1:** If a vehicle is detected on the small road, the highway signal turns **yellow**.
2. **S1 → S2:** After `G2YDELAY` cycles, the highway signal turns **red**.
3. **S2 → S3:** After `Y2RDELAY` cycles, the small road signal turns **green**.
4. **S3 → S4:** If no vehicle is detected, the small road signal turns **yellow**.
5. **S4 → S0:** After `G2YDELAY` cycles, the small road signal turns **red**, and the highway signal turns **green**.

## Verilog Implementation
The FSM is implemented using a **state register (`state`)** and a **next state logic (`next_state`)**. The traffic signals are controlled based on the current state.

### **Inputs & Outputs**
- **Inputs:**
  - `clk` (Clock signal)
  - `clr` (Reset signal)
  - `sensor` (Vehicle detection on small road)
- **Outputs:**
  - `highway` (Traffic light for highway: `RED`, `YELLOW`, `GREEN`)
  - `small_road` (Traffic light for small road: `RED`, `YELLOW`, `GREEN`)

## Simulation & Testing
- **Test the FSM using a Verilog testbench.**
- **Vary the sensor input** to check transitions.
- Observe the **waveforms in a simulator (ModelSim/Xilinx Vivado)**.
- Verify correct **state transitions and delays**.

## Conclusion
This FSM-based traffic light controller ensures **efficient traffic flow**, reducing waiting time for vehicles on the small road while prioritizing the highway. The design can be extended to **multi-road intersections** and integrated with **smart traffic systems**.

---
**Author:** Aneket Burman  
**Date:** March 2025  
**Tools Used:** Verilog, ModelSim, Xilinx Vivado  
