# SHORTCIRCUITSOMOPHERS
#  4-Bit ALU — NI Multisim

A 4-bit ALU designed in NI Multisim supporting add/sub and bitwise logic operations with decimal display output.
##  Overview

This project implements a **4-bit Arithmetic Logic Unit (ALU)** designed in **NI Multisim** using TTL ICs.
The ALU supports arithmetic and bitwise logic operations selected using two control lines placed at the **top of the schematic**.

---

##  Operations (Select Lines)

| S1 S0  | Operation                    |
| ------ | ---------------------------- |
| **00** | Add / Sub (depends on `Cin`) |
| **01** | Bitwise AND                  |
| **10** | Bitwise OR                   |
| **11** | Bitwise XOR                  |

**Arithmetic Mode (S1S0 = 00)**

* `Cin = 0` → Addition
* `Cin = 1` → Subtraction (two’s complement)

---

##  Decimal Display Logic

To generate decimal output, a **three-stage correction logic** is used:

* **Stage-1:** If result ≥ 10 → add 6
* **Stage-2:** If result ≥ 20 → add 6
* **Stage-3:** If result ≥ 30 → add 6

If the condition is not satisfied, `0000` is added at that stage.

Each stage produces a carry output.
The three stage carries along with the original ALU carry-out are treated as **four single bits**, which are added together to form the **tens digit**.
The corrected lower 4 bits drive the **ones digit** display.

---

##  Main Components

* 7483 — 4-bit Adder
* 74LS86 — XOR (Subtraction & XOR operation)
* 74LS08 — AND gates
* 7432 — OR gates
* 74153 — Multiplexer
* HEX / Seven-Segment Displays

---

##  Inputs & Outputs

**Inputs:**
`A[3:0]`, `B[3:0]`, `Cin`, `S1 S0`

**Outputs:**
Decimal result displayed on two digits (tens & ones).

---

##  Notes

* Designed using gate-level and IC-level logic.
* Select lines are positioned at the top for easier simulation control.
* Focuses on practical digital design using basic TTL components.

---
