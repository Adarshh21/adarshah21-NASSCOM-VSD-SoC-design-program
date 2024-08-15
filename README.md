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

We place the components of stage 1 (orange). As FF1 is connected to Din 1, it is placed near Din 1 similarly FF2 is placed near Dout 1 and in between FF1 and FF2 we place 1 and 2 with some gap between each componemnts. While placing stage 2 componemnts(yellow), FF1 is placed a bit far from Din 2 due to many reasons. FF1,1,2 and FF2 are placed very close to each other such that there is almost no delay in signal transmission, this is called as abutmend this is done for may reasons, one of them being that this circuit works at very high speed. Similarly we place stage 3 (blue) in a diagonal way as shown in the figure,there is a huge distance between 2 and FF2. The placement of stage 4 (green) is the most difficult as there is a block of preplaced cells near Din 4 hence FF1 is placed a bit far from Din 4 and FF2 is placed near Dout 4, there a huge gab betten component 1 an 2 in stage 4.

![image](https://github.com/user-attachments/assets/6e8c4e0d-2b34-4643-b09e-3d648e2b6456)


**Optimize placement using estimated wirelength and capacitence**

In optimize placement we will resolve the problem of distancing. Let's take the example of FF1 to Din2. There must be a wire going from Din2 to FF1 but before going into routing the desing or wiring we will try to estimate the capacitances. If we look the capacitance from Din2 to FF1 it is very huge because wire length is huge in that case even the resistance will also be huge because of that length. If we send the signal from Din2 then it will be difficult for FF1 to catch that input because distance is large. So we can place some intermediate steps to maitain the Signal integrity. By this the input is succesfully driven to the FF1 from Din2. These intermediate steps are called here Repeaters , Repeaters are basically buffers that will recondition the original signal and make a new signal which replicates the original signal and send it forward, this process repeates untill we reach to the actual cell where we want to send the input in this way signal integrity is maintained. By using repeaters we resolve the problem of signal integrity but there will be a loose of area because more and more repeaters are used more area will be used of the particular floorplan.

![image](https://github.com/user-attachments/assets/ea86420e-fe2e-48bf-9204-dc9659897732)

Stage 4 circuit is a bit tricky to do as there is criscrossing of wires in that case we route one set of wires from one layer and other connection from some different layer. There is also a situation where while routing from buffer to 2 it overlaps on FF2 of stage 2 this can allso be taken care of by placing them in different layers each.

![image](https://github.com/user-attachments/assets/3887d6ee-53b1-4343-9e73-48375b42c2ea)

Now we have to check that, what we have done is correct or not. For that we need to do Timing analysis by considering the ideal clocks and according to the data of analysis, we will understand that, the placement is correct or not.

**Need for libraries and characterization**

Every IC design Flow needs to go through several steps. First step to go through is Logic Synthesis, let's say if we have a functionality which is coded in a form of an RTL so first we need to convert the functionality into legal hardware is refered to as Logic Synthesis. Ouput of the logic synthesis is arrangement of gates that will represent the original functionality that has been described using an RTL. Next step of logic synthesis is Floorplaning, in this we import the output of logic synthesis or the netlist and decide the size of the Core and Die. The next step after floorplaning is Placement, in this we take a particular logic cell send place them on the chip in such a fashion that initial timing is better. Next step is CTS(Clock tree synthesis), in this we take care that clk should reach each and every signal at the same time also take care of each clk signal has equal rise and fall.Next step is Routing, routing has to go through the certain flow dependendent on the characterization of the flip flop.And now comes the last step STA(Static timing analysis), in this we try to see the set up time, hold time, maximum achieved frequency of the circuit. One common thing across all stages 'GATES or Cells'.This collection of gates is referred to as Library.

# Placement in openlane

After completing floorplanning, the design process moves on to the placement stage. The placement-related variables/switches can be seen in the README.md file under the directory path:

    /Desktop/work/tools/openlane_working_dir/openlane/configuration

The variable PL_TARGET_DENSITY: describes the placement density of cells in the core. It reflects how spread the cells would be in the core area. 1 = closely dense, 0= widely spread (Default: 0.55). Initially, the placement is coarse to avoid congestion. When the design approach towards closing then timing constraints come in, where the cells would be closed as much as possible to avoid delays.

![image](https://github.com/user-attachments/assets/31654bce-3447-454c-9d82-fc8fceb08747)

The placement step comprises two main phases:

Global Placement: It is a coarse placement where no legalization is happening. During this phase, the tool determines the approximate locations for all the standard cells in the design. Detailed Placement: In this phase, the tool finalizes the exact positions for all the standard cells and ensures the placement is legal. Legalization involves verifying that no standard cells overlap and that they are all correctly positioned within the designated site rows.

To initiate the placement process, use the following command:

    run_placement
During placement execution the reduction of half parameter wire length is the main focus. The placement is stop when the overflow is converged After the Placement is done. To view the results Go to the following location:
    
     /Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/10-08_10-17/results/placement

![image](https://github.com/user-attachments/assets/8945ff4d-242e-4c95-81a3-47085b0d90b4)

**Load placement.def in magic layout**

Change directory to path containing generated placement def

    cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-07_10-25/results/placement/
Command to load the placement def in magic tool

    magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

![image](https://github.com/user-attachments/assets/56b387df-a842-46e3-a949-55fa31c40243)

![image](https://github.com/user-attachments/assets/3d776924-4c96-45dc-9906-24a896fd5d48)
__________________________________________________________________

# Cell design and characterization flows

**Inputs for cell design flow**

In Cell Design Flow, Gates, flipflops, buffers are named as 'Standard Cells'. These standard cells are being placed in the section called as 'Library'. A library has many cells with different functionalities. A libraryu also has many cells which have same functionality but differ in size and threshold voltages.

![image](https://github.com/user-attachments/assets/ecc42f08-a49c-4279-bd1d-0d1f8e6dccc0)

![image](https://github.com/user-attachments/assets/7967a360-c0a4-4e7d-9caa-a986cec80a7e)

If you look into one of the inverter from the library the cell design flowis as follows

The inverter has to represented in form of the shape, drive strength, power charracteristic and so on. Here cell design flow is devided into three parts.
1. Inputs :

   Inputs are the PDKs that we get from foundries which includes:
    - DRC and LVS rules: These are the rulse that ensure layout compliance.
    - Spice Models: There are some parameters in the characteristic equations that are used to model the cell and its behaviours. These parameters depend on the foundry,and are called SPICE model parameters. 
    - library and user defined specifications: 
      - Cell Height: The seperation between power and ground rails defines the cell height. It is the responsibility of the linrary developer to maintain cell height.
      - Cell Width: It is dependent on timing information. The library developer is give a specification that we need drive speed from 1 to x. Higher is the drive strength high is the ability to drive huge wires.
      - Supply Voltage: The top level designer decides on what level of supply voltage will this chip operate on and accordingly the library developer has to design the cells on that supply voltage.He also has to take care of noise margin levels with respect to that supply voltage.
      - Metal Layers: There may be a specification that certian libraries have to be built under certian metal layers itself. For example in some cases there may be a requirement that the mettal layers, poly layers and the power rails should be built on layer 3,,4,and 5 respectively.
      - Pin Location: The library developer has to decide on pin location based on the specification provided by user.                                         
      
2. Design steps:
  
   The design again involves 3 edifferent steps:
    - Circuit Design: In circuit Design there are two steps. These are mostly based on SPICE simulations:
       - First step is to create the logical schematic of your circuit that is implement the function itself.
       - second step is to model the PMOS nad NMOS transistor in such a fashion in order to meet the libraray. The specification may be like W/L of PMOS is 2.5 times the W/L of NMOS. Other example is that the drain current has to be some x microamps.
    - Layout Design: The Steps of Layout design are as follows:
       - First step is to implement function itself based on the set of PMOS and NMOS transistors.
       - Next step is to derive the PMOS network graph and NMOS network graph out of the design that has been implemented.
       - After getting the network graphs next step is to obtain the Euler's path. Eule's path is basically the path which is traced only once.
       - Next step is to draw stick diagram based on the Euler's path. This stick diagram is derived out of the circuit diagram.
       - Next step is to convert this stick diagram into a typical Layout, adhering DRC and LVS rules we have discissed earlier and also the user defined specifications.
       - Final step is to extract the parasatics of that particular layout and charaterise it in terms of timing. 
    - Characterisation: It helps to get the timing noise and power information.
3. Outputs:
  
   We get Outputs at each design phase as follows:
    - The typical output what we get from the circuit design is CDL(circuit description language) file.
    - The output of the layout design will be GDSll which is a typical layout files. LEF defines the width and height of the cell and extracted spice netlist(.cir) is nothing but the paracitics that is the resistance and capacitance of each and every element extracted out of a particular layout.
    - The output of Characterization is the timing, noise and power libs. 

**Typical characterization flow**

Lwr us figure out what all we have from the inputs and design stage. The inputs available with us are Layout lets say a buffer, next we have the description of the buffer along with the power source, capacitance etc that is getting connected, next we have the spice extracted netlist, next we have inverter sub circuit which in turn has the PMOS and NMOS SPICE Models. 

The standard characterization flow followed in industries is as follows:
1. Read the PMOS and NMOS model files
2. Read the extracted SPICE netlist.
3. Recognize the behaviour of the circuit, here buffer.
4. Read the sub circuit, here the inverter.
5. Attach the necessary power sources.
6. Apply and read the stimulus given to characterization setup.
7. Provide the necessary output capacitances.
8. Provide necessary simulation command. Here we are doing transient simulation so we give *.tran* if we do DC simulation we give *.dc*.

Next step is to feed in all this inputs from 1 to 8 in a form of a configuration file to the characterization software "GUNA".

![image](https://github.com/user-attachments/assets/98a62a10-4d7d-42ad-b8a9-0a343f267d60)

![image](https://github.com/user-attachments/assets/53e645a9-940a-41a6-81f9-9d9c3f4b3c03)
______________________________________________________________________________________________________________________________

# General timing characterization

**Timing Thershold Definations**
![image](https://github.com/user-attachments/assets/13974464-1df1-43e4-9ee1-5c4df3e5b5a9)

- Slew Low Rise Threshold: Start point of the rising edge transition, that is lower side of the power supply. Its typical value is about 20% or 30% from the lower side of power supply or minimum power supply.
- Slew High Rise Threshold: End point of the rising edge transition, that is upper side of the power supply. Its typical value is about 20% or 30% from the upper side of power supplyor maximum  power supply.
- Slew Low Fall Threshold: Start point of the falling edge transition, that is lower side of the power supply. Its typical value is about 20% or 30% from the lower side of power supply or minimum power supply.
- Slew High Fall Threshold: End point of the falling edge transition, that is upper side of the power supply. Its typical value is about 20% or 30% from the upper side of power supplyor maximum  power supply.
- Input Rise Threshold: Voltage level where input is considered 'high'. Generally this point is taken at the 50% of the waveform.
- Input Fall Threshold: Voltage level where input is considered 'low'.  Generally this point is taken at the 50% of the waveform.
- Output Rise Threshold: Voltage level where output is considered 'high'.  Generally this point is taken at the 50% of the waveform.
- Output Fall Threshold: Voltage level where output is considered 'low'.  Generally this point is taken at the 50% of the waveform.

![image](https://github.com/user-attachments/assets/bc541039-a09d-4620-8ddd-072f3f3d7dc5)

![image](https://github.com/user-attachments/assets/ad7e8257-dccd-4375-b144-4bb848835231)


**Propogation Delay**:

Time for a signal to propagate through a circuit element. Measured at the 50% points of input and output transitions. Affects circuit speed.

Let us consider the buffer circuit. Red waveform reperesents the Inverter output while blue represets the Buffer output. If we choose the threshold point as 50%, the calculation of propogation delay is as shown in figure:
![image](https://github.com/user-attachments/assets/a08ce69d-5574-4317-85fc-1272ae4dca1e)

If we choose the threshold point as 66.66%, the calculation of propogation delay is as shown in figure:
![image](https://github.com/user-attachments/assets/6582f59b-ef46-4eab-a908-df9bae929f5c)

We can see that the propogation delay is negative which is not desirasble. This happens due to the poor choice of threshold points.

There is another exaple in which even though threshold point is desired one still we have negative propogation delay:
![image](https://github.com/user-attachments/assets/7b0fa50b-ff80-4a3c-9c4f-ef554129c880)

![image](https://github.com/user-attachments/assets/1c69ebef-3a29-48a8-a7ec-7e6c6236ba7d)

This happens due to the timing delay between the two inverters due to which the inverter output streches as shown.

**Transition Time**:

Time for a signal to transition between voltage levels. Rise time (tr): 20% to 80% transition. Fall time (tf): 80% to 20% transition. Affects signal integrity and performance.
![image](https://github.com/user-attachments/assets/adbdfbe0-5d88-4de3-9952-3ab995038b79)

# Day 3 Design library cells using magic layout and ngspice characterization

# D3 SK1 Labs for CMOS Inverter and ngspice simulation

**IO PLACER REVISION**

Till now, we have done floor planning and run placement also. But if we want to change the floorplanning, for example, in our floor planning, pins are at equal distance and if we want to change it then we can also make it by Set command. In this way openlane provides us iterative flow which helps us to make changes view resukts and make changes again in the same file.

TO CHANGE THE IO pins alignment in the layout, first we can verify the current configuration of the Pins, Go to the following directory as shown in the image below:

    home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/10-08_10-17/results/floorplan
Then use the command to open the '.def' file in magic:    

    magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &

![image](https://github.com/user-attachments/assets/5037df88-4914-4fb7-bf8d-afacd9667032)

As we can see pins are randomly equidistant. There are four strategies supported by IO placer (Open source EDA tool). Now, if want it to change to some other IO pins strategy, first go to the following directory and open floorplan.tcl file:

    home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/configuration

![image](https://github.com/user-attachments/assets/21d42020-3651-4d86-a710-9a9bffe466fd)

From here we can see the switching variable FP_IO_MODE = 1, hence pins are randomly equidistant. Now, we run the following command and change the IO placer settings:

    set ::env(FP_IO_MODE) 2

Go to the tab below to run the command to change the IO placer settings and run the floorplan again.

![image](https://github.com/user-attachments/assets/02e25b66-e6e2-47ca-a985-559232b6ab35)

We see that PDN generation was successful.

![image](https://github.com/user-attachments/assets/69005301-6d2d-4c0d-8d03-b19cb5647ea5)

Now, we can check the change in the IO placer strategy: We can see that .def file has been updated from the time stamps and date:

![image](https://github.com/user-attachments/assets/cc511fe1-ed41-420a-bca2-109c3a9009dd)

Now, let us open it in magic using the earlier used command and we see that IO pin configuration is changed

![image](https://github.com/user-attachments/assets/dbad8c82-0d6e-4587-8669-487fd87ed5c4)

**SPICE deck creation for CMOS inverter**

SPICE Deck is nothing but connectivity informationabout the netlist. It is basically a netlist that has got every information. It has got the connectivity information, the inputs that have to be provided to the simulation, it has got tap points at which we take the outputs and so on.

![image](https://github.com/user-attachments/assets/0ac62637-5d1f-45f3-a3da-59d0df6fa9d4)

Steps for SPICE deck creation for CMOS inverter:
- **Component connectivity**: In this we need to define the connectivity of the substrate pin. Substrate pin tunes the threshold voltage of the PMOS and NMOS.
- **Component values**: Values for the PMOS nad NMOS. We have taken the same size of both PMOS and NMOS.
- **Identify the nodes**: Node mean the points between which there is a component.These nodes are required to define the netlist.
- **Name the nodes**: Now we wiil name these nodes as Vin, Vss, Vdd, out.
- **Connections**:
  - For M1 MOSFET drain is connected to out node, gate is connected to in node, source and substrate are connected to Vdd node. It is a  PMOS transistor.
  - For M2 MOSFET drain is connected to out node, gate is connected to in node, source and substrate are connected to 0. It is a  NMOS transistor.
  - C load is connected between out node and the node 0. And it's value is 10fF.
  - Supply voltage(Vdd) which is connected between Vdd and node 0 and value of it is 2.5. Usually the  Vdd value is a multiple of channel length of MOS.
  - Similarly we have input voltage which is connected between Vin and node 0 and its value is 2.5.
- SIMULATION COMMANDS: Now we have to give the simulation commands in which we are sweeping the Vin from 0 to 2.5 with the stepsize of 0.05. Because we want Vout while changing the Vin.
- Final modelling: Final step is to model files. It has the complete description about NMOS and PMOS.
![image](https://github.com/user-attachments/assets/4b9aaf06-5e69-4bac-a3d3-4b0f6fd25088)

We set the Wn=Wp= 0.375um and Lp=Ln=0.25um Hence the W/L ratio of PMOS and NMOS is 1.5

The SPICE simulation for this specifications is shown:
![image](https://github.com/user-attachments/assets/03d675ce-0bfe-4241-8d9d-0c6eaf48f5f4)

We can see that the transfer characteristics is shifted towards the left.

Next We set the Wp= 0.375um , Wn= 0.9375um and Lp=Ln=0.25um Hence the W/L ratio of PMOS is 3.75 and NMOS is 1.5
![image](https://github.com/user-attachments/assets/fd8e7c54-2fa6-4d59-bb6b-73a2fc51a25a)

We can see that the transfer characteristics is at the centre of voltage range.

On comparing both the cases we see that the output waveform shapes are same. This says that the CMOS is a robust device. It means that whener input is 0 output is 1 and whenever the input is 1 the output is 0. The parameters that explain the robustness of CMOS are:

**Switching Threshold**:

Switching thresold, Vm (the point at which the device switches the level) is the one of the parameter that defined the robustness of the Inverter. Switching thresold is a point at which Vin=Vout.

![image](https://github.com/user-attachments/assets/29c94068-4205-4ea5-a3a9-6fde3a37d69d)

At switching voltage Vm both the PMOS and NMOS are in saturation region ie, both the PMOS and NMOS are on. This means that the gate voltage is very very greater than the threshold voltage and the currents flowing in PMOS and NMOS are same but opposite in direction.

![image](https://github.com/user-attachments/assets/fd7d893e-f276-4bd2-9053-4b34a56adfb5)

**STATIC AND DYNAMIC BEHAVIOUR OF CMOS**
![image](https://github.com/user-attachments/assets/c8bd4d35-f566-4731-ad89-0362aafd587c)

In Dynamic simulation we will know about the rise and fall delay of CMOS inverter and how does it varying with Vout. In this simulation everything else will remian same except the input which is provided will be a pulse and simulation command will be .tran

The graph Time vs Voltage will be plotted here from where we can calculate the rise and fall delay
![image](https://github.com/user-attachments/assets/b5624549-48b9-4797-9b6a-97acd6e81c9f)

To calculate the rise delay we choose the 50% point of output and mark its timing and then we substract it from the timing of 50% mark of input similarly we do it for falling input and output to calculate fall delay.

**Steps to get clone of git "vsdstdcelldesign" repo**

The repository "vsdstdcelldesign" contains the .mag file for the inverter and spice models for sky130 nmos/pmos transistors.

Got to the openlane directory and run the following command to clone the git repository:
    
    git clone https://github.com/nickson-jose/vsdstdcelldesign.git

![image](https://github.com/user-attachments/assets/7962006b-ef48-4e04-8a80-c18b5173df99)

As we can see from the above image the repo has been successfully copied to the openlane directory. Now, we will open the .mag file and to do that we require the sky130A.tech file from the following directory:

    /Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic

we copy the file in the .mag file locattion using the following command

    cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign

![image](https://github.com/user-attachments/assets/df533468-1a5b-4966-b611-7bb8c3faa05a)

Now we see that the *sky130A.tech* file is copied in the Vsdstdcelldesign folder

![image](https://github.com/user-attachments/assets/032ca3b8-b624-42c0-ac74-af79efd1564e)

Now, open the sky130_inv.mag file in magic:

    magic -T sky130A.tech sky130_inv.mag &

![image](https://github.com/user-attachments/assets/c9b31f25-280b-4353-9af5-230b1382682f)

Explore the Layout:

![image](https://github.com/user-attachments/assets/d24c7c90-c707-4c68-bc9e-2c7d08119ac7)

we can see that the selected part where poly meets gate is a NMOS.

![image](https://github.com/user-attachments/assets/8cc3e737-93c6-4fbb-9c65-637bdf475535)

It is visible that the output is connected to drains of both PMOS and NMOS.
![image](https://github.com/user-attachments/assets/5d0d86fc-c1c2-4706-be40-ce372a8512ad)

We can see that the source of PMOS is connected to VDD.
____________________________________________________________

# Inception of layout and CMOS fabrication process

**16 Mass CMOS Process**
1. **Selection of substrate**: Substrate is something on which we fabricate our complete design. The layout that we see gets fabricated on the substrate itself. The most commonly used substrate is a p-type substrate with the folliwing properties ie, high resistivity and the doping concentration which is the process of adding foreign impurity in p-type substrate and the orientation.

   The dopping level is usually 10^15 cm^3 .The reason for having this kind of doping level is that the doping concentration of substrate should be less than that of well doping.
2. **Creating active region for transistors**: Active region is the place where we actually place our PMOS and NMOS. The first step to do it is to create the isolation between the wells or pockets which we are gonna form. To do that we first grow a Silicon dioxide SiO2 of 40nm on p-type substrate which acts as a very good insulator. Next we place a Silicon Nitrate Si3N4 of 80nm, next we deposit 1um layer of photoresist on wnhich we create Mask 1. Then we apply UV light to the mask1. 
 ![image](https://github.com/user-attachments/assets/e9563274-28ab-4c49-b4ef-14304cee61ed)

  The mask protects the UV light from hitting the photoresist, the part of photoresist that is exposed to UV light gets washed awaymthis process is called photolithography. Next we remove the mask 1, Next we etch off the Silicon Nitrate, the region below the phohoresist is protected again. next we remove the photoresist itself because Silicon Nitrate itself acts as a protection layer to grow the oxides on the other areas. 

![image](https://github.com/user-attachments/assets/0c8599c8-d062-4fc7-9d97-174b9f05f929)

We put this entire thing into a furnace which have temperature of about 900-1000C, which helps to grow oxide layer in other areas in which silicon nitrate is not present. This is called as field oxide and the process is called as LOCOS ( Local Oxidation of Silicon).

![image](https://github.com/user-attachments/assets/6cc0144d-2859-4af4-b382-5d65019b1dc3)

3. **N-Well and P-Well formation**: N-Well is used for PMOS application and P-Well is used for NMOS application, we cannot form N-Well and P-Well at the same time. We again do the same process, we put a layer of photoresist then put a mask 2 and wash it by subjecting it to UV light. Next we remove the Mask 2. Then we do ion implantation to form p-well using boron which is p type material. We need the energy of 200keV to diffuse the boron through oxide layer to form P-Well.

![image](https://github.com/user-attachments/assets/0f64490d-900e-4027-8722-51a671be1cdc)

Then we use the same process to form N-Well by using Mask 3 and ion implantation of Phosperous using the energy of 400eV.

![image](https://github.com/user-attachments/assets/041ca279-7546-4da1-9bcf-fc55f23583ec)

Then we place the complete structure into a high temperature furnace called as dry wind furnace which is placed at high temperature of about 1100C for 4 to 6 hours that will diffuse the boron and phosperous into forming clear wells. This is known as Twin tub process.

![image](https://github.com/user-attachments/assets/8b87a154-c85d-4e89-9a8a-cc737d555365)

4. **Formation of Gate**: Gate bifer is the most important terminal of the NMOS or PMOS transistor because that is where we control the threshold voltage which is the turning on voltage of the transistor. So maintaining that voltage is very important so fabrigating gate voltage is very crutial.

![image](https://github.com/user-attachments/assets/213f7e6c-55f2-431a-9ebb-00fbd26bd740)

We can see from the snippet that the threshold voltyage is dependent on  the body effect coefficient gamma which iis factored by Doping concentration and oxide capacitance. Hence thses are the two important terms for gate formation as they control Vt.

We again follow the same process using mask 4 and we have p-well exposed with boron for ion implantation we use the dose of boron so as to maintain the required doping concentration which is dependent on Vt , at 60keV which is low energy than used during formation of p well. Similarly we do the same process for NMOS also using Mask 5 and controlling the ion implantation of arsenic  so as to maintain the required doping concentration which is dependent on Vt.

![image](https://github.com/user-attachments/assets/c0a9da20-aed6-41d4-aab0-8995a094b2c9)

During the process of ion implantation the oxide layer gets damaged so we etch the oxide layer using hydroflouric acid solution, then we again regrow the oxide layer of required concentration to maintain the required Vt. Next we deposit a polysilicon layer roughly about 0.4 micron. The gate area is supposed to be low resistance so we implant a N-type arsenic or polysilicon layer which has a low sheet resistance. Next we use the mask 6 and repeat the same procedure to get gate layer.

![image](https://github.com/user-attachments/assets/1870f090-cbc8-4dca-9ef0-1c42357cc96f)

5. **Lightly Doped Drain (LDD) formation**: We want to attain a doping profile of P+ P- N in the N-well where P+ is the source and drain , P- is the LDD and N is already done. similary P-well will have a doping profile of N+ for p source and drain and P is what we already have.

    There are 2 reasons to form LDD:
    - Hot electron effect: Electric field is given by V/d therefore when the device size reduces Electric field increases. Due to this high energy carriers break the Si-Si bond leading to some more elecrons and holes which we do need because we are controlling the doping profile very well. The second reason is that the energy might be so high that it crosses the 3.2eV barrier between the Si conduction band and SiO2 conduction band, if it crosses this band it might just enter into the oxide layer which is present above the substrate and my create liability issue.This is the hot electron effect.
  
    - Short channel effect: When the device size reduces the short channels move from basically 1 micron gate length to 0.5 micron gate length. Because of this the drain field or voltage penitrates into the channel area thus it becomes difficult for the gate to control the current.

    The process remains same to generate the LDD layers as we did in the past, we use the Mask 7, so in case of p well we create NMOS so we add a n type material Phosperous. The doses and energy of phosperous are carefully chosen so that the N- implant dosent penetrates well into the P-well. Similarly we implement the same process using mask 8 to implant P- ions carefully so that they dont penetrate into the N-well.

![image](https://github.com/user-attachments/assets/314da651-1113-416c-9bb5-ca21970b3ad7)

When we fabricate source and drain they will try to disturb this LDD layer, hence we have to protect this LDD structure. We create side wall spacers to accomplish this, to do this we deposit a layer of SiO2 or Si3N4 layer of 0.1um on the complete structure. then we do anisotrophic plasma etching which is a directed etching which etches everything except the oxides at the side walls. The layer of LDD below this side wall will be protected.

![image](https://github.com/user-attachments/assets/d76ee9a0-e2ce-4a70-878c-7222e487cf69)

6. **Source and Drain formation**: We add a thin layer of screen oxide to avoid the effect of channeling. Channeling is the effect where when we do a lot of ion implantation, if the vector velocity of the ions matches to that of the crystalline structure of the p type substrate, the ions may go deep into the p type substrate without even hitting any silicon atoms. It will help to ranc=domize the direction of implantation and they will try to settle down in the areas that we want them to settle.

Next we use Mask 9 to expose the p well using the samy photo lithography process. Then we ion implant the arsenic at 75keV which is n type impurity, the arsenic settles in the source and drain but the LDD are still maintained below the side walls. similarly we use the mask 10 to expose n well and we ion implant it with boron at 50keV 

![image](https://github.com/user-attachments/assets/8966e496-bf32-4079-bb89-43e111270c8a)

Next we put the hald built Mosfet into the high temperature furnace for  temperature of about 1000C and then we expose this to high temperature anelling which will push the N+ and the P+ impurities  even more into p substrate.
   
![image](https://github.com/user-attachments/assets/cbc4e94e-bab5-4811-b2c1-4626243d79cc)

7. **Steps to form contacts and interconnects**: First we remove the thin screen oxide that we had deposired by etching it with Hydroflouride solution. Next we deposit a titanium metal having low resistivity , using sputtering method. We hit titanium metal with argon gases then the particles of the metals or the titanium atoms get sputtered or removed from titanium metal and get settled on the substrate.

![image](https://github.com/user-attachments/assets/ede609d2-565b-4cbe-997d-8675b86a1446)

Next step is to create a contact between titanium metal that we have deposited and the source, drain and gate terminals, to do this we heat it into a nitrogen ambient at the temperature of 650-700C for 60 seconds. Certian chemical reactions occur and result into Titanium silicon dioxide  TiSi2, these are low resistive contacts which are being made at source drain and gate. there is another reaction that occurs between titanium and nitride and the nitrogen ambient to form Titanium Nitride TiN and this is used only for local communication because of the kind of resistibity that it has.

![image](https://github.com/user-attachments/assets/c5abd8b0-ccff-4289-8640-cb3cc88c1a5f)

We again use the photolithography using mask 11 to form the local connections, where we etch off the extra titaniun nitrate we have using RCA cleaning, which is the solution  with 1 part of deionized water , 1 part of ammonium hydroxide and 1 part of hydrogen peroxide.

![image](https://github.com/user-attachments/assets/3e72c75d-e1e4-48cc-acc9-b3c23c668a00)

8. **Higher Level Metal formation**: We notice a non planar suface topography of the wafer which is not ideal to deposit the metal interconnects.So we planarize this surface by depositing 1um of SiO2 doped with phosperous or boron known as phosposilicate glass or borophosposilicate glass one of the reasons to dope it with phosperous is that it acts as a barrier for sodium ions and boron helps to reduce the temperature. We can still observe that the surface is not completely planar. So the next step is to polish and get a plane surface which is called as Chemical Mechanical Polishing (CMP) process.

![image](https://github.com/user-attachments/assets/efb10597-8ae7-4011-9b0b-1632ac802691)

We again do the Photolithiography process using mask 12 to do the contact holes. Then we remove the mask and photoresist and deposite a thin layer of Titanium Nitrate.TiN acts a a very good adhesion layer for SiO2 and iit also acts as a barrier layer between top and bottom interconnects. Next we deposit a blanket tungsten layer and do CMP to remove the extra tungsten and planarize the surface.


The blanket tungsten is the contact layer this need to be connected to the higher metal level. We use a aluminium layer and pattern it using mask 13 using photolithography. We block the almuinium layer part where we want to take out the contact holes to the top. We then add a SiO2 layer by and do CMP process to planarize it. Then we again use Mask 14 to remove the area where we want to deposit metal layer. then we again deposit the thin TiN layer and deposit tungsten and repat the same process to etch mask of aluminium layer and deposit Si3N4 which is a strong dielectric and protects the chip. Finally we use the mask 16 to bring the metal layer to the top.

![image](https://github.com/user-attachments/assets/d429598f-d2ae-4756-b0f1-669a54427812)


**Inception of layout and CMOS fabrication process**

Spice extraction of inverter in magic:

Check current directory
    
    pwd

Extraction command to extract to .ext format

    extract all
Then we check the same file in vsdstdcelldesigns folder in the follwing directory:

    /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
![image](https://github.com/user-attachments/assets/bebf5ac7-8d7d-41e0-9c4d-6ad92464e32b)

Before converting ext to spice this command enable the parasitic extraction also in magic

    ext2spice cthresh 0 rthresh 0

Converting to ext to spice

    ext2spice
![image](https://github.com/user-attachments/assets/06c7d4de-9388-4305-9b78-3f3ff9f02935)

This creates a new file *sky130_inv.spice* in vsdstdcelldesigns folder.

![image](https://github.com/user-attachments/assets/011ee192-76f2-40e0-a2cf-0e30288d8e22)

Next we view the *sky130_inv.spice* folder

![image](https://github.com/user-attachments/assets/882905f9-d448-4716-9ba9-c3b697055a75)

# Tech Lab Files

**Creating Final SPICE Deck using Sky130 Tech**

 We wish to vizualize the transient analysis of the CMOS inverter hence we need to add VDD, VSS, Vin to the CMOS Inverter.

We need to ensur that the scaling is proper, right now the scaling is any dimension*10000u we need it to be the value equal to the grid value specified in the layout visible in tkcon window it is 0.01u.

Inside libs folder of vsdstdcelldesigns folder we have the PMOS and NMOS lib files which we add in 'sky130_inv.spice' file
![image](https://github.com/user-attachments/assets/7f9e0fc5-6128-4a95-9763-2b4893367e6b)

Now let's check what is inside the the model files ie, 'pshort.lib':
![image](https://github.com/user-attachments/assets/3048e4d6-433d-4bdb-b57d-300fea32cb22)

we see that the model file for PMOS starts with pshort_model.0 hence we need to change the model name in .spice file
![image](https://github.com/user-attachments/assets/a4ae494d-f0da-47fd-96ad-46c951cc02de)

Make the following changes in the 'sky130_inv.spice' file from Vim:

![image](https://github.com/user-attachments/assets/dcce4037-3cae-4977-b20e-cf0b6ff1d812)

Next we simulate this file in ngspice using the following command 

    /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign ngspice sky130_inv.spice

If you dont have ngspice install it in new terminal window using the command:

    sudo apt-get install ngspice
 Now that we have entered ngspice with the simulation spice file loaded we just have to load the plot
      
      plot y vs time a
![image](https://github.com/user-attachments/assets/edda71c1-ce2b-4c97-83de-961c9104fe75)


![image](https://github.com/user-attachments/assets/0517a713-f192-4704-9845-84e957af7e4f)

The spikes are a bit larger at the edges of inverter output. We can increase the value of load capacitor (C3) in spice netlist to 2fF. The results are shown below.
![image](https://github.com/user-attachments/assets/c07a1152-e452-41ed-b145-fc765193f2ea)

We can right click and zoom the plot and then leftclick to get the coordinates of any point 

![image](https://github.com/user-attachments/assets/dec66673-3551-47da-8db6-a2898a3eb621)

![image](https://github.com/user-attachments/assets/91e10bb7-1469-48ab-a5c0-26d9e62a4918)

**Characterization of inverter using sky130 tech files**

To characterize the inverter, we analyze the ngspice plot and determined the following parameters:

- Rise Time: The time for the output waveform to transition from 20% to 80% of its maximum value.
From plot points: (x0 = 2.283962ns, y0 = 0.664151) to (x0 = 2.24571ns, y0 = 2.64018). Calculated Rise Time = 0.0634 ns

- Fall Time: The time for the output waveform to transition from 80% to 20% of its maximum value.
From plot points: (x0 = 4.0525ns, y0 = 2.63976) to (x0 = 4.09516ns, y0 = 0.659249). Calculated Fall Time = 0.0422 ns

- Propagation Delay(Cell Rise Delay): The time for the output to transition 50% in response to a 50% change at the input.
From plot points: Input(x0 = 2.15018ns, y0 = 1.65018) to Output(x0 = 2.21088ns, y0 = 1.65). Calculated Propagation Delay = 0.064 ns

- Cell Fall Delay: The delay for the output to transition 50% due to a 50% change at the input.
From plot points: (x0 = 4.04997ns, y0 = 1.65) to (x0 = 4.07748ns, y0 = 1.65). Calculated Cell Fall Delay = 0.0277 ns

We have now characterized the inverter cell for a room temperature of 27 degC. Similarly, this cell can be characterized for different process, voltage, and temperature (PVT) corners to fully characterize this cell for different PVT corners.

With these parameters successfully characterized, the next step is to create a LEF file from this cell, which will be plugged into openlane picorv32a design flow.

**Introduction to Magic tool and DRC rules**

- To know more about the Magic DRC we can go to the website: [The Magic Technology File Manual](http://opencircuitdesign.com/magic/)
- Link to Google_Skywaters Design Rules: [SkyWater PDK Documentation - Periphery Rules](https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html)
- For reference , we can use the github repo of Google-Skywater: [SkyWater PDK GitHub Repository](https://github.com/google/skywater-pdk)

**Sky130 Tech File labs**
Follow the commands below :

Change to home directory
    
     cd

Command to download the lab files

    wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

Since lab file is compressed command to extract it

    tar xfz drc_tests.tgz

Change directory into the lab folder

    cd drc_tests

List all files and directories present in the current directory

    ls -al

![image](https://github.com/user-attachments/assets/f3cc6221-612c-4a9e-96f2-e2a524ad1f0f)

Command to view .magicrc file

    gvim .magicrc
![image](https://github.com/user-attachments/assets/6f77cceb-9d5a-4e92-9648-9872282b44ee)

Command to open magic tool in better graphics

    magic -d XR &
then go to file and open *met3.mag* in the magic.

![image](https://github.com/user-attachments/assets/335910fb-49c7-4840-8055-a651b1538bc6)

We are shown some examples of m3 errors

![image](https://github.com/user-attachments/assets/902533c8-f1ef-46bb-936e-66cf065c1a40)

In this m3.6 has an area of 150um<sup>2</sup> where as the drc rule is that it should have minimum area of 240um<sup>2</sup>.

![image](https://github.com/user-attachments/assets/5ad13533-d167-47b9-9383-35e1ff08bcc3)

here the spacing between two m3 layers is 0.140um but itnshould be more than 0.3um.

Next we fill an Area with Metal 3 and Creating a VIA2 Mask

Steps:
1. Select an Area and Fill with Metal 3:
- Open the Magic GUI.
- Select the desired area on your layout.
- Guide the pointer to the metal 3  contact layer.
- Press P to fill the selected region with metal 3.
2. Create the VIA2 Mask:
- Open the *tkcon* terminal within Magic.
- Type the command: cif see VIA2.
- The metal 3-filled area will now be associated with the VIA2 mask.

![image](https://github.com/user-attachments/assets/5dc1c480-d66e-496b-93f4-24dcfa6057aa)

**Fixing Poly9 error in sky130 tech file**

Open the poly.mag file in magic

![image](https://github.com/user-attachments/assets/404dc2f7-ef7a-4bd8-996d-fbb0414edc85)

Zoom in on the "Incorrect poly.p" layout and measure the spacing between the poly resistor and poly, using the "box" command. The measurement shows a spacing of 0.210 µm, which is smaller than the "poly.9" DRC rule (0.480 µm). But, we do not get a DRC error. Let's correct this problem.

![image](https://github.com/user-attachments/assets/2e6d5f66-d27f-49d4-8a7c-11c81a703c2f)

![image](https://github.com/user-attachments/assets/32d9c81c-1ccd-4c4f-bda3-d83aea034d91)

Open the Sky130a.tech file located in the drc_tests directory. Search for the "poly.9" keyword and apply the changes shown in the images below. Save the file after making the modifications.

![image](https://github.com/user-attachments/assets/6389b23d-3abd-48f8-88c1-ad0fc80065d1)
![image](https://github.com/user-attachments/assets/c0a82278-e5a1-4873-9804-dceb8cb583b6)

![image](https://github.com/user-attachments/assets/ef1c7e2a-dba1-4038-a622-299ec4c58fe3)

Commands in tkcon

Loading updated tech file

    tech load sky130A.tech

Must re-run drc check to see updated drc errors

    drc check

Selecting region displaying the new errors and getting the error messages 
    
    drc why

![image](https://github.com/user-attachments/assets/06954fd1-75a3-46e2-b71b-00257a504776)













