# Microwatt-Controlled GPIO Pattern Generator

##  Project Summary

This project proposes the development of a lightweight, programmable GPIO pattern generator controlled by the Microwatt soft-core CPU. The goal is to enable real-time digital waveform generation—such as square waves, PWM signals, and custom bit sequences—using memory-mapped control registers. The design will be integrated with the OpenFrame harness chip and hardened using the OpenLane flow for SKY130, making it suitable for tapeout and deployment in low-power embedded systems.

Unlike traditional designs that rely on external microcontrollers or dedicated timer peripherals, this project embeds waveform logic directly into the Microwatt ecosystem. This demonstrates how open-source RISC architectures can be extended for real-time control applications, bridging the gap between computation and physical interfacing.

---

##  Motivation

Open-source silicon platforms have made significant strides in computation and acceleration, but real-time control applications—such as robotics, sensor interfacing, and embedded automation—remain underserved. Most open-source CPU cores lack simple, reusable modules for waveform generation that integrate cleanly with GPIO and memory-mapped I/O.

This project addresses that gap by creating a minimal yet powerful waveform generator that can be configured and triggered by Microwatt. It serves as a proof-of-concept for using open-source RISC cores in control-centric applications, which are critical for edge computing and low-power environments.

Additionally, the project is designed to be achievable within a limited time budget (2 hours/week), making it ideal for solo developers or students participating in the Microwatt Design Challenge.

---

##  Core Features

- **Memory-Mapped Control Interface**  
  A set of registers accessible by Microwatt to configure waveform parameters such as frequency, duty cycle, and pattern type.

- **Configurable Waveform Generator**  
  A Verilog module that generates digital waveforms using counters and finite state machines (FSMs). Supports square wave, PWM, and custom bitstream modes.

- **GPIO Output Compatibility**  
  Outputs are routed to GPIO pins defined in the OpenFrame harness, enabling physical signal generation for external devices.

- **RTL Simulation and Verification**  
  A testbench will verify waveform timing, edge transitions, and register control logic using open-source simulation tools.

- **SKY130 Hardening via OpenLane**  
  The design will be synthesized, placed, and routed using OpenLane, ensuring compatibility with the SKY130 process node.

- **OpenFrame Integration**  
  The final hardened block will be wrapped with the OpenFrame padframe and power macros, ready for tapeout submission.

---

##  Implementation

### 1. RTL Design (`gpio_wavegen.v`)
- Implements a counter-based waveform generator.
- Supports runtime configuration of frequency and duty cycle.
- Uses FSM to manage waveform state transitions.

### 2. Microwatt MMIO Interface (`wavegen_mmio.vhdl`)
- Defines memory-mapped registers for waveform control.
- Integrates with Microwatt’s bus architecture.
- Allows software-driven waveform updates.

### 3. Simulation (`wavegen_tb.v`)
- Verifies waveform output under various configurations.
- Checks edge timing, duty cycle accuracy, and register responsiveness.

### 4. OpenLane Flow (`config.json`)
- Synthesizes and hardens the design using SKY130 PDK.
- Includes floorplanning, power routing, and DRC/LVS checks.
- Generates GDS and DEF files for tapeout.

### 5. OpenFrame Wrapper
- Connects hardened block to OpenFrame GPIO and power pads.
- Ensures compatibility with Caravel/Caravan-style padframes.
- Uses `vccd1_connection` and `vssd1_connection` macros for power.

---

##  Expected Outcome

- A functional, tapeout-ready GPIO waveform generator controlled by Microwatt.
- Verified waveform output on physical GPIO pins with configurable parameters.
- Demonstration of real-time control using open-source RISC architecture.
- A reusable module for future open-source silicon projects, including robotics, sensor drivers, and embedded automation.
- Full documentation, simulation results, and integration flow submitted to the Microwatt Design Challenge.

---


##  License

MIT License © 2025 Dheeraj Reddy

