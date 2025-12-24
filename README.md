# Network-on-Chip-NoC-Verilog-RTL-Implementation
Verilog RTL implementation of a packet-switched Network-on-Chip with input buffering, virtual channel allocation, switch allocation, and crossbar-based routing.

---

## 📌 Overview

This repository contains a **modular and synthesizable Verilog RTL implementation of a Network-on-Chip (NoC)**.
The design models a **packet-switched NoC router with virtual channels, switch allocation, and crossbar-based data movement**, suitable for academic study, RTL practice, FPGA simulation, and SoC interconnect exploration.

The implementation closely follows **classic NoC micro-architecture concepts** such as:

* Input buffering
* Virtual Channel (VC) allocation
* Switch allocation
* Switch traversal
* Output buffering

---

## 🧠 Key Features

* Packet-based NoC communication
* **Input & output buffering**
* **Virtual Channel (VC) allocation**
* **Switch allocator & crossbar**
* Parameterized and modular RTL
* Clean separation of datapath and control
* Synthesizable Verilog (no vendor primitives)

---

## 🏗️ NoC Router Micro-Architecture

Each router consists of the following pipeline stages:

1. **Input Unit**

   * Packet reception
   * Buffering
   * Route computation

2. **Virtual Channel Allocation (VA)**

   * Arbitration among competing packets
   * VC availability checking

3. **Switch Allocation (SA)**

   * Grants switch access per cycle

4. **Switch Traversal (ST)**

   * Data transfer through crossbar

5. **Output Unit**

   * Output buffering
   * Flow control signaling

---

## 📂 Repository Structure

```
NoC-Verilog/
│
├── Buffer.v                  # FIFO buffer for flits
├── Counter.v                 # Generic counters
├── CrossBar.v                # Crossbar switch fabric
├── input_Unit.v              # Input port logic
├── output_unit.v             # Output port logic
├── Output_Buffer_availability.v
│
├── Route_Func.v              # Routing computation logic
├── Router.v                  # Top-level router module
├── Network.v                 # NoC network integration
├── Process_Node.v            # Processing node interface
│
├── VC_Alloc.v                # Virtual Channel allocation
├── S_Alloc.v                 # Switch allocation
├── set_Alloc.v               # Allocation setup logic
├── Select_gen.v              # Grant selection logic
│
├── ST.v                      # Switch traversal stage
├── ST_Controller.v           # ST control FSM
│
├── Packet_gen.v              # Packet generator
├── Packet_recv.v             # Packet receiver
├── out_en_gen.v              # Output enable generation
│
├── Test.v                    # Testbench
└── README.md
```

---

## ⚙️ Design Highlights

### 🔹 Routing

* Deterministic routing (via `Route_Func.v`)
* Easily extensible to adaptive routing

### 🔹 Flow Control

* Credit / availability-based output buffer checking
* Prevents buffer overflow

### 🔹 Arbitration

* VC-level arbitration
* Switch-level arbitration
* Fairness logic via select generators

### 🔹 Switch Fabric

* Centralized **crossbar (CrossBar.v)**
* Controlled by switch allocator & ST controller

---

## 🧪 Verification

* **Cycle-accurate Verilog testbench** (`Test.v`)
* Packet injection using `Packet_gen.v`
* Packet reception & checking via `Packet_recv.v`
* Suitable for:

  * Icarus Verilog
  * Verilator
  * Questa / VCS

### Run Simulation (Icarus Verilog)

```bash
iverilog -g2012 *.v
vvp a.out
```

---

## 🎯 Use Cases

* RTL / VLSI learning project
* NoC micro-architecture understanding
* FPGA simulation & experimentation
* Interview portfolio (Qualcomm / NVIDIA / AMD)
* Research prototyping

---

## 📈 Possible Extensions

* Multi-router 2D mesh topology
* Adaptive routing algorithms
* AXI / CHI Network Interface
* Power-aware NoC (clock gating)
* UVM-based verification
* Performance metrics (latency, throughput)

---

## 📚 References

* William J. Dally & Brian Towles – *Principles and Practices of Interconnection Networks*
* On-Chip Networks (MIT / Stanford lectures)
* AMBA AXI / CHI specifications

---

## 📜 License

This project is intended for **educational and research use**.
You are free to modify and extend it with proper attribution.

---

## 🤝 Contributions

Contributions and improvements are welcome via pull requests or issues.


