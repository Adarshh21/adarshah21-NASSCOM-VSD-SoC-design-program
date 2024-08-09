********# adarshah21-NASSCOM-VSD-SoC-design-program

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

![image](https://github.com/user-attachments/assets/cc1a3ef6-8914-4f63-a63f-8561ed26691c)

Then we write the RTL (Register Transfer Level) description language for the above instruction sets which implements the specifications of the instruction set.RTL is then getting synthasized into netlist, whichbis the synthasized version of the RTL and then we do the Physical design implementation of the above netlist. 


Let us consider the example of a stop watch. A simple program for a stop watch in C language is as shown in figure. Let us consider the system to be RISC-V hardware, then the output of the compiler is RISC-V instructions. The RISC-V instructions go as input to the Assembler and the output is a Hexa decimal number which is converted to binary and fed to the hardware which enter into the chip layout and hence the stop watch behaves as the way it is expected to behave.

![image](https://github.com/user-attachments/assets/d6fb541d-86ad-4f90-b9e3-3a630404c4e2)

_________________________________________________________________________________________________________________

# Introduction to Opensource Digital ASIC Design Tools

![image](https://github.com/user-attachments/assets/4fc97d54-7792-43f0-9e4d-aa0bbec913ef)

  RTL Designs

  EDA Tools

  PDK Data

**Register Transfer Level Designs**: RTL is used in the logic design phase of the integrated circuit design cycle.It involves specifing digital circuits by defining signal flow between hardware registers and the logical operations performed on these signals.

**Electronic Design Automation Tools**: EDA tools are software applications used to design and verify the functionality of integrated circuits (ICs). They ensure that the IC meets the required performance and density specifications. Spice simulator, SIS and Magic are some opensource EDA tools. Openroad, qflow are some academic purpose EDA tools.

**Process Design Kit**: PDK is a set of files used to model a fabrication process for EDA tools during IC design. This kit includes Process Design Rules: DRC (Design Rule Check), LVS (Layout Versus Schematic), PEX (Parasitic Extraction) Device Models, Digital Standard Cell Libraries, I/O linraries etc.
_________________________________________________________________________________________

# Simplified RTL to GDS flow





  
