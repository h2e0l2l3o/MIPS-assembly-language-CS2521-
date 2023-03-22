# MIPS-assembly-language-CS2521-
## MIPS(Microprocessor without Interlocked Pipelined Stages)
  * A type of computer processor architecture, specifically a Reduced Instruction Set Computer (RISC) architecture. It was developed by MIPS Technologies and is used in a variety of applications, including embedded systems, gaming consoles, and supercomputers.

## Assembly language
  * A low-level programming language that is specific to a particular processor architecture. It uses mnemonics and symbols to represent machine instructions, making it easier for humans to read and write code than using raw binary machine code.

## MIPS assembly language 
  * The specific assembly language used to write programs for the MIPS architecture. It is a human-readable representation of the machine code that the processor can execute directly.

## MARS
  * MARS, the Mips Assembly and Runtime Simulator, is an IDE capable of assembling and executing MIPS assembly language programs.
  
## SYSCALL TABLE
| Service | Value in $v0 | Arguments | Result
| --- | --- | --- | ---|
| print integer | 1 | $a0 = integer to print | |
| print float | 2 | $f12 = float to print | |
| print double | 3 | $f12 = double to print | |
| print string | 4 | $a0 = address of null-terminated string to print | |
| read integer | 5 | | $v0 contains integer read|
| read float | 6 | | $f0 contains float read|
| read double | 7 | | $f0 contains double read|
| exit (terminate execution) | 10 | | |

 ## Conditionals Table
| b label | Branches to label unconditionally |
| --- | --- |
| beq a1 a2 label | Branches to label if a1 = a2 |
| bne a1 a2 label | Branches to label if a1 ~= a2 |
| blt a1 a2 label | Branches to label if a1 < a2 |
| bgt a1 a2 label | Branches to label if a1 > a2 |
| ble a1 a2 label | Branches to label if a1 <= a2 |
| bge a1 a2 label | Branches to label if a1 >= a2 |

 ### Labs
 * Lab 1: Translate the following C++ code into MIPS
          > <br/> A=6;
          > <br/> B=9;
          > <br/> C=B-A;
          > <br/> cout<< C;
          
 * Lab 2: This code is modified from the previoud code. It will print out an additional statement if the result is greater than 10. “The sum is greater than 10”
    * Declare this new string in the .data section. 
    * Add a new label to the .txt section to jump there
    
 * Lab 3: Create a MIPS program that will take an integer input from the user, and output numbers the number the user entered, followed by every integer between that integer and its square(inclusive). For instance, if the user entered the number 3, the output might look like the following: 
<br/> Please enter a number: 
<br/> 3 
<br/> 3 
<br/> 4 
<br/> 5 
<br/> 6 
<br/> 7 
<br/> 8 
<br/> 9 
<br/> -- program is finished running -
      
