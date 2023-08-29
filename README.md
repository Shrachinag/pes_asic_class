# VLSI Physical Design for ASICs
## Objective
The objective of VLSI (Very Large Scale Integration) physical design for ASICs (Application-Specific Integrated Circuits) is to transform a logical design description (RTL - Register Transfer Level) into a physical layout that can be fabricated as an integrated circuit. This involves translating the high-level functional representation of the circuit into a physical implementation that meets design constraints, performance targets, and manufacturability requirements.

# SKILL OUTCOMES
+ Architectural Design
+ RTL Design / Behavioral Modeling
+ Floorplanning
+ placement
+ clock Tree Synthesis
+ Routing

# INSTALLATION
<details>
<summary> Riscv_toolchain Installation </summary>I installed the needed tools.

</details>	
	
 <details>
 <summary> Yosys </summary>
I installed Yosys using the following commands:
     
```
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys-master 
$ sudo apt install make 
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make 
$ sudo make install
```
     
Below is the screenshot showing sucessful launch:

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/e86b7422-3d3f-451c-8540-63f42a7893a8)

</details>

I installed iverilog using the following command:

```
sudo apt-get install iverilog
```

</details>

<details>  
    
<summary> Gtkwave </summary>

I installed gtkwave using the following command:

```
sudo apt-get install gtkwave
```

Below is the screenshot showing sucessful launch:

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/04f00a1e-3035-402e-9bb7-5d3ed7e93ae4)

</details> <details>

<summary> Magic </summary>

I installed magic using the following commands:

```
sudo apt-get install m4
sudo apt-get install tcsh
sudo apt-get install csh
sudo apt-get install libx11-dev
sudo apt-get install tcl-dev tk-dev
sudo apt-get install libcairo2-dev
sudo apt-get install mesa-common-dev libglu1-mesa-dev
sudo apt-get install libncurses-dev

```
Below is the screenshot showing sucessful launch:
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/f4cf561b-1367-481d-b9f8-b6e757a13bae)

</details>
	
https://github.com/kunalg123/riscv_workshop_collaterals/blob/master/run.sh
+ Download the run.sh
+ Open terminal
+ cd Downloads
+ ./run.sh
  
