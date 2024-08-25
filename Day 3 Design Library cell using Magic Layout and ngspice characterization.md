
# Day3 Design library cell using Magic Layout and ngspice characterization


# Labs CMOS inverter ngspice simulations:


IO placer revision: 

we can reset any variable in openlane and re run a particular stage and changes will be reflected in the output


Spice deck creation for CMOS inverter

![image](https://github.com/user-attachments/assets/0be47d02-4fbf-4b74-94fc-a4cb6522adcc)

![image](https://github.com/user-attachments/assets/16d36ea9-43af-4592-a966-425a8e592e1c)

CASE 1:
width is same for nmos and pmos in this case 
VTC:  slightly shifted to left 
![image](https://github.com/user-attachments/assets/c15d5062-34cf-4180-bafc-c875e6768030)

CASE 2 :
width of pmos 2.5 * width of nmos
![image](https://github.com/user-attachments/assets/5a774491-4342-4073-8e8f-0deea4268e78)


switching threshold: point where vin = vout
point where both nmos and pmos are in saturation

case 1 switching threshold ~ .9 
case 2 switching threshold ~ 1.2 

![image](https://github.com/user-attachments/assets/ac21ddd7-a100-4203-aa37-c6ce6f1ba5d9)

![image](https://github.com/user-attachments/assets/302fb546-321e-4ece-b949-0176ff52243b)

![image](https://github.com/user-attachments/assets/c40cc96d-b6d0-4039-863a-f74bbe7dd410)
 
indentifying the how rise and fall delay vary with the change in switching threshold

 
![image](https://github.com/user-attachments/assets/d4f1ff2c-f5cb-4568-bc67-501f1610d791)



