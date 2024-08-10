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
# Day 2: Good floorplan vs bad floorplan and introduction to library cells
__________________________________________________

# Chip floor planning considerations

It is the first step in physical design flow to find out the width and height. Let's begin with a netlist, netlist is two flipflops and have a simple combination logic in between. A netlist describes the connectivity of an electronic design. 
 
The height and width of core area will be decided by the netlist of the design. It will be based on the number of components required in order to execute the logic and the height and width of the die area will be dependent on the core area height and width.


![image](https://github.com/user-attachments/assets/6fd1aefc-aa2f-4ba7-82de-4bc39409658a)

For example, lets consider a netlist that is having two logic gates and two flipflops.Now, let's convert the symbols into physical dimensions. We are interested in the dimensions of the Core and Die not in the dimensions of the wires.

Let's standard cell have dimensions of 1unit*1unit

So, area= 1 Sq. units

Asuume same area for the flipflop as well = 1 Sq. units

with help of these dimensions and netlist let's calculate the area occupied by the netlist on a silicon wafer.

![image](https://github.com/user-attachments/assets/f5acf7e1-d4e9-42fe-8b54-12e206ca4e58)

In order to roughly calculate the minimum area occupied by netlist, we remove all wires and bring all the flops and logic gates in a single plate.So after combining them together width and length will be 2 units each and if we calculate the total area the it will be 4 Sq. units.

What is 'Core' and 'Die' section of a chip?

Let's have a silicon wafer on which all the logics are implemented. In thes one section is refered as 'Die' and inside the Die we have the Core.

A Die which consists of core, is small semicondcutor material specimen on which the fundamental circuit is fabricated.

A 'Core is the section of the chip where the fundamental logic of the design is placed.

![image](https://github.com/user-attachments/assets/2c905db8-61f1-449a-a9da-c7bb4785820d)

**Utilization Factor**: Utilization Factor is defined as "The ratio of the core area occupied by the netlist to the total core area".For a good FloorPlan, The Utilization Factor should never be '1' because when the Utilization factor becomes '1' , there will be no place for adding additional logic if needed and it will be considered as a bad FloorPlan.

    Utilization Factor = (Area occupied by netlist / Total core area)

**Aspect Ratio**: Aspect Ratio is defined as "The ratio of Height of the core to the width of the core". If the Aspect ratio is '1' , then the core is said to be in a square shape and other than '1' the core will be a rectangle.

    Aspect Ratio = (Height of the core / Width of the core)

![image](https://github.com/user-attachments/assets/b92df87a-afb9-4fd8-828f-e8535f5c76a7)

let us consider this silicon wafer with core dimensions 2units x 2 units. 

In this case, when calculated
- Utilization factor = (4 squnits)/(4 squnits) = 1
- Aspect Ratio = (2 units)/(2 units) = 1 (The core is in a square shape.)

![image](https://github.com/user-attachments/assets/15456d53-a34a-4dcc-b164-b1763742728c)

let us consider this silicon wafer with core dimensions 2units x 2 units. 

In this case, when calculated
- Utilization factor = (4 squnits)/(8 squnits) = 0.5
- Aspect Ratio = (2 units)/(4 units) = 0.5 (The core is in a rectangular shape.)
________________________________________________________________________________________________________
# Pre Placed Cells

Let us consider a combinational logic circuit  which does some function it may be a memory, complex mux which basically does some amount of job.It does a huge job so the output of combinational logic circuit assume to be a huge circuit having some N Logic gates so let's devide it into some small numbers of gates. We will cut the whole circuit into two parts, and separate both of them into two blocks and both block will be implemented seperately. We have all the connectivity information from cut 1 and cut 2. We seperate these cuts into 2 different blocks as block 1 and block 2.

![image](https://github.com/user-attachments/assets/4545eb5e-42b3-41f2-92f6-c15accf6ebcd)
 
Let us extend the inputs and outputs of both the blocks. The section of the circuitry of the blocks is invisible to the person who is looking into the main netlist hence can be imagined as black boxes. Next we seperate those black boxes into two seperate blocks or IPs.

![image](https://github.com/user-attachments/assets/9a36a292-556d-4d40-b61b-07756c789f54)

Advantage of doing this is we can reuse them multiple times after implimenting once only. Similary there are other IP's also available for eg. Memory, Clock-gating cell, Comporator, MUX all of these are part of the top level netlist.They recieve some signals and perform functions and deliver the outputs but the functionality of the cell is implemented only once.

The arrangement of these IP's in a chip is refferd as floorplanning.

These IP's have user-defined locations, and hence are placed in chip before automated placement and routing are called "pre-placed cells".

These cells are placed in such a way that, the placement and routing tool do not touch the location of the cell. 
________________________________________________________________________________________________________________

# De-coupling Capacitors

Let us consider  block a, b, c as 3 Pre placed cells. The design baground says that all the inputs are placed at the left side of the floorplan and outputs at the right side. We also understand from the design summary that most of these pre placed cells are communicating with the input pins. So we come up with the decision to place these blocks close to the input side. The locations of these pre placed cells are never touched while we go through the design cycle. 

![image](https://github.com/user-attachments/assets/165b87d7-c40e-48d4-a7c0-e8cd670339f9)

Let us consider the below shown piece of circuit is a part of any of the block a,b or c. When some gate (let consider AND gate) switched from 0 to 1 or 1 to 0, there is a capacitor sitting at each gate which charges and discharges respectively. This amount of charge is sent by the supply voltage. It is the responsibility of the vdd to supply current to charge the capacitor whenever the logic switches from 0 to 1 and the vss accounts to take back that current whenever logic switches from 1 to 0 that is the capacitor discharges. 

![image](https://github.com/user-attachments/assets/3dee3dcb-9e99-4130-bfea-09d31d0071c2)

In reality when the power supply flows from vdd to vdd' there is a voltage drop in the wire because the wires are physical and anything that has physical dimensions will have inducatance capacitance and resisitance associated with it.Consider capacitance to be 0. Rdd,Ldd,and Lss are well defined values. During switching operation, the circuit demands switching current i.e. peak current. Now, due to the presence of Rdd and Ldd, there will be a voltage drop across them and the voltage at Node 'A' would be Vdd' instead of Vdd.

![image](https://github.com/user-attachments/assets/12a49f5b-4c2a-4966-a00b-4e3decb4f322)

![image](https://github.com/user-attachments/assets/90d58348-235f-4cb0-8887-a1b004567a9e)

In order to get the logic 1 during charging the vdd' should lie within the noise margin range of NMh and to get logic 0  Noise margin range of NMl. If Vdd' lies in the Undefined region then the output may either be logic 1 or logic 0 hence this reange is highly unstable and undesired. 

![image](https://github.com/user-attachments/assets/8806fd83-3976-49f8-8c30-cb8da8b62d36)

We can solve this problem with the help of  de-coupling capacitors.this  De-coupling capacitor is a huge capacitor which is completely filled with charge.it is placed in parallel with the circuit. Every time the circuit switches, it draws current from Cd, whereas, the RL network is used to replenish the charge into Cd. And the amount of current needed for the circuit is supplied by the De- Coupling Capacitor.
 
![image](https://github.com/user-attachments/assets/2b603495-7a36-4553-a9ae-e739aab9f423)

In the chip it will look something like shown below Decoupling capacitors are placed in between the block a, block b and block c. So here in this whole block it has been ensured that supply is being done by the de-coupling capacitor. Once we are done with this we have taken care of the local communication.
_____________________________________________________________________________________________________




