# 🔌 Microwatt-Controlled GPIO Pattern Generator

## 🧠 Overview
This project implements a lightweight GPIO pattern generator controlled by the Microwatt soft-core CPU. It leverages the OpenFrame harness chip to output programmable digital waveforms—such as square waves, PWM signals, or custom bit sequences—via GPIO pins.

Designed for the [Microwatt Design Challenge](https://chipfoundry.io/challenges/microwatt), this project emphasizes simplicity, reproducibility, and low-power digital control.

---

## 🎯 Objectives
- ✅ Use Microwatt to configure and trigger waveform patterns.
- ✅ Map control registers to GPIO outputs via memory-mapped I/O.
- ✅ Harden the design using OpenLane for SKY130 compatibility.
- ✅ Integrate with OpenFrame wrapper for tapeout readiness.

---

## 🛠️ Repository Structure

```bash
chipfoundry_microwatt_gpio/
├── rtl/                    # Verilog modules for pattern generator
│   └── gpio_wavegen.v
├── microwatt_integration/ # Memory-mapped control logic
│   └── wavegen_mmio.vhdl
├── openlane/              # OpenLane flow configs
│   └── config.json
├── testbench/             # Simulation files
│   └── wavegen_tb.v
├── docs/                  # Diagrams and documentation
│   └── architecture.md
└── README.md              # This file
