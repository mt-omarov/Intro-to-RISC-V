# RISC-V Hello World
## Обзор окружения
Вот приложение hello world, которое мы будем использовать:
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

Существует также два способа компиляции этого кода: либо с помощью GCC, либо вызывая "as" и "ld" напрямую: 
```
-----code-----
# GCC
riscv64-linux-gnu-gcc -o rv-hello rv-hello.s -nostdlib -static                                                                      

# AS & LD
riscv64-linux-gnu-as -march=rv64imac -o rv-hello.o rv-hello.s
riscv64-linux-gnu-ld -o rv-hello rv-hello.o 
-----end code-----
```
