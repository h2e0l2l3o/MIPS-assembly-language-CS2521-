# MIPS-assembly-language-CS2521-
## MIPS(Microprocessor without Interlocked Pipelined Stages)
  * A type of computer processor architecture, specifically a Reduced Instruction Set Computer (RISC) architecture. It was developed by MIPS Technologies and is used in a variety of applications, including embedded systems, gaming consoles, and supercomputers.

## Assembly Language
  * A low-level programming language that is specific to a particular processor architecture. It uses mnemonics and symbols to represent machine instructions, making it easier for humans to read and write code than using raw binary machine code.

## MIPS Assembly Language 
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


 ## Conventions About What Registers Should Be Used
 * $a0-$a3: four argument registers in which to pass parameters
 * $v0-$v1: two value registers in which to return values
 * $t0-$t7: temporary registers (not preserved between calls)
 * $$s0-$s7: (less) temporary registers (preserved between calls)
 
 ## *jal*, *jr*, and *$ra*
  * *jal* instruction will jump to a label but will also store the address where it was called in a special register called the return address(*$ra*) register. *jr* is called jump register. It is used to go to and from our function.

 ## How the **Stack** works in MIPS: Storing data in the stack
  * Begin at the highest memory addresses and work its way downward as more data is added
  * Using the stack pointer (*$sp*) hold the current location in the Stack
  * To point to the next location in the Stack that doesn't have any data in it, use the return address register (*$ra*)
  * Decrement *$sp* in order to get to the next location in the Stack because we begin storing data at the highest memory address. (MIPS "word" = 4 bytes (32bits) --> decrement 4)
  * *sw* instruction tells the computer that we want to store a word at a location in memory, using an offset (the number outside of parentheses) and a register (*$sp*) 
  * The offset is assumed to be given in bytes, so 4 will be one word away from where *$sp* currently is.
  * Example:
 
    addi $sp, $sp, -8 # set the stack two words down

    addi $t0,$zero,23 # 23 is stored in $t0
    
    addi $t1, $zero, 12 # 12 is stored in $t1
    
    sw $t1, 0($sp) # $t1 stored 2 words from orig stack position
    
    sw $t0, 4($sp) # $t0 stored 1 word from orig stack position

 ## How the **Stack** works in MIPS: Getting data back from the stack
   * Use **load word (*lw*)** instruciton; it works in a similar way to *sw*
   * Example:
     
     lw $t0, 4($sp) # store data from (4bytes + $sp’s memory address) in $t0
     
     lw $t1, 0($sp) # store data from $sp’s memory address in $t1
     
     addi $sp,$sp,-8 # move the stack pointer back to where it was
     
 ### Labs
 * Lab 1: Translate the following C++ code into MIPS
 
            A=6;
 
            B=9;
          
            C=B-A;
          
            cout<< C;
          
 * Lab 2: This code is modified from the previoud code. It will print out an additional statement if the result is greater than 10. “The sum is greater than 10”
    * Declare this new string in the .data section. 
    * Add a new label to the .txt section to jump there
    
 * Lab 3: Create a MIPS program that will take an integer input from the user, and output numbers the number the user entered, followed by every integer between that integer and its square(inclusive). For instance, if the user entered the number 3, the output might look like the following: 
         
         Please enter a number: 
 
         3
         
         3
         
         4
         
         5
         
         6
         
         7
        
         8
         
         9
 
         -- program is finished running -
      
 * Lab 4: Create a program that, given a Celsius temperature as input, will output a Fahrenheit temperature, and ask if the user would like to continue. The program should exit if the user declines to continue. Use a function to do the conversion and assume that the user will input an integer.

     An example run of the program:
     
          Please input a Celsius temperature:
     
          100

          This is 212 degrees Fahrenheit.

          Would you like to continue? (y/n)

          y

          Please input a Celsius temperature:

          0

          This is 32 degrees Fahrenheit.

          Would you like to continue? (y/n)

          n

          Exiting.

          -- program is finished running –

 * Lab 5: Create a program that will continuously take in numbers from the user until the user enters 0, and will then output all of the numbers that were entered, in order. [Use a stack!!!]
For example, the program output might look something like the following:

        Please enter numbers, press (0) to exit:

        393

        21

        5

        120

        456

        3

        22

        0

        Your numbers were:

        393

        21

        5

        120

        456

        3

        22
