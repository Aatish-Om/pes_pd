# Advanced OpenLANE Workshop

<!-- PROJECT LOGO -->
<br />
<p align="center">

  ![](/images/advanced_physical_design.png)

  <h3 align="center">Advanced Physical Design - OpenLANE Workshop</h3>
</p>


<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li>
      <a href="#rtl-to-gdsii-introduction">RTL to GDSII Introduction</a>
    </li>
    <li>
      <a href="#workshop-introduction">Workshop Introduction</a>
    </li>
    <li>
      <a href="#day-1-inception-of-open-source-eda">Day 1 Inception of Open Source EDA</a>
      <ul>
        <li><a href="#skywater-pdk-files">Skywater PDK Files</a></li>
        <li><a href="#invoking-openlane">Invoking OpenLANE</a></li>
        <li><a href="#package-importing">Package Importing</a></li>
        <li><a href="#design-folder">Design Folder</a></li>
        <li><a href="#design-folder-hierarchy">Design Folder Hierarchy</a></li>
        <li><a href="#configuration-files">Configuration Files</a></li>
        <li><a href="#prepare-design">Prepare Design</a></li>
        <li><a href="#synthesis">Synthesis</a></li>
      </ul>
    </li>
    <li>
      <a href="#day-2-chip-floorplanning-and-standard-cells">Day 2 - Floorplanning and Standard Cells</a>
      <ul>
        <li><a href="#aspect-ratio-and-utilization-factor">Aspect Ratio and Utilization Factor</a></li>
        <li><a href="#preplaced-cells">Preplaced Cells</a></li>
        <li><a href="#decoupling-capacitors">Decouping Capacitors</a></li>
        <li><a href="#power-planning">Power Planning</a></li>
        <li><a href="#pin-placement">Pin Placement</a></li>
        <li><a href="#floorplanning-with-openlane">Floorplanning with OpenLANE</a></li>
        <li><a href="#viewing-floorplan-in-magic">Viewing Floorplan in Magic</a></li>
        <li><a href="#placement">Placement</a></li>
        <li><a href="#viewing-placement-in-magic">Viewing Placement in Magic</a></li>
        <li><a href="#standard-cell-design-flow">Standard Cell Design Flow</a></li>
        <li><a href="#standard-cell-characterization">Standard Cell Characterization</a></li>
      </ul>
    </li>
    <li>
      <a href="#day-3-design-library-cell">Day 3 - Design Library Cell</a>
      <ul>
        <li><a href="#spice-simulations">Spice Simulations</a></li>
        <li><a href="#switching-threshold-of-a-cmos-inverter">Switching Threshold of a CMOS Inverter</a></li>
        <li><a href="#16-mask-cmos-process-steps">16 Mask CMOS Process Steps</a></li>
        <li><a href="#magic-layout-view-of-inverter-standard-cell">Magic Layout View of Inverter Standard Cell</a></li>
        <li><a href="#magic-key-features">Magic Key Features</a></li>
        <li><a href="#device-inference">Device Inference</a></li>
        <li><a href="#drc-errors">DRC Errors</a></li>
        <li><a href="#pex-extraction-with-magic">PEX Extraction with Magic</a></li>
        <li><a href="#spice-wrapper-for-simulation">Spice Wrapper for Simulation</a></li>
      </ul>
    </li>  
    <li>
      <a href="#day-4-layout-timing-analysis-and-cts">Day 4 Layout Timing Analysis and CTS</a>
      <ul>
        <li><a href="#an-introduction-to-lef-files">An Introduciton to LEF Files</a></li>
        <li><a href="#standard-cell-pin-placement">Standard Cell Pin Placement</a></li>
        <li><a href="#lef-generation-in-magic">LEF Generation in Magic</a></li>
        <li><a href="#including-custom-cells-in-openlane">Including Custom Cells in OpenLANE</a></li>
        <li><a href="#fixing-slack-violations">Fixing Slack Violations</a></li>
        <li><a href="#clock-tree-synthesis">Clock Tree Synthesis</a></li>
        <li><a href="#viewing-post-cts-netlist">Viewing Post-CTS Netlist</a></li>
        <li><a href="#post-cts-sta-analysis">Post-CTS STA Analysis</a></li>
      </ul>
    </li>
    <li>
      <a href="#day-5-final-steps-in-rtl-to-gdsii">Day 5 Final Steps in RTL to GDSII</a>
      <ul>
        <li><a href="#power-distribution-network-generation">Power Distribution Network Generation</a></li>
        <li><a href="#global-and-detailed-routing">Global and Detailed Routing</a></li>
        <li><a href="#spef-extraction">SPEF Extraction</a></li>
      </ul>
    </li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

This project gives an interactive tutorial experied during the VSD Advanced Physical Design workshop using OpenLANE.

OpenLANE is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen, Fault, OpenPhySyn, SPEF-Extractor and custom methodology scripts for design exploration and optimization. It is a tool started for true open source tape-out experience and comes with APACHE version 2.0 . The goal of OpenLANE is to produce clean GDSII without any human intervention. OpenLANE is tuned for Skywater 130nm open-source PDK and can be used to produce hard macros and chips.


<!-- GETTING STARTED -->
## Getting Started

This is an example of how you may give instructions on setting up your project locally.
To get a local copy up and running follow these simple example steps.

### Prerequisites

  1. Ubuntu OS-based System
  2. 25GB+ Disk Space

## Inception of open-source EDA, OpenLANE and Sky130 PDK
 How to talk to computers 

### Introduction to QFN-48 Package, chip, pads, core, die and IPs

Lets take an example of an Arduino Board,An Arduino board is a small computer that you can use to control and interact with electronic devices. It's a physical platform that allows you to write and upload programs (called "sketches") to make things like lights, motors, sensors, and other components work together.
we take an Arduino board since we will be working with something similar, **we will be talking about a field which is lying inside the chip shown below**:

