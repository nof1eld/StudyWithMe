
## Introduction

MIPS (Microprocessor without Interlocked Pipeline Stages) is a reduced instruction set computer (RISC) instruction set architecture developed by MIPS Technologies. It's widely used in embedded systems and serves as an educational tool in computer architecture courses.

## Structure of MIPS Code

MIPS programs typically consist of two main sections:

1. `.data` section:
   - This is where variables are declared.

2. `.text` section:
   - This contains the program instructions.

At the end of the program, we use the `syscall` instruction to execute the code.

## Key Features

### Register Naming
- Register names are prefixed with a dollar sign ($)
- Examples: $t0, $t1, $t2, $a0

### Common Instructions

| Instruction | Description |
|-------------|-------------|
| `li`        | Load immediate |
| `add`       | Addition |
| `move`      | Move data between registers |
| `syscall`   | System call |

## Writing MIPS Code

When writing MIPS assembly, keep these points in mind:
1. Begin with the `.data` section for variable declarations.
2. Follow with the `.text` section for your program instructions.
3. End your program with a `syscall` to execute the code.

## Example

```.text
    li $t0, 12          # Load immediate value 12 into $t0
    li $t1, 14          # Load immediate value 14 into $t1
    add $t2, $t0, $t1   # Add $t0 and $t1, store result in $t2
    
    # Move the result to $a0 for printing
    move $a0, $t2       

	# System call code for print_integer
    li $v0, 1           

	# Make the system call to print the integer
    syscall             

	# System call code for exit
    li $v0, 10          
    
    # Make the system call to exit
    syscall             

```

## Example 2

```
.data
    message: .asciiz "Hello, MIPS!"

.text
main:
    li $v0, 4           # System call code for print_string
    la $a0, message     # Load address of the string
    syscall             # Make the system call

    li $v0, 10          # System call code for exit
    syscall             # Make the system call
```