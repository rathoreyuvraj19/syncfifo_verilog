# 🧮 Synchronous FIFO (sync_fifo)

> A parameterizable synchronous FIFO (First-In-First-Out) buffer designed and verified using VHDL in Xilinx Vivado.

---

## 🧩 Table of Contents
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

This project implements a **synchronous FIFO** memory that buffers data between two subsystems operating on the **same clock domain**.  
It supports parameterizable **data width** and **FIFO depth**, with proper **full** and **empty** flag generation.

The design is written in **VHDL** and is compatible with **Xilinx Vivado** for synthesis and simulation.

---

## ✨ Features
- Fully synchronous read and write operations  
- Parameterizable data width and depth  
- Supports simultaneous read/write in same clock cycle  
- Proper `full`, `empty`, and `data_count` flag generation  
- Cleanly synthesizable and simulation-friendly  
- Verified through a self-checking testbench

---

## 🧱 Design Overview

The FIFO uses a **circular buffer architecture** implemented with a memory array and two pointers:
- **Write Pointer (wr_ptr)** — increments on valid write  
- **Read Pointer (rd_ptr)** — increments on valid read  
- **Full/Empty Logic** — determines FIFO status using pointer comparison  

```text
            +---------------------------+
i_clk  ---> |                           |
i_rst  ---> |        SYNC FIFO          |
i_wr_en --->|                           |
i_rd_en --->|      +---------------+    |
i_data  --->| ---> | Memory Array  | --->|---> o_data
             |      +---------------+    |
             |     ^             ^       |
             |  wr_ptr        rd_ptr     |
             +---------------------------+
                  | FULL | EMPTY | COUNT |
