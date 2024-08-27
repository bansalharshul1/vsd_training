![image](https://github.com/user-attachments/assets/7466d68c-79a3-4a3e-bf8f-51dff9955bfb)# Day4 Pre-layout timing analysis and implortance of good clock tree

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



# Timing analysis with ideal clock using openSTA


# clock Tree synthesis TritonCTS and signal integrity


# Timing analysis with real clock using openSTA
