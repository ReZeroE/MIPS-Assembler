# MIPS-Assembler (CS 2506)
This program is an assembler implemented in C that supports a subset of instructions in the MIPS32 assembly language. The program handles both `.data` and `.text` sections and translates them into raw machine code (binary format).

Please read [Code Access Request](## Code Access Request) for the source code of the program.

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

## Sample Usage
Given a sample program in MIPS32, the assembler will translate such program into machine code.
### INPUT
```
# Test file 10
# Tests:  - comprehensive test of all instructions
#         - full-featured data segment
#         - full-line comments
#         - end-of-line comments

.data
x01:    .word    14324143
s01:    .asciiz  "a"
x02:    .word    -323434
s02:    .asciiz  "ab"
x03:    .word    873124
s03:    .asciiz  "abc"
x04:    .word    -1343241
s04:    .asciiz  "abcd"
arr01:  .word    23:6
s05:    .asciiz  "How did that one go?"
arr02:  .word    6, 28, 496, 8128

.text
main:
        la     $t0, arr01          # get address of first array
        lw     $t1, x01            # load value of x01
        sw     $t1, 4($t1)         # store value of x01 into arr01[1]
        lui    $t1, -1             # load 0xFFFF to top half of $t1

# Check basic R-type and I-type instructions
label1:
        add    $t4, $t2, $t3
        addi   $s0, $s0, 31214
        addu   $s1, $s1, $s2
        addiu  $s2, $s2, -31214
        mul    $s3, $s4, $s5
        mult   $s3, $s4
label2:
        mul    $t4, $t7, $t9
        nop
        nor    $t3, $t6, $t8
        sll    $s2, $s2, 31
        slt    $t3, $s2, $s3
        slti   $t3, $s2, -21497
label3:
        sra    $s0, $s1, 17
        srav   $s7, $s2, $s0
        sub    $t0, $zero, $s1

# Check some conditional branch instructions and j
        beq    $t1, $a0, label1
        blez   $t3, label2
        bgtz   $s7, label3
        bne    $s5, $zero, label2
        j      label1
# Check remaining pseudo-instructions, and syscall
label4:
        move   $t3, $s3
        blt    $t0, $t1, label4
        li     $t3, -4123
        syscall

# Load addresses of selected variables
# These check the alignment, which and therefore padding
        la     $t3, x02
        la     $t3, x03
        la     $t3, x04
        la     $t3, s05
        la     $t3, arr02
```

### OUTPUT
```
00100000000010000010000000100100
10001100000010010010000000000000
10101101001010010000000000000100
00111100000010011111111111111111
00000001010010110110000000100000
00100010000100000111100111101110
00000010001100101000100000100001
00100110010100101000011000010010
01110010100101011001100000000010
00000010011101000000000000011000
01110001111110010110000000000010
00000000000000000000000000000000
00000001110110000101100000100111
00000000000100101001011111000000
00000010010100110101100000101010
00101010010010111010110000000111
00000000000100011000010001000011
00000010000100101011100000000111
00000000000100010100000000100010
00010001001001001111111111110000
00011001011000001111111111110101
00011110111000001111111111111010
00010110101000001111111111110011
00001000000000000000000000000100
00000000000100110101100000100001
00000001000010010000100000101010
00010100001000001111111111111101
00100100000010111110111111100101
00000000000000000000000000001100
00100000000010110010000000001000
00100000000010110010000000010000
00100000000010110010000000011000
00100000000010110010000000111100
00100000000010110010000001010100

00000000110110101001000110101111
01100001000000000000000000000000
11111111111110110001000010010110
01100001011000100000000000000000
00000000000011010101001010100100
01100001011000100110001100000000
11111111111010111000000011110111
01100001011000100110001101100100
00000000000000000000000000000000
00000000000000000000000000010111
00000000000000000000000000010111
00000000000000000000000000010111
00000000000000000000000000010111
00000000000000000000000000010111
00000000000000000000000000010111
01001000011011110111011100100000
01100100011010010110010000100000
01110100011010000110000101110100
00100000011011110110111001100101
00100000011001110110111100111111
00000000000000000000000000000000
00000000000000000000000000000110
00000000000000000000000000011100
00000000000000000000000111110000
00000000000000000001111111000000

``` 


## Valgrind Report & Testing
This program is fully tested through both manual testing and Valgrind. The program handles all corner cases and memory allocation/deallocation flawlessly.
```
Grading:  kevinliu.tar
Time:     Mon Nov 29 22:22:28 EST 2021
Option:   -final

================================================================================
Valgrind issues:
==752470==     in use at exit: 0 bytes in 0 blocks
==752470==     total heap usage: 258 allocs, 258 frees, 27,345 bytes allocated
Invalid reads: 0
Invalid writes: 0
Uses of uninitialized values: 0
================================================================================
```
Please note that the program has certain preset limits and is not garenteed to function correctly beyound those limits (specified below).

## Code Access Request
Due to Honor Code concerns, this program is not publicly visible as of right now. If you would like to access the code for recruitment purposes, please contact me at kevinliu@vt.edu. 
