# RISC-V Hello World
## Environment Overview

Here is the hello world application we will be using:
```
-----code-----
# Simple RISC-V Hello World                                                                                       

.global _start                                                                                      

_start: addi  a0, x0, 1
        la    a1, helloworld
        addi  a2, x0, 13
        addi  a7, x0, 64
        ecall

        addi    a0, x0, 0
        addi    a7, x0, 93
        ecall

.data
helloworld:      .ascii “Hello World!\n” 
-----end code-----
```

There are also two ways of compiling this code, either using GCC or calling “as” and “ld” directly:
```
-----code-----
# GCC
riscv64-linux-gnu-gcc -o rv-hello rv-hello.s -nostdlib -static                                                                      

# AS & LD
riscv64-linux-gnu-as -march=rv64imac -o rv-hello.o rv-hello.s
riscv64-linux-gnu-ld -o rv-hello rv-hello.o 
-----end code-----
```