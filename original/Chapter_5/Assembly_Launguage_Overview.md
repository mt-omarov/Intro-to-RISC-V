# RISC-V Assembly Language Overview
## Required Documentation
First off, Chapter 2 of the RISC-V Unprivileged Specification goes into detail about the RV32I Base Integer Instruction Set, including a programming model and an explanation of instruction formats. While this information is not required for this course it is certainly helpful in understanding how the RISC-V architecture executes instructions.

For programming assembly instructions, we can use both the ABI reference documentation and the ASM manual to answer any questions we may have along the way. You can find those documents here:

- [RISC-V Specifications](https://riscv.org/technical/specifications/)
- [ABI Documentation](https://github.com/riscv/riscv-elf-psabi-doc/blob/master/riscv-elf.md)
- [ASM Manual](https://github.com/riscv/riscv-asm-manual/blob/master/riscv-asm.md)

Again, none of this information is required knowledge for this chapter, but you can reference it if you have any questions not answered here.

## Assembly Language Overview
This chapter will be a very high level overview of RISC-V assembly instructions and will only cover a few of those instructions in practice. The hope is that this tutorial will give you the tools you need to continue your journey programming assembly language. If your goal is simply to understand the basics and develop applications in a higher level language, this course will likely cover most of the information you need.

RISC-V is a “reduced instruction set” architecture, and as such, there are not many instructions to learn. In this tutorial, we only use 3 instructions: LA (load absolute address), ADDI (add immediate), and ECALL. The ECALL instruction is used to make a service request to the execution environment. We will only use two calls in our Hello World app, one to “write” and one to “exit”.

For a full list of instructions you can see the RISC-V Unprivileged Specification Chapter 24 “RV32/64G Instruction Set Listings”. If you’d like to learn more about assembly language programming there are plenty of books and courses available. For more information, visit [RISC-V website](https://riscv.org/community/learn/).