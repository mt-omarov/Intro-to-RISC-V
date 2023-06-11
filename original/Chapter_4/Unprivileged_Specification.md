# The Unprivileged Specification
## Organizing the Specifications
The RISC-V ISA is broken up into two parts:
- Volume 1, Unprivileged Specification
- Volume 2, Privileged Specification

To understand why the specification is broken up into two different parts, we must first understand a bit about computer architecture and security. Historically, processors used hierarchical protection domains, often called protection rings, to protect data and code from malicious actors.

![Alt text](image.png)
**By Hertzsprung at English Wikipedia, CC BY-SA 3.0** \
[https://commons.wikimedia.org/w/index.php?curid=8950144](https://commons.wikimedia.org/w/index.php?curid=8950144)

The most privileged code runs in “Ring 0” and has access to the entire system. The processor will decide which privileges to grant executing code based on the privilege level. As an example, accessing memory by physical address may be restricted to “Ring 0” such that other rings must reference the virtual address space. Typically the processor can run in only one of the privilege modes at a time and there are special instructions to move between modes. All of these details can change from system to system, however they must follow the rules set out in the specification documents of a given architecture.

RISC-V currently has three privilege levels: User Mode (U-mode), Supervisor Mode (S-mode), and Machine Mode (M-mode). One can think of these as “Ring 2”, “Ring 1”, and “Ring 0” respectively. Other modes like a hypervisor mode (H-mode) will likely be added in the near future. Much like in the figure above, U-mode is for user processes, S-mode is for kernel and/or device drivers, and M-mode is used for bootloader and/or firmware. Each privilege level has access to specific Control and Status Registers (CSRs), and higher privilege levels can access the CSRs of those less privileged levels.

## Inside the Unprivileged Specification
Simply put, the unprivileged specification details items that are not related to machine mode (M-mode) or to Supervisor Mode (S-mode). The unprivileged specification includes the base ISA as well as extensions to that base like integer (I), float (F), double (D), compressed instructions (C), and many more.

The base instruction sets describe the instruction format, basic integer instructions, load and store instructions, and other fundamental details of the ISA. We break these up into several bases:
1. RV32I - Integer 32 bit 
2. RV32E - Reduced RV32I for embedded purposes
3. RV64I - Integer 64 bit
4. RV128I - Integer 128 bit

All these “Base ISA’s” either reduce or extend off the RV32I base instruction set. As an example, RV64I widens the integer registers and the supported user address space to 64 bits. This means that the LOAD and STORE instructions work a bit differently than in RV32I and the unprivileged specification contains the chapter explaining these differences.

## Base ISA Extensions
The unprivileged specification also contains the descriptions of the extensions to these base ISAs. Again, any extension that does note require M-mode to operate can be described in the unprivileged specification.

Each extension to the base ISA is developed and maintained by a Task Group:
- *Crypto Task Group* working on cryptographic extensions which can move many complex cryptographic algorithms into hardware, improving reliability and speed.
- *B Extension Task Group* working on bit manipulation extensions which can speed up many common mathematical tasks.
- *Vector (V) Extension Task Group* working on vector instructions which are at the heart of many graphical processing computations.

Once ratified, these extensions are added to the unprivileged specification. The following are some of the ratified extensions that you might see in a RISC-V processor:

**“M” Standard Extension**
Chapter 7 of the [Unprivileged Specification](https://riscv.org/technical/specifications/) describes how integer multiplication and division should be accomplished. It describes how each of the multiplication instructions (MUL, MULH, MULHU, MULHU, MULW) will behave, which registers are used for the multiplier and multiplicand, and where the result will be stored. It does the same for division since functionally one can view division as simply the inverse of multiplication. It may seem odd to you that this extension is not required. However, for many embedded processors, multiplication can be done in software if it is not required very often or even at all. Removing this logic from a processor will save money on development, keeping the end product cost lower.

**“F” Standard Extension**
Chapter 11 describes how we add single-precision floating-point computational instructions that are compliant with the IEEE 754-2008 arithmetic standard. There are many resources available covering the details of floating-point arithmetic in computing. It is enough to understand that this chapter describes how this process is implemented in RISC-V, and is complimented by Chapter 12 (the D extension) which describes double-precision floating-point computational instructions. Lastly, Chapter 13 covers the Q standard extension for 128-bit quad-precision binary floating-point instructions. All three of these conform to IEEE standards. Again, many embedded applications do not require floating point logic, and hence this extension is not part of the Base ISAs.

**“C” Standard Extension**
Chapter 16 describes the compressed instruction-set extension which reduces static and dynamic code size by adding short 16-bit instruction encodings for common operations. Typically, 50%–60% of the RISC-V instructions in a program can be replaced with RVC instructions, resulting in a 25%–30% code-size reduction. The C extension is compatible with all other standard instruction extensions. The C extension allows 16-bit instructions to be freely intermixed with 32-bit instructions, with the latter able to start on any 16-bit boundary. As such, with the addition of the C extension to any system, no instructions can raise instruction-address-misaligned exceptions.

This covers most of the currently ratified extensions in the unprivileged specification. However, it is important to note that many extensions are included in the specification in a “draft” or “frozen” stage. As we discussed in the section on “RISC-V Extension Lifecycle”, these specifications are not yet ratified and any implementation should avoid using them in production.