# TABLE OF CONTENTS
## DAY 1 
**Introduction to RISCV ISA and GNU Compiler Toolchain**
+ Introduction to Basic Keywords
  - [Introduction](#introduction)
  - [From Apps to Hardware](#from-apps-to-hardware)
  - [Detail Description of Course Content](#detail-description-of-course-content)

+ Labwork for RISCV Toolchain
  - [C Program](#c-program)
  - [RISCV GCC Compiler and Dissemble](#riscv-gcc-compiler-and-dissemble)
  - [Spike Simulation and Debug](#spike-simulation-and-debug)

+ Integer Number Representation  
  - [64-bit Unsigned Numbers](#64-bit-unsigned-numbers)
  - [64-bit Signed Numbers](#64-bit-signed-numbers)
  - [Labwork For Signed and Unsigned Numbers](#labwork-for-signed-and-unsigned-numbers)

## DAY 2 
**Introduction to ABI and Basic Verification Flow**
+ Application Binary Interface
  - [Introduction to ABI](#introduction-to-abi)
  - [Memory Allocation for Double Words](#memory-allocation-for-double-words)
  - [Load, Add and Store Instructions](#load,-add-and-store-instructions)
  - [32-Registers and their ABI Names](#32-registers-and-their-abi-names)

+ Labwork using ABI Function Calls
  - [Algorithm for C Program using ASM](#algorithm-for-c-program-using-asm)
  - [Review ASM Function Calls](#review-asm-function-calls)
  - [Simulate C Program using Function Call](#simulate-c-program-using-function-call)
# Introduction to Basic Keywords
## Introduction
- **ISA (Instruction Set Archhitecture)**
  - ISA defines the interface between a computer's hardware and its software, specifically how the processor and its components interact with the software instructions that drive the execution of tasks.
  - It encompasses a set of instructions, addressing modes, data types, registers, memory organization, and the mechanisms for executing and managing instructions.

- **RISC-V (Reduced Instruction Set Computing - Five)**.
  - It is an open-source Instruction Set Architecture (ISA) that has gained significant attention and adoption in the world of computer architecture and semiconductor design.
  - RISC architectures simplify the instruction set by focusing on a smaller set of instructions, each of which can be executed in a single clock cycle. This approach usually leads to faster execution of individual instructions. 

<img width="536" alt="image" src="https://github.com/Veda1809/pes_asic_class/assets/142098395/4eabe0b7-4581-419b-88e7-84c7ac1dac8e">

## From Apps to Hardware
1. **Apps:** Application software, often referred to simply as "applications" or "apps," is a type of computer software that is designed to perform specific tasks or functions for end-users.
2. **System software:** System software refers to a category of computer software that acts as an intermediary between the hardware components of a computer system and the user-facing application software. It provides essential services, manages hardware resources, and enables the execution of application programs. System software plays a critical role in maintaining the overall functionality, security, and performance of a computer system.'
3. **Operating System:** The operating system is a fundamental piece of software that manages hardware resources and provides various services for both users and application programs. It controls tasks such as memory management, process scheduling, file system management, and user interface interaction. Examples of operating systems include Microsoft Windows, macOS, Linux, and Android.

4. **Compiler:** A compiler is a type of software tool that translates high-level programming code written by developers into assembly-level language.

5. **Assembler:** An assembler is a software tool that translates assembly language code into machine code or binary code that can be directly executed by a computer's processor.

6. **RTL:** RTL serves as an abstraction level in the design process that represents the behavior of a digital circuit in terms of registers and the operations that transfer data between them.

 7. **Hardware:** Hardware refers to the physical components of a computer system or any electronic device. It encompasses all the tangible parts that make up a computing or electronic device and enable it to perform various tasks.

## Detail Description of Course Content
**Pseudo Instructions:** Pseudo-instructions are used to simplify programming, improve code readability, and reduce the number of explicit instructions a programmer needs to write. They are especially useful for common programming patterns that involve multiple instructions.
`Ex: li, mv`.

**Base Integer Instructions:** The term "base integer instructions" refers to the fundamental set of instructions that form the foundation for performing basic arithmetic, logical, and data movement operations.
`Ex: add, sub, and, or, xor, sll`.

**Multiply Extension Intructions:** The RISC-V architecture includes a set of multiply and multiply-accumulate (MAC) extension instructions that enhance the instruction set to perform efficient multiplication and multiplication-accumulate operations.
`Ex: mul, mulh, mulhu, mulhsu`.

**Single and Double Precision Floating Point Extension:** The RISC-V architecture includes floating-point extensions that provide support for both single-precision (32-bit) and double-precision (64-bit) floating-point arithmetic operations. These extensions are often referred to as the "F" and "D" extensions, respectively. Floating-point arithmetic is essential for handling real numbers with fractional parts and for performing accurate calculations involving decimal values.

**Application Binary Interface:** ABI stands for "Application Binary Interface." It is a set of rules and conventions that govern how software components interact with each other at the binary level. The ABI defines various aspects of program execution, including how function calls are made, how parameters are passed and returned, how memory is allocated and managed, and more.

**Memory Allocation and Stack Pointer** 
- Memory allocation refers to the process of assigning and managing memory segments for various data structures, variables, and objects used by a program. It involves allocating memory space from the system's memory pool and releasing it when it is no longer needed to prevent memory leaks.
- The stack pointer is a register used by a program to keep track of the current position of the program's execution on the call stack. 

# Labwork for RISCV Toolchain
## C Program
We wrote a C program for calculating the sum from 1 to n using a text editor, leafpad.

`leafpad sumton.c`
``` c
#include<stdio.h>

int main(){
	int i, sum=0, n=5;
	for (i=1;i<=n; ++i) {
	sum +=i;
	}
	printf("Sum of numbers from 1 to  5 %d is %d \n",n,sum);
	return 0;
}
```
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/910e65b6-6b9d-45d2-a015-d5c9e11dcc88)

Using the gcc compiler, we compiled the program to get the output.

`gcc sumton.c`
`.\a.out`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/01ae2507-a475-45e9-9402-8d37a1d02c05)


## RISCV GCC Compiler and Dissemble

Using the riscv gcc compiler, we compiled the C program.

`riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c`

Using `ls -ltr sum1ton.c`, we can check that the object file is created.

To get the dissembled ALP code for the C program, 

`riscv64-unknown-elf-objdump -d sum1ton.o | less` .

In order to view the main section, type 
`/main`.
                            q
Here, since we used -O1 optimisation, the number of instructions are 15.

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/e3c9e14c-0092-4fc7-a96f-04f2ba5c6e37)


When we use -Ofast optimisation, we can see that the number of instructions have been reduced to 12.

<img width="422" alt="image" src="https://github.com/Veda1809/pes_asic_class/assets/142098395/3eb7afcd-0645-4340-bcac-ae2dc3258ce3">

- -Onumber : level of optimisation required
- -mabi : specifies the ABI (Application Binary Interface) to be used during code generation according to the requirements
- -march : specifies target architecture

In order to view the different options available for these fields, use the following commands

go to the directory where riscv64-unkonwn-elf is present

- -O1 : ``` riscv64-unkonwn-elf --help=optimizer```
- -mabi : ```riscv64-unknown-elf-gcc --target-help```
- -march : ```riscv64-unknown-elf-gcc --target-help```

For different instances,
- use the command ```riscv64-unknown-elf-objdump -d 1_to_N.o | less```
- use ``` /instance``` to search for an instance 
- press ENTER
- press ```n``` to search next occurance
- press ```N``` to search for previous occurance. 
- use ```esc :q``` to quit


## Spike Simulation and Debug

`spike pk sum1ton.o` is used to check whether the instructions produced are right to give the correct output.


![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/cb5e81cf-1629-4e94-adb7-994d9ebb2230)
)



`spike -d pk sum1ton.c` is used for debugging.

The contents of the registers can also be viewed.


![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/602b5f9b-9dbf-455b-b59d-eff69e780990)




- press ENTER : to show the first line and successive ENTER to show successive lines
- reg 0 a2 : to check content of register a2 0th core
- q : to quit the debug process

# Integer Number Representation 

## Unsigned Numbers
- Unsigned numbers, also known as non-negative numbers, are numerical values that represent magnitudes without indicating direction or sign.
- Range: [0, (2^n)-1 ]

## Signed Numbers
- Signed numbers are numerical values that can represent both positive and negative magnitudes, along with zero.
- Range : Positive : [0 , 2^(n-1)-1]
          Negative : [-1 to 2^(n-1)]
 
## Labwork

We wrote a C program that shows the maximum and minimum values of 64bit unsigned numbers.

``` c
#include <stdio.h>
#include <math.h>

int main(){
	unsigned long long int max = (unsigned long long int) (pow(2,64) -1);
	unsigned long long int min = (unsigned long long int) (pow(2,64) *(-1));
	printf("lowest number represented by unsigned 64-bit integer is %llu\n",min);
	printf("highest number represented by unsigned 64-bit integer is %llu\n",max);
	return 0;
}
```
![S![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/2de347af-b287-446f-ab2d-4ca6c2ad3611)




# Application Binary Interface
## Introduction to ABI
+ An Application Binary Interface (ABI) is a set of rules and conventions that dictate how binary code interacts with and communicates with other binary code, typically at the level of machine code or compiled code. In simpler terms, it defines the interface between two software components or systems that are written in different programming languages, compiled by different compilers, or running on different hardware architectures.
+ The ABI is crucial for enabling interoperability between different software components, such as different libraries, object files, or even entire programs. It allows components compiled independently and potentially on different platforms to work seamlessly together by adhering to a common set of rules for communication and data representation.
## Memmory Allocation for Double Words
64-bit number (or any multi-byte value) can be loaded into memory in little-endian or big-endian. It involves understanding the byte order and arranging the bytes accordingly
1. **Little-Endian:**
In little-endian representation, you store the least significant byte (LSB) at the lowest memory address and the most significant byte (MSB) at the highest memory address.
2. **Big-Endian:**
In big-endian representation, you store the most significant byte (MSB) at the lowest memory address and the least significant byte (LSB) at the highest memory address.
#### For example, consider the 64-bit hexadecimal value 0x0123456789ABCDEF. 
In Little-Endian representation, it would be stored as follows in memory:

<img width="453" alt="image" src="https://github.com/Veda1809/pes_asic_class/assets/142098395/8c63e751-8882-4b1e-a2f8-84da628ee604">


In Big-Endian representation, it would be stored as follows in memory:

<img width="454" alt="image" src="https://github.com/Veda1809/pes_asic_class/assets/142098395/3954540e-800f-4503-97ef-6c77daacd058">

## Load, Add and Store Instructions
Load, Add, and Store instructions are fundamental operations in computer architecture and assembly programming. They are often used to manipulate data within a computer's memory and registers.
1. **Load Instructions:**
Load instructions are used to transfer data from memory to registers. They allow you to fetch data from a specified memory address and place it into a register for further processing.

Example `ld x6, 8(x5)`

In this Example
- `ld` is the load double-word instruction.
- `x6` is the destination register.
- `8(x5)` is the memory address pointed to by register `x5` (base address + offset).
2. **Store Instructions:**
Store instructions are used to write data from registers into memory.They store values from registers into memory addresses

Example `sd x8, 8(x9)`

In this Example
- `sd` is the store double-word instruction.
- `x8` is the source register.
- `8(x9)` is the memory address pointed to by register `x9` (base address + offset).
3. Add Instructions:
  Add instructions are used to perform addition operations on registers. They add the values of two source registers and store the result in a destination register.

Example `add x9, x10, x11`

In this Example
- `add` is the add instruction.
- `x9` is the destination register.
- `x10` and `x11` are the source registers.
## 32-Registers and their ABI Names
The choice of the number of registers in a processor's architecture, such as the RISC-V RV64 architecture with its 32 general-purpose registers, involves a trade-off between various factors. While modern processors can have more registers but increasing the number of registers could lead to larger instructions, which would take up more memory and potentially slow down instruction fetch and decode.
#### ABI Names
ABI names for registers serve as a standardized way to designate the purpose and usage of specific registers within a software ecosystem. These names play a critical role in maintaining compatibility, optimizing code generation, and facilitating communication between different software components. 

<img width="430" alt="image" src="https://github.com/Veda1809/pes_asic_class/assets/142098395/3b7aed64-37cd-492f-b9b5-cd840103566a">

# Labwork using ABI Function Calls
## Algorithm for C Program using ASM
- Incorporating assembly language code into a C program can be done using inline assembly or by linking separate assembly files with your C code.
- When you call an assembly function from your C code, the C calling convention is followed, including pushing arguments onto the stack or passing them in registers as required.
- The program executes the assembly function, following the assembly instructions you've provided.

## Review ASM Function Calls
- We wrote C code in one file and your assembly code in a separate file.
- In the assembly file, we declared assembly functions with appropriate signatures that match the calling conventions of your platform.

**C Program**
`custom1to9.c`
  ``` c
  #include <stdio.h>
  
  extern int load(int x, int y);
  
  int main()
  {
    int result = 0;
    int count = 9;
    result = load(0x0, count+1);
    printf("Sum of numbers from 1 to 9 is %d\n", result);
  }
```
**Asseembly File**
`load.s`
``` s
.section .text
.global load
.type load, @function

load:

add a4, a0, zero
add a2, a0, a1
add a3, a0, zero

loop:

add a4, a3, a4
addi a3, a3, 1
blt a3, a2, loop
add a0, a4, zero
ret
```
## Simulate C Program using Function Call
**Compilation:** To compile C code and Asseembly file use the command

`riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o custom1to9.o custom1to9.c load.s` 

this would generate object file `custom1to9.o`.

**Execution:** To execute the object file run the command 

`spike pk custom1to9.o`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/ea24d1ad-91e9-4611-a717-5813b8670848)


# Day-3
## Introduction to Open-Source Simulator iVerilog
<details>
<summary> Introduction to iVerilog Design Testbench </summary>

 - **Simulator**
   - It is a tool used for simulating the design. It looks for the changes on the input signals to evaluate the outputs.
   - If there is no change in the inputs, the simulator doesn't evaluate the outputs.
   - RTL is checked for adherence to the spec by simulating the design.
   - The tool used here is **iverilog** .

- **iVerilog**
  -  It is an open-source Verilog simulator used for testing and simulating digital circuit designs described in the Verilog hardware description language (HDL).
  -  Both the design and the testbench are fed to the simulator and it produces a vcd (value change dump) file.
  -  In order to view the vcd file, we use the GTKwave where we can see the wave forms.
    
  ![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/0632e281-deb8-4e50-bb94-cb641b6f394e)

- **Design**
  - It is the actual verilog code or set of verilog codes which ahs the intended functionality to meet with the required specifications.
  - Verilog is used to describe the behavior and structure of digital circuits at different levels of abstraction, from high-level system descriptions down to low-level gate-level representations. 

- **Testbench**
  - A testbench is a specialized Verilog module or program used to verify the functionality and behavior of another Verilog module, circuit, or design. Testbenches are essential for testing and simulating digital designs before they are synthesized or manufactured as physical chips.
  - It is a setup to apply stimulus to the design to check its functionality.
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/b3dc0af7-4f24-4178-b944-5d57477d9854)


</details>

## Labs using iVerilog and GTKwave
<summary> Introduction to Lab </summary>

+ Make a directory named vlsi `mkdir vlsi`.
+ `cd vlsi`.
+ `git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git`
+ Creates a folder called `sky130RTLDesignAndSynthesisWorkshop` in the `vlsi` directory.

  - my_lib : contains all the library files

  - lib : contains sky130 standard cell library used for our synthesis

  - verilog_model : contains all the standard cell verilog modules of the standard cells contained in the .lib

  - verilog_files : contains all the verilog source files and testbench files which are required for labs

</details>

<details>
<summary> iVerilog GTKwave Part-1 </summary>	


+ `cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files`

+ we have loaded the source code along with the testbench code into the iverilog simulator

+ `iverilog good_mux.v tb_good_mux.v`

+ We can see that an output file `a.out` has been created.

+ `./a.out`

+ The output of the iverilog, a vcd file,  is created which is loaded into the simualtor gtkwave.

+ ` gtkwave tb_good_mux.vcd `

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/fa45d0cc-d20e-4820-85a6-a66e6b41ca34)
 
!![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/0dfbd38b-affe-4263-a43a-10509be21cf9)
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/512e58ae-3fbd-443c-9f32-6edb5c1ea9a9)


</details>

<details>
<summary> iVerilog GTKwave Part-2 </summary>

+ In order to view the contents in the files,

+ `gvim tb_good_mux.v -o good_mux.v`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/4cdf1af3-8b9d-44f7-9f19-15ea84bfacfb)

</details>

## Introduction to Yosys and Logic Synthesis

<details>
<summary> Introduction to Yosys </summary>

+ **Synthesizer**
  - It is a tool used for converting RTL design code to netlist.
  - Here, the synthesizer used is **Yosys**.

+ **Yosys**
  - It is an open-source framework for Verilog RTL synthesis and formal verification.
  - Yosys provides a collection of tools and algorithms that enable designers to transform high-level RTL (Register Transfer Level) descriptions of digital circuits into optimized gate-level representations suitable for physical implementation on hardware.

 ![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/ed93b17c-aa25-40c4-af74-05da5408e6c0)


   - Design and .lib files are fed to the synthesizer to get a netlist file.
   - **Netlist** is the representation of the design in the form of standard cells in the .lib
     
+ Commands used to perform different opertions:
  - `read_verilog` to read the design
  - `read_liberty` to read the .lib file
  - `write_verilog` to write out the netlist file
 
+ To verify the synthesis

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/2e69a27b-a6cd-4933-aa6d-7ad073a394b3)


   - Netlist along with the tesbench is fed to the iverilog simulator.
   - The vcd file generated is fed to the gtkwave simulator.
   - The output on the simulator must be same as the output observed during RTL simulation.
   - Same RTL testbench can be used as the primary inputs and primary outputs remain same between the RTL design and synthesised netlist.

</details>

<details>
<summary> Introduction to Logic Synthesis </summary>

+ **Logic Synthesis**
  - Logic synthesis is a process in digital design that transforms a high-level hardware description of a digital circuit, typically in a hardware description language (HDL) like Verilog or VHDL, into a lower-level representation composed of logic gates and flip-flops.
  - The goal of logic synthesis is to optimize the design for various criteria such as performance, area, power consumption, and timing.

 + **.lib**
   - It is a collection of logical modules like And, Or, Not etc.
   - It has different flavors of same gate like 2 input AND gate, 3 input AND gate etc with different performace speed.
  
+ **Why different flavors  of gate?**
  - In order to make a circuit faster, the clock frequency should be high.
  - For that, the time period of the clock should be as low as possible.
  
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/40b58217-a022-4e76-901a-4fe49c06132d)


+ In a sequential circuit, clock period depends on:
  - Clock to Q of flip-flop A.
  - Propagation delay of combinational circuit.
  - Setup time of flip-flop B.
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/8d687386-01fe-431d-8907-34455d6c8123)


+ **Why need fast and slow cells?**
  - To ensure that there are no HOLD issues at flip-flop B, we require slow cells.
  - For a smaller propagation time, we need faster cells.
  - The collection forms the .lib

+ **Faster Cells vs Slower Cells**
  - Load in digital circuit is of Capacitence.
  - Faster the charging or dicharging of capacitance, lesser is the cell delay.
  - However, for a quick charge/ discharge of capacitor, we need transistors capable of sourcing more current i.e, we need **wide transistors**.
  - Wider transistors have lesser delay but consume more area and power.
  - Narrow transistors have more delay but consume less area and performance.
  - Faster cells come with a cost of area and power.
 
+ **Selection of the Cells**
  - We have to guide the Synthesizer to choose the flavour of cells that is optimum for implementation of logic circuit.
  - More use of faster cells leads to bad circuit in terms of power and area and also hold time violations.
  - More use of slower cells leads to sluggish circuits amd may not meet the performance needs.
  - Hence the guidance is offered to the synthesiser in the form of **constraints**.
 
</details>

## Labs using Yosys and Sky130 PDKs
<details>
<summary> Yosys good_mux  </summary>	

+ To invoke **yosys**
  - `cd`
  - `cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files`
  - Type `yosys`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/e6876aba-77b4-4b34-94a3-453196125d26)



+ To read the library
    
     ` read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
    
+ To read the design

    `read_verilog good_mux.v`

 + To syntheis the module

      ` synth -top good_mux`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/fb4696e8-f9e0-4e34-a4c7-ffc868a45de8)

  
  
 + To generate the netlist

  `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`

<img width="865" alt="Screenshot 2023-08-29 at 7 09 34 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/2b24640f-9f16-4946-bfe6-5c8b5a1c016c">
b)

 
It gives a report of what cells are used and the number of input and output signals.

+ To see the logic realised

  `show`
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/387e9e9d-74e6-4dd6-b97d-08f4ffe3ebe3)

  The mux is completely realised in the form of sky130 library cells.

+ To write the netlist

   - `write_verilog good_mux_netlist.v`
   - `!gvim good_mux_netlist.v`
     
   - To view a simplified code
     
     ` write_verilog -noattr good_mux_netlist.v`
     
     `!gvim good_mux_netlist.v`
  
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/5de7383d-ba57-48f0-92a9-14957e309a04)

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/6321c9ae-6dd2-4c1a-8c57-1588c7f56e79)



</details>

# Day 4
## Introduction to Timing Dot Libs
<details>
<summary> Introduction to Dot Lib </summary>	

+ To view the contents in the .lib

  `gvim ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
  <img width="800" alt="Screenshot 2023-08-29 at 7 13 04 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/b6ad06b2-f22b-4fad-a3b6-1f923cbb32f3">

  + The first line in the file `library ("sky130_fd_sc_hd__tt_025C_1v80") ` :
    
    - tt : indicates variations due to process and here it indicates **Typical Process**.
    - 025C : indicates the variations due to temperatures where the silicon will be used.
    - 1v80 : indicates the variations due to the voltage levels where the silicon will be incorporated.
+ It also displays the units of various parameters.
+ 
<img width="522" alt="Screenshot 2023-08-29 at 7 15 28 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/b58a1fd8-1383-4f7e-8aad-8c654f660160">
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/2208b526-9753-4d23-b0ad-6a9c681a5ba4)

+ It gives the features of the cells
+ To enable line number `:se nu`
+ To view all the cells `:g//`
+ To view any instance `:/instance`
+ Since there are 5 inputs, for all the 32 possible combinations, it gives the delay, power and all the other parameters for each cell.
+ The below image shows the power consumption and area comparision.
  
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/e5dcf5c3-166f-4a51-8096-853f45d97ff5)

</details>

## Hierarchical vs Flat Synthesis
<details>
<summary> Hierarchical Synthesis Flat Synthesis </summary>	

**Hierarchical Synthesis**
  Hierarchical synthesis is an approach in digital design and logic synthesis where complex designs are broken down into smaller, more manageable modules or sub-circuits, and each module is synthesized individually. These synthesized modules are then integrated back into the overall design hierarchy. This approach helps manage the complexity of large designs and allows designers to work on different parts of the design independently.
  
+ The file we used in this lab is `multiple_modules.v`

  - `cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files`
  -  `gvim multiple_modules.v`


![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/1b5abcfc-c9f9-4624-8ebf-39cf13d8bd73)




+  `multiple_modules` instantiates `sub_module1` and `sub_module2`

+  Launch `yosys`
+  read the library file  `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+  read the verilog file ` read_verilog multiple_modules.v`
+  `synth -top multiple_modules` to set it as top module

 ![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/cbad88b3-3196-4296-8559-faaea1f44485)

 ![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/0d9a593a-2327-43c5-82eb-316e20a2103e)

  
+  `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ To view the netlist `show multiple_modules`

 ![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/03051d2c-110c-47ab-beb4-7aa3c9c47ed0)


- Here it shows `sub_module1` and `sub_module2` instead of AND gate and OR gate.

+ `write_verilog -noattr multiple_modules_hier.v`
+ `!gvim multiple_modules_hier.v`
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/0a633ba5-9864-42ec-a30b-3d642ba24333)

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/bcd7ad03-ac55-42a5-a1d5-522e276f31e1)


 **Flattened Synthesis**
  Flattened synthesis is the opposite of hierarchical synthesis. Instead of maintaining the hierarchical structure of the design during synthesis, flattened synthesis combines all modules and sub-modules into a single, flat representation. This means that the entire design is synthesized as a single unit, without preserving the modular organization present in the original high-level description.

