# TRUEx96 CPU Architecture
Designed by **TRUEx**

---

## 中文说明
TRUEx96 架构 CPU 是我独自设计的极简 CPU。
未学习过专业数字电路课程，仅上课无聊时创作。
本作品 **开源，禁止商用**。

协议：GPLv3
Copyright © 2026 TRUEx

---

## English Description
The TRUEx96 CPU architecture is an extremely simple CPU designed entirely by myself.
I have not taken any professional digital circuit courses.
I just came up with it when I was bored in class.
This work is **open-source, commercial use prohibited**.

License: GPLv3
Copyright © 2026 TRUEx

---

# Instruction Format
Operand [5 bits] + Opcode [3 bits]

# Instruction Set
xxxxx 000  Immediate value
00xxx 001  ALU operation
xxxxx 010  Move xxxxx register to REG_I (buffer register, 16-bit)
xxxxx 011  Move REG_I to xxxxx register
0000x 100  JE
00000 101  JMP
xxxxx 110  IN from address xxxxx to REG_5
xxxxx 111  OUT from REG_4 to address xxxxx

# Immediate
Max immediate value: 32

# ALU Operations (REG1 op REG2 → REG3)
add  00 000 001
sub  00 001 001
and  00 010 001
or   00 011 001
not  00 100 001

# JE
Check REG2:
=0 → 00 00 0 100
>0 → 00 00 1 100
Jump address in REG0

# JMP
Unconditional jump
Jump address in REG0

# Halt Mechanism
When immediate value 0 appears, counter increases.
If 0 appears again (check opcode & REG0),
and this happens **5 times total**, the CPU halts.

---

## License
GNU General Public License v3.0 (GPLv3)
Commercial use is NOT allowed.
