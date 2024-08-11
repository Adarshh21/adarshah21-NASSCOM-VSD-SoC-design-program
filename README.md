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

In the chip it will look something like shown in the figure. Decoupling capacitors are placed in between the block a, block b and block c. So here in this whole block it has been ensured that supply is being done by the de-coupling capacitor. Once we are done with this we have taken care of the local communication.
_____________________________________________________________________________________________________

# Power Planning

Let us consider the Previous circuit as a black box called as a macro. If this macro is repeated multiple times on the chip then there will be current demand for each and every element of the macro. The current demends for each of the macro is solved with the help of de-coupling capacitor.

![image](https://github.com/user-attachments/assets/5bb53811-17f3-4354-ac08-e677da17983e)


Let one of the macro be a driver and the other one be a load and there  is signal which is send from driver to load and the signal is basically logic 0 to logic 1. Here we need to maintain the particular driver to load line with same signal so that the load recieves the same. Now power supply is applied. Now assume 16 bit bus has to retain the same signal from driver to the load. so it should get the sufficient power from the supply. But at this bus, there is no de-coupling capacitor is available because it is not physible to put capacitor at all over the place. now, power supply is far away from the bus, that is why some voltage drop between them will occur definetly.  

When we say one particular line of 16-bit bus is logic 1 it says that the capacitor is being charged to Vdd, and whenever we say logic 0 it says that the capacitor is discharged to ground.Let consider this 16 bit bus connected to inverter. So, all the capacitor are initially charged will get discharged and vice-versa due to inverter.

![image](https://github.com/user-attachments/assets/0ea585b3-edb0-4a7a-bbdd-6826f5588775)

But the problem is occuring due to all capacitors are connected to the single ground. This will cause a bump in 'ground' tap point during discharging this bump is called as Ground Bounce. If the size of the bump exceeds the noise margin level it might enter into an undefined state and due to undefined state it can either go to logic 1 or logic 0, this state is not desired.

![image](https://github.com/user-attachments/assets/4a518e50-c371-4275-83a3-fa899d28b400)

Also , all capacitors which were'0' volts will have to charge to 'V'volts through single 'vdd'tap point. This will cause lowering of voltage at Vdd tap point. As long as this voltage drop is in noise margin level we are good enough but if it goes into an undefined region then things become unpredictable.

![image](https://github.com/user-attachments/assets/8865a16a-3bcb-4f14-a9ca-c09abf80b02f)

The phenomenon we have seen was causing the lowering of the supply voltage,this problem occured because power has applied to one point only. The solution of the problem is use multiple power supply. So, every block will take charge from neartest power supply and similarly dump the charge to the nearest ground this type of power supply is called mesh. Hence we can see a large amount of meesh power supply in all the new chips.

The final power planning will be as shown:
![image](https://github.com/user-attachments/assets/72969424-2e46-41fb-b527-90cdad19ba3a)

______________________________________________________

# Pin placement and logical placement blockage

![image](https://github.com/user-attachments/assets/973aa1f2-fb38-447e-8667-fb7602d944b2)

Let us consider a circuit a sample circuit with inputs and clocks connected to the flip flops, logic gates and pre placed blocks. Now complete design becomes like given below which has 6 input ports and 5 output ports. This types of circuits are very much helpful to understand the timing analysis of inter clocks. 

The connectivity information between the gates is coded using VHDL/Verilog language and is called as 'Netlist'.

![image](https://github.com/user-attachments/assets/12046bb9-765b-440b-944d-b0afd98628ad)

The area between core and die is used to place the pins. The general trend is to put all the input pins on left side and output pins on the right, but it varies from designer to designer or design to design. Some might prefer to put input pins at top and output pins at bottom. Some may prefer to put input pins on left and top, and the output pins on right and bottom. We follow the general trend and place the input pins on left side and output pins on right side. we can observe that the ordering of input and output pins is random and not in order. This is due to the reason that where we are planning to place the cells.

Complete knowledge of the functionality of the design is required to understand the pin placement. This creates a handshake between frontend and backend team. The frontend team defines the netlist connectivity while the backend team decides the pin placements. The second thing to observe is the clock pins, the clock ports are bigger than the data ports the reason is that these clock ports drive all the flops in the complete chip continiously, hence they need the least resistance path to travel. Bigger is the size lower is the resistance.

![image](https://github.com/user-attachments/assets/6cfc9d4b-a22e-4c7e-9a56-e1d3f315b734)

Once the pin placement is done the next step is to block the area between the core and die for automatic placement and routing tool. So we do a logical placement cell blockage in that area. Now our floorplan is ready for placement and routing.
_______________________________________________\

# Lab 2 : Floor Planning and Placement

**Steps to run Floorplan**:

To ensure a smooth floorplanning process, designers must pay attention to certain variables, known as switches, which can significantly impact the floorplan. For instance, the utilization factor and aspect ratio are among the important switches. Designers need to verify that these parameters align with the project requirements before initiating the floorplanning stage. The file README.md in the openlane configuration displays the different variables of the design flow. The path is shown below :

    Desktop/work/tools/openlane_working_dir/openlane/configuration
![image](https://github.com/user-attachments/assets/adede6f2-fa0d-4028-85cd-c1dd401e1075)

The image below illustrates various types of switches involved in the floorplanning phase and their description inside thr README.md file.

![image](https://github.com/user-attachments/assets/2e5f68c1-a8e8-4542-bb3b-75ec4bef16aa)

One can set any of these variables depending on where we are in the flow.

The default value of these variables is set in the floorplan.tcl file of openlane configuration. The file path is the same as for README.md and is shown below :
    
    Desktop/work/tools/openlane_working_dir/openlane/configuration

![image](https://github.com/user-attachments/assets/78de6c16-f3f5-4bbb-914c-a7f2da3665a7)

In the figure above several floorplan variables are set by default. One important variable to mention here is FP_IO_MODE which is highlighted in the figure. This is set as 1 which means are the pins are set random and equidistant.

In the picorv32a design, there are *config.tcl* and *sky130A_sky130_fd_sc_hd_config.tcl* files which contain design-specific floorplan settings.

The file path is shown in the image below:

    Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a

![image](https://github.com/user-attachments/assets/db745457-c9cc-4aa8-ab4d-3c0ddd16252b)

The contents of  *sky130A_sky130_fd_sc_hd_config.tcl* file are shown below

![image](https://github.com/user-attachments/assets/075a4e30-37d1-41db-9aaa-1c8c4486e1f5)

Similarly the contents of  *config.tcl* file are shown below

![image](https://github.com/user-attachments/assets/082a3e7d-c088-485a-ac39-8c6871e0b466)

The core utilization and IO metal layers are added in the file through following text by opening the *config.tcl* file in the GVim/Vim app and editing it.

    set ::env(CLOCK_NET) $::env(CLOCK_PORT)
    set ::env(FP_CORE_UTIL) 65 
    set ::env(FP_IO_VMETAL) 4
    set ::env(FP_IO_HMETAL) 3
We have set the flooplan IO vertical metal as layer 4 and horizontal metal as layer 3. In the openlane flow the vmetal and hmetal are 1 more than what is specified.

![image](https://github.com/user-attachments/assets/5e435656-3c3b-4f4c-84db-df7f87b2ad46)

Hence the edited *config.tcl* file fine be viewed from the terminal window :

![image](https://github.com/user-attachments/assets/5f67b188-870f-4dca-917f-01ba1f70dd73)

The priority is given to *sky130A_sky130_fd_sc_hd_config.tcl*, then *config.tcl* and then to the default *floorplan.tcl* file above.

Now we are ready to run the floorplan using the command:

    run_floorplan
_________________________________________

# Review floorplan files

After floorplan execution we go to the runs folder of picorv32a and open the latest date file name. Here one can check the implemented floorplan variables from the logs. The file name ioPlacer.log will give metal layers number for verical and horizontal IO pins. The path to the file is below:

    /Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/10-08_10-17/logs/floorplan

![image](https://github.com/user-attachments/assets/c61d2327-8aa6-4d1e-8e5d-d6e6f88a3f7a)

The contents of the file are shown beow:
![image](https://github.com/user-attachments/assets/8ad6a5da-db58-46ef-8278-7389f322a92f)

Now to check what configuration settings were used to run floorplan we can open the config.tcl from the directory given below:

    /Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/10-08_10-17

![image](https://github.com/user-attachments/assets/583d2b14-11bd-4659-a685-5862ea23cb50)

Now we can observe that the IO Vmetal and Hmetal yayers are changed to 4 and 3 while the core utilization has changed to 35% but we had set it to 65% in *config.tcl* file this is due to the fact that the core utilization percentage was set to 35 in *sky130A_sky130_fd_sc_hd_config.tcl* which has the highest priority.

We view the results of the floorplan in the results path of picorv32a. the path is as shown

    /Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/10-08_10-17/results/floorplan
![image](https://github.com/user-attachments/assets/236c7a42-1940-4ae5-beba-be9a1b6dbd92)

we can see a design exchange file (.def) which has some useful information:

![image](https://github.com/user-attachments/assets/d9418ac6-a236-48ef-9756-2451840f2ab7)

**Calculate the die are in microns**

1000 unit distance microns = 1µm. 

Hence to calculate the die area in micrometer we divide the die height and widh by 1000.

Die width in µm = (660685 − 0)/1000 = 660.685 µm

Die height in µm = (671405−0)/1000 = 671.405 µm

Area of die in micron = 660.685 x 671.405 = 443,587.212425 sq µm.

Now, to open this ".def" file in magic, use the following command:

    magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
![image](https://github.com/user-attachments/assets/caf17129-7b11-445a-be2f-053d1c84eb69)

**Review Floorplan layout in magic**

Design Alignment Instructions:

**Centering the Design:**
1. Press S to select the entire design.
2. Press V to vertically align it to the middle of the screen.

**Zooming In on a Specific Area:**
1. Left-click and drag to select the desired region.
2. Right-click to bring up the context menu.
3. Press Z to zoom in on the selected area.

**Getting Details of a Cell:**
1. Move your cursor to the cell of interest.
2. Press S to select the cell.
3. In the tkcon window, enter the command "what" to display cell details.

![image](https://github.com/user-attachments/assets/3768baca-40c3-4411-ac59-ce672748f1a5)

![image](https://github.com/user-attachments/assets/fca10a17-309e-4378-a9b0-6a42747fefb6)

![image](https://github.com/user-attachments/assets/076f2064-47a7-415d-bbd6-0193b0dff85e)

![image](https://github.com/user-attachments/assets/54209cc5-769f-4c85-82fc-f34af6041b6d)

____________________________________________________________________________

# Library binding and placement

**Netlist binding and initial place design**:

The first and very important step in the placement and routing is to bind the netlist with the physical cells. We have the netlist of gates and shape of these gates represents the functionality of these gates. For example we have NOT gate as a tringular shape which determines that it functions as or gate, but in reality it is a box with physical dimensions it has width and height.Similarly AND gate also has a box shape in reality, Flipfops are also square boxes. So we have given the physical dimensions to all the gates and flipflops. For every component of the netlist we will give the particular shape with particular dimensions because in real world the shapes like AND,OR gates does not exists so we make them as square all the blocks also have the width and height and proper shape.


![image](https://github.com/user-attachments/assets/a7ab8462-92e2-4889-899d-b1f417952708)

Now we will remove the wires,all the gates, flipflops and blocks are present in the shelf which is called as Library.

A library is a place where you can find all kinds all gates flipflops. Library also has the timing information of the perticular component like delay of the gates. Library can be devides into two sublibraries, One library consist of shape and size and other library might consist only of the delay information. The library also has information about when the component's output is changed. Library has the various flavours of each and every cell. Like same cell can have bigger size in different self, bigger the size of cell lesser the resistnce path so it will work faster and will have lesser delay. We can pick up from these what we want based on the timing conditions and available space on the floorplan.


![image](https://github.com/user-attachments/assets/7192784d-1032-40a3-a180-89547e585702)

In the image above, there are three different sets of each element. The larger elements are faster but take up more space, while the smaller elements occupy less area but operate more slowly compared to the larger ones.

**Placement**:

Once we have given proper shape and size to each and every gates the next step is to take those particular gates and place it on the floorplan. We have the floorplan with inout and output ports, we have particular netlist, and we have particular size given to each component of this netlist. So we have the physical view of the logic gates. Next step is to place the netlist onto the floorplan. We have to take the connectivity information from the netlist and design the physical view gates on the floorplan.


![image](https://github.com/user-attachments/assets/76393a48-e909-4c7f-840c-a4881892eb56)

Now, we have the floorplan where we have the preplaced cells from the previous slides, Placement will make sure that the pre placed cells location are not affected and they are kept as it as and the second thing which will be taken care of that is no cell should be placed over the pre-placed cells. 

We need to place the physical view of the netlist onto the floorplan in such a fashion that logical connectivity should be maintained and that particular circuit should interact with their input and output ports to maintain the timing with minimal delay.

![image](https://github.com/user-attachments/assets/38a95ee3-ed00-41b3-a2ab-ac9e82672712)