+  Launch `yosys`
+  read the library file  `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+  read the verilog file ` read_verilog multiple_modules.v`
+  `synth -top multiple_modules` to set it as top module
+  `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `flatten` to write out a flattened netlist
+ `show`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/305b722c-cbe4-43b6-97ad-346a33d98486)

+ `write_verilog -noattr multiple_modules_flat.v`
+ `!gvim multiple_modules_flat.v`
  
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/1d3b84ca-83e7-4e2e-aac4-b43b9d758f41)

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/98c108e7-6782-4684-93f3-d3f656f8692f)


</details>

## Various Flop Coding Styles and Optimization
<details>
<summary> Why Flops and Flop Coding Styles</summary>	

**Why do we need a Flop?**

+ A flip-flop (often abbreviated as "flop") is a fundamental building block in digital circuit design.
+ It's a type of sequential logic element that stores binary information (0 or 1) and can change its output based on clock signals and input values.
+ In a combinational circuit, the output changes after the propagation delay of the circuit once inputs are changed.
+ During the propagation of data, if there are different paths with different propagation delays, then a glitch might occur.
+ There will be multiple glitches for multiple combinational circuits.
+ Hence, we need flops to store the data from the combinational circuits.
+ When a flop is used, the output of combinational circuit is stored in it and it is propagated only at the posedge or negedge of the clock so that the next combinational circuit gets a glitch free input thereby stabilising the output.
+ We use control pins like **set** and **reset** to initialise the flops.
+ They can be synchronous and asynchronous.

