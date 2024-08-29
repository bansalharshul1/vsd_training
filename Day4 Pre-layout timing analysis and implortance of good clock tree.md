# Day4 Pre-layout timing analysis and implortance of good clock tree



# Timing Modelling using delay Tables



Lef file had the info about the port information input out power and ground

Command to extract the lef: 

guidelines : input and outpur ports must lie on the intersection of the horizontal and vertical tracks

Width of Std cells should be in the odd multiples of track pitch

height of std cell should be in odd multiples of vertical pitch

![image](https://github.com/user-attachments/assets/7af6513d-279b-4d17-8eb9-aca057b952cc)

![image](https://github.com/user-attachments/assets/049bbc2c-802f-422b-9898-9164b96b9dc3)


Port class, port  

![image](https://github.com/user-attachments/assets/375cebb6-b2da-4e52-9297-68605ea27129)

command to extract the lef file:  lef write

checking the lef file 

![image](https://github.com/user-attachments/assets/83931caf-490f-4ca8-8d3e-d4af7276d082)

Next step is to use this lef in our picorv32

copy lib files and lef files to src folder

modify the config.tcl to change the LIB synthesis vaiable

![image](https://github.com/user-attachments/assets/5a4dceb4-6699-476f-8c35-f5ebf88ae093)

![image](https://github.com/user-attachments/assets/b9e056ec-a6f3-4ce6-a3e5-406e607795b5)

prep -design picorv32a -tag xyz -overwrite

add_lefs -src $lefs

run_synthesis again 

![image](https://github.com/user-attachments/assets/33240702-d4b5-414d-825f-d43173a5dd0f)

Introduction to delay tables 

![image](https://github.com/user-attachments/assets/2efcef73-1d84-4c06-bb4f-29de9c2d9eff)

saving the dynamic clock tree power 

![image](https://github.com/user-attachments/assets/6bb8849c-31f0-41b2-ba95-c74be496633c)

Delay tables 

input transition of a cell is varied and output load was also varied from 10fm to 100pf

there is a seperate transition table 

![image](https://github.com/user-attachments/assets/92a5f325-9c7a-457d-9c28-1acca6f3d30b)


# Timing analysis with ideal clock using openSTA
![image](https://github.com/user-attachments/assets/0e5cce82-c8a4-49c5-874c-fa955e207809)


Timing drivien synthesis:

1st case 

![image](https://github.com/user-attachments/assets/d80049bd-a696-4e42-b3d7-782a88097876)

![image](https://github.com/user-attachments/assets/5a90b209-d653-497d-93d4-847d40d059a6)

wns -23.89

tns -711.59

Chip area : 147712.918

![image](https://github.com/user-attachments/assets/99a970d0-d385-405b-89dc-3e2e10013441)


2ns Case: 
SYNTH_BUFFERING, SYNTH_STRATERGY, SYNTH_SIZING

![image](https://github.com/user-attachments/assets/4363c2d9-e281-45d4-b2dd-a403824e6564)

![image](https://github.com/user-attachments/assets/f0781f6c-309c-452f-8bc4-e31666411548)

running synthesis again : 

![image](https://github.com/user-attachments/assets/bff583e4-a26f-401b-bb6c-6bfebb87a5dd)

![image](https://github.com/user-attachments/assets/6476ef1b-c1c2-455d-93d8-5924a8307e1a)


NEw floorplan commands

init_floorplan

place_io

global_placement_or

tap_decap_or

checking the floorplan def in the results 

![image](https://github.com/user-attachments/assets/8f8ad0a9-eec3-4b6b-8987-d354d5061bce)

![image](https://github.com/user-attachments/assets/09449dc4-2f31-4640-951d-ce52d2a8f84c)

![image](https://github.com/user-attachments/assets/a2f8ec0f-58eb-44e0-81e3-942277041227)

# Timing analysis with ideal clock using openSTA

![image](https://github.com/user-attachments/assets/b8ccebd2-aa8b-4aca-a68c-01491251cfe7)

Setup time of FF

![image](https://github.com/user-attachments/assets/ee18f6b4-962b-489f-afda-2d38bb61ecf4)

Clock jitter effect 

Delay < time_period - Setup - uncertainity



# clock Tree synthesis TritonCTS and signal integrity


# Timing analysis with real clock using openSTA
