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

6. Placement & routing



7. 