![image](https://github.com/Tawfeeq2507/pes_pd/assets/142083027/0783c87c-1949-4fa8-8a9b-b6fb487ad22c)

- if we want to desgin this particular Arduino board, we can describe it in a form of a block diagram shown below:

![image](https://github.com/Tawfeeq2507/pes_pd/assets/142083027/5f0aa3ef-2b05-414d-9234-ddc4d438b5ec)

- the highlighted area of the chip is nothing but the processor shown above and along with the processors we have all the interfaces that we see around the particular processor.
- This is the typical arduino board diagram looks like.

we wont be talking about the embedded desgin and rather will be looking into the chip desgining.

when we open up the IC it looks something like this shown below:

![image](https://github.com/Tawfeeq2507/pes_pd/assets/142083027/049a19cc-766c-46f6-9879-ca05b3c9ae8b)

what we see above is usually what we call a **"chip"**, but its known as a **"PACKAGE"**, these packages have been assigned with certain names for ex: we see that the above package is named **"QNF-48"**.Similarly there are multiple packages in the market with different flavours and pins.
- Here the pin loacations of the particular package are all given by the particular arduino board.
- the package seen above has a size of 7mm x 7mm

- the main Brain of the package the chip sits in the middle of the package and the way the chip is connected to the package is shown below:

![image](https://github.com/Tawfeeq2507/pes_pd/assets/142083027/9ff58809-bd74-41fa-9043-cb09f788ed90)

- Here we have used **"wire bounds"** to connect the pins to the boundaries of the Chip, In this way we are able to transfer all the signal from outside world into the chip.

When we Open the chip it looks like this shown below:

![image](https://github.com/Tawfeeq2507/pes_pd/assets/142083027/f90561ac-8bc0-4f3f-9ab0-6c4cf846bb62)

- The chip that is shown above has many various components and one of the Important componants is the **"PADs"**.
- **"PADs"** in a chip are like the little metal feet or points on the bottom of the chip. They're used to connect the chip to a circuit through which we can send the outside signal into the chip so it can do its job.
- the Middle free space area seen above inside is known as the **"Core"** of the chip.
- **"Core"** of a chip is like the brain of the chip. It's the central part that does most of the actual thinking and processing of information.Its a place where all our Digital logical sits,ex:AND gate,OR gate,MUXs,etc.
- the size of the chip is known as the **"Die"**.
- **"Die"** is like the heart of a computer chip. It's a tiny, flat piece of silicon that contains the actual electronic circuits. It's where all the important computations and operations happen.This the Die that gets manufactured on the **"Silicon Wafer"**.

The typical **Core** of a CHIP consists of an SoC(we will be working with RISC-V SoC),SRAM,ADCs,DACs,PLL,SPI and couple of components shown below:

![image](https://github.com/Tawfeeq2507/pes_pd/assets/142083027/e88f8c8a-3d09-4555-8b92-89a7bb29b5e9)

- these SRAM,ADC,DAC,PLL all together are known As **"Foundry IP's(Intellectual Properties)"**
- **Foundry** is an important term in chip Designing Chips, all our devices,mobiles,everything is depended on the Foundry's.
- Foundry is a place where the chips are manufactured, Foundry's are set of machines that we communicate with.
- The digital Blocks placed the SoC and the SPI are basically called as **"Macros"**.

### What is RISC-V?
**"RISC-V intruction set architecture"** popularly known as **"ISA"**.It is nothing but a language of the computer,a way through which we are able to talk and communicate with the computers.RISC-V is an open-source instruction set architecture (ISA) based on established reduced instruction set computing (RISC) principles. An instruction set architecture is essentially the set of instructions that a computer's processor can execute. 

For a C program to run on a computer hardware which has got a particular Layout(qFlow), where this layout is nothing but interior of a chip present inside our devices,There are certain flow to pass the C program to the layout.



- here the C program is first compiled in its assembly language program which is nothing but the RISC-V assembly language program.
- this Aseembly language program is then converted into machine language program aka the binary language program(ie: 1's and 0's) which is understood by the hardware of the computer.
- here the codes in hexadecimal format but in real term they are in binary format, therefore this needs to be converted into binary format.
- after converting these bits gets finnaly executed in the layout and get the required output.


Another layer present betweeen the C pragram and the layout is the **"HDL(Hardware discriptive language)"**.

#### What is HDL?
**"HDL"** stands for **Hardware Description Language**. It's a specialized programming language used to describe the structure and behavior of electronic circuits and systems. HDLs are used in the design, simulation, and synthesis of digital circuits, such as those found in microprocessors, memory chips, and other integrated circuits.
There are two main types of HDLs:
 1)**Verilog**: Developed by Phil Moorby and Prabhu Goel in the 1980s
 2)**VHDL (VHSIC Hardware Description Language)**:Developed by the U.S. Department of Defense in the 1980s


- To Implement these RISC-V specifications we need **RTL(Register-Transfer Level)**,in this case shown below the RTL used is **picorv32 cpu core**

![image](https://github.com/Tawfeeq2507/pes_pd/assets/142083027/f8e12d12-72af-4d9a-b951-14769924a11f)


- this RTL implments these RISC-V specifications.
- and from here its RTL-GDS flow

### From Software Applications to Hardware 

Any **application software** or aka **"Apps"** run on **Hardware**... but how does this happen??

- First the Application software enters the Blocks called the **System Software**,where the system software intern converts the application program into the binary language.
- the Major components of **"System Software"** concists of the OS(Operating system),Assembler,compiler.
- The **"Opertaing system:** handles lots of things, it handles the IO operations,allocate memory, low level system functions, OS also helps in taking the application program and converting it into its respective assembly language and finally inot binary program that is understood by the hardware.
- The output of the OS are nothing but small functions in the given programs(C++,Java,C,python,etc).
- these are taken by the respective **Compiler** and then converted into intstructions.
- The syntax of these instructions depends on what kind of the hardware is,(ex if the hardware is for intel x86 then the instructions will be of intel x86 only).
- all these instructions all together form the **.exe file**

![image](https://github.com/Tawfeeq2507/pes_pd/assets/142083027/79883606-8f16-453f-a8e0-7ace2b93f68f)

- The job of the **"Assembler"** is to take these instructions and convert it into its respective binary numbers aka **Machine language** program.
- These binary numbers aka machine language is then fed to the hardware, where hardware understands the type of pattern of the machine language and does the respective operation.

This is the flow how the application software runs through many different layers before entering the hardware.

lets take an example of a application of "stop watch".

- the C program for the stop watch enters the compiler and the output of the compiler will be intructions based on the type of the hardware(ex RISC-V) therefore the instructions will be of RISC-V.
- these intructions go into the assembler as a .exe file which gives the output in form of machine language.
- these hexadecimals are converted into binary before entering into the hardware.

![image](https://github.com/Tawfeeq2507/pes_pd/assets/142083027/cd3ff2fc-9fd5-4a77-b1f2-4daa50b6ba1f)

- in general terms these binary numbers are entering into the chip layout and the functions are performed in this layout.

when we take a much deeper look into the program we try to understand the RISC-V intrucstions-

![image](https://github.com/Tawfeeq2507/pes_pd/assets/142083027/ac8b1be7-b508-4ee6-915e-243c495668cf)

- here we see that in left we have the input to the compiler,in the left we have the output of the compiler and the output of the assembler is in hexadecimal in the middle we have assembler output.
- the instructions after the compiler acts as an **"Abstract interface"** between the C language and the hardware, this Abstract interface is called as the **"Instruction set architecture"** or **"Architecture of the computer"**,in the case shown above its the RISC-V architecture.

There is another inteface between the Assembly language and the hardware which is known as the **HDL(Hardware discriptive language**.

#### What is RTL?

RTL stands for Register-Transfer Level. It's a level of abstraction used in digital circuit design and describes how data moves between registers and how operations are performed on that data.In RTL design, the behavior of the digital system is defined by describing how data is transferred between registers and how operations are performed on that data. This is typically done using a hardware description language (HDL) like Verilog or VHDL.

![image](https://github.com/Tawfeeq2507/pes_pd/assets/142083027/52f5c6ce-ea1a-4bf8-8b89-dc223163f440)

- Our hardware only understands 1's and 0's therefore we need An RTL which implements the output of the assembly language that is the machine language into the Hardware.This is known as the RTL implementation of our instruction set.
- This RTL is then Synthesized into a Netlist, where this Synthesized Netlist of the RTL consists of Gates,flip flops,inverters,MUX's,etc.
- and from this Synthesized Netlist to hardware is **Physical design implementation of the Netlist**.

### SoC design and OpenLANE

### Introduction to all components of open-source Digital ASIC Design

- To implement Digital ASIC design we require certain elements these elements are RTL IP's,EDA Tools,PDK data.

**What is PDK?**

- **"PDK"** a **(Process Design Kit)** is a set of files provided by semiconductor manufacturers to help designers use their fabrication process to create integrated circuits (ICs). It contains a comprehensive set of information, models, and files that enable designers to develop and verify their designs using the specific process technology offered by the manufacturer.


**What is EDA Tools?**

- **EDA** stands for **(Electronic Design Automation)**, and EDA tools refer to a category of software applications and tools used in the design and development of electronic systems, including integrated circuits (ICs), printed circuit boards (PCBs), and other electronic components.EDA tools are essential for designing and testing electronic hardware and ensuring that it functions correctly before it is manufactured.hese tools automate various aspects of the design process, making it more efficient and error-free. 

![image](https://github.com/Tawfeeq2507/pes_pd/assets/142083027/e2db98f6-b946-45ef-8c33-b2ce3ea80889)

- Therfore for making Open source Digital ASIC Design we have Open source for RTL IP's(librecores.org,opencores.org,github.com,etc),EDA tools(qflow,openROAD,openLANE,etc),PDK(Foss 130nm production PDK).

![image](https://github.com/Tawfeeq2507/pes_pd/assets/142083027/ce2d29cb-02c9-4f40-b68b-3472527cbea1)

- these 3 Elements can be used to achieve 100% open-source Digital ASIC design.

- The methodology is then Implemented Through A Flow, this Flow is nothing but a piece of software known as RTL to GDS2,this is the main objective of the ASIC Design Flow which takes the design from RTL(REgister transfer level) to GDS2 format used for final layout.


<!-- Workshop Introduction -->
## Workshop Introduction

The inputs to the ASIC design flow are:

    - Process Design Rules: DRC, LVS, PEX
    - Device Models (SPICE)
    - Digital Standard Cell Libraries
    - I/O Libraries

Process Design Kit (PDK) is the interface between the CAD designers and the foundry. The PDK is a collection of files used to model a fabrication process for the EDA tools used in designing an IC. PDK’s are traditionally closed-source and hence are the limiting factor to open-source Digital ASIC Design. Google and Skywater have broken this stigma and published the world’s first open-source PDK on June 30th, 2020. This breakthrough has been a catalyst for open-source EDA tools. This workshop focuses on using the open-source RTL2GDS EDA tool, OpenLANE, in conjunction with the Skywater 130nm PDK to perform the full RTL2GDS flow as shown below:
![intro2](https://github.com/poornima-chetty/pes_pd/assets/142583396/27550243-099b-4340-b82f-91aa1e8e4802)


OpenLANE flow consists of several stages. By default, all flow steps are run in sequence. Each stage may consist of multiple sub-stages. OpenLANE can also be run interactively as shown here.

  1. Synthesis

  <ul>
      <li> Yosys - Performs RTL synthesis using GTech mapping</li>
      <li>abc - Performs technology mappin to standard cells described in the PDK. We can adjust synthesis techniques using different integrated abc scripts to get desired results</li>
      <li>OpenSTA - Performs static timing analysis on the resulting netlist to generate timing reports</li>
      <li>Fault – Scan-chain insertion used for testing post fabrication. Supports ATPG and test patterns compaction</li>
  </ul>

  2. Floorplan and PDN

  <ul>
      <li>Init_fp - Defines the core area for the macro as well as the rows (used for placement) and the tracks (used for routing)</li>
      <li>Ioplacer - Places the macro input and output ports</li>
      <li>PDN - Generates the power distribution network</li>
      <li>Tapcell - Inserts welltap and decap cells in the floorplan</li>
      <li>Placement – Placement is done in two steps, one with global placement in which we place the designs across the chip, but they will not be legal placement with some standard cells overlapping each other, to fix this we perform a detailed placement which legalizes the design and ensures they fit in the standard cell rows</li>
      <li>RePLace - Performs global placement</li>
      <li>Resizer - Performs optional optimizations on the design</li>
      <li>OpenPhySyn - Performs timing optimizations on the design</li>
      <li>OpenDP - Perfroms detailed placement to legalize the globally placed components</li>
  </ul>
  3. CTS

  <ul>
      <li>TritonCTS - Synthesizes the clock distribution network</li>
  </ul>

  4. Routing

  <ul>
      <li>FastRoute - Performs global routing to generate a guide file for the detailed router
      </li>
      <li>TritonRoute - Performs detailed routing from global routing guides</li>
      <li>SPEF-Extractor - Performs SPEF extraction that include parasitic information</li>
  </ul>

  5. GDSII Generation

  <ul>
      <li>Magic - Streams out the final GDSII layout file from the routed def</li>
  </ul>

  6. Checks

  <ul>
      <li>Magic - Performs DRC Checks & Antenna Checks</li>
      <li>Netgen - Performs LVS Checks </li>
  </ul>

<!-- Day 1 Inception of Open Source EDA -->
## Day 1 Inception of Open Source EDA

### Skywater PDK Files

The Skywater PDK files we are working with are described under $PDK_ROOT. There are three subdirectories needed for the workshop:
![D1_1](https://github.com/Aatish-Om/pes_pd/assets/125562864/4c78c423-6931-4742-ab49-17c65e4fccd3)


  1. Skywater-pdk – Contains all the foundry provided PDK related files
  2. Open_pdks – Contains scripts that are used to bridge the gap between closed-source and open-source PDK to EDA tool compatibility
  3. Sky130A – The open-source compatible PDK files

### Invoking OpenLane
![aatd12](https://github.com/Aatish-Om/pes_pd/assets/125562864/011cd810-8f6f-4084-9eb5-8572d2ba8ad6)



  - ./flow.tcl is the script which runs the OpenLANE flow
  - OpenLANE can be run interactively or in autonomous mode 
  - To run interactively, use the -interactive option with the ./flow.tcl script 

### Package Importing
Different software dependencies are needed to run OpenLANE. To import these into the OpenLANE tool we need to run:
![aatd13](https://github.com/Aatish-Om/pes_pd/assets/125562864/ca6670af-b2a2-4741-befd-625a190f05ae)


### Design Folder
All designs run within OpenLANE are extracted from the openlane/designs folder:
![aatd141](https://github.com/Aatish-Om/pes_pd/assets/125562864/14029405-b1dc-4c0a-af1d-90916b9ae413)


### Design Folder Hierarchy
![aatd14](https://github.com/Aatish-Om/pes_pd/assets/125562864/bac620ec-9286-4c26-b8a9-66d72e463222)


Each design hierarchy comes with two distinct components:
  1. Src folder - Contains verilog files and sdc constraint files
  2. Config.tcl files - Design specific configuration switches used by OpenLANE



### Prepare Design
Prep is used to make file structure for our design. To set this up do:
![aatd15](https://github.com/Aatish-Om/pes_pd/assets/125562864/3d750568-9210-46b5-81a8-bdad53dadbfb)


After running this look in the openlane/design/picro32a folder and you will see there is a new directory structure created in this folder under the runs folder so to enable OpenLANE flow:
![aatd16](https://github.com/Aatish-Om/pes_pd/assets/125562864/8fd3c2ce-769f-4ea8-b940-ae58b3706e52)


The config.tcl file shown in this folder contains all the parameters used by OpenLANE for this specific run.

In addition, preparing the design in OpenLANE merges the technology LEF and cell LEF information. Technology LEF information contains layer definitions and a set of restricted design rules needed for PnR flow. The cell LEF contains obstruction information of each standard cell needed to minimize DRC errors during PnR flow:

![aatd17](https://github.com/Aatish-Om/pes_pd/assets/125562864/d87d84c5-6af6-426f-b06a-e321c24ac6c8)


### Synthesis

To run synthesis:
![aatd18](https://github.com/Aatish-Om/pes_pd/assets/125562864/6ffe2bad-a394-466c-a873-611b0df933c7)


Note: Ensure the WNS is an acceptable number, if not please adjust the clock period to fix STA errors.

<!-- Day 2 Chip Floorplanning and Standard Cells-->
##  Day 2 Chip Floorplanning and Standard Cells

In Floorplanning we typically set the:
  1. 	Die Area
  2. 	Core Area
  3. 	Core Utilization
  4. 	Aspect Ratio
  5. 	Place Macros
  6. 	Power distribution network (Normally done here but done later in OpenLANE)
  7. 	Place input and output pins

### Aspect Ratio and Utilization Factor

Two key descriptions of a floorplan are utilization and aspect ratio. The amount of area of the die core the standard cells are taking up is called utilization. Normally we go for 50-70% utilization to, or utilization factor of 0.5-0.7. Keeping within this range allows for optimization of placement and realizable routing of a system. Aspect ratio can specify the shape of your chip by the height of the core area divided by the width of the core area. An aspect ratio of 1 discribes the chip as a square.

### Preplaced Cells

Preplaced cells, or MACRO’s, are important to enable hierarchical PnR flow. Preplaced cells enable VLSI engineers to granularize a larger design. In floorplanning we define locations and blockages for preplaced cells. Blockages are needed to ensure no standard cells are mapped where the placeplaced cells are located.

### Decoupling Capacitors

Decoupling capacitors are placed local to preplaced cells during Floorplanning. Voltage drops associated with interconnect wires can heavily affect our noise margin or put it into an indeterminate state. Decoupling capacitor is a big capacitor located next to the macros to fix this problem. The capacitor will charge up to the power supply voltage over time and it will work as a charge reservoir when a transition is needed by the circuit instead of the charge coming from the power supply. Therefore it “decouples” the circuit from the main supply. The capacitor acts like the power supply.

### Power Planning

Power planning during the Floorplanning phase is essential to lower noise in digital circuits attributed to voltage droop and ground bounce. Coupling capacitance is formed between interconnect wires and the substrate which needs to be charged or discharged to represent either logic 1 or logic 0. When a transition occurs on a net, charge associated with coupling capacitors may be dumped to ground. If there are not enough ground taps charge will accumulate at the tap and the ground line will act like a large resistor, raising the ground voltage and lowering our noise margin. To bypass this problem a robust PDN with many power strap taps are needed to lower the resistance associated with the PDN.

### Pin Placement

Pin placement is an essential part of floorplanning to minimize buffering and improve power consumption and timing delays. The goal of pin placement is to use the connectivity information of the HDL netlist to determine where along the I/O ring a specific pin should be placed. In many cases, optimal pin placement will be accompanied with less buffering and therefore less power consumption. After pin placement is formed we need to place logical cell blockages along the I/O ring to discriminate between the core area and I/O area.

### Floorplanning with OpenLANE

To run floorplan in OpenLANE:

``` % run_floorplam_ ```
As with all other stages, the floorplanning will be run according to configuration settings in the design specific config.tcl file. The output the the floorplanning phase is a DEF file which describes core area and placement of standard cell SITES:
![aatd21](https://github.com/Aatish-Om/pes_pd/assets/125562864/f2c65392-d031-428c-a90e-140daf6ac04c)


### Viewing Floorplan in Magic
To view our floorplan in Magic we need to provide three files as input:

  1. Magic technology file (sky130A.tech)
  2. Def file of floorplan
  3. Merged LEF file

![aatd22](https://github.com/Aatish-Om/pes_pd/assets/125562864/e5109dda-89ae-4198-aebc-09ffacc061ad)

![D2_2](https://github.com/poornima-chetty/pes_pd/assets/142583396/e4363ffb-a39d-4223-9908-f114267686d1)


### Placement

The next step in the Digital ASIC design flow after floorplanning is placement. The synthesized netlist has been mapped to standard cells and floorplanning phase has determined the standard cells rows, enabling placement. OpenLANE does placement in two stages:

  1. Global Placement - Optimized but not legal placement. Optimization works to reduce wirelength by reducing half parameter wirelength
  2. Detailed Placement - Legalizes placement of cells into standard cell rows while adhering to global placement

To do placement in OpenLANE:

``` % run_placement ```
For placement to converge the overflow value needs to be converging to 0. At the end of placement cell legalization will be reported:

![16](https://github.com/poornima-chetty/pes_pd/assets/142583396/8b1fd990-48a4-4341-a8b2-1e80a7380a69)


### Viewing Placement in Magic

To view placement in Magic the command mirrors viewing floorplanning:

![aatd23](https://github.com/Aatish-Om/pes_pd/assets/125562864/23806e92-af11-4dd7-b1e3-0ae30bae3d89)

![D2_5](https://github.com/poornima-chetty/pes_pd/assets/142583396/35d5b523-6b50-4155-9211-534593417a4d)


### Standard Cell Design Flow

Cell design is done in 3 parts:

  1. Inputs - PDKs (Process design kits), DRC & LVS rules, SPICE models, library & user-defined specs.
  2. Design Steps - Design steps of cell design involves Circuit Design, Layout Design, Characterization. The software GUNA used for characterization. The characterization can be classified as Timing characterization, Power characterization and Noise characterization.
  3. Outputs - Outputs of the Design are CDL (Circuit Description Language), GDSII, LEF, extracted Spice netlist (.cir), timing, noise, power.libs, function.

### Standard Cell Characterization

Standard Cell Libraries consist of cells with different functionality/drive strengths. These cells need to be characterized by liberty files to be used by synthesis tools to determine optimal circuit arrangement. The open-source software GUNA is used for characterization.

Characterization is a well-defined flow consisting of the following steps:

  1. Link Model File of CMOS containing property definitions
  2. Specify process corner(s) for the cell to be characterized
  3. Specify cell delay and slew thresholds percentages
  4. Specify timing and power tables
  5. Read the parasitic extracted netlist
  6. Apply input or stimulus
  7. Provide necessary simulation commands 

<!-- Day 3 Design Library Cell -->
# Day 3
## Labs for CMOS inverter ngspice simulations
**IO Placer Revision**

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/fabe5ca4-7dde-43f9-a8e4-260ed11ed820)
- The following command can be typed to change the I/O pins placemnt configuration.

## Inception of Layout and CMOS Fabrication Process
**SPICE Deck Creation for CMOS Inverter**
- SPICE Deck is a netlist that has information on:
  - component connectivity 
  - component values
  - identifying the nodes
  - giving a designation to the nodes

**SPICE Simulation and Switching Threshold**

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/29e6f5c4-d166-4283-85c2-81947d29f165)
- The CMOS on the right side has a bigger size than the one on the left.
- These waveforms tell us that the CMOS is a very robust device. The characteristics of the CMOS are maintained across a variety of sizes.
- The arrow is pointing to the point where 'Vin = Vout'.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/247e37b7-b3b3-4036-9eaf-2c5380a6c71a)
- Above graph gives details on each point and its significance

**A Git Clone and some other Steps**

- We need to perform a git clone here from a repository that we require, to do the future labs.
- We can type the following command
```
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
```

- Now we need to copy the 'sky130A.tech' file into the directory we just cloned
- We can do this by using
```
cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
```
in the follwoing directory shown in the figure
![aatd31](https://github.com/Aatish-Om/pes_pd/assets/125562864/04b7b6df-648e-4927-a106-cc887ecda037)


**16 Mask CMOS Process**
1) Selecting a Substrate - Selecting the appropriate substrate to synthsize the design on.
2) Creating active reagion for transistors - Adding layers of SiO2(40nm), Si3N4(80nm) and photoresist(1um). On top of the photoresist we put a mask layer. Pass UV light and remove the mask. Resist is removed. LOCOS(Local Oxidation of Silicon) is performed. Si3N4 is etched.
3) N-Well and P-Well formation - The next masks are used to create the source and drain regions of the MOSFETs. Boron is used to make P-Well using ion implantation. Phosphorus is used to create N-Well. Put the MOSFET in a Drive In furnace.
4) Formation of Gate - Gate formation involves depositing a gate oxide, defining gate patterns using photolithography, depositing gate material, etching to create gates, doping the substrate and insulating the gates.
5) Lightly Doped Drain Formation(LDD) - Lightly doped drain (LDD) formation involves implanting the drain and source regions of a MOSFET transistor with a lighter concentration of dopants to reduce hot electron effect and short channel effect and enhance device performance.
6) Source and Drain Formation - Source and drain formation in a MOSFET transistor typically involves doping the silicon substrate with chemicals such as arsenic or phosphorous for n-type regions (source and drain) and boron for p-type regions (source and drain). High temperature annealing is performed.
7) Steps to form Contacts and Interconnects(local) - Titanium is deposited with a process known as sputtering. Wafer is heated to about 650 - 700 C in an N2 ambient furnace for 60 seconds. TiSi2 contacts are formed.  TiN is also formed used for local communication. TiN is etched using RCA cleaning.
8) Higher Level Metal Formation - Forming contacts and interconnects locally involves depositing a dielectric material like silicon dioxide, patterning it using photolithography, etching contact holes, depositing a barrier metal (e.g., titanium or titanium nitride), filling with a conductor (e.g., aluminum or copper) using chemical vapor deposition (CVD), and then planarizing through chemical-mechanical polishing (CMP).

**Sky130 Basic Layers Layout and LEF using Inverter**
- Now let us look at the layout of a CMOS inverter. To open this we type the command
![aatd32](https://github.com/Aatish-Om/pes_pd/assets/125562864/0a9a6df6-70c8-441e-8e57-fd2277a89045)

```
 magic -T sky130A.tech sky130_inv.mag &
```

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/4544d764-7b49-4b1f-b3d7-0ae61961bd81)
- The following layout is displayed.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/f10146f9-71a2-4d15-b377-43a72034b9fc)
- We can get to know the details of the inverter by hovering the mouse cursor over it and pressing 's' on the keyboard. Then we can type ```what``` in the tkcon.
- Pressing 's' three times will show what parts are connected to the selected part.

- We shall look at the difference between LEF and Layout. The above image is a Layout.
- LEF represents abstract component data in a machine-readable format for IC libraries, while layout is the physical geometric arrangement of these components on a semiconductor chip.

**Steps to Create Standard Cell Layout and Extract Spice Netlist**

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/aa5b0d26-1711-4fb3-84ff-817ca929110f)
![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/7a2bca47-28d8-4c2e-96cd-4fdcb983fcf0)
- DRC errors can be viewed in the tkcon.

To extract Spice Netlist we perform the following steps in the tkcon window:

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/deb99366-4eb3-40b6-8172-ecce6962db33)
- We use the commands
```
ext2spice cthresh 0 rthresh 0 -> this is done to copy the parasitic capacitances
```
- The next command is
```
ext2spice
```
![aatd33](https://github.com/Aatish-Om/pes_pd/assets/125562864/92867d58-9bbf-40be-aad5-1e781e973cda)

- We can see that a sky130_inv.spice file is created

## Sky130 Tech File Labs

**Create Final SPICE Deck**
- To start off we look at the minimum value of the layout window.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/6a5d5d43-94d8-4248-8681-5d8d94e924e4)
- We can use 'g' on the keyboard to activate the grid and after selecting a grid by right clicking on the mouse, we type ```box``` in tkcon window to check the minimum value of the layout window.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/fcadbb47-849c-4d5f-a15d-4612fb015be6)
- Next we need to open the spice file using the command
```
gedit sky130_inv.spice
```
- We need to configure it to the above specifications.

**Characterize Inverter using Sky130 Models**
![aatd34](https://github.com/Aatish-Om/pes_pd/assets/125562864/528f8792-cef1-4d5a-a4b8-240a3eb13644)

- We now plot the graph for output vs input sweeping the time.
- We first use the command
```
ngspice sky130_inv.spice
```
- In the ngspice shell we use the command
```
plot y vs time a
```
![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/b810d9fe-11e4-44f7-863c-ed19593e0b3c)
- The following graph is displayed.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/400506ec-61c3-458c-9130-7147ec496c6a)

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/55c43b65-5c02-451a-bb11-391de8d87571)
- Rise Time -> time taken to rise from 20% to 80% of the max value -> 2.25075e-09 - 2.184e-09 = 0.006675e-09 s.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/93f95ac2-43e2-48de-93e1-07399e20b4b1)

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/fc3b2887-d910-4864-ae33-ef02fdb8035f)
- Propogation Delay/Cell Rise Delay -> 2.21379e-09 - 2.15e-09 = 0.06379e-09 s.

**Sky130 PDKS and Steps to Download Magic Tool**
![aatd35](https://github.com/Aatish-Om/pes_pd/assets/125562864/973a5356-d72f-4023-b4ec-c38e67a0c7ef)

- Enter the command
```
 wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
```

- Move the file to desktop using
```
mv drc_tests.tgz Desktop/
```
![aatd36](https://github.com/Aatish-Om/pes_pd/assets/125562864/87c1dfa3-35de-48af-a3a7-6782a63a3bc5)

- Extract the file using
```
tar xfz drc_tests.tgz 
```
- Do ```ls``` to view all the files in it.

To open the software we type
```
magic -d XR
```

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/8571a471-4937-4b89-8197-99c2648dfa66)
- We click 'file' and open the 'met3.mag' file.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/cbec69ce-fedb-41cd-af31-0dd9750c1ed9)
![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/b9551c50-a44b-472b-bf63-d4979c2f8caa)
- If we select an area and type ```drc why``` in the tkcon wndow, it will show us the DRC error.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/53fdfab7-7d24-4638-9fb3-855589c89b83)
- To add contact cuts to metal3, first select an area using left and right click. Then hovering over the m3contact we click middle mouse button.

**Fixing DRC Errors**
- There is a DRC error in the poly.mag file in 'poly.9'.
- Open the sky130A.tech file in the editor and make the following changes

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/d786e946-95e0-42c8-a0bd-a83a57697e04)

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/4274217a-ba1b-499d-b81a-fa26b4262301)

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/efafb2d3-520d-4405-b1ae-731b0308ac99)
- Now open the tkcon window and type
```
load tech sky130A.tech
drc check
```

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/ebd7630c-128d-46ba-adb7-a30169ba7fe6)
- As we can see the error is fixed.

**DRC Error as Geometrical Construct**
- We open the nwell.mag file.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/4c49e5c5-4738-449c-9df0-048d2034825d)
- We type the above commands

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/40097614-0dfe-4479-b85c-4418e7b43787)
- The following is displayed

**Find Missing or Incorrect Rules and Fix Them**

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/338b998a-9a6b-4485-8d2b-095fbbcf3d83)

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/cc00bc2f-31ed-45b3-96d8-a12b28697bd4)
- As we can see this is an incorrect implementation and the above rule is violated.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/d689590d-b9a7-43b2-b1da-72e95a9f4dcb)

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/71d62451-245b-4010-8246-234727062c8b)
- We make the following changes

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/08900ffa-8f91-4550-be8c-375b4cb42866)
- Now we select the nwell.4 and type the following commands
```
tech load sky130A.tech
drc check
drc style drc(full)
drc check
```

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/dbb58cd3-4845-4d28-a22b-0228b8260cf6)
- As we can see the error still persists
- We can fix it by the following method.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/4bc70446-9a20-47cd-95b9-d850e170887a)
- Select the existing nwell.4 and make a copy of it by selecting it and clicking 'c'.
- Now select a small area on the nwell.4 and add an 'nsubstratecontact' by hovering over it and clicking middle mouse button.