**D Flip-Flop with Asynchronous Reset**
+ When the reset is high, the output of the flip-flop is forced to 0, irrespective of the clock signal.
+ Else, on the positive edge of the clock, the stored value is updated at the output.

 `gvim dff_asyncres_syncres.v`
 
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/b66b5a86-af5c-44ae-b9df-75e60f1bcbea)

**D Flip_Flop with Asynchronous Set**
+ When the set is high, the output of the flip-flop is forced to 1, irrespective of the clock signal.
+ Else, on positive edge of the clock, the stored value is updated at the output.

`gvim dff_async_set.v`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/e7914b22-e8b3-4ffe-b833-48895da39144)

**D Flip-Flop with Synchronous Reset**
+ When the reset is high on the positive edge of the clock, the output of the flip-flop is forced to 0.
+ Else, on the positive edge of the clock, the stored value is updated at the output.

  `gvim dff_syncres.v`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/229412e9-37c1-45ad-ab98-e266cff00b3d)


**D Flip-Flop with Asynchronous Reset and Synchronous Reset**
+ When the asynchronous resest is high, the output is forced to 0.
+ When the synchronous reset is high at the positive edge of the clock, the output is forced to 0.
+ Else, on the positive edge of the clock, the stored value is updated at the output.
+ Here, it is a combination of both synchronous and asynchronous reset DFF.

