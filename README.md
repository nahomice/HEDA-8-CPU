# HEDA-8: High-Efficiency Digital Architecture (8-Bit CPU)

![Logisim](https://img.shields.io/badge/Simulation-Logisim_2.7.1-orange)
![Architecture](https://img.shields.io/badge/Architecture-Von_Neumann-blue)
![Grade](https://img.shields.io/badge/Grade-48%2F50_Distinction-brightgreen)

The **HEDA-8** is a fully functional 8-bit CPU Datapath and Control Unit designed and simulated from scratch in Logisim. It implements a Von Neumann architecture with a hardwired Control Unit capable of executing a complete Fetch-Decode-Execute cycle.

## 🚀 Key Features

*   **8-Bit Shared Bus Architecture:** Utilizes Tri-State Logic (Controlled Buffers) to manage data flow between components without signal contention.
*   **Custom ALU:** A parallel-processing Arithmetic Logic Unit supporting 10 operations (Math, Logic, Shifts) with real-time Status Flags (Zero, Negative, Overflow).
*   **Register File:**
    *   4 General Purpose Registers (A, B, C, D)
    *   4 Special Purpose Registers (PC, IR, MAR, MBR)
*   **Integrated Memory:** 256-Byte RAM module with manual and automatic addressing modes.
*   **Hardwired Control Unit:** A Finite State Machine (FSM) utilizing a Sequence Counter and Decoder Matrix to automate instruction execution.

## 🛠️ Architecture Overview

The system is built on three main layers:
1.  **Execution Layer:** ALU and temporary Latches.
2.  **Memory Layer:** RAM, Memory Address Register (MAR), and Memory Buffer Register (MBR).
3.  **Control Layer:** A logical matrix mapping OpCodes and Time Steps (T0-T4) to specific control signals.

### The Datapath
![CPU Overview](screenshots/cpu_overview.png)
*The complete HEDA-8 Datapath showing the Vertical Bus (Right) connecting Registers (Center) and Memory (Left).*

## 📋 Instruction Set

The CPU supports the following Micro-Operations based on a 3-bit OpCode:

| OpCode | Mnemonic | Operation | Description |
| :--- | :--- | :--- | :--- |
| `000` | **ADD** | `A = A + B` | Add Register B to A |
| `001` | **SUB** | `A = A - B` | Subtract Register B from A |
| `010` | **AND** | `A = A & B` | Bitwise AND |
| `011` | **OR** | `A = A \| B` | Bitwise OR |
| `100` | **NOT** | `A = ~A` | Bitwise NOT (Invert) |
| `101` | **SHL** | `A = A << B` | Shift Left (by value in B) |
| `110` | **SHR** | `A = A >> B` | Shift Right (by value in B) |
| `111` | **INC** | `A = A + 1` | Increment Register A |

## 💻 How to Run

**⚠️ Important:** This project was built in **Logisim 2.7.1** (Standard). Opening it in *Logisim Evolution* (v3.0+) may break wire connections due to grid handling differences.

1.  **Download Logisim 2.7.1**: [Link to Official Site](http://www.cburch.com/logisim/)
2.  **Clone this Repository**:
    ```bash
    git clone https://github.com/[YOUR-USERNAME]/HEDA-8-CPU-Architecture.git
    ```
3.  Open `HEDA8_CPU_Final.circ` in Logisim.
4.  **Enable Simulation:** Go to `Simulate` -> `Simulation Enabled`.
5.  **Start the Clock:** Press `Ctrl + K` (or `Cmd + K` on Mac) to start the automatic Fetch-Execute cycle.

## 🧪 Verification

The system was verified by calculating **5 + 2 = 7** via memory fetch.
1.  **Fetch:** Instruction retrieved from RAM.
2.  **Execute:** Data loaded from Reg A (5) and Reg B (2).
3.  **Result:** Bus displays `07`, stored back to Register A.

![Verification](screenshots/verification_7.png)

## 📄 Documentation

For a deep dive into the engineering choices, timing diagrams, and troubleshooting logs (solving Bus Contention and Red Wire errors), please read the full report:
[📄 Read the Design Documentation (PDF)](docs/HEDA8_Design_Report.pdf)

## 👤 Author

**[Nahom Wondale]** - *Lead Architect & Engineer*
*   Designed ALU Logic & Flags
*   Implemented Tri-State Bus System
*   Designed Hardwired Control Unit
*   Performed all Testing & Verification

---
*Educational Project for [Addis Ababa Niveirsity/Computer Architechture & Organization]*