# Day 4
## Timing Modelling using Delay Tables

**Convert Grid Info to Track Info**

![aatd41](https://github.com/Aatish-Om/pes_pd/assets/125562864/3d5da6f4-076d-440c-b8f4-ed98bb70a984)


- We must go to the following directory and type
```
less tracks.info
```

![aatd42](https://github.com/Aatish-Om/pes_pd/assets/125562864/b3c1ff8b-c056-417b-8ee0-51d2f3e6bcce)


- The 'tracks.info' file is used during the routing stage.
- Routes are the metal traces.
- Since the PNR is an automated flow, we need to specify where all we want the routes to go.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/15744b5a-0fc9-4ad5-b4ce-dfefd26e860d)
- Now we converge the grid definition in the layout to track definition, by typing the following command

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/dbc80960-e5cb-4b75-9f8d-d30c0e48febb)
- The following is the result.
- This shows that the routing of 'li1' layer can happen only along this grid

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/026c5733-e48a-4454-8bed-82a3dd6e1697)
- Having the ports at the intersection of horizontal and vertical tracks ensure that the route can reach that port from the 'y' as well as 'x' direction.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/a1022ba3-b42d-4fed-987f-d4823c0e5550)
- The next requirement is that the width of the cell should be the odd multiple of xpitch which is '0.46' as seen in the 'tracks.info' file.
- As we can see it encloses two full boxes and two halves of one box, totally making three boxes as indicated by the white rectangle.

