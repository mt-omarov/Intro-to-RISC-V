# Обзор языка ассемблера RISC-V
## Необходимая документация
Во-первых, в главе 2 спецификации RISC-V Unprivileged Specification подробно рассматривается набор команд RV32I Base Integer Instruction Set, 
включая модель программирования и объяснение форматов команд. Хотя эта информация не является обязательной для данного курса, она, безусловно, 
полезна для понимания того, как архитектура RISC-V выполняет инструкции.

Для программирования инструкций ассемблера мы можем использовать справочную документацию ABI и руководство ASM, чтобы ответить на любые вопросы, 
которые могут возникнуть в процессе работы. Вы можете найти эти документы здесь:
- [Спецификации RISC-V](https://riscv.org/technical/specifications/)
- [Документация ABI](https://riscv.org/technical/specifications/)
- [Руководство по ASM](https://github.com/riscv-non-isa/riscv-asm-manual/blob/master/riscv-asm.md)

Опять же, ни один из этих документов не является обязательным для изучения в данной главе, но вы можете обратиться к ним, 
если у вас возникнут вопросы, на которые здесь нет ответов.

## Обзор языка ассемблера
Эта глава будет представлять собой очень высокоуровневый обзор инструкций ассемблера RISC-V и 
лишь некоторые из них будут рассмотрены на практике. Мы надеемся, что этот учебник даст вам инструменты, 
необходимые для продолжения вашего путешествия по программированию на языке ассемблера. Если ваша цель - просто понять основы и 
разрабатывать приложения на языке более высокого уровня, этот курс, скорее всего, покроет большую часть необходимой вам информации.

RISC-V - это архитектура с "сокращенным набором инструкций", и поэтому в ней не так много инструкций, которые нужно изучать. 
В этом учебнике мы используем только 3 инструкции: LA (загрузка абсолютного адреса), ADDI (немедленное добавление) и ECALL. 
Инструкция ECALL используется для выполнения служебного запроса к среде выполнения. В нашем приложении Hello World мы будем использовать 
только два вызова, один для "записи" и один для "выхода".

Полный список инструкций можно найти в спецификации RISC-V Unprivileged Specification в главе 24 "RV32/64G Instruction Set Listings". 
Если вы хотите узнать больше о программировании на языке ассемблера, существует множество книг и курсов. 
Для получения дополнительной информации посетите [веб-сайт](https://riscv.org/learn/) RISC-V.
