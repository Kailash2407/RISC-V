# RISC-V Verilog RTL Design & Verification

**4-Day Student Assignment — Official Infoziant Training Curriculum**

A structured, professional hardware design repository implementing digital building blocks, finite state machines (FSM), a single-cycle RV32I RISC-V processor, and a 5-stage pipelined RISC-V processor with hardware hazard detection and forwarding.

---

## 1. Project Context & Objectives

This repository contains the completed and in-progress assignments developed according to the official **Infoziant "Verilog RTL and RISC-V Practice Activities — 4-Day Student Assignment"** workbook.

The curriculum covers practical digital design and verification techniques using Verilog HDL:
- **Day 1:** Synthesizable RTL building blocks and self-checking verification testbenches.
- **Day 2:** Synchronous FSM controllers (Moore & Mealy architectures), synchronous FIFO memory, and design review.
- **Day 3:** Single-cycle RISC-V (RV32I) CPU microarchitecture, instruction extensions, assembly programs, and datapath verification.
- **Day 4:** 5-stage pipelined RISC-V CPU with hazard resolution (data forwarding, load-use interlocks, and branch flushes) and performance/CPI analysis.

---

## 2. Tools & Environment

- **Hardware Description Language:** Verilog HDL (IEEE 1364-2001) / SystemVerilog testbench constructs
- **Simulation & Verification:** Mentor Graphics ModelSim / QuestaSim
- **Version Control:** Git & GitHub
- **Operating System:** Windows 11 / Linux compatible

---

## 3. Repository Structure

