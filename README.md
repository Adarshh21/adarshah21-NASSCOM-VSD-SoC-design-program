# adarshah21-NASSCOM-VSD-SoC-design-program

# Day1
______________________________________

# Introduction to QFN-48 Package, chip, pads, core, die, IPs 

![image](https://github.com/user-attachments/assets/8b490443-aee3-456a-95c3-a8c159a81d94)

![image](https://github.com/user-attachments/assets/3fcf6d7a-078b-44a1-8754-8fc3eb349b47)

**QFN-48 Package**: It is one of the type of chip package in which the chip is quadilateral, flat, non linear with 48 pins.

**Core**: Core is the area in the chip where the fundamental logic of the design is placed. It includes all the gates, Muxes and different logics.

**Pads**: Pads are the pins the act as the link between the core and outside world. It is used to send signals from the external world to signal and viceversa.

**Die**: Die is the total size of the chip including the core nad pads.Die is imprinted multiple times along the silicon area or wafer to increase the throughput.

**IPs**: Foundry IPs are manually designed or they need some human intelligence essentially to define and create them like SRAM, ADC, DAC, PLLs.

**Macros**: Macro Cells are the Memory cells. These IPs have been designed by some other Analog design team, which can be used in the floor plan stage of the design.

**PDKs**: Process Design kits are the set of files that are used in the semicundoctor industry to communicate between Foundry and design engineer. It is used  to model a fabrication process for the design tools used to design an integrated circuit. The PDK is created by the foundry defining a certain technology variation for their processes. It is then passed to their customers to use in the design process.
__________________________________________

# Introduction to Risk-V

**ISA**: Instruction Set Architecture popularly known as ISA is the way we interact with computers. We usually write programs in High level lnguages like C, Java, Python etc but these languages are not understood by machines. Here's when ISA comes to picture.The written codes will be translated to its assembly language program, which is then converted to machine level program which is binary program which is understood by the hardware of the computer using ISA. 

**HDL**: Hardware Description Language is another interface that need to be implemented between RISC-V architecture and Layout.We need to implement the RISC-V specifications using some Register Transfer Language such as picorev 32 cup core, then it is converted to Layout using standard RTL to GDS (Graphical Design System) flow.

![image](https://github.com/user-attachments/assets/7f3d0a9a-5e50-40af-bbc9-2f5034af113f)
_________________________________________________________________________

#  From Software Application to Hardware

We interact with application software (apps) to communicate with the hardware, this happens due to a layer which is between the application software and the hardware called system software. The applications interface with the system software, which then translates them into a language the hardware can understand, namely binary language.

![image](https://github.com/user-attachments/assets/5d9bf05c-a374-4f9f-98f1-2191284a043d)


The major layers of system software are:

**Operating Syste (OS)**: The Operating system handels a lot of things including I/O operations, allocation of memory and low level system functions, the OS translates application software into corresponding code in languages such as C, C++, or Java.

**Compiler**: The compiler takes the code produced by OS and converts them into an instruction set (ex: .exe file). The syntax of this instruction set depends on specific hardware being is used.

**Assembler**: The assembler then converts these executable files into binary language, which the hardware can understand and execute to perform the desired operations.
