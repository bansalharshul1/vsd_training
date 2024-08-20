# Day1 Introduction to Opensource EDA and PDK

Workflow -->

  --> Chip modelling to verify the spec vs complier output

  --> soft copy of hardware using Bluespec
  
  --> RTL using verilog

  --> mircroprocessor vs microcontroller ( IO/peripherals ) 
  

![1](https://github.com/user-attachments/assets/df24ac76-881a-4c5a-b0c1-0a73ce7d3e55)

Introduction to Open-source ASIC resources

![image](https://github.com/user-attachments/assets/99641a2e-b6a3-4f1f-b0ce-5ab71e8d00ea)

![image](https://github.com/user-attachments/assets/cb847228-cf27-4699-9d25-1a1992bc25cc)


# Simplified RTL2GDS flow

Backend

--> Floorplanning Macro planning, pin locations, row definations

![image](https://github.com/user-attachments/assets/31f3e526-6de7-45ae-937c-d0527d93085b)

![image](https://github.com/user-attachments/assets/d7ba955e-21cc-40cb-a209-021ca8c42b07)

--> Power planning  


![image](https://github.com/user-attachments/assets/057ec6dc-7866-4049-8878-dbba40207c07)

--> Placements   Global/detailed placements

![image](https://github.com/user-attachments/assets/9276fb7b-ac0e-4287-af6e-1d21a2c3d26c)

![image](https://github.com/user-attachments/assets/aee89839-2d85-4c98-8f33-4f18f6c3e5a8)

--> CTS 

![image](https://github.com/user-attachments/assets/04bd96c1-bef1-42bd-92e2-60e429883cb3)

--> routing

![image](https://github.com/user-attachments/assets/3e3e364c-1714-4e43-b2c6-30e07cb4f650)


-->  Physical Verification 

   DRC & LVS

--> Timing and IR signoff


# OpenLane ASIC Flow

![image](https://github.com/user-attachments/assets/33eeb813-4565-4c0e-a60d-0b50a7da9838)

![image](https://github.com/user-attachments/assets/cddd9d01-6707-430f-b2fc-2ab3c97024d6)

![image](https://github.com/user-attachments/assets/3cb3eabc-1e9d-4fe3-9c34-c526bb359464)

Magic for extraction 
Netgen for LVS

# Directory Structure

PDK Directory : -

sky130A --> compatible with open source tools

![image](https://github.com/user-attachments/assets/8abc2556-0ad8-4460-ba56-1332b3c0772a)

we will be using sky130_fd_sc_hd  library

![image](https://github.com/user-attachments/assets/06525252-5145-4dae-8165-4e2e87945e26)

Different corners --> FF - fast-fast TT - Typical SS -  slow slow

lef flies --> cell lef and tech lef (layer information )


Working Directory: - openlane

# Design Preparation


1. docker
2. ./flow.tcl -interactive {invole step by step flow}
3. package require openlane 0.9  {import all the packages required to run openlane}

   contents of design folder for picorv32a:

   ![image](https://github.com/user-attachments/assets/9c478ce3-baac-4042-82fe-4b46fbbef25c)

   config.tcl --> bypass any default configuration

   pdk specific config.tcl --> higher precedence than config.tcl

   scr --> contains the verilog and SDC for our design

4. prep -design picorv32a {setting the pdk path, choosing the std library, sourcing config.tcl}

   ![image](https://github.com/user-attachments/assets/c9c68a2d-7ec9-4b1e-9898-caf32d83d2bc)

   --> this step creates a run directory in design/picorv32a/results/new_run_directory

   --> mergerd tech lef with cell lefs


# Review design prep & run syntesis 
![image](https://github.com/user-attachments/assets/e7315b4c-f3c4-4685-b38e-e243c673ec5d)

tmp folders contains the temporary files --> merged.led  (techlef and cell lefs appended)

reports and results  folders will be empty as of now.

config.tcl --> shows all the configs that are being used in setup. This can be used to verify if configurations are correctly applied or not

![image](https://github.com/user-attachments/assets/a118dfdf-8730-47bb-b3f1-1a83c833f1fa)

cmds.log --> to check all the commands that were performed 


5. run_synthesis  {invokes syntesis and ABC}



# openLANE github link
https://github.com/efabless/openlane2

# steps to characterize synthesis results

![image](https://github.com/user-attachments/assets/2db074e8-4185-4c7a-a924-a717007b694f)


5.1 calculate the flop ratio 

![image](https://github.com/user-attachments/assets/5519c986-f76a-4765-8d4f-4e2f97d04911)
No of D-FF's 1613

![image](https://github.com/user-attachments/assets/406145d5-b4c5-44bc-9a99-e28dea8773cf)

Total number of cells/ instances : 14876

flop ratio  no of FF/ total no. of cells  =  10.8%


5.2 Viewing the results of syntesis

![image](https://github.com/user-attachments/assets/ba9416f7-b102-4a90-b8d8-75a4877e16ae)