```
RISC-V/
│
├── README.md                          <- Project documentation and completion checklist
├── .gitignore                         <- ModelSim and temporary artifact ignore rules
│
├── day1/                              <- Day 1: RTL Building Blocks & Verification
│   ├── src/
│   │   ├── alu.v                      <- Parameterized 32-bit ALU
│   │   ├── counter.v                  <- 8-bit Up/Down counter with synchronous load
│   │   ├── shifter.v                  <- 32-bit Barrel Shifter (SLL, SRL, SRA)
│   │   └── regfile.v                  <- 32x32 Register File with write-through bypass
│   ├── tb/
│   │   ├── alu_tb.v                   <- Directed ALU testbench (25 corner cases)
│   │   ├── counter_tb.v               <- Counter functional testbench
│   │   ├── shifter_tb.v               <- Exhaustive reference-model self-checking testbench
│   │   └── regfile_tb.v               <- Randomized self-checking register file testbench
│   └── waves/
│       ├── 1.1alu.png                 <- ModelSim simulation waveform
│       ├── 1.2counter.png             <- ModelSim simulation waveform
│       ├── 1.3shifter waveform.png    <- ModelSim simulation waveform
│       └── 1.4regfile waveform.png    <- ModelSim simulation waveform
│
├── day2/                              <- Day 2: FSM Controllers & Memory Design
│   ├── src/
│   │   ├── seq_moore.v                <- Moore 1011 sequence detector
│   │   ├── seq_mealy.v                <- Mealy 1011 sequence detector
│   │   ├── vending.v                  <- Vending machine controller with refund
│   │   └── fifo.v                     <- Synchronous circular FIFO (Depth 16)
│   ├── tb/
│   │   ├── seq_tb.v                   <- Dual testbench validating Moore and Mealy FSMs
│   │   ├── vending_tb.v               <- Vending machine testbench (exact/over/cancel)
│   │   └── fifo_tb.v                  <- FIFO directed testbench (overflow/underflow)
│   └── waves/
│       ├── 2.1 sequence.png           <- ModelSim simulation waveform
│       ├── 2.2 vending machine.png    <- ModelSim simulation waveform
│       └── 2.3fifo.png                <- ModelSim simulation waveform
│
├── day3/                              <- Day 3: Single-Cycle RV32I RISC-V CPU
│   ├── src/
│   │   └── single_cycle_cpu/
│   │       ├── cpu.v                  <- Top-level single-cycle CPU datapath & control
│   │       ├── alu.v                  <- RV32I 4-bit ALU
│   │       ├── control_unit.v         <- RV32I main control unit
│   │       ├── immediate_generator.v  <- Immediate unpacker (I, S, B, U, J types)
│   │       ├── register_file.v        <- 32x32 register file with hardwired x0
│   │       └── shifter.v              <- 32-bit barrel shifter
│   ├── programs/
│   │   ├── program1.asm               <- Assembly Program 1: Sum 1..10 (Result x2=55)
│   │   ├── program2.asm               <- Assembly Program 2: First 10 Fibonacci numbers
│   │   └── program3.asm               <- Assembly Program 3: Max of 8 words in memory
│   ├── tb/
│   │   ├── cpu_tb.v                   <- Top-level self-checking testbench (Program 1)
│   │   └── unit_tests/
│   │       ├── alu_tb.v               <- Submodule ALU testbench
│   │       ├── control_unit_tb.v      <- Submodule Control Unit testbench
│   │       ├── immediate_generator_tb.v <- Submodule Immediate Generator testbench
│   │       ├── register_file_tb.v     <- Submodule Register File testbench
│   │       └── shifter_tb.v           <- Submodule Shifter testbench
│   └── waves/                         <- [Placeholder for Day 3 ModelSim waveforms]
│
├── day4/                              <- Day 4: 5-Stage Pipelined RISC-V CPU
│   ├── src/
│   │   └── pipelined_cpu/
│   │       └── pipeline_cpu.v         <- 5-stage pipeline with hazard & forwarding logic
│   ├── tb/
│   │   └── pipeline_tb.v              <- Hazard & load-use stall verification testbench
│   └── waves/                         <- [Placeholder for Day 4 ModelSim waveforms]
│
├── report/                            <- Technical Reports & Documentation
│   ├── design_review.txt              <- Day 2 Activity 2.4: FSM & FIFO design review
│   ├── instruction_encoding.md        <- Day 3 Activity 3.1: Instruction encoding & control signals
│   ├── waveform_analysis.md           <- Day 3 Activity 3.4: PC, ALU, and writeback waveform analysis
│   └── cpi_comparison.md              <- Day 4 Activity 4.3: CPI & architectural performance comparison
│
└── archive/                           <- Isolated non-core activities (preserved)
    └── additional_activities/
        ├── traffic.v                  <- Activity 2.5: Traffic light controller RTL
        ├── traffic_tb.v               <- Activity 2.5: Traffic light testbench
        ├── 2.5traffic controller.png  <- Activity 2.5: Traffic light waveform
        ├── atm.v                      <- Activity 2.6: ATM controller RTL
        └── atm_tb.v                   <- Activity 2.6: ATM controller testbench
```

---

## 4. Day-Wise Activity Descriptions

### Day 1: RTL Building Blocks & Self-Checking Verification
- **Activity 1.1 — Parameterized ALU:** 32-bit ALU supporting 8 operations (ADD, SUB, AND, OR, XOR, SLT, SLL, SRL) with status flags (`zero`, `negative`, `carry`, `overflow`).
- **Activity 1.2 — Up/Down Counter:** Synchronous 8-bit counter supporting enable, direction control, and parallel load.
- **Activity 1.3 — Barrel Shifter:** 32-bit multi-mode shifter (logical left, logical right, arithmetic right) verified against a behavioral reference model across 96 test scenarios.
- **Activity 1.4 — Register File:** 32x32-bit dual-read, single-write register file with hardwired `x0 = 0` and internal write-through bypass for same-cycle read/write collision prevention.

### Day 2: FSM Controllers & Memory Design
- **Activity 2.1 — Sequence Detector:** Overlapping `1011` sequence detectors implementing both Moore (output asserted in state S4) and Mealy (output asserted during transition) architectures.
- **Activity 2.2 — Vending Machine Controller:** Synchronous state machine handling 5 and 10 coin pulses, item dispensing at cost 15, change return, and cancellation.
- **Activity 2.3 — Synchronous FIFO:** Circular FIFO buffer of depth 16 with status indicators (`full`, `empty`) and concurrent read/write protection.
- **Activity 2.4 — Design Review:** Analysis of latch avoidance, complete case branches, and default combinational assignments.

