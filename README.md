# SoC Design and Planning Workshop by NASSCOM and VSD

## Workshop Overview
A two-week workshop on digital VLSI SoC design and planning, covering the complete RTL to GDSII flow, organized by VSD in collaboration with NASSCOM.

### Sky130 Day 1: Introduction to Open-Source EDA, OpenLANE, and Sky130 PDK

#### Session 1: Communicating with Computers
An exploration of the foundational principles of how computers interpret and execute instructions, essential for understanding hardware design and development. The session included examples using Arduino ICs and outlined the specific areas of focus for the workshop.

---

#### Overview of QFN-48 Package, Chip, Pads, Core, Die, and IPs
An introduction to the QFN-48 package, covering its components including the chip, pads, core, die, and intellectual properties (IPs).


| ![QFN-48 Package](https://github.com/user-attachments/assets/d561bf42-1f37-4813-bd08-3f448210c9f1) | ![QFN-48 Components](https://github.com/user-attachments/assets/d32de5bb-2ba1-4b8f-9456-b19df112f707) |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|

---

#### Introduction to RISC-V
A comprehensive look at the RISC-V architecture, its design principles, and its significance in modern hardware development. The session provided a detailed analysis of RISC-V instruction sets, the critical role of the compiler in the development process, and the methodology for converting the PicoRV32 RTL (Register Transfer Level) core into physical layout and hardware implementation.

![RISC-V Architecture](https://github.com/user-attachments/assets/8d7b3ccc-f550-4d0f-b01b-60d48a73419e)

---

#### Transitioning from Software Applications to Hardware
A discussion on how software applications are translated into hardware implementations, emphasizing the importance of understanding both software and hardware paradigms.

![Software to Hardware Transition](https://github.com/user-attachments/assets/e8217f52-880c-4d84-80df-1bdd2d1c6631)



### Session 2: Introduction to SoC design and OpenLANE
An overview of the various components involved in the open-source digital ASIC design process, providing foundational knowledge necessary for understanding the entire design flow.
A streamlined explanation of the RTL (Register Transfer Level) to GDSII (Graphic Data System II) flow, highlighting the key steps and processes involved in converting high-level hardware descriptions into final chip layouts.
| ![image](https://github.com/user-attachments/assets/39fce547-9492-4791-a503-22d012bec072) | ![image](https://github.com/user-attachments/assets/fc500614-d558-4874-bbe2-aebe2a1d91d1) |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|


#### OpenLANE Overview:
  - OpenLANE is an open-source ASIC (Application-Specific Integrated Circuit) design flow that aims to automate the RTL-to-GDSII process.
  - It provides a complete RTL-to-GDSII flow with several automated steps, reducing manual intervention and improving productivity.
  - OpenLANE includes tools for synthesis, floorplanning, placement, routing, and signoff stages of ASIC design.
  - It integrates various open-source tools and libraries to facilitate the design of digital ASICs.
  - OpenLANE supports customization and optimization of design parameters such as area, power, and timing constraints.
  - The platform is maintained by efabless corporation and is widely used in the academic and industry communities for ASIC development.

#### Introduction to OpenLANE detailed ASIC flow:  

<img src="https://github.com/user-attachments/assets/7d9d4fe9-b65c-48fb-870d-fe36f6dbc905" alt="image" width="800">


- **Synthesis:**
  - **RTL Analysis:**
    - Ensure correctness and completeness of RTL design, addressing issues like loops and clock domain crossings.
  - **Logic Synthesis:**
    - Convert RTL to gate-level netlist, optimizing for area, power, and timing.
  - **Technology Mapping:**
    - Map logic gates to target technology cells, optimizing timing and area.

- **Floor Planning with Power Planning:**
  - **Floor Planning:**
    - Allocate chip space for logic, memory, I/O, and power structures based on size and placement.
  - **Power Planning:**
    - Design power distribution for stable delivery, minimizing noise and voltage drop.

- **Placement:**
  - **Global Placement:**
    - Initial cell placement considering timing, congestion, and wire length.
  - **Detailed Placement:**
    - Optimize cell positions for minimal wire length, congestion, and meet timing requirements.

- **Clock Tree Synthesis (CTS):**
  - **Clock Tree Synthesis:**
    - Design clock distribution network for reliable signals, minimizing skew and meeting timing.

- **Routing:**
  - **Global Routing:**
    - Establish initial signal, clock, and power paths, resolving conflicts.
  - **Detailed Routing:**
    - Implement optimized routing paths, ensuring signal integrity and minimizing parasitic effects.

- **Signoff:**
  - **Design Rule Checking (DRC):**
    - Verify layout meets manufacturing rules.
  - **Layout vs. Schematic (LVS) Verification:**
    - Ensure layout matches circuit design.
  - **Timing Analysis:**
    - Verify timing constraints across the chip.
  - **Power Analysis:**
    - Analyze power consumption and distribution.
  - **Physical Verification:**
    - Ensure layout is defect-free and meets reliability criteria.
      
### Session 3: OpenLANE Directory Structure


| ![image](https://github.com/user-attachments/assets/cfd931ff-9322-48b3-8ffe-4f364d0df8c5) | ![image](https://github.com/user-attachments/assets/85101707-fbe5-49c5-88c4-a6cfc60f1ad3) |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
    
        cd Desktop/work/tools               # Navigate to the tools directory
        cd openlane_working_dir             # Move to the openlane_working_dir directory
        cd pdks/sky130A/                    # Navigate to the sky130A directory within pdks
        ls -ltr                             # List files in sky130A directory (reverse chronological order)
        cd libs.ref                         # all process specific files
        ls -ltr                             # List files in libs.ref directory
        cd ../libs.tech                     # Move to libs.tech directory (files specific to the tools)
        ls -ltr                             # List files in libs.tech directory
     


- **Introduction to the SkyWater 130nm PDK:**
  Explored the features and components of the SkyWater 130nm Process Design Kit (PDK), detailing its specifications and capabilities for semiconductor design.

- **Significance of Open PDKs in Silicon Foundry Files:**
  Discussed the importance of open Process Design Kits (PDKs) in providing accessible semiconductor manufacturing files, compatible with commercial Electronic Design Automation (EDA) tools.

- **Importance of libs.ref and libs.tech:**
  Emphasized the critical role of `libs.ref` (reference libraries) and `libs.tech` (technology libraries) in standardizing design components and process parameters within the EDA toolchain, ensuring consistency and compatibility across design phases.

- **sky130_fd_sc_hd Library:**
  Utilizes the `sky130_fd_sc_hd` library, where "hd" signifies high density. This library offers optimized standard cells designed to maximize packing density while maintaining performance, tailored for various digital design applications within the SkyWater 130nm Process Design Kit (PDK).

####  Commands to invoke OpenLANE:
To get into the openlane directory and invoke OpenLANE type following commands:

    
        cd Desktop/work/tools               # Navigate to the tools directory
        cd openlane_working_dir             # Move to the openlane_working_dir directory
        cd openlane
        docker                              # Launch Docker to run OpenLANE
        ls -ltr
        ./flow.tcl -interactive
     
<img src="https://github.com/user-attachments/assets/7a2f40f6-13bf-46b0-8a63-e07f4160b665" alt="image" width="700">

**Steps involved in preparing for the design process:**

    
        package require openlane 0.9
        prep - design picorv32a
        run_synthesis
   

    
  ![image](https://github.com/user-attachments/assets/53a0ab0e-7fa4-4c37-8424-45f052c10980)
  
  ![image](https://github.com/user-attachments/assets/20c5a347-db56-4e8c-b78d-9805f447bda3)

  ![image](https://github.com/user-attachments/assets/c04363c1-58c0-4a48-a097-e55f1dd7b7a2) 
   
  ![image](https://github.com/user-attachments/assets/5a786780-aaa2-42e1-9ed0-04877e8d6e37) 

  **Flip flop ratio calculation**

  ![image](https://github.com/user-attachments/assets/bcc66742-cd14-417f-8bc0-847a978335b2)

  ![image](https://github.com/user-attachments/assets/62ff74b0-70c2-4612-b482-8d568424eb1c)

  ```
Flip Flop ratio = 1613 / 14876 = 0.108 or 10.8%

```

 

 ### Sky130 Day 2: Good floorplan vs bad floorplan and introduction to library cells
 ### Session 1: Chip Floor Planning Considerations**

  1. **Define Width and Height of Core and Die:**
     - Establish core and die dimensions to fit the design within the chip's physical constraints.
     - Ensure that the aspect ratio aligns with design and manufacturing requirements for optimal layout.

  2. **Define Location of Pre-placed Cells:**
     - Position essential cells before automated placement to meet design constraints and functionality.
     - Ensure critical components are placed in locations that support optimal performance and connectivity.

  3. **Surround Pre-placed Cells with Decoupling Capacitors:**
     - Place capacitors around pre-placed cells to stabilize power and mitigate noise interference.
     - Ensure adequate coverage to prevent power supply issues and maintain signal integrity.

  4. **Power Planning:**
     - Design a robust power distribution network to ensure stable power delivery across the chip.
     - Address potential voltage drop and noise issues by strategically placing power pads and distribution elements.

  5. **Pin Placement:**
     - Optimize pin locations to facilitate efficient signal routing and minimize congestion.
     - Ensure that pin placement supports effective connectivity and meets design requirements.

  6. **Logical Cell Placement Blockage:**
     - Define areas where logical cells cannot be placed to avoid interference with critical paths.
     - Ensure that blockages do not hinder the placement of essential cells and that routing is feasible.
    
Configuration variables in floorplan

|![image](https://github.com/user-attachments/assets/8172f17f-1d2b-432d-bdb8-15f21371b202) | ![image](https://github.com/user-attachments/assets/a2841ce0-0cba-4003-a5d5-322935c8bbac) |
 |-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|

 Commands to run floorplan

 ```
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a
run_synthesis
run_floorplan
```
To Calculate the die area in microns 

![image](https://github.com/user-attachments/assets/485d7563-379a-4828-af8b-93ef73708804)

1. **Conversion Factor:**
   - 1000 unit distance = 1 Micron

2. **Distance Calculation:**
   - Distance in Micron = Value / 1000

3. **Die Dimensions:**
   - Die Width in Micron = 660685 / 1000 = 660.685 Microns
   - Die Height in Micron = 671405 / 1000 = 671.405 Microns

4. **Die Area Calculation:**
   - Area of Die in Micron² = 660.685 * 671.405 Microns²

**floorplan def in magic tool**

Commands
```
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-07_08-32/results/floorplan/
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
![image](https://github.com/user-attachments/assets/56c0364c-4499-4543-9159-da3fa09b81f7)

![image](https://github.com/user-attachments/assets/3b0ca512-62cf-4d4c-bdb7-25bd9db2eb9b)

Command to run placement

```
run_placement
```
![image](https://github.com/user-attachments/assets/0782627a-ee44-4840-9bf8-f73e0450b18e)

To open generated placement def in magic tool

```
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-07_08-32/results/placement/

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
![image](https://github.com/user-attachments/assets/8ae209fd-c1de-4f1c-b014-3426164f8df6)

![image](https://github.com/user-attachments/assets/147027b0-16e1-4d74-99c1-03f894dfd253)




 ### Sky130 Day 3: Design library cell using Magic layout and ngspice characteriztaion

 ### Session 1: CMOS inverter ngspice simulations**
 
**IO Spacer Revision**
 ![image](https://github.com/user-attachments/assets/f0b038c8-8760-4155-8b36-9f530e3211ef)

 ![image](https://github.com/user-attachments/assets/f45f25a3-e98d-4867-ad6a-ff4b52d68be3)

 **Spice deck creation and simulations**
 
| ![image](https://github.com/user-attachments/assets/c7d13525-09f2-461a-a941-673ffa5fdb0a) | ![image](https://github.com/user-attachments/assets/f080f297-6be0-409b-b07f-b90557d4d7d3) |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|

| ![image](https://github.com/user-attachments/assets/78707a05-cc53-46e9-bd6d-67267d0b9b99) | ![image](https://github.com/user-attachments/assets/4636c08b-faf3-4c56-9b04-f8fba22713b0) |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|

| ![image](https://github.com/user-attachments/assets/6309301c-9e16-423e-b0d8-3780f1ab5cb0) | ![image](https://github.com/user-attachments/assets/2cb13adb-c7cc-429e-960f-d85d95b9c8d3) |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
![image](https://github.com/user-attachments/assets/f9d5f531-3540-4079-85a4-99e15380b360)

- **Circuit Description:**
  - A SPICE deck is a text file that describes an electronic circuit's components and their interconnections. It includes elements such as resistors, capacitors, transistors, voltage sources, and more, each defined by specific syntax and parameters.

- **Simulation Commands:**
  - The SPICE deck contains control statements and commands that instruct the simulator on what type of analysis to perform, such as DC analysis, AC analysis, transient analysis, and more. These commands help in evaluating the circuit's behavior under different conditions.

- **Model and Parameter Definitions:**
  - The SPICE deck includes model definitions and parameter values for the components, specifying their electrical characteristics. This ensures accurate simulation results by providing detailed information about the devices used in the circuit.

**Lab steps to git clone vsdstdcelldesign**
```
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Clone the repository with custom inverter design
git clone https://github.com/nickson-jose/vsdstdcelldesign

# Change into repository directory
cd vsdstdcelldesign

# Copy magic tech file to the repo directory for easy access
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .

# Check contents whether everything is present
ls

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &
```
![image](https://github.com/user-attachments/assets/c4cdd78d-0012-4c91-9596-b3bd2a87aa7d)

![image](https://github.com/user-attachments/assets/69f4fa19-7916-4027-9628-5ef158a47cf5)

PMOS source connectivity to VDD

![image](https://github.com/user-attachments/assets/915ff727-0f93-454b-b715-f2d01c8cbb6b)

![image](https://github.com/user-attachments/assets/678ae32b-4fdb-48f2-ae7c-0d9c53ea8c34)


### Session 2: Inception of Layout and CMOS Fabrication process
| ![image](https://github.com/user-attachments/assets/b2bcc12b-fee0-4182-bde5-65c87dff4217) | ![image](https://github.com/user-attachments/assets/6b40e926-b694-46b9-afb8-b47a9ea5b788) |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|

| ![image](https://github.com/user-attachments/assets/05d316df-c5bd-4e2a-8e9d-8266d748a0de) | ![image](https://github.com/user-attachments/assets/ffa4f4cd-4020-4db5-9bf2-60992b4f4d94) | 
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|

| ![image](https://github.com/user-attachments/assets/d07cd9c0-126c-4507-8f81-78a5fc20f4cd) | ![image](https://github.com/user-attachments/assets/dd7103e6-167f-4245-a9a4-6f83adfd83ad) |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
- **16-mask CMOS Process**

  1. **Selecting a Substrate:**
     - Choose a high-purity silicon wafer as the starting material.
     - Ensure the substrate has the appropriate doping type (p-type or n-type) to support the desired device characteristics.

  2. **Creating an Active Region for Transistors:**
     - Define the active regions using photolithography and etching to isolate transistors.
     - Apply a field oxide layer to separate and protect these active regions.

  3. **N-well and P-well Formation:**
     - Use ion implantation to create n-well and p-well regions for NMOS and PMOS transistors, respectively.
     - Perform a high-temperature annealing step to drive in and activate the dopants.

  4. **Gate Formation:**
     - Deposit a thin layer of gate oxide followed by a polysilicon layer.
     - Pattern and etch the polysilicon to form the transistor gates, defining the channel length.

  5. **Lightly Doped Drain Formation:**
     - Perform ion implantation to create lightly doped drain (LDD) regions near the gate edges.
     - This step helps to reduce the electric field and improve device performance.

  6. **Source and Drain Formation:**
     - Use ion implantation to heavily dope the source and drain regions, providing low-resistance contacts.
     - Anneal the wafer to activate the dopants and repair implantation-induced damage.

  7. **Steps to Form Contacts and Interconnects:**
     - Deposit an insulating layer (e.g., silicon dioxide) and etch contact holes to the source, drain, and gate regions.
     - Fill the contact holes with metal (e.g., aluminum or copper) to establish electrical connections.

  8. **High-level Metal Formation:**
     - Deposit and pattern multiple metal layers to create the interconnect network.
     - Use dielectric layers between metal layers to insulate and protect the interconnects.



**SPICE extraction of inverter in magic**

![image](https://github.com/user-attachments/assets/180e79a9-56f7-4b96-8e80-8c7f25ce3245)
```
pwd

# Extraction command to extract to .ext format
extract all

# Before converting ext to spice this command enable the parasitic extraction also
ext2spice cthresh 0 rthresh 0

# Converting to ext to spice
ext2spice
```
**Creation of std cell layout and extract spice netlist**
Spice File
![image](https://github.com/user-attachments/assets/f723d947-ac3b-4e69-96bf-421d9f7653c5)

![image](https://github.com/user-attachments/assets/1ab0333e-0a4a-40fd-92ef-5a4e09f6d773)

![image](https://github.com/user-attachments/assets/fde80788-a4e0-4af3-8c6d-b2c0cf5b56f0)

![image](https://github.com/user-attachments/assets/f7ebe9ab-8b90-4887-aaa0-ef71fbcd37bd)

```
#Rise Transistion time = Time taken for output to rise to 80% -Time taken for output to rise to 20%
Rise Transition time = 2.24569 - 2.18206 = 63.63ps

#Fall Transition Delay = Time taken for output to fall to 80% -Time taken for output to fall to 20%
Fall Transition time = 4.1755 - 4.1337 = 41.8ps

#Rise Cell Delay = Time taken for output to rise to 50% - Time taken for input to fall to 50%
Rise Cell Delay time = 2.21093 - 2.14987 = 61ps

#Fall Cell Delay = Time taken for output to fall to 50% - Time taken for input to rise to 50%
Fall Cell Delay time = 4.0773 - 4.05 = 27ps
```

### Session 3: Tech file labs
Link to Sky130 Periphery Rules: Sky130 Periphery Rules
Steps to Download and View the Corrupted SkyWater Process Magic Tech File and Associated Files for DRC Corrections:
```
# Navigate to the home directory
cd

# Download the lab files archive
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

# Extract the contents of the downloaded archive
tar xfz drc_tests.tgz

# Change to the extracted lab directory
cd drc_tests

# Display all files and directories in the current directory
ls -al

# Open the .magicrc configuration file for editing
gvim .magicrc

# Launch the Magic tool with enhanced graphics
magic -d XR &
```
| ![image](https://github.com/user-attachments/assets/72a09894-783c-42de-984d-dcd67155b8cd) | ![image](https://github.com/user-attachments/assets/c95a0a9b-2f15-4a6f-82a0-b000d76077ef) |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|



**Poly.9 simple rule correction**

![image](https://github.com/user-attachments/assets/798edf84-3853-4f8a-88af-5651330e709c)

![image](https://github.com/user-attachments/assets/dd4a30a6-5663-4fb1-886c-8dd5dce5070f)
New commands inserted in sky130A.tech file to update drc
![image](https://github.com/user-attachments/assets/16d39348-bc00-4f49-bd86-e0d96ec9a5ac)
```
# Loading updated tech file
tech load sky130A.tech

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```
**After correction**

![image](https://github.com/user-attachments/assets/e3660b1b-a875-49e9-a8a6-06db6476bb5a)

**nwell complex rule correction**

<img src="https://github.com/user-attachments/assets/fc3483ea-df21-44e3-b4ed-f89dc8b324cf" width="600" />


<img src="https://github.com/user-attachments/assets/0b63f06b-57ef-4571-a15c-1acf395ce7a7" width="800" />

Changes made in sky130A.tech file to update DRC
<img src="https://github.com/user-attachments/assets/cc8a4369-c297-4476-a239-82f1e854caf5" width="800" />


<img src="https://github.com/user-attachments/assets/787cf7ca-e085-4e89-a23a-a9e312493fe8" width="800" />

 ### Sky130 Day 4: Pre-layout liming analysis and importance of good clock tree

 tracks.info of sky130_fd_sc_hd

 ![image](https://github.com/user-attachments/assets/4c5412f2-bfba-4ea0-ac4b-7a1338ad403d)

 Condition 1: Input and output ports are at the interaction of vertical and horizontal grid lines
 
 Condition 2: Width of the standard cell should be odd multiples of x-pitch
 
 Condition 3: Height of the standard cells should be odd multiples of y-pitch
 
 All the 3 conditions are verified

 ![image](https://github.com/user-attachments/assets/3b34a3d9-e441-4608-9a37-bd727789b92a)
 
 ![image](https://github.com/user-attachments/assets/26681fbb-617b-4866-a898-78f1c71c39f4)
 
 ![image](https://github.com/user-attachments/assets/d6b858af-2c74-4f77-ade1-56a47d011b15)
 
 In lef file declaring layer as ports is considered as pins of the macro in order
 
 ![image](https://github.com/user-attachments/assets/010abd15-99b5-4c47-a4d2-c6ef2933ef6f)

 To copy generated lef files to 'picorv32a' design 'src' directory
 ```
cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```
Modified config.tcl file

 ![image](https://github.com/user-attachments/assets/addc2a4d-16b8-49a0-9431-98485daee9a4)

 **Introduction to delay tables**

 ![image](https://github.com/user-attachments/assets/084b4aae-f0a5-45c8-ba57-c14978412101)

 - **Purpose of Delay Tables:**
Delay tables in Static Timing Analysis (STA) model the propagation delays of signals through various cells in an integrated circuit. They provide pre-characterized data on signal travel times from input to output under different input slew rates and output load capacitances, ensuring accurate timing predictions.

- **Structure of Delay Tables:**
Delay tables are multi-dimensional arrays with entries for specific combinations of input slew rates and output load capacitances. These entries contain delay values measured during cell characterization, allowing the STA tool to interpolate delays for intermediate conditions and ensure precise timing analysis.

- **CTS Impact:**
During Clock Tree Synthesis (CTS), delay tables are crucial for accurately modeling the delays introduced by clock buffers and inverters in the clock network. CTS affects the timing of the clock signal distribution, and precise delay tables help STA tools assess the timing impact of the clock tree on the overall circuit performance.


 Synthesis with custom built inverter standard cell
 
 ![image](https://github.com/user-attachments/assets/a3b42882-9ca4-44eb-889b-9c971d22f13f)

 ![image](https://github.com/user-attachments/assets/deb3c22f-1031-4560-a98f-69adf1517aee)

 **Changes made to reduce the delay**
 
 Observation: Chip area of the module is increased
 ```
prep -design picorv32a -tag 21-07_17-09 -overwrite
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
echo $::env(SYNTH_STRATEGY)
set ::env(SYNTH_STRATEGY) "DELAY 3"
echo $::env(SYNTH_BUFFERING)
set ::env(SYNTH_SIZING) 1
echo $::env(SYNTH_DRIVING_CELL)
run_synthesis
```

 ![image](https://github.com/user-attachments/assets/a06e9c6d-09f4-43a6-b115-2187236dc20a)
 
 To run Floorplan
 ```
init_floorplan
place_io
tap_decap_or
run_placement
```
To run placement def in magic 
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
 ![image](https://github.com/user-attachments/assets/2b2d1744-06d0-4a3c-9221-5a03dd1101bf)
 
 ![image](https://github.com/user-attachments/assets/a91ac080-58ba-46e4-8748-0596123a7795)
 
Command for tkcon window to view internal layers of cells
```
expand
```
 ![image](https://github.com/user-attachments/assets/73200597-c736-4588-9226-9ff27caefcd9)

**Steps to configure OpenSTA for post-synth timing analysis**

my_base.sdc file

![image](https://github.com/user-attachments/assets/641940f6-3e56-4cdf-932b-301765ea57eb)

pre_sta.conf for automating STA

![image](https://github.com/user-attachments/assets/46ed587e-ee59-4746-8656-478ce8b45d71)

Commands to run STA

```
cd Desktop/work/tools/openlane_working_dir/openlane
sta pre_sta.conf
```
 ![image](https://github.com/user-attachments/assets/22e89e36-8a07-422a-ad8f-f67cc4db1a74)
 
 ![image](https://github.com/user-attachments/assets/23a353e8-8c87-4087-89d8-55bd8bc307ce)
 
 ![image](https://github.com/user-attachments/assets/fd8d4162-e775-43cb-8d08-75b34b2b0a06)
 
 Make suitable timing ECO fixes to remove all violations. Repeat the process untill violations are removed.

Commands
 ```
report_net -connections _11672_
help replace_cell
#replace_cell instance standard_cell_name
replace_cell _14510_ sky130_fd_sc_hd__or3_4
report_checks -fields {net cap slew input_pins} -digits 4
 ```
Final Slack achieved from -36.63ns to -4.4238ns

![image](https://github.com/user-attachments/assets/8c1f916e-76b1-4604-b642-56b599c70a8f)

![image](https://github.com/user-attachments/assets/63378473-652f-45a1-83b7-4d11b7180b8a)


**Session 3: Clock tree synthesis TritonCTC and signal integrity**

 | ![image](https://github.com/user-attachments/assets/df8c106b-b062-41ef-bb03-06cebdc7a31a) | ![image](https://github.com/user-attachments/assets/9475282f-9f1e-4635-891b-d809d3799229) |
 |-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
 
**Clock Tree Synthesis (CTS)**
Purpose:

- To distribute the clock signal evenly to all sequential elements (flip-flops) in the design.
- To ensure minimal clock skew and latency for reliable operation and meeting timing constraints.

**Clock Net Shielding**
Purpose:

- To protect the clock net from noise and interference from neighboring signal nets.
- To maintain signal integrity and ensure the clock signal is delivered cleanly and without distortion.


 cts results
 ![image](https://github.com/user-attachments/assets/02e6a198-d1d9-41b2-982c-b7bcc4a3d4f6)

 procs found in cts.tcl
 ![image](https://github.com/user-attachments/assets/8f6860fd-022a-460d-9809-b97dacfddb92)

 ![image](https://github.com/user-attachments/assets/19cc8d59-b677-484b-b504-673139a73b4b)

 Post_synthesis slack results
 
Commands to run in OpenLANE
 ```
openroad
read_lef /openLANE_flow/designs/picorv32a/runs/21-07_17-09/tmp/merged.lef
read_def /openLANE_flow/designs/picorv32a/runs/21-07_17-09/results/cts/picorv32a.cts.def
write_db pico_cts.db
read_db pico_cts.db
read_verilog /openLANE_flow/designs/picorv32a/runs/21-07_17-09/results/synthesis/picorv32a.synthesis_cts.v
read_liberty $::env(LIB_SYNTH_COMPLETE)
link_design picorv32a
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
set_propagated_clock [all_clocks]
help report_checks
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4
exit

```
 
 ![image](https://github.com/user-attachments/assets/cffce61d-8295-4ee1-99b7-80280056497c)

 Hold slack
 
 ![image](https://github.com/user-attachments/assets/8180fca9-57de-45ac-9b00-4eaac418f1d9)

 Setup slack
 
 ![image](https://github.com/user-attachments/assets/3544a98a-e280-4e04-ac6c-cc80209680f3)

### Sky130 Day 5: Final steps for RTL2GDS using tritonRoute and openSTA

**Session 1: Routing and Design Rule check**

| ![image](https://github.com/user-attachments/assets/7e4d49db-5ede-4102-a1b2-ef33137b25d4)  | ![image](https://github.com/user-attachments/assets/57888211-da85-4b09-b335-ad4d08d94e47) |
 |-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|

| ![image](https://github.com/user-attachments/assets/1be7dfb8-23e9-468a-8a6e-bb53755922da) |![image](https://github.com/user-attachments/assets/8280a86a-50bd-4627-a1e1-99a3785dc84e)|
 |-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|


**Routing**  
Purpose:

- **Interconnect Creation:** Routing connects various components on an IC, such as transistors, capacitors, and other devices, to form the desired electrical circuits.
- **Performance Optimization:** It aims to optimize performance metrics like signal delay, power consumption, and area.

Key Objectives:

- **Global Routing:** Determines a coarse route for each net, identifying which regions of the chip the wires will pass through without specifying exact paths.
- **Detailed Routing:** Specifies the exact paths for the wires within the regions defined by global routing, ensuring that all design rules are followed and there are no violations.

**Lee's Algorithm (Maze Routing Algorithm)**  
Purpose:

- **Pathfinding:** Lee's algorithm finds a path between a start point and an end point in a grid, ensuring that the path is feasible and avoids obstacles.
- **Guarantee of Solution:** The algorithm guarantees to find the shortest path if one exists, making it a reliable method for maze routing.

Key Objectives:

- **Breadth-First Search:** Lee's algorithm uses a breadth-first search (BFS) approach to explore all possible paths layer by layer, ensuring that the shortest path is found.
- **Wave Propagation:** The algorithm works by propagating a wave from the start point and marking each cell with the distance from the start, until it reaches the end point or determines that no path exists.

**Design Rule Checking (DRC)**  
Purpose:

- **Rule Compliance:** DRC ensures that the IC design adheres to all the manufacturing process rules and constraints. This helps avoid issues that could cause manufacturing defects or functional problems.
- **Design Integrity:** It validates the design layout to ensure that all components are properly placed and routed according to the design rules, maintaining the integrity of the design.

Key Objectives:

- **Error Detection:** Identify and flag design rule violations, such as spacing errors between metal layers, minimum width violations, and other layout issues that could affect manufacturing or performance.
- **Design Validation:** Ensure that the layout is feasible for fabrication, preventing issues like short circuits, open circuits, and other potential defects that could impact the final product's functionality and reliability.


 Visualisation of power pins, straps and rails
 
|  ![image](https://github.com/user-attachments/assets/c4cddfbc-c7a4-4343-919f-0753a7e4ef3e) | ![image](https://github.com/user-attachments/assets/7fa537ef-7c39-4a4d-aeb4-bf021c4863d0) |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|

| ![image](https://github.com/user-attachments/assets/5c7ee1ec-f799-4821-b2d1-d6edf7417b01) | ![image](https://github.com/user-attachments/assets/a750786a-f822-437e-b0b5-a80e030d98f1) |
 |-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|

| ![image](https://github.com/user-attachments/assets/378326b0-ac1a-450c-8ce8-13142294e221) | ![image](https://github.com/user-attachments/assets/a30e7ae9-384e-40a4-ba79-1bc459243f70) |
 |-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|

| ![image](https://github.com/user-attachments/assets/f9ea0063-87c3-4f81-88c5-fda5fc371ae7) | ![image](https://github.com/user-attachments/assets/ebf65e36-7f97-4106-8819-754a9a0c3a3f) |
 |-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|

| ![image](https://github.com/user-attachments/assets/2eb14afe-cfef-42be-949e-a413009bd17d) |                                                                                           |

 
 **Commands for the generation of Power Distribution Network (PDN)**
 
 ```
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
set ::env(SYNTH_STRATEGY) "DELAY 3"
set ::env(SYNTH_SIZING) 1
run_synthesis
init_floorplan
place_io
tap_decap_or
run_placement
run_cts
gen_pdn
run_routing
```
**Results of generation of PDN**

![image](https://github.com/user-attachments/assets/acaf531b-528c-46ad-8e25-a991788d533f)

![image](https://github.com/user-attachments/assets/fcb181ec-1498-434b-92e1-646ab414d6ce)

![image](https://github.com/user-attachments/assets/b4860254-5f24-4b76-b71c-f3ab157dbbf0)

**Results of succesfull routing**

![image](https://github.com/user-attachments/assets/a5922421-2bb3-4430-b2c8-026e26775cee)

![image](https://github.com/user-attachments/assets/21bb048d-51e7-4ddf-940b-e27a864dee0d)

![image](https://github.com/user-attachments/assets/1dfdfe6c-822c-4469-a2e3-ae5c49faaacc)


SPEF Extraction

Commands
```
cd Desktop/work/tools/SPEF_EXTRACTOR

python3 main.py /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/21-07_17-09/tmp/merged.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/21-07_17-09/results/routing/picorv32a.def
```
![image](https://github.com/user-attachments/assets/50c83daa-6b29-4216-8352-1f3e04e2801d)

![image](https://github.com/user-attachments/assets/4db1198f-b694-4efe-8fff-1e804bf09f47)

Post route STA

**Post-Route OpenSTA timing analysis**

Commands to be run in OpenLANE

```
openroad
read_lef /openLANE_flow/designs/picorv32a/runs/21-07_17-09/tmp/merged.lef
read_def /openLANE_flow/designs/picorv32a/runs/21-07_17-09/results/routing/picorv32a.def
write_db pico_route.db
read_db pico_route.db
read_verilog /openLANE_flow/designs/picorv32a/runs/21-07_17-09/results/synthesis/picorv32a.synthesis_preroute.v
read_liberty $::env(LIB_SYNTH_COMPLETE)
link_design picorv32a
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
set_propagated_clock [all_clocks]
read_spef /openLANE_flow/designs/picorv32a/runs/21-07_17-09/results/routing/picorv32a.spef
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4
exit

```

![image](https://github.com/user-attachments/assets/c2917835-721c-4bb8-a57f-79671702b4c5)

![image](https://github.com/user-attachments/assets/0ce415c1-5a01-4a94-a1e5-6f62d29c1882)