`gvim dff_asyncres_syncres.v`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/83f79197-c84e-4708-88aa-25a111ad7eb1)

</details>

<details>
<summary> Lab Flop Synthesis Simulations </summary>	

**D Flip-Flop with Asynchronous Reset**
+ **Simulation**
  - `cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files`
  - `iverilog dff_asyncres.v tb_dff_asyncres.v`
  - `./a.out`
  - `gtkwave tb_dff_asyncres.vcd`
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/6514d2fa-7780-4aff-85f9-0641331b527b)


+ **Synthesis**
  - `cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files`
  - `yosys`
  - `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
  - `read_verilog dff_asyncres.v`
  - `synth -top dff_asyncres`
  - `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
  - `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
  - `show`

    ![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/18b1e1f7-3c1e-4ca6-b266-2914d88a591d)


 **D Flip_Flop with Asynchronous Set**
 + **Simulation**
   - `cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files`
   - `iverilog dff_async_set.v tb_dff_async_set.v`
   - `./a.out`
   - `gtkwave tb_dff_async_set.vcd`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/f3627864-bc2c-4199-9d1f-9d947b4ce619)



+ **Synthesis**
  - `cd vlsi/sky130RTLDesignAndSynthesisWorkshop/verilog_files`
  - `yosys`
  - `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
  - `read_verilog dff_async_set.v`
  - `synth -top dff_async_set`
  - `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
  - `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
  - `show` 
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/1b0b01a3-00b3-4fa1-8027-773d3aa228ac)

