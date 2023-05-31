# Systems Architecture

Here are my notes on the architecture of computing machines.

(section-label)=
## MIPS
---

### Memory Organization 

What is inside a computational machine?
I have a processor that takes numbers in and then numbers come out. The numbers come **from** memory to the processor and from the processor (cpu) **to** memory.

Memory is viewed as a 1-dimension array, where the index is the memory address, and each index stores 8 bits, 1 byte, of data. This is called "Byte addressing".

Data items are grouped into *words*. A word is **a unit of data of a defined bit length**. MIPS (**M**illion **I**nstructions **P**er **S**econd) instructions are grouped in 32-bit (4-byte) words. Words only start at address 0, 4, 8, 12, etc.

Some part of the memory contains words, some part of the memory contains numbers, and some part of the memory remains unused. There are 32 available registers numbered from 0-31: 

```{list-table}
:header-rows: 1

* - Name
  - Register Number
  - Usage
  - Preserved on call?
* - \$zero ($0)
  - 0
  - The constant value 0
  - n.a.
* - \$v0, \$v1
  - 2, 3
  - Values for results and expression evaluation
  - no
* - \$a0-\$a3
  - 4-7
  - Arguments
  - no
* - \$t0-\$t7
  - 8-15
  - Temporaries
  - no
* - \$s0-\$s7
  - 16-23
  - Saved
  - yes
* - \$t8, \$t9
  - 24, 25
  - More Temporaries
  - no
* - \$gp
  - 28
  - Global pointer
  - yes
* - \$sp
  - 29
  - Stack pointer
  - yes
* - \$fp
  - 30
  - Frame pointer
  - yes
* - \$ra
  - 31
  - Return address
  - yes
```

### MIPS Arithmetic

All MIPS arithmetic instructions have 3 operands in a fixed order, starting with the destination. Here's an example:

```html
C Code:         A = B + C
```
```html
MIPS Code:      add $s0, $s1, $s2
```

The operands for arithmetic instructions **must be registers**. The compiler handles the association between
compilers and registers.

If the statements are more complex than the previous example, we use temporary registers to break the statements up like so:

```html
C Code:         f = (g + h) - (i + j)
```
```html
MIPS Code:      add $t0, $s1, $s2
                add $t1, $s3, $s4
                sub $s0, $t0, $t1
```
### Load & Store

In order to do arithmetic instructions, memory must sometimes be accesed through load and store instructions. Here's and example:

```html
C Code:         A[12] = h + A[8];
```
```html
MIPS Code:      lw $t0, 32($s3);
                add $t0, $t0, $s2
                sw $t0, 48($s3);
```
::::{important}
    The **Store Word Instruction** (sw) has the destination last!
::::

### Logical Operators

```html
and $t0, $t1, $t2
or $t0, $t1, $t2
nor $t0, $t1, $zero     
```

### Machine Language

How are instructions represented? 
<table class="mips-table">
  <tr>
    <th>Name</th>
    <th colspan="6">Fields</th>
    <th>Comments</th>
  </tr>
  <tr>
    <td>Field Size</td>
    <td>6 bits</td>
    <td>5 bits</td>
    <td>5 bits</td>
    <td>5 bits</td>
    <td>5 bits</td>
    <td>6 bits</td>
    <td>MIPS instructions are 32 bits long</td>
  </tr>
  <tr>
    <td>R-Format</td>
    <td>op</td>
    <td>rs</td>
    <td>rt</td>
    <td>rd</td>
    <td>shamt</td>
    <td>funct</td>
    <td>Arithmetic instruction format</td>
  </tr>
  <tr>
    <td>I-Format</td>
    <td>op</td>
    <td>rs</td>
    <td>rt</td>
    <td colspan="3">address/immediate</td>
    <td>Transfer/Branch immediate format</td>
  </tr>
  <tr>
    <td>J-Format</td>
    <td>op</td>
    <td colspan="5">target address</td>
    <td>Jump instruction format</td>
  </tr>
</table><br/>

Each instruction is 32 bits. Each instruction is broken down into different 
sections listed below:

- **op** – The **Op**code
- **rs** – **R**egister **S**ource 1
- **rt** – **R**egister Source **2**
- **rd** – **D**estination **R**egister
- **shamt** – **Sh**ift **Am**oun**t**, 0 if not shift instruction
- **funct** – **Funct**ion code, selects the specific variant of the operation in the opcode field

<table class="mips-table instructions-table">
  <tr>
    <th>Opcode</th>
    <th>Name</th>
    <th>Action</th>
    <th colspan="6">Bit fields</th>
  </tr>
  <tr>
    <td>ADD rd,rs,rt</td>	
    <td>Add</td>	
    <td>rd=rs+rt</td>	
    <td>000000</td>	
    <td>rs</td>	
    <td>rt</td>		
    <td>rd</td>		
    <td>00000</td>		
    <td>100000</td>	
  </tr>
</table><br/>