### Day 3: Single-Cycle RISC-V CPU
- **Activity 3.1 — Instruction Extensions:** Implementation of RV32I base instructions including R-type arithmetic/logic, I-type immediates and `lw`, S-type `sw`, B-type conditional branches, `lui`, and `jal`.
- **Activity 3.2 — Assembly Programs:** Three hand-crafted assembly programs demonstrating arithmetic loops (Sum 1..10), sequential series generation (Fibonacci), and memory traversal/search (Array Maximum).
- **Activity 3.3 — Self-Checking CPU Testbench:** Execution of Program 1 with automatic end-of-test checking (`x2 == 55` and `dmem[0] == 55`).
- **Activity 3.4 — Waveform Analysis:** Datapath signal tracing across PC increments, instruction decode, ALU execution, and memory write-back.

### Day 4: 5-Stage Pipelined RISC-V CPU
- **Activity 4.1 — Data Hazard Handling:** Implementation of EX-to-EX and MEM-to-EX forwarding paths, alongside hardware load-use hazard detection inserting a 1-cycle stall bubble.
- **Activity 4.2 — Control Hazard Handling:** Early branch and jump evaluation in the EX stage accompanied by pipeline flushes of the IF/ID and ID/EX registers.
- **Activity 4.3 — Performance Comparison:** Theoretical and empirical comparison of Single-Cycle (CPI = 1.0) vs. 5-Stage Pipelined architecture throughput and cycle time.
- **Activity 4.4 — Git Submission:** Repository organisation adhering strictly to submission requirements.

---

## 5. ModelSim Simulation Guide

Follow these commands to compile and simulate any activity in ModelSim outside Antigravity:

### Setup Working Library
Open ModelSim, change directory to the repository root, and create the work library:
```tcl
cd {C:/Users/Kaila/OneDrive/Desktop/RISC-V}
vlib work
```

### Day 1 Simulations
```tcl
# Activity 1.1: ALU
vlog day1/src/alu.v day1/tb/alu_tb.v
vsim -voptargs=+acc work.alu_tb
run -all

# Activity 1.2: Counter
vlog day1/src/counter.v day1/tb/counter_tb.v
vsim -voptargs=+acc work.counter_tb
run -all

# Activity 1.3: Shifter
vlog day1/src/shifter.v day1/tb/shifter_tb.v
vsim -voptargs=+acc work.shifter_tb
run -all

# Activity 1.4: Register File
vlog day1/src/regfile.v day1/tb/regfile_tb.v
vsim -voptargs=+acc work.regfile_tb
run -all
```

### Day 2 Simulations
```tcl
# Activity 2.1: Sequence Detector
vlog day2/src/seq_moore.v day2/src/seq_mealy.v day2/tb/seq_tb.v
vsim -voptargs=+acc work.seq_tb
run -all

# Activity 2.2: Vending Machine
vlog day2/src/vending.v day2/tb/vending_tb.v
vsim -voptargs=+acc work.vending_tb
run -all

# Activity 2.3: FIFO
vlog day2/src/fifo.v day2/tb/fifo_tb.v
vsim -voptargs=+acc work.fifo_tb
run -all
```

### Day 3 Simulations
```tcl
# Activity 3.1 & 3.3: Single-Cycle CPU
vlog day3/src/single_cycle_cpu/*.v
vlog day3/tb/cpu_tb.v
vsim -voptargs=+acc work.cpu_tb
add wave -radix hex /cpu_tb/*
add wave -radix decimal /cpu_tb/dut/rf/regs[2]
add wave -radix decimal /cpu_tb/dut/dmem[0]
run 1200ns
```

### Day 4 Simulations
```tcl
# Activity 4.1 & 4.2: Pipelined CPU
vlog day4/src/pipelined_cpu/pipeline_cpu.v day4/tb/pipeline_tb.v
vsim -voptargs=+acc work.pipeline_tb
add wave -radix hex /pipeline_tb/*
add wave -radix decimal /pipeline_tb/dut/regs[1] /pipeline_tb/dut/regs[2] /pipeline_tb/dut/regs[3] /pipeline_tb/dut/regs[4]
run 500ns
```