**D Flip-Flop with Synchronous Reset**
+ **Simulation**
   - `cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files`
   - `iverilog dff_syncres.v tb_dff_syncres.v`
   - `./a.out`
   - `gtkwave tb_dff_syncres.vcd`
    

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/045a7ff5-42f7-49c0-9968-f6e118f2065a)

  

+ **Synthesis**
  - `cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files`
  - `yosys`
  - `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
  - `read_verilog dff_syncres.v`
  - `synth -top dff_syncres`
  - `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib `
  - `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
  - `show`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/df5c2b9a-da1f-4001-b337-a5fee0f35a0a)


</details>

<details>
<summary> Interesting Optimisations </summary>	

+ `gvim mult_2.v`

<img width="879" alt="Screenshot 2023-08-29 at 7 35 42 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/4562ae30-da8b-4185-a5c2-dafd13ec2dbe">


+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog mult_2.v`
+ `synth -top mul2`

 ![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/0f27d099-ed61-42ee-bf6a-d2c7ef704865)


+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/58e73cf3-6e64-4adf-8359-069076a361f5)


</details>

# Day 5
## Introduction to Optimisations 

<details>
<summary> Combinational Optimisation </summary>
	
+ Combinational logic refers to logic circuits where the outputs depend only on the current inputs and not on any previous states.
+ Combinational optimization is a field of study in computer science and operations research that focuses on finding the best possible solution from a finite set of options for problems that involve discrete variables and have no inherent notion of time.
+ Optimising the combinational logic circuit is squeezing the logic to get the most optimized digital design so that the circuit finally is area and power efficient.
+ Techniques for Optimisations:
  - **Constant propagation** is an optimization technique used in compiler design and digital circuit synthesis to improve the efficiency of code and circuit implementations by replacing variables or expressions with their constant values where applicable.
  - **Boolean logic optimization**, also known as logic minimization or Boolean function simplification, is a process in digital design that aims to simplify Boolean expressions or logic circuits by reducing the number of terms, literals, and gates required to implement a given logical function.

</details>

<details>
<summary> Sequential Logic Optimisations </summary>	

+ Sequential logic optimizations involve improving the efficiency, performance, and resource utilization of digital circuits that include memory elements like flip-flops and latches.
+ Optimizing sequential logic is crucial in ensuring that digital circuits meet timing requirements, consume minimal power, and occupy the least possible area while maintaining correct functionality.
+ Optimisation methods:
  - **Sequential constant propagation**, also known as constant propagation across sequential elements, is an optimization technique used in digital design to identify and propagate constant values through sequential logic elements like flip-flops and registers. This technique aims to replace variable values with their known constant values at various stages of the logic circuit, optimizing the design for better performance and resource utilization.
  - **State optimization**, also known as state minimization or state reduction, is an optimization technique used in digital design to reduce the number of states in finite state machines (FSMs) while preserving the original functionality.
  - **Sequential logic cloning**, also known as retiming-based cloning or register cloning, is a technique used in digital design to improve the performance of a circuit by duplicating or cloning existing registers (flip-flops) and introducing additional pipeline stages. This technique aims to balance the critical paths within a circuit and reduce its overall clock period, leading to improved timing performance and better overall efficiency.
  - **Retiming** is an optimization technique used in digital design to improve the performance of a circuit by repositioning registers (flip-flops) along its paths to balance the timing and reduce the critical path delay. The primary goal of retiming is to achieve a shorter clock period without changing the functionality of the circuit.
 
</details>

## Combinational Logic Optimisations

<details>
<summary> opt_check </summary>	
	
+ `gvim opt_check.v`

  ![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/1ac70cbb-777b-4e24-9dfa-00d5810cf206)


+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog opt_check.v`
+ `synth -top opt_check`
+ `opt_clean -purge`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

 ![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/152d92fe-1aa0-4133-9e02-a06b503ba2d5)


  ![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/0bb4c8bf-c4ea-492e-b127-cdd60bdc04d6)

</details>

<details>
<summary> opt_check2 </summary>	
	
+ `gvim opt_check2.v`

 ![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/0fff454c-a841-46c2-9377-aff32f5bdeea)

  
+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog opt_check2.v`
+ `synth -top opt_check2`
+ `opt_clean -purge`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/a0e1b6e5-8cb1-49a9-9a6e-ec7eb0d9ecfb)


![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/dda1fbab-467b-4dc0-b8eb-80b7e62b66bd)

</details>

<details>
<summary> opt_check3 </summary>	
	
+ `gvim opt_check3.v`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/52db2fcb-8955-4e96-ae1b-3035c245022e)

+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog opt_check3.v`
+ `synth -top opt_check3`
+ `opt_clean -purge`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/69956986-bdb4-443f-ad45-e2499adc3f25)


![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/fb9d26c7-70b5-480a-8232-f7f4059f398c)


</details>

<details>
<summary> opt_check4 </summary>
	
+ `gvim opt_check4.v`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/f0691816-3ec5-4d08-8cad-bc24d51fa594)


