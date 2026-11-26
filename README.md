# RISC-V Instruction Set Simulator (ISS)

## Project Overview

A Python-based simulator that executes 32-bit RISC-V machine instructions and simulates CPU behavior, including register operations, memory access, and program control flow.

**Machine Code → Instruction Decoder → Execution → Register & Memory States**

## System Architecture

The simulator follows the **Fetch–Decode–Execute** cycle.

| Stage | Operation |
|---|---|
| **Fetch** | Retrieve the instruction based on the current address |
| **Decode** | Extract opcode, registers, function codes, and immediate values |
| **Execute** | Perform the corresponding operation |
| **Update** | Update registers, data memory, and Program Counter |

### Core Components

| Component | Responsibility |
|---|---|
| Instruction Decoder | Identify instruction formats and operands |
| Register File | Store the values of 32 integer registers |
| Execution Unit | Perform arithmetic and logical operations |
| Data Memory | Handle load and store operations |
| Program Counter (PC) | Control instruction execution flow |
| System Call Handler | Handle basic I/O, heap and file operations |

## Instruction Decoding & Execution

### Instruction Formats

| Format | Examples | Execution |
|---|---|---|
| R-Type | ADD, SUB, AND, OR | Register-to-register operations |
| I-Type | ADDI, LW, JALR | Immediate, load and jump operations |
| S-Type | SW, SH, SB | Store data into memory |
| B-Type | BEQ, BNE, BLT | Conditional branching |
| U-Type | LUI, AUIPC | Upper immediate operations |
| J-Type | JAL | Jump and save return address |

### Instruction Decoding

| Binary Field | Size | Purpose |
|---|---|---|
| opcode | 7 bits | Identify instruction group |
| rd | 5 bits | Destination register |
| rs1 | 5 bits | Source register 1 |
| rs2 | 5 bits | Source register 2 |
| funct3 | 3 bits | Identify operation |
| funct7 | 7 bits | Distinguish operations |
| immediate | Format-dependent | Constant value or address offset |

### Execution Mechanism

| Operation | Result |
|---|---|
| Arithmetic / Logic | Update destination register |
| Load | Memory → Register |
| Store | Register → Memory |
| Branch | Update PC if condition is met |
| Jump | Update PC and save return address |

**Final Output:** Register values and data memory states after normal program completion.