**Convert Magic Layout to Standard Cell LEF**
- In the tkcon window of the 'sky130_inv.mag' file we type
```
save sky130_vsdinv.mag
```
to make our own .mag file

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/c5cbd3be-e520-4548-b863-51c211664688)
- To make the .lef file we type
```
lef write
```
to make our own lef file.

- Type ```less sky130_vsdinv.lef```
  
![pk43](https://github.com/poornima-chetty/pes_pd/assets/142583396/03988d7e-2a0f-40cf-a668-9771cd70aad0)

- The .lef file is as follows

**Steps to Include New Cell in Synthesis**
![aatd43](https://github.com/Aatish-Om/pes_pd/assets/125562864/b4378203-9d5c-400d-a882-5c03ae3f2377)

- We copy the .mag file that we created to the 'src' folder of picorv32a folder.
![aatd44](https://github.com/Aatish-Om/pes_pd/assets/125562864/60f98ee4-c964-4078-b27e-00801ce71ed0)

- We then perform this copy command.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/acb2c280-ba86-4f84-947e-450fc242eee8)
- Next we modify the 'config.tcl' file in the picorv32a folder as follows.
- Open the OpenLANE interactive window and retrieve the 0.9 package.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/2d3fb8cd-43e6-46c2-b2de-69a338320fe4)
- Type the following
```
prep -design picorv32a -tag 16-09_19-58 -overwrite
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs 
```
- Next we type ```run_synthesis```.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/e3fdfe4f-0139-4bd1-8617-b9aa6c54d0e2)

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/527db989-1cd9-403a-8b02-3028400befc0)
- The following results are displayed.