```
ADD rd,rs,rt	Add	rd=rs+rt	000000	rs	rt	rd	00000	100000
ADDI rt,rs,imm	Add Immediate	rt=rs+imm	001000	rs	rt	imm
ADDIU rt,rs,imm	Add Immediate Unsigned	rt=rs+imm	001001	rs	rt	imm
ADDU rd,rs,rt	Add Unsigned	rd=rs+rt	000000	rs	rt	rd	00000	100001
AND rd,rs,rt	And	rd=rs&rt	000000	rs	rt	rd	00000	100100
ANDI rt,rs,imm	And Immediate	rt=rs&imm	001100	rs	rt	imm
LUI rt,imm	Load Upper Immediate	rt=imm<<16	001111	rs	rt	imm
NOR rd,rs,rt	Nor	rd=~(rs|rt)	000000	rs	rt	rd	00000	100111
OR rd,rs,rt	Or	rd=rs|rt	000000	rs	rt	rd	00000	100101
ORI rt,rs,imm	Or Immediate	rt=rs|imm	001101	rs	rt	imm
SLT rd,rs,rt	Set On Less Than	rd=rs<rt	000000	rs	rt	rd	00000	101010
SLTI rt,rs,imm	Set On Less Than Immediate	rt=rs<imm	001010	rs	rt	imm
SLTIU rt,rs,imm	Set On < Immediate Unsigned	rt=rs<imm	001011	rs	rt	imm
SLTU rd,rs,rt	Set On Less Than Unsigned	rd=rs<rt	000000	rs	rt	rd	00000	101011
SUB rd,rs,rt	Subtract	rd=rs-rt	000000	rs	rt	rd	00000	100010
SUBU rd,rs,rt	Subtract Unsigned	rd=rs-rt	000000	rs	rt	rd	00000	100011
XOR rd,rs,rt	Exclusive Or	rd=rs^rt	000000	rs	rt	rd	00000	100110
XORI rt,rs,imm	Exclusive Or Immediate	rt=rs^imm	001110	rs	rt	imm
Shifter
SLL rd,rt,sa	Shift Left Logical	rd=rt<<sa	000000	rs	rt	rd	sa	000000
SLLV rd,rt,rs	Shift Left Logical Variable	rd=rt<<rs	000000	rs	rt	rd	00000	000100
SRA rd,rt,sa	Shift Right Arithmetic	rd=rt>>sa	000000	00000	rt	rd	sa	000011
SRAV rd,rt,rs	Shift Right Arithmetic Variable	rd=rt>>rs	000000	rs	rt	rd	00000	000111
SRL rd,rt,sa	Shift Right Logical	rd=rt>>sa	000000	rs	rt	rd	sa	000010
SRLV rd,rt,rs	Shift Right Logical Variable	rd=rt>>rs	000000	rs	rt	rd	00000	000110
Multiply
DIV rs,rt	Divide	HI=rs%rt; LO=rs/rt	000000	rs	rt	0000000000	011010
DIVU rs,rt	Divide Unsigned	HI=rs%rt; LO=rs/rt	000000	rs	rt	0000000000	011011
MFHI rd	Move From HI	rd=HI	000000	0000000000	rd	00000	010000
MFLO rd	Move From LO	rd=LO	000000	0000000000	rd	00000	010010
MTHI rs	Move To HI	HI=rs	000000	rs	000000000000000	010001
MTLO rs	Move To LO	LO=rs	000000	rs	000000000000000	010011
MULT rs,rt	Multiply	HI,LO=rs*rt	000000	rs	rt	0000000000	011000
MULTU rs,rt	Multiply Unsigned	HI,LO=rs*rt	000000	rs	rt	0000000000	011001
Branch
BEQ rs,rt,offset	Branch On Equal	if(rs==rt) pc+=offset*4	000100	rs	rt	offset
BGEZ rs,offset	Branch On >= 0	if(rs>=0) pc+=offset*4	000001	rs	00001	offset
BGEZAL rs,offset	Branch On >= 0 And Link	r31=pc; if(rs>=0) pc+=offset*4	000001	rs	10001	offset
BGTZ rs,offset	Branch On > 0	if(rs>0) pc+=offset*4	000111	rs	00000	offset
BLEZ rs,offset	Branch On	if(rs<=0) pc+=offset*4	000110	rs	00000	offset
BLTZ rs,offset	Branch On < 0	if(rs<0) pc+=offset*4	000001	rs	00000	offset
BLTZAL rs,offset	Branch On < 0 And Link	r31=pc; if(rs<0) pc+=offset*4	000001	rs	10000	offset
BNE rs,rt,offset	Branch On Not Equal	if(rs!=rt) pc+=offset*4	000101	rs	rt	offset
BREAK	Breakpoint	epc=pc; pc=0x3c	000000	code	001101
J target	Jump	pc=pc_upper|(target<<2)	000010	target
JAL target	Jump And Link	r31=pc; pc=target<<2	000011	target
JALR rs	Jump And Link Register	rd=pc; pc=rs	000000	rs	00000	rd	00000	001001
JR rs	Jump Register	pc=rs	000000	rs	000000000000000	001000
MFC0 rt,rd	Move From Coprocessor	rt=CPR[0,rd]	010000	00000	rt	rd	00000000000
MTC0 rt,rd	Move To Coprocessor	CPR[0,rd]=rt	010000	00100	rt	rd	00000000000
SYSCALL	System Call	epc=pc; pc=0x3c	000000	00000000000000000000	001100
Memory Access
LB rt,offset(rs)	Load Byte	rt=*(char*)(offset+rs)	100000	rs	rt	offset
LBU rt,offset(rs)	Load Byte Unsigned	rt=*(Uchar*)(offset+rs)	100100	rs	rt	offset
LH rt,offset(rs)	Load Halfword	rt=*(short*)(offset+rs)	100001	rs	rt	offset
LBU rt,offset(rs)	Load Halfword Unsigned	rt=*(Ushort*)(offset+rs)	100101	rs	rt	offset
LW rt,offset(rs)	Load Word	rt=*(int*)(offset+rs)	100011	rs	rt	offset
SB rt,offset(rs)	Store Byte	*(char*)(offset+rs)=rt	101000	rs	rt	offset
SH rt,offset(rs)	Store Halfword	*(short*)(offset+rs)=rt	101001	rs	rt	offset
SW rt,offset(rs)	Store Word	*(int*)(offset+rs)=rt	101011	rs	rt	offset
```