+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog opt_check4.v`
+ `synth -top opt_check4`
+ `opt_clean -purge`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/1ac5b9dd-3887-4f0f-81be-665833c0c041)


![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/e7102762-5514-4d67-8f91-ae494b6930a6)


</details>

<details>
<summary> multiple_module_opt </summary>
	
+ `gvim multiple_module_opt.v`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/7017a8b1-e9ce-4d41-8a3b-8c211a35a234)


+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog multiple_module_opt.v`
+ `synth -top multiple_module_opt`
+ `opt_clean -purge`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`
 
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/ce9c7ea8-3459-43b9-849f-3e5c9009b35c)
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/d6be3829-2c62-4132-a8d3-cbd8dead3314)


</details>

## Sequential Logic Optimisations

<details>
<summary> dff_const1 </summary>	

+ `gvim dff_const1.v`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/7721c817-5003-41c7-a0ee-372afed562c1)


**Simulation**

+ `iverilog dff_const1.v tb_dff_const1.v`
+ `/a.out`
+ `gtkwave tb_dff_const1.vcd`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/72c3be7d-24b5-4bea-8cca-4012d6201525)



**Synthesis**

+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog dff_const1.v`
+ `synth -top dff_const1`
+ `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib `
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/5b4e9166-d2bf-4541-9b3f-8f2cdd0d7bf5)


![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/2ea488c0-d5af-4f35-a21d-a7103ee4b831)

</details>

<details>
<summary> dff_const2 </summary>	

+ `gvim dff_const2.v`

<img width="355" alt="image" src="https://github.com/Veda1809/pes_asic_class/assets/142098395/e0e6e4da-0429-49db-b687-d99ab365ed17">

**Simulation**

+  `iverilog dff_const2.v tb_dff_const2.v`
+ `/a.out`
+ `gtkwave tb_dff_const2.vcd`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/3dc78352-158b-431e-a70c-8f9c733e6f05)


 **Synthesis**
 
+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog dff_const2.v`
+ `synth -top dff_const2`
+ `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib `
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/d3d2e049-1e20-4d4b-92b1-fc363253c6e3)



![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/6375243c-380a-4a83-bb39-a42810c4bb25)![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/1ee184c4-7f89-44a1-b513-c6679a7e32d4)



</details>

<details>
<summary> dff_const3 </summary>

+ `gvim dff_const3.v`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/efd47eba-6563-4e7b-a3f7-5a0a99ec6079)

**Simulation**

+ `iverilog dff_const3.v tb_dff_const3.v`
+ `/a.out`
+ `gtkwave tb_dff_const3.vcd`

<img width="652" alt="Screenshot 2023-08-29 at 7 58 29 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/28a58e3d-4c22-4367-8de8-82bd0a8e74ea">


**Synthesis**

+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog dff_const3.v`
+ `synth -top dff_const3`
+ `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib `
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/c9c281cd-1e78-4b71-93a3-b0a693a01fab)

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/5a501822-b2ee-43ee-a5f4-3996d13a3982)


</details>

<details>
<summary> dff_const4 </summary>	

+ `gvim dff_const4.v`



**Simulation**

+ `iverilog dff_const4.v tb_dff_const4.v`
+ `/a.out`
+ `gtkwave tb_dff_const4.vcd`

<img width="857" alt="Screenshot 2023-08-29 at 8 03 18 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/ad027760-6103-434c-9201-84454a8587e9">


**Synthesis**

