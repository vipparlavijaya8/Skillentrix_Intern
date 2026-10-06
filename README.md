# 🚦 Traffic Light Controller with Pedestrian Crossing Using Verilog HDL

## 📌 Project Overview

The **Traffic Light Controller with Pedestrian Crossing** is a digital system designed using Verilog Hardware Description Language (HDL) and a Finite State Machine (FSM). The controller manages traffic flow between a highway and a side road while providing a dedicated pedestrian crossing phase.

The system transitions between predefined states based on a timer and a pedestrian request input. During the pedestrian crossing phase, both highway and side-road traffic signals turn red, and the pedestrian WALK signal is activated.

This project demonstrates the practical application of FSM-based control logic, sequential digital design, RTL development, and simulation-based verification.

## 🎯 Objectives

* Design an FSM-based traffic light controller using Verilog HDL.
* Control highway and side-road traffic signals.
* Implement pedestrian crossing functionality.
* Manage signal transitions using a clock-driven timer.
* Verify the design through simulation in Xilinx Vivado.
* Understand RTL design and sequential circuit behavior.

## 🛠️ Technologies and Tools

* **Hardware Description Language:** Verilog HDL
* **Design Methodology:** Finite State Machine (FSM)
* **Simulation and Design Tool:** Xilinx Vivado
* **Verification Method:** Verilog testbench and waveform analysis
* **Design Analysis:** RTL schematic and power analysis

## ⚙️ System Inputs and Outputs

### Inputs

| Signal       | Description                                |
| ------------ | ------------------------------------------ |
| `clk`        | Clock signal that drives state transitions |
| `reset`      | Active-high asynchronous reset             |
| `pedestrian` | Input request for pedestrian crossing      |

### Outputs

| Signal           | Description                    |
| ---------------- | ------------------------------ |
| `highway[2:0]`   | Highway traffic light output   |
| `side_road[2:0]` | Side-road traffic light output |
| `ped_walk`       | Pedestrian WALK indicator      |

### Traffic Light Encoding

| Signal | Binary Encoding |
| ------ | --------------- |
| Red    | `3'b100`        |
| Yellow | `3'b010`        |
| Green  | `3'b001`        |

## 🔄 FSM Design

The controller consists of four states:

| State       | Highway Signal | Side-Road Signal | Pedestrian Signal |
| ----------- | -------------- | ---------------- | ----------------- |
| `HW_GREEN`  | Green          | Red              | STOP              |
| `HW_YELLOW` | Yellow         | Red              | STOP              |
| `SR_GREEN`  | Red            | Green            | STOP              |
| `PED_STATE` | Red            | Red              | WALK              |

### State Transition Description

1. **HW_GREEN:** Highway traffic is allowed to move while the side-road signal remains red.
2. **HW_YELLOW:** The highway signal changes to yellow before the controller proceeds to the next phase.
3. **SR_GREEN:** The highway signal turns red, and side-road traffic receives a green signal.
4. **PED_STATE:** When a pedestrian request is detected at the relevant transition, both vehicle signals remain red and the pedestrian WALK output is activated.
5. **Return to Traffic Control:** After the pedestrian phase, the controller proceeds to `SR_GREEN` and continues the traffic sequence.

The state transitions are controlled by the clock, timer, and pedestrian request input.

## 💻 Implementation Details

The Verilog design uses:

* A sequential `always` block triggered by the positive edge of the clock or reset.
* A state register to represent the current FSM state.
* A timer register to control phase durations.
* A `case` statement to implement the state-dependent output and transition logic.
* Non-blocking assignments for sequential updates.
* A separate testbench to stimulate the inputs and observe the outputs.

The implemented timer thresholds are 5 for `HW_GREEN`, 2 for `HW_YELLOW`, 5 for `SR_GREEN`, and 4 for `PED_STATE`. These values are clock-count thresholds in the RTL, not real-world seconds.

## 🧪 Simulation and Verification

The design includes a Verilog testbench that generates a clock, applies reset, changes the pedestrian request, and monitors the controller outputs.

### Verification Scenarios

* Verify the initial state after reset.
* Check the highway green-to-yellow transition.
* Verify the side-road green phase.
* Apply a pedestrian request and check the crossing phase.
* Confirm that both vehicle signals are red during pedestrian WALK.
* Observe the output transitions using simulation waveforms.

The project documentation includes Vivado simulation waveforms, an RTL schematic, console output, and power analysis.

## 📊 Design Results

The design was implemented using Verilog HDL and evaluated through simulation in Xilinx Vivado. The documented results include the simulation waveform, RTL schematic, console output, and power analysis.

The simulation-based approach helps examine FSM operation, traffic signal sequencing, and pedestrian crossing behavior.

## 🚀 Future Enhancements

* Add a pedestrian countdown timer.
* Synchronize and debounce the pedestrian request input.
* Add vehicle detection for adaptive traffic control.
* Extend the controller to a four-way intersection.
* Add emergency vehicle priority.
* Verify additional operating scenarios using an expanded testbench.

## 📚 Key Learning Outcomes

* Understanding FSM-based digital system design.
* Writing and organizing synthesizable Verilog RTL.
* Designing clock-driven sequential logic.
* Developing testbenches for functional verification.
* Interpreting simulation waveforms and RTL schematics.
* Exploring power analysis in a digital design workflow.

## 👩‍💻 Author

**Vijaya Lakshmi**
Electronics and VLSI Technology
SRK Institute of Technology
Interested in Digital Design and Design Verification

## ⭐ Conclusion

The Traffic Light Controller with Pedestrian Crossing demonstrates the use of an FSM to coordinate highway traffic, side-road traffic, and pedestrian movement. The Verilog implementation and Vivado simulation provide practical experience in RTL design, sequential logic, and simulation-based verification.

---

**Keywords:** Verilog HDL, FSM, Traffic Light Controller, Pedestrian Crossing, RTL Design, Digital Electronics, Xilinx Vivado, Testbench, Simulation, Design Verification.
