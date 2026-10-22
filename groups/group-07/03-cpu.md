# 3. CPU
MIMD stands for Multiple Instructions, Multiple Data. It is a computer architecture in which multiple processors can execute multiple instructions on different sets of data simultaneously. In MIMD CPUs and CPU cores can work independently. Depending on your system design it can be used with the same main memory or separated local memories, which makes the MIMD´s architecture suitable for a wide range of applications, such as personal computers and supercomputers.

## 3.1 Processor Overview
In MIMD´s architecture, it may contain multiple processors or multiple cores in a single processor. Each processor usually has the following components: r
Registers; ALU; Control Unit (CU); Clock.

## 3.2 Registers
The registers are the high-speed storage inside a CPU. It holds instructions, memory adresses, data and intermediate results. They are faster to access compared to the main memory, allowing CPU to operate more efficiently. In MIMD architecture each core usually have their own architectural registers that allows it to mantain an independent execution flow, meanig they can process different instructions and datasets simultaneously.

## 3.3 ALU
ALU stands for Arithmetic Logic Unit, as the name suggests this component responsible for arithmetic calculations and logic operations that are essential for mathematical calculations, data processing, program execution and decision making. After it receives data from the registers, it performs the opeeration  specified by an instruction, producing a result that can be stored in a register or used by another operation. In MIMD, the different processors or cores may perform different ALU operations at the same time, increasing the processing capacity of the entire system.

## 3.4 Control Unit
The Control Unit directs and coordinates the operations of the processor. It interprets instructions, generates control signals, and determines how data moves between registers, memory, execution units, and aother components of the CPU. It determines which operation should be performed and which internal components are needed to do so. It helps manage the program flow. In MIMD´s architecture each processor or core usually have their own instruction-control and scheduling mechanisms, allowing different cores to execute different instructions independently, being essential to MIMD architecture as it enables independent instruction execution while coordinating the activities of the components within each processor.

## 3.5 Clock
The CPU Clock syncronizes internal activities, including moving data between registers, advancing instructions through different stages of the processing pipeline and starting execution operations, by timing signals that coordinate processor operations.
In MIMD architecture, the Clock signals help to coordinate activities within each core or processor. The cores may operate at different frequencies or adjust their speeds according to what is being done, such as workload, power requirements or temperature. Even tho it ensures the processor components perform their operations in a cordinated manner, it may need additional mechanisms to syncronize separate processors, such as locks, communication protocols and atomic operations.

## 3.6 Instruction Cycle
The instruction cycle is a fundamental part of CPU operation because programs consist in instructions that must be processed by the CPU, the cycle itself is a sequence of steps followed by a processor to retrieve, interpret, and execute an instruction. Fetch, Decode, and Execute.

Fetch:
The processor retrieves the next instruction from memory or instruction cache, the Program Counter contains the address associated with the next instruction to be fetched, which the processor uses to retrieve it and make it available for decoding, and finally the Program Counter is normally updated to identify the following instruction. nevertheless, a branch or jump instruction can change the execution sequence causing the processor to fetch an instruction from a different address. In MIMD architecture, each core or processors can retrieve different instructions at the same time, allowing them to work independently because they can fetch instructions from their own instruction stream.

Decode:
The processor interprets the instruction that has been fetched, the Control Unit determines what operation the instructions represents and then identifies the data and resources needed to perform it. In MIMD architecture, different processors can decode different instrutions at the same time, allowing the cores to process their own work independently.

Execute:
when the operation is completed , it´s result may be stored in memory or in a register, then the processor continues with its following instructions. In MIMD architecture, as said many times previously, the processors can execute different instructions on different datasets simultaneously.

## 3.7 CPU Diagram

<img width="997" height="908" alt="Captura de tela 2026-10-22 012035" src="https://github.com/user-attachments/assets/453a7b8b-24bc-47b7-8da8-dac46493d675" />

## 3.8 Advantages
The main advantages of the MIMD architecture is the parallel processing capability, that improves the performance of the system by dividing the workload, making it flexible and efficient to multitask and allows a wide range of applications.

## 3.9 Limitations
The concerns around the MIMD architecture include the programming complexity, since parallel programs tend to be more difficult to develop than sequential programs. Communication and syncronization overhead, especially in large multiprocessor systems. Higher hardware costs and power consumption. Memory contention, when multiple processors try to acces the same memory resource at the same time, reducing performance and also the difficulties and conflicts in load-balancing and shared-resources.
