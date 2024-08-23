# Day 2 Floorplaning and introduction to std cell library


# Chip Floor planning considerations 

# utilization factor and aspect ratio

1. First step is to define the width and height of the Die and Core

![image](https://github.com/user-attachments/assets/50927129-b7c8-4abc-84a0-374fccd917ee)


Calculating the rough area using the number of instances in the netlist 
![image](https://github.com/user-attachments/assets/b68093ff-054a-4c26-aba2-9714785c86ba)

utilization factor = Area occupied by netlist / total area of the core
utilization factor <1 signifies extra area present in core


aspect ratio = height of core / width of core


# concept of pre- placed cells

2. defining locations of preplaced cells
![image](https://github.com/user-attachments/assets/e5640d91-6c64-4207-b4c4-f71f294afd78)

![image](https://github.com/user-attachments/assets/d1cafd23-dfe3-4fa4-9637-743b6c882003)

The placemnt of these cells are placed before the actual placment and locations are fixed

Macro or ips to be re-used multiple times

depanding on design bakgroung pre place cells are choosen. Once placed they are not moved in deisgn cycle

pre place cells are surrounded by decaps.

decaps are added to take care of voltage drop and mantain a relaiable voltage level

![image](https://github.com/user-attachments/assets/09da046e-cda2-416b-b74b-d6fb0078e835)

![image](https://github.com/user-attachments/assets/d0e89d2d-b13c-41d2-bce0-f78eed0b1fff)


![image](https://github.com/user-attachments/assets/686c8001-22f9-4bf6-8504-3bff3ed7998d)

3. Power Planing

![image](https://github.com/user-attachments/assets/559e4efe-227d-4460-acb0-676ed37bf470)


4. Pin placement

generally all input ports in the left and output ports on the right side


depending on connectivty and location of blocks to determine to best possible possition for a particular pin


Clock ports are bigger in size compared to other inputs 
![image](https://github.com/user-attachments/assets/29305f7c-fd28-42fd-801b-e776a447f1b3)

5. logical cell placement blockages

so that automatic placment tool doesn't place any cells in pin area we place blockages

![image](https://github.com/user-attachments/assets/54dc5e6d-6924-4e2c-afc6-9fd1b2e9a5cb)


#LAB Floorplaning
openlane/congifuration/README.md

Floorplanning switches variables like aspect ratio core utilization factor

![image](https://github.com/user-attachments/assets/7dd0c11f-e0a9-43bb-9aa2-ca3331667eb0)

Floor planning options set in our config.tcl 

Vertical and horizontal metals will be one more than what is specified here. so 5 verical and 4 horizontal

![image](https://github.com/user-attachments/assets/174729bb-4e9f-412f-8d76-0265ec1854c5)

Running the floorplan

command --> run_floorplan

![image](https://github.com/user-attachments/assets/01076139-5a37-4067-9d2a-16774f0d5163)


# reviewing the floorplaning

# Not seeing the logs present in vedio to verify the floorplaning ioplacer log different than vedio


Def file snipped 

Can calculate the die area from the dimensions

![image](https://github.com/user-attachments/assets/bc3708d3-6e4f-403f-9804-7c5dc3cc54b5)

Command to run magic and open the def 

output def present in results/floorplan

magic -T tech_file_path lef read mergerd.lef def read def_path

# checking floorplan in magic

Since we set FP_IO_MODE 1 . so input outpout pin are at equal distance


Z , shift Z for zoom and zoom out

S to select any object 

horizontal io on metal 3 
![image](https://github.com/user-attachments/assets/e4c6ac77-893d-4935-ac30-bd00a23abede)

# verical io on metal 2 not in 4 as said in vedio
![image](https://github.com/user-attachments/assets/a2abfa5d-6010-4d15-9f19-2a801c28cea8)


tap cells and decaps cells
taps cells are diagonally apart by some distance which can be set using the the config keyword
![image](https://github.com/user-attachments/assets/54c5042e-db77-4fd3-b3a9-2e50f7305dac)


the std cells are not placed in floorplan stage you can see them at the lower left corner

![image](https://github.com/user-attachments/assets/4597d7c4-0052-4695-8bdf-e96b2505e3f7)


# Library Binding and palcement

1. Bind netlist and physical cells
   all cells are rectangular with proper height and width

   ![image](https://github.com/user-attachments/assets/735da6bb-b3b2-43b0-8328-1465ededf555)

   library --> contains the timing physical and electrical info of different cells

2. placement

   pre-place cells are already present

   ![image](https://github.com/user-attachments/assets/c569dccc-fe4a-499e-b8cc-e182bd3d7c75)

3. optize placement
  
   optimizing the placement with etimated wirelength and capacitances

   Repeater/buffer stages are added to maintain signal integrity

   ![image](https://github.com/user-attachments/assets/65570014-4cc9-46d5-91ac-f1e5aaf79ca4)

   part of circuit which operates at high speed we might place the cells with no gap in such cases to save wire delay

   during routhing the connection can go from different metal layers

   we do setup analysis with ideal clocks to verify if the placement is reasonable or not


4. Need for libraries and characterizatio
   
![image](https://github.com/user-attachments/assets/4f99fc52-3568-4b9e-ba89-c88349a75e33)


5. Congestion aware placemnet using RePLAce
   two stages -->
   Global placement or coarse placement - no legalization (std cells should have any overlaps) --> main objective is to reduce the wire length

   Half perimeter wire length  (HPWL) : 

   OverFlow (OVFL)

   if OVFL decreases that mean design is converging
   
# LAB run_placement

magic after global placement

![image](https://github.com/user-attachments/assets/2b246fbd-69db-4abe-8e8b-8f53af48f553)

Power distribution network should be created during the floorplaning but currently in openlance flow it will be done after CTS


# Cell Design Flow

1. Inputs of cell design Flow
   
   ![image](https://github.com/user-attachments/assets/593ebfa3-235d-4353-8ec7-1ed247334cd7)

   library contains the cells of different functionality, multi vt cells, different sizes.

   taking INV as exapmple

   Inputs for cell Design Flow
   1. PDK: DRC & LVS rules, spice models, library & user-defined specs
      example of Design rules
      ![image](https://github.com/user-attachments/assets/2770dead-4c5c-4e02-adfe-4e38a66ee855)
      Spice model parameters:
      ![image](https://github.com/user-attachments/assets/9f2b02cc-9ef2-4f77-ad4f-9ec3c2127d50)
      
2. Circuit Deisgn step
   cell height is fixed for a particular technology,  cell witdths are dependent on drive strength
   User defiend specifications : 
   cell height, Supply voltage, Metal Layers, Pin locations, Drawn gate length

   1. Implement the functionality
   2. model PMOS and NMOS in such a way to meet the library requirements such as W/L ratio, mostly based on spice simulation
      ![image](https://github.com/user-attachments/assets/0325da4d-af4f-43da-b484-a20bc72e64db)
   3. CDL file is the output of this step circuit description language

4. Layout deisgn step
   1. get Pmos and nmos network path
   2. draw a stick diagram using it
      ![image](https://github.com/user-attachments/assets/84af4e49-6b8b-4f16-b83a-24f4caa572ed)
   3. convert the stick diagrom into the layout keeping DRC in mind 

6. Typical characterization Flow
   ![image](https://github.com/user-attachments/assets/55bf9b87-8af8-4dfb-a1ce-2eb3c33a0af5)
   ![image](https://github.com/user-attachments/assets/47d43dca-c917-421a-982d-48447703fdf8)

   1. read the models
   2. read the extracted spice netlisted
   3. define / recognise the behaviour of buffer
   4. read the subcircuit of the inverter
   5. attach the necessary power sources
   6. apply the stimulus.
   7. apply the load this needs to be varied in a range
   8. provide a simulation command tran or dc
   Characterization tool GUNA

   output: timing,noise,power libs, functions

 # General timing characterization parameters

 1. Timing threshold definations
    1. slew_low_rise_thr , slew_high_rise_thr
    2. slew_low_fall_thr, slew_high_fall_thr
    3. in_rise_thr - 50% point in input and output
    4. in_fall_thr - 50% points in 
    5. out_rise_thr
    6. out_fall_thr
      
2. propagation delay and transition time
   