- To run floorplan and placement we type
```
init_floorplan
run_placement
```
- Now to view the design we type the command
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/84fad4e0-bda4-4026-a9a4-4dc9bc9edec6)

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/7fd1b736-d6dd-4a98-8567-1ee6d0cc5813)
- The following is displayed.
- Zooming into the design using 'z' we can see the sky130_vsdinv than we defined.
- We have plugged in our custon cell in the OpenLANE flow.

## Timing Analysis with Ideal Clocks using OpenSTA

**Configure OpenSTA for Post-Synth Timing Analysis**
- We must create two files

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/c9867e29-810f-4aca-87cb-c71032f823e4)
- The first one must be in the openlane directory
- This file is known as the 'pre_sta.conf' file.

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/9e849dac-a4ff-4420-9a48-bf759f6c82e4)

- The second is the my_base.sdc file.
- This should be in the 'src/sky130' directory under the picorv32a directory.

- To run the timing analysis we type
```
sta pre_sta.conf
```

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/130dfd6a-d980-4cd8-99e0-4ca26d7cd32b)
- Following result is displayed
- There is a slack violation

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/a033e771-31e5-4b36-b783-d37e0fc52001)

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/48528ec3-a353-4809-8d67-4238ad7880fc)
- Settinf MAX_FANOUT value to 4 reduces the slack violation.

