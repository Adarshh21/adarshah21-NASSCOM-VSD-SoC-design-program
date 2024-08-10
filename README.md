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

The simplified ASIC design flow starts with the ready RTL file and passes through a series of stages to produce a GDS file, which can be then sent to foundry for the fabrication.The main stages of RTL to GDS are as follows:

![image](https://github.com/user-attachments/assets/dbd2f62f-89b3-4125-8866-c15ec3d8d9fd)

Synthesis:

Synthesis is the process of converting the RTL code into a gate-level netlist ie, a circuit out of standard cell library. The synthesis process uses a synthesis tool to convert the RTL code into a gate-level representation of the design. 

![image](https://github.com/user-attachments/assets/34873487-d480-4649-8165-f47e40cc44ba)
  
Flooor and Power planning:

The objective is to plan the silicon area and create robust power distribution network to power the circuits.

Chip Floor planning: Partition the chip die between different system building blocks and place the I/O pads. 

Macro planning: Here we define the Macro dimension and its pin locations, also the rows n routing steps are defined which will be used in later steps.

![image](https://github.com/user-attachments/assets/ef791c09-9e47-4569-ab9b-ad34210e5f37)

Power planning: The chips are powered through multiple VDD and VSS pins. The power pins are connected to all components through rings and horizontal and vertical metal straps such parallel structures reduce the resistance. 

![image](https://github.com/user-attachments/assets/0cc70a14-25fb-4845-8b10-bf52ba0b86ef)

Placement:

Place the gate level netlist list cells in macros on the virtual rows. It is advised to place the connected cells nearby.

![image](https://github.com/user-attachments/assets/da1effe0-382c-4ab5-9612-cf8721efcfe1)

Placement is done in two stages:

Global Placement: It tries to find optimal positions for all cells such positions may not be necessarily legal so the cells may overlap and may go off rows.

Detailed Placement: Here the placements obtained from Global placement are manually altered and the cells are optimally placed following placement rules.

![image](https://github.com/user-attachments/assets/7f943dd8-d7ee-4f42-a322-c6d05520b858)

Clock Tree Synthesis:

Clock routing is done before signal routing by creating clock distribution network in order to deliver the clock to all sequential like flipflops. The clock distribution is done in symmetric tree design 
(H-tree, X-tree) so that it has minimum skew.

![image](https://github.com/user-attachments/assets/595519ad-2e15-47cc-9bfa-fb603ea5214b)

Routing:
   
After clock routing, signal routing is performed using the remaining metal layers as defined by the PDK. The PDK is used to define the thickness, pitch, tracks and the minimum width. It also defines the VS that can be used to connect wirensegments on different metal layers. The sky130 PDK defines 6 routing layers. The lowest layer is called the Local interconnect layer which is titanium layer anf following 5 layers are aluminium layers.Routing is divided into Global Routing (generates a routing guide based on PDK instructions) and Detailed Routing (actual routing according to the guide).

![image](https://github.com/user-attachments/assets/a0180373-c2c7-4497-ab0b-1eeed0a2b0a0)

Sign-off:

Once routing is completed, the chip undergoes various checks during the sign-off stage:

Physical Verification Checks: Design Rule Check (DRC) and Layout vs. Schematic (LVS). DRC verifies design rule compliance, while LVS ensures functional correctness against the gate-level netlist.
        
Timing Checks: Static Timing Analysis (STA) checks the design for timing violations.
__________________________________________________________________________________________________

# Introduction to OpenLANE

OpenLANE started as a Open-Source for a true Open Source Tapeout Experiment.The main goal of OpenLANE ASIC flow is to produce a clean GDSII without any human intervention.Clean means no LVS voilations, no DRC Voilations and no timing voilations. OpenLANE is tumed for SkyWater 130 nm PDK it also supports XAB180 anf GF130G. It is used to Produce GDSII for both Macros and Chips. It has two modes of operations: 

Autonomous: Here we configure the flow and push button  the flow and then wait for some time based on the design size and then we get the final GDSII. 

Interactive: Here we can run programs and steps one by one so that we can do experementation and also view results of the intermediate setps while we are executing the frontfloor sreps.

**OpenLANE ASIC Design Flow**

![image](https://github.com/user-attachments/assets/aa3800b3-e93e-4687-b2af-3f0d6378166e)

The image illustrates the detailed ASIC design flow in OpenLANE. The process begins with the Design RTL, which undergoes RTL synthesis using Yosys and ABC to produce an optimized gate-level netlist. This netlist is then subjected to STA (Static Timing Analysis) to check for timing violations. Following STA, Design for Test (DFT) is performed, though this step is optional and uses the FAULT tool.

![image](https://github.com/user-attachments/assets/5836dab6-1faf-4c9a-868f-793eafecb7d7)

FAULT (for DFT) includes:

- Scan Insertion

- Automatic Test Pattern Generation (ATPG)

- Test Pattern Compaction

- Fault Coverage

- Fault Simulation

After DFT, the next phase is Physical Implementation, also known as Automated Place and Route (PnR), using OpenRoad.

OpenRoad (for Physical Implementation) includes:

- Floor/Power Planning

- End Decoupling Capacitors and Tap Cells Insertion

- Placement: Global and Detailed

- Post-Placement Optimization

- Clock Tree Synthesis

- Routing: Global and Detailed

The next step is the Logic Equivalence Checking (LEC) which must be performed for each design change.Here the netlist is modified either by CTS or Post Placement Optimizations. LEC is used to confirm the functionality remains unchanged after netlist modifications. An important step during physical implementation is the "Fake Antenna Diodes Insertion Script."

Dealing with Antenna Rule Violations: When a metal wire segment is fabricated, it can act as an antenna. Reactive ion etching can cause charge accumulation on the wire, potentially damaging transistor gates during fabrication.

It has two solutions:

 - Bridging: Attaching a higher layer intermediary, which requires router awareness.

 - Add an antenna diode cell to leak away charges. Antenna diodes are provided by the SCL.

![image](https://github.com/user-attachments/assets/43cec02e-84d5-4c4e-bd19-1c23cbb11c2c)
 
For this we took a preventive approach:

  - Add a Fake antenna didoe next to every cell input after placement.

  * Run the Antenna Checker(Magic) on the routed layout.

  * If the checker reports violation on the cell input pin, replace the fake diode cell by a real one.

And at the end, we perform Physical Verification. Which includes DRC(Design Rule Checking) , LVS(Layout Vs Schematic). Along with the P.V we also performs STA to check for timing violations in the design.

MAGIC is used for DRC and SPICE Extraction from Layout.

MAGIC and Netgen are used for LVS by comparing Extracted SPICE by MAGIC and Verilog Netlist.
_____________________________________________________________________________
# Day 1 Lab: Getting Familiar with OpenSource EDA tools

**Useful LINUX Commands**

- pwd : It displays the present working directory and its path.
- cd : Using this command we can move in both ways in the directory tree.
- ls : It lists all the sub-directories and files present in the current directory.
- ls -ltr : lists the directory contents in long format, sorted by modification time in reverse order (oldest first).
-  ls --help: displays a help message for the "ls" command.
- clear: clears the terminal screen.
- less "filename": opens the file to view.
-  vim "filename": opens the file to edit. Press "i" to edit, press Esc, then ":wq" to save and exit, "q!" exit without save.
- touch "filename": creates a new file Now, we go to the work directory where all files related to the workshop are stored.
- mkdir : Using this command, we can create a new directory.
- rmdir : Using his command, we can delete an existing directory.
- rm : This command is used to delete the files.
_______________________________________________________________________________________________

**Commands to start Openlane using a docker and run synthesis**

choose directory:

    cd Desktop/work/tools/openlane_working_dir/openlane
    docker

Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command:

    flow.tcl -interactive
Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow:
    
    package require openlane 0.9    
Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a':

    prep -design picorv32a

![image](https://github.com/user-attachments/assets/c8b2c651-d698-490a-a3a1-8ca5b2c8d455)

Once the preparation is complete, a new directory with the current date will be generated within the “runs” folder. Inside this directory, all the necessary subdirectories for storing results, reports, and other relevant data will be created. All the folders except for 'tmp' folder will be empty.

![image](https://github.com/user-attachments/assets/f6cd7139-80b1-49a8-97e3-10180aef7bba)

Merged.lef is the new file created in the same folder which is opened by 'less Merged.lef' command.

The results of each layer get stored in results folder similarly the reports of timing analysis is in stored in timing folder, at this thage these two folders are empty.

![image](https://github.com/user-attachments/assets/3d15c887-82c1-4f46-bc5f-9d7687e5c602)

Now that the design is prepared and ready, we can run synthesis using following command:
    
    run_synthesis
![image](https://github.com/user-attachments/assets/e6727eed-18f7-4269-9044-88b7f7f91ee2)

After synthesis is done we will see the results of synthesis both in docker winodw and also in openlane directory under synthesis

After synthesis we have to calculate

FLOP RATIO = No of D flipflop / Total Number of cells

Percentage = Flop Ratio × 100
![image](https://github.com/user-attachments/assets/2ed93833-e057-424d-a871-c794f8f6000a)

hence the flop ratio is 0.1084 and the percentage is 10.84%.

Now we can view the synthesis results in the 'Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/10-8_10-17/results/synthesis' directory with the folder name 'picorv32a.synthesis.v' 

Similarly there is a systhesis report created in 'Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/10-8_10-17/reports/synthesis' directory with the last yosys report to be generated gives the actual synthesis statistics report which can be viewed using command 'less (folder name)'.

![image](https://github.com/user-attachments/assets/f75e6521-9ece-4269-89a7-e16e0d808c01)


___________________________________________________________________________________________________________________
