## Introduction

MIPS (Microprocessor without Interlocked Pipeline Stages) is a reduced instruction set computer (RISC) instruction set architecture developed by MIPS Technologies. Widely used in embedded systems, MIPS serves as an educational tool in computer architecture courses due to its simplicity and ease of understanding.

## Structure of MIPS Code

MIPS programs are typically structured with two main sections:

1. **`.data` section**:
   - This is where variables and data are declared.

2. **`.text` section**:
   - This section contains the program instructions.
   - Programs often end with a `syscall` instruction to execute system calls, such as printing or exiting.

## Key Features

### Register Naming
- Register names are prefixed with a dollar sign (`$`).
- Common registers include:
  - `$t0` to `$t9`: Temporary registers for computations.
  - `$s0` to `$s7`: Saved registers that retain their values across function calls.
  - `$a0` to `$a3`: Argument registers for function inputs.
  - `$v0`, `$v1`: Used for function return values and system call codes.

### Common Instructions and System Calls

| Instruction | Description                          |
|-------------|--------------------------------------|
| `li`        | Load immediate                       |
| `lw`        | Load word                            |
| `sw`        | Store word                           |
| `add`       | Addition                             |
| `sub`       | Subtraction                          |
| `mul`       | Multiplication                       |
| `div`       | Division (integer)                   |
| `move`      | Move data between registers          |
| `syscall`   | System call for input/output         |

#### Common System Call Codes (using `$v0` register)

| `li $v0, x` | System Call Code | Description                               |
|-------------|------------------|-------------------------------------------|
| `li $v0, 1` | Print Integer    | Outputs the integer in `$a0`              |
| `li $v0, 4` | Print String     | Outputs the string at the address in `$a0`|
| `li $v0, 5` | Read Integer     | Reads an integer from user input          |
| `li $v0, 8` | Read String      | Reads a string input into memory          |
| `li $v0, 10`| Exit Program     | Terminates the program                    |
| `li $v0, 11`| Print Character  | Outputs a single character in `$a0`       |
| `li $v0, 12`| Read Character   | Reads a single character from input       |
| `li $v0, 3` | Print Floating-Point Number | Outputs a float (in `$f12`) |

### Example of Using System Calls

Below is a simple example to show how to use various system calls in MIPS assembly.

```assembly
.data
    prompt: .asciiz "Enter a number: "   # Message for input prompt

.text
main:
    # Display a prompt for input
    li $v0, 4              # Syscall code for print_string
    la $a0, prompt         # Load address of the prompt
    syscall                # Make the syscall to print the prompt

    # Read an integer from user
    li $v0, 5              # Syscall code for read_integer
    syscall                # Read integer input into $v0
    move $t0, $v0          # Move the input value from $v0 to $t0

    # Display the entered number
    li $v0, 1              # Syscall code for print_integer
    move $a0, $t0          # Move the value in $t0 to $a0
    syscall                # Print the integer stored in $a0

    # Exit the program
    li $v0, 10             # Syscall code for exit
    syscall                # Terminate the program
    
```

## Writing MIPS Code

When writing MIPS assembly, follow these steps: 
1. Begin with the `.data` section for variable declarations. 
2. Follow with the `.text` section for your program instructions.
3. End your program with a `syscall` to execute the final system call (e.g., exit).
## Example Code

### Example 1: Basic Addition and Print

```assembly
.text
    li $t0, 12           # Load immediate value 12 into $t0
    li $t1, 14           # Load immediate value 14 into $t1
    add $t2, $t0, $t1    # Add $t0 and $t1, store result in $t2

    move $a0, $t2        # Move the result to $a0 for printing
    li $v0, 1            # System call code for print_integer
    syscall              # Print the integer

    li $v0, 10           # System call code for exit
    syscall              # Exit the program


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

## Example 3

```assembly
        .data                   # Section for declaring variables
num1:   .word   5               # Declare the first integer (5)
num2:   .word   10              # Declare the second integer (10)
result: .word   0               # To store the result (initially 0)

        .text                   # Section for code
        .globl  main            # Declare the main function

main:   
        # Load the values of num1 and num2 into registers
        lw      $t0, num1       # Load the value of num1 into register $t0
        lw      $t1, num2       # Load the value of num2 into register $t1

        # Perform addition
        add     $t2, $t0, $t1   # Add $t0 and $t1, store result in $t2

        # Store the result
        sw      $t2, result     # Store the result from $t2 into memory at the address of 'result'

        # Exit the program (system call to terminate)
        li      $v0, 10         # System call code 10 for exit
        syscall

```

# Different data types in MIPS

![[les différents types de données sur MIPS.pdf]]