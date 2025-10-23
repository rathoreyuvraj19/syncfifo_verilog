# 🧮 Synchronous FIFO (sync_fifo)
> A parameterizable synchronous FIFO buffer designed and verified using VHDL in Xilinx Vivado.

---

## 📚 Table of Contents
- [About](#-about)
- [Features](#-features)
- [Design Overview](#-design-overview)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Prerequisites](#prerequisites)
- [Setup and Simulation](#setup-and-simulation)
- [Generics and I/O Description](#-generics-and-io-description)
- [Verification](#-verification)
- [Results](#-results)
- [License](#-license)
- [Acknowledgements](#-acknowledgements)

---

## 📖 About
This project implements a **synchronous FIFO** memory that buffers data between two subsystems operating on the **same clock domain**. It supports configurable **data width** and **FIFO depth**, with proper **full** and **empty** flag generation. The design is written in **VHDL** and is compatible with **Xilinx Vivado** for synthesis and simulation.

---

## ✨ Features
- Fully synchronous read and write operations
- Parameterizable data width and depth
- Simultaneous read/write support
- Proper `full`, `empty`, and `data_count` flag generation
- Synthesizable and simulation-friendly
- Verified with a self-checking testbench

---

## 🧠 Design Overview
The FIFO uses a **circular buffer** with two pointers:
- **Write Pointer (`wr_ptr`)** — increments on valid write
- **Read Pointer (`rd_ptr`)** — increments on valid read
- **Full/Empty Logic** — compares pointers to determine status
  +---------------------------+
  | SYNC FIFO |
  | +---------------------+ |
  | | Memory Array | |
  | +---------------------+ |
  | ↑ wr_ptr rd_ptr ↑
  | FULL EMPTY COUNT |
  +---------------------------+
  
---

## 📁 Project Structure
```bash
├── src/
│   ├── sync_fifo.vhd         # FIFO design
│   └── fifo_pkg.vhd          # Constants/package (optional)
├── sim/
│   ├── tb_sync_fifo.vhd      # Testbench
│   └── sim.do                # Simulation script
├── docs/
│   ├── block_diagram.png     # Architecture diagram
│   └── timing_waveform.png   # Waveform capture
├── scripts/
│   └── create_project.tcl    # Vivado automation script
├── README.md
└── LICENSE


