# 3. CPU

## 3.1 Processor Overview
In a MIMD architecture, the CPU subsystem consists of multiple autonomous processing units (cores or independent processors). Unlike single-stream models, each processor maintains its own program counter and control logic, allowing them to fetch, decode, and execute entirely different instruction streams on independent data sets simultaneously.
## 3.2 Registers
Each processing core is equipped with its own dedicated set of internal registers, including:

Program Counter (PC): Tracks the independent execution address for each core's active instruction stream.

General-Purpose Registers: Store temporary operands and intermediate calculation results locally within each core.

Status/Flag Registers: Maintain the state of arithmetic and logical conditions (such as zero, carry, or overflow) specific to each core's current operation.
## 3.3 ALU
The system features multiple Arithmetic Logic Units (ALUs)—typically one or more per core. This design enables concurrent arithmetic and logical operations across different cores without interfering with each other, maximizing parallel processing throughput.
## 3.4 Control Unit
The control mechanism in a MIMD processor is decentralized or distributed. Each core has its own Control Unit (CU) responsible for:

Directing the internal operations and data paths of its respective core.

Managing independent branch decisions, conditional jumps, and loop repetitions without locking other cores.

Coordinating with synchronization primitives (such as hardware locks or barriers) when shared memory resources must be accessed safely.
## 3.5 Clock
The processing cores may operate under a synchronized global clock or within independent clock domains. While timing coordinates the internal register transfers of each core, execution pacing can diverge because cores process distinct instruction paths at varying speeds.
## 3.6 Instruction Cycle

The classical sequential model (Fetch → Decode → Execute → Write Back) operates independently and concurrently across each core in the MIMD architecture:   Fetch: Each core retrieves the next instruction from its designated memory space using its own Program Counter.Decode: The local Control Unit interprets the fetched instruction. Because cores handle distinct tasks, Core A might decode a floating-point multiplication while Core B decodes a branch instruction.Execute: The respective ALU or execution unit performs the operation on independent data streams.Write Back: Results are stored back into local registers or transferred to shared memory structures through the interconnection network.

## 3.7 CPU Diagram

![alt text](image-2.png)

## 3.8 Advantages
High Parallelism: Capable of executing completely unrelated tasks and algorithms concurrently.

Flexibility: Highly efficient for complex, non-uniform workloads where different data sets require distinct processing steps.

Scalability: Performance scales effectively with the addition of more processing cores.
## 3.9 Limitations
Synchronization Overhead: Requires careful management using barriers and locks to prevent race conditions when accessing shared data.

Memory Contention: Multiple cores attempting to access shared memory simultaneously can saturate the interconnection bus.

Programming Complexity: Designing and debugging multi-threaded, independent instruction flows is significantly harder than sequential programming
.
## 3.10 Example of Execution (Concrete Task)
To demonstrate the control and sequence of operations in this MIMD system, consider the parallel processing of a large array split between Core 1 and Core 2:

Initiation: The operating system assigns two distinct tasks—processing the first half of an array on Core 1 and the second half on Core 2.

Independent Sequence: Each core independently steps through its instruction cycle (Fetch → Decode → Execute), executing separate loop iterations on its local data subset.

Control Flow & Divergence: Core 1 encounters a conditional branch and takes a different execution path than Core 2, showcasing the independence of MIMD instruction streams.

Synchronization and Termination: Both cores reach a synchronization barrier. Once both tasks complete their individual execution conditions, the results are consolidated, and the program flow concludes.