+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog dff_const4.v`
+ `synth -top dff_const4`
+ `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib `
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/3407b373-852f-40d0-87b9-63017a5d65fd)


![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/1aefd1a6-0d1b-4a51-b997-969003a2b4c2)

</details>


**Synthesis**


<summary> counter_opt </summary>

 + `gvim counter_opt.v`

<img width="701" alt="Screenshot 2023-08-29 at 8 00 11 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/89f927c5-d579-47a3-bd06-8a330beb2a73">


**Simulation**
+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog counter_opt.v`
+ `synth -top counter_opt`
+ `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/fba506b1-b76c-4015-957c-90958bc25aa4)


![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/82505b07-494e-47ba-91aa-c275e9a77eef)


</details>

<details>
<summary> counter_opt2 </summary>	

+ `gvim counter_opt2.v`

<img width="682" alt="Screenshot 2023-08-29 at 8 06 42 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/857a3b0d-49c4-4e74-8873-203396c0f1dd">


+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog counter_opt2.v`
+ `synth -top counter_opt2`
+ `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/2ce8d0f1-36e8-4657-ac19-cf0898de4ba0)

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/075b09ee-a8f6-4e25-b3b1-3f4dd967bbcf)


</details>

# Day 6
## GLS Synthesis-Simulation Mismatch and Blocking Non-blocking Statements

<details>
<summary> GLS Concepts And Flow Using Iverilog </summary>	

 + **Gate Level Simualtion**
   - Gate-level simulation is a technique used in digital design and verification to validate the functionality of a digital circuit at the gate-level implementation.
   - It involves simulating the circuit using the actual logic gates and flip-flops that make up the design, as opposed to higher-level abstractions like RTL (Register Transfer Level) descriptions.
   - This type of simulation is typically performed after the logic synthesis process, where a high-level description of the design is transformed into a netlist of gates and flip-flops.
   - We perform this to verify logical correctness of the design after synthesizing it. Also ensuring the timing of the design is met.
  
![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/3c0c6207-e607-4555-a1ad-92bfa124f00b)

+ **Synthesis-Simulation Mismatch**
  - A synthesis-simulation mismatch refers to a situation in digital design where the behavior of a circuit, as observed during simulation, doesn't match the expected or desired behavior of the circuit after it has been synthesized.
  - This discrepancy can occur due to various reasons, such as timing issues, optimization conflicts, and differences in modeling between the simulation and synthesis tools.
  - This mismatch is a critical concern in digital design because it indicates that the actual hardware implementation might not perform as expected, potentially leading to functional or timing failures in the fabricated chip.

+ **Blocking Statements**
  - Blocking statements are executed sequentially in the order they appear in the code and have an immediate effect on signal assignments.
  - Example:

  ``` v
   module BlockingExample(input A, input B, input C, output Y, output Z);
    wire temp;

    // Blocking assignment
    assign temp = A & B;

    always @(posedge C) begin
        // Blocking assignment
        Y = temp;
        Z = ~temp;
    end
   endmodule
  ```

+ **Non-Blocking Statements**
  - Non-blocking assignments are used to model concurrent signal updates, where all assignments are evaluated simultaneously and then scheduled to be updated at the end of the time step.
  - Example:
   ``` v
    module NonBlockingExample(input clock, input D, input reset, output reg Q);

    always @(posedge clock or posedge reset) begin
        if (reset)
            Q <= 0;  // Reset the flip-flop
        else
            Q <= D;  // Non-blocking assignment to update Q with D on clock edge
    end
  endmodule
   ```

+ **Caveats with Blocking Statements**
  + Blocking statements in hardware description languages like Verilog have their uses, but there are certain caveats and considerations to be aware of when working with them. Here are some important caveats associated with using blocking statements:
    - Procedural Execution: Blocking statements are executed sequentially in the order they appear within a procedural block (such as an always block). This can lead to unexpected behavior if the order of execution matters and is not well understood.
    - Lack of Parallelism: Blocking statements do not accurately represent the parallel nature of hardware. In hardware, multiple signals can update concurrently, but blocking statements model sequential behavior. As a result, using blocking statements for modeling complex concurrent logic can lead to incorrect simulations.
    - Race Conditions: When multiple blocking assignments operate on the same signal within the same procedural block, a race condition can occur. The outcome of such assignments depends on their order of execution, which might lead to inconsistent or unpredictable behavior.
    - Limited Representation of Hardware: Hardware systems are inherently concurrent and parallel, but blocking statements do not capture this aspect effectively. Using blocking assignments to model complex combinational or sequential logic can lead to models that are difficult to understand, maintain, and debug.
    - Combinatorial Loops: Incorrect use of blocking statements can lead to unintentional combinational logic loops, which can result in simulation or synthesis errors.
    - Debugging Challenges: Debugging code with many blocking assignments can be challenging, especially when trying to track down timing-related issues.
    - Not Suitable for Flip-Flops: Blocking assignments are not suitable for modeling flip-flop behavior. Non-blocking assignments (<=) are generally preferred for modeling flip-flop updates to ensure accurate representation of concurrent behavior.
    - Sequential Logic Misrepresentation: Using blocking assignments to model sequential logic might not capture the intended behavior accurately. Sequential elements like registers and flip-flops are better represented using non-blocking assignments.
    - Synthesis Implications: The behavior of blocking assignments might not translate well during synthesis, leading to potential mismatches between simulation and synthesis results.

</details>

## Labs on GLS and Synthesis-Simulation Mismatch
<details>
<summary> ternary_operator_mux </summary>	

+ `gvim teranry_operator_mux.v`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/09d02d2f-d390-41dd-988a-48995f46d723)

**Simulation**

+ `iverilog ternary_operator_mux.v tb_ternary_operator_mux.v`
+ `./a.out`
+ `gtkwave tb_ternary_operator_mux.vcd`

<img width="700" alt="Screenshot 2023-08-29 at 8 10 55 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/69590371-b738-4c46-b65d-a1bccb2e7cde">


**Synthesis**

+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog ternary_operator_mux.v`
+ `synth -top ternary_operator_mux`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/eea97457-773e-454b-9349-33c3e440d3cc)


![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/b37e6f89-793c-4779-9a1d-2aed0e8b701a)


**GLS to Gate-Level Simulation**

+ `iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v`
+ `./a.out`
+ `gtkwave tb_bad_mux.vcd`

<img width="690" alt="Screenshot 2023-08-29 at 8 12 24 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/47880d9e-e4c2-443d-a720-76dd47ea374e">


</details>

<details>
<summary> bad_mux </summary>	

 + `gvim bad_mux.v`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/ecd6ad98-20b3-48aa-b674-d7cdb2b80bec)


**Simualtion**

+ `iverilog bad_mux.v tb_bad_mux.v`
+ `./a.out`
+ `gtkwave tb_bad_mux.vcd`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/32767817-26ac-45e0-9354-5ab3f3183ad8)



**Synthesis**

+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog bad_mux.v`
+ `synth -top bad_mux`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/a32ac1a8-c192-4f09-8785-3b151adfb212)


![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/f1bf0c53-ca3c-4fee-839d-c0b47cdf60ac)

**GLS to Gate-Level Simulation**

+ `iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux_net.v tb_bad_mux.v`
+ `./a.out`
+ `gtkwave tb_bad_mux.vcd`

<img width="828" alt="Screenshot 2023-08-29 at 8 16 25 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/02cc28f9-dcd5-40c8-8da5-63b1f401991f">


</details>

## Labs on Synth-Sim Mismatch for Blocking Statement

<details>
<summary> blocking_caveat </summary>	

+ `gvim blocking_caveat.v`

![image](https://github.com/Shrachinag/pes_asic_class/assets/119600435/4d8b1cfe-efb3-49da-9611-ba65367a4f53)


**Simualtion**

+ `iverilog blocking_caveat.v tb_blocking_caveat.v`
+ `./a.out`
+ `gtkwave tb_blocking_caveat.vcd`

<img width="891" alt="Screenshot 2023-08-29 at 8 19 27 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/c0ce9232-3eca-4264-a566-1b73c51c7f48">



**Synthesis**

+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog blocking_caveat.v`
+ `synth -top blocking_caveat`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`


<img width="973" alt="Screenshot 2023-08-29 at 8 20 13 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/260df60f-051c-4501-a684-79b4fbc7c5de">


<img width="880" alt="Screenshot 2023-08-29 at 8 21 15 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/57cef5c8-8f54-4ba8-be50-94b163491277">

**GLS to Gate-Level Simulation**

+ `iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat.v`
+ `./a.out`
+ `gtkwave tb_blocking_caveat.vcd`

<img width="643" alt="Screenshot 2023-08-29 at 8 21 51 PM" src="https://github.com/Shrachinag/pes_asic_class/assets/119600435/f8c49982-e733-49cd-9128-f63167c5c3e0">


</details>




