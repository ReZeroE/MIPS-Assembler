# MIPS-Assembler (CS 3114)
This program is an assembler implemented in C that supports a subset of instructions in the MIPS32 assembly language.

## Supported Instructions
The program supports a subset of the instructions from the MIPS32 assembly language. (28 instructions)
```
lw      rt, offset(rs)
sw      rt, offset(rs)
lui     rt, imm16
add     rd, rs, rt
addi    rt, rs, imm16
addu    rd, rs, rt 
addiu   rt, rs, imm16
mul     rd, rs, rt
mult    rs, rt
nop
nor     rd, rs, rt
sll     rd, rt, sa
slt     rd, rs, rt 
slti    rt, rs, imm16
sra     rd, rt, sa
srav    rd, rt, rs 
sub     rd, rs, rt
beq     rs, rt, offset
blez    rs, offset 
bgtz    rs, offset
bne     rs, rt, offset
j       target
syscall

move    rd, rs
blt     rs, rt, offset
la      rt, label 
li      rt, imm16
lw      rt, label
```

## Valgrind Report & Testing
This program is fully tested through both manual testing and Valgrind. The program handles all corner cases and memory allocation/deallocation flawlessly.

Please note that the program has certain preset limits and is not garenteed to function correctly beyound those limits (specified below).
```
Grading:  kevinliu.tar
Time:     Mon Nov 29 22:22:28 EST 2021
Option:   -final

>>Scores from testing<<
  1 >> Score for final/ftest01.o: 12.00 / 12.00
  2 >> Score for final/ftest02.o: 17.00 / 17.00
  3 >> Score for final/ftest03.o: 10.00 / 10.00
  4 >> Score for final/ftest04.o: 14.00 / 14.00
  5 >> Score for final/ftest05.o: 22.00 / 22.00
  6 >> Score for final/ftest06.o: 20.00 / 20.00
  7 >> Score for final/ftest07.o: 22.00 / 22.00
  8 >> Score for final/ftest08.o: 11.00 / 11.00
  9 >> Score for final/ftest09.o: 30.00 / 30.00
 10 >> Score for final/ftest10.o: 60.00 / 60.00
 11 >>  sortedsyms01.txt symbols: 3 / 3
 12 >>  sortedsyms04.txt symbols: 9 / 9
 13 >>  sortedsyms07.txt symbols: 10 / 10
============================================================

Valgrind issues:
==752470==     in use at exit: 0 bytes in 0 blocks
==752470==   total heap usage: 258 allocs, 258 frees, 27,345 bytes allocated
Invalid reads: 0
Invalid writes: 0
Uses of uninitialized values: 0
============================================================
```

## Code Access Request
Due to Honor Code issues, this program is not publicly visible as of right now. If you would like to access the code for non-academic purposes (recruitment or related), please contact me at kevinliu@vt.edu. 