## Clock Tree Synthesis TritonCTS and Signal Integrity
**Run CTS**
- To run CTS we need to type the command
```
run_cts
```

- New .v is created

**Timing Analysis with Real CLocks using OpenSTA**

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/9946a62e-f301-4eab-afe7-f3127d4e56b6)
- First we type the command ```openroad```.
- Then we read the .lef file using the command
```
read_lef /openLANE_flow/designs/picorv32a/runs/16-09_19-58/tmp/merged.lef
```

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/168b1183-65aa-4e51-ab9f-8c6e227e188c)
- Then we read the .def file.
```
read_def /openLANE_flow/designs/picorv32a/runs/16-09_19-58/results/cts/picorv32a.cts.def
```

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/0e3199ee-c1dc-43fb-8097-0c688b685c48)
- We then do
```
write_db pico_cts.db
read_db pico_cts.db
read_verilog /openLANE_flow/designs/picorv32a/runs/16-09_19-58/results/synthesis/picorv32a.synthesis_cts.v
read_liberty -max $::env(LIB_SLOWEST)
read_liberty -max $::env(LIB_FASTEST)
```

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/4b35830f-9822-48c7-ab41-5bcfb1eea4f6)
- We read the .src file.
```
read_sdc /openLANE_flow/designs/picorv32a/src/sky130/my_base.sdc
```
- We set the clock
```
set_propagated_clock [all_clocks]
```
- Checking the report
```
report_checks -path_delay min_max -format full_clock_expanded -digits 4
```

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/f637e66a-db20-4cb6-8b84-75c11267c0eb)

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/184e7412-dc84-453c-b2f0-76b40e3588f4)
- Above results are displayed

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/7fd17b40-dfe1-4b1f-b597-fa5b5c911f74)
- We perform it again for a more accurate result

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/a563b159-c6bb-44ec-a44a-e406c16f5ed3)

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/19435f73-e4c7-4663-9c21-0780cdd3f2a6)
- Above results are displayed

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/0415b653-7c0b-478d-91c3-e70d0e94d654)
```
report_clock_skew -hold
report clock_skew -setup
```

# Day 5
## Power Distribution Network and Routing

**Build Power Distribution Network**

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/02713233-6b98-4280-b70b-c54aea1d9ddb)

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/965b7342-ccfa-41ee-9798-4180265a6119)
- To do this first we type
```
gen_pdn
```

![image](https://github.com/AniruddhaN2203/pes_pd/assets/142299140/8467354c-875a-44e9-8ef1-f5be38bd0cc4)
- We see that there is a change in the DEF.
- To run the rounting we type ```run_routing```.
- To check for DRC errors we need to check the 'tritonRoute.drc' folder
- To extract the parasitics we need to use an extractor engine.
- We use the SPEF Extraction.

**SPEF Extraction**
- To use this engine we need to go to
```
cd Desktop/work/tools/SPEF_Extractor
```
- Next we need to use this command
```
python3 /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-09_19-58/tmp/merged.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-09_19-58/results/routing/picorv32a.def
```
- SPEF file is created in ```/home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-09_19-58/results/routing/```
