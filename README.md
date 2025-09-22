This project contains the Verilog implementation of a 16-bit Arithmetic Logic Unit (ALU) in both pipelined and non-pipelined architectures. The goal is to demonstrate the benefits of pipelining in digital design, specifically in terms of increased throughput and improved clock frequency. The non-pipelined version serves as a performance baseline for comparison.

Design Details ⚙️
Pipelined ALU (pipelined_alu.v)
The pipelined ALU uses a two-stage pipeline to break down the execution of an instruction, allowing multiple instructions to be in flight simultaneously. This significantly reduces the critical path delay.

Stage 1: Execute

This is the combinatorial part of the ALU.

All 8 operations are computed in parallel.

Flags like carry and overflow are generated for arithmetic operations.

Stage 2: Write-back

This is the register stage.

The result from Stage 1 is stored in a register on the positive edge of the clock.

The zero flag is calculated based on the registered result.

This stage's output (result, zero, carry, overflow) becomes the final output of the module.

Non-Pipelined ALU (nonpipelined_alu.v)
This is a single-cycle, purely combinatorial design. The entire computation, from receiving the operands to outputting the result, happens in a single, long propagation delay. It is useful for understanding the performance limitations that pipelining aims to solve.

Operations 🧮
Both ALUs support the following 8 operations, selected by a 3-bit opcode:

3'b000: ADD (Addition)

3'b001: SUB (Subtraction)

3'b010: AND (Bitwise AND)

3'b011: OR (Bitwise OR)

3'b100: XOR (Bitwise XOR)

3'b101: NOT (Bitwise NOT on operand A)

3'b110: SHL (Shift Left)

3'b111: SHR (Shift Right)

Repository Structure 📂
src/: Contains the Verilog source code.

pipelined_alu.v

nonpipelined_alu.v

testbench/: Contains the testbenches for verification.

tb_pipelined_alu.v

tb_nonpipelined_alu.v