---

## 6. Activity Completion Checklist

Status definitions:
- **Not Started:** Implementation not yet begun.
- **In Progress:** Work started; partial files or deliverables pending.
- **Implemented:** Source code and testbenches present; awaits simulation verification.
- **Verified:** Simulation verified with physical evidence (waveform screenshots / pass logs).

### Day 1: RTL Building Blocks
- [x] **Activity 1.1:** Parameterized ALU — **Verified** *(Design, testbench, waveform `1.1alu.png` present)*
- [x] **Activity 1.2:** Up/Down Counter — **Verified** *(Design, testbench, waveform `1.2counter.png` present)*
- [x] **Activity 1.3:** Barrel Shifter — **Verified** *(Design, self-checking testbench, waveform `1.3shifter waveform.png` present)*
- [x] **Activity 1.4:** Register File — **Verified** *(Design with bypass, randomized testbench, waveform `1.4regfile waveform.png` present)*

### Day 2: FSMs & Memory Design
- [x] **Activity 2.1:** Sequence Detector (Moore & Mealy) — **Verified** *(Design, dual testbench, waveform `2.1 sequence.png` present)*
- [x] **Activity 2.2:** Vending Machine Controller — **Verified** *(Design, testbench, waveform `2.2 vending machine.png` present)*
- [x] **Activity 2.3:** Synchronous FIFO — **Verified** *(Design, testbench, waveform `2.3fifo.png` present)*
- [x] **Activity 2.4:** Design Review — **Verified** *(Report `report/design_review.txt` completed)*

### Day 3: Single-Cycle RISC-V CPU
- [x] **Activity 3.1:** Instruction Extensions — **Implemented** *(CPU modules & `report/instruction_encoding.md` present; ModelSim verification pending)*
- [ ] **Activity 3.2:** Assembly Programs — **In Progress** *(Assembly source files `program1.asm`, `program2.asm`, `program3.asm` present; HEX files not yet generated)*
- [x] **Activity 3.3:** Self-Checking CPU Testbench — **Implemented** *(Testbench `cpu_tb.v` and unit testbenches present; ModelSim simulation pending)*
- [ ] **Activity 3.4:** Waveform Analysis — **In Progress** *(Report `report/waveform_analysis.md` created; ModelSim waveform capture pending)*

### Day 4: Pipelined RISC-V CPU
- [x] **Activity 4.1:** Data Hazard Handling — **Implemented** *(Forwarding and load-use interlock implemented in `pipeline_cpu.v`; ModelSim waveform capture pending)*
- [x] **Activity 4.2:** Control Hazard Handling — **Implemented** *(Branch/jump detection and pipeline flush implemented in `pipeline_cpu.v`; ModelSim waveform capture pending)*
- [x] **Activity 4.3:** Performance Comparison — **Implemented** *(Report `report/cpi_comparison.md` created; empirical cycle count pending simulation)*
- [x] **Activity 4.4:** Git Submission — **Verified** *(Repository structured and published to GitHub: https://github.com/Kailash2407/RISC-V)*

---

## 7. Known Issues & Pending Deliverables

1. **Pending HEX Machine Files (Activity 3.2):**
   - `day3/programs/program1.hex`, `program2.hex`, `program3.hex` need to be assembled/exported into hexadecimal memory format for runtime `$readmemh` loading.
2. **Pending Simulation Waveforms (Activities 3.4 & 4.1/4.2):**
   - Waveform screenshots for the single-cycle CPU (`day3/waves/`) and 5-stage pipelined CPU (`day4/waves/`) are pending manual simulation in ModelSim.
3. **Static Linting Observations for Day 3 & Day 4 RTL:**
   - In `day3/src/single_cycle_cpu/control_unit.v`, `branch_type` is declared as `reg [1:0]`, causing truncation for values 4 and 5 (BLTU/BGEU).
   - In `day4/src/pipelined_cpu/pipeline_cpu.v`, line 66 has `memwb_jal <= 0;` rather than propagating from the EX/MEM pipeline stage.

