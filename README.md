Custom 32-bit Verilog Processor
This repository contains the Verilog implementation of a custom 32-bit processor designed with a simple finite state machine and a custom instruction set architecture (ISA). The processor supports basic arithmetic, logical, memory, and control flow operations, making it suitable for simulation-based CPU design.

Features
Instruction Set: Supports operations like add, sub, mul, and, or, xor, not, along with conditional and unconditional jumps, memory access, and data movement between registers and memory.

Registers: Includes 32 general-purpose 16-bit registers (GPR) and a 16-bit special-purpose register (SGPR) for storing the upper bits of multiplication results.

Memory:

16-entry instruction memory (inst_mem), initialized from an external binary file (data.mem)

16-entry data memory (data_mem) for load/store operations and simulated I/O.

Condition Flags: Automatically updates zero, sign, carry, and overflow flags based on instruction results, enabling conditional branching.

Immediate Mode: All arithmetic and logic instructions support both register and immediate inputs.

FSM-Controlled Execution: Six-state FSM handles instruction fetch, decode, execute, delay, PC update, and halt conditions.

I/O Support: Accepts external 16-bit input (din) and drives a 16-bit output (dout) via memory-mapped instructions.

How it Works
The processor reads a binary program from data.mem at startup and begins execution from program counter zero. Instructions are decoded using macros for clarity, executed through the FSM, and condition flags are updated as needed. Jump and halt instructions control flow and termination.

Testbench
The included testbench provides a basic simulation setup, toggling clock and reset signals while observing output. It can be extended to test various programs and input patterns.

Usage
Write or compile a program into a binary format and save it as data.mem.

Run the simulation in Vivado, ModelSim, or any compatible Verilog tool.

Observe outputs through dout, internal registers, and memory.