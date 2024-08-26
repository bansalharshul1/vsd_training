
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


# Labs 

Git repo link: https://github.com/nickson-jose/vsdstdcelldesign
![image](https://github.com/user-attachments/assets/cc46a6a5-bf9f-4773-8dd7-2c725f9ee40f)

checking the mag file. 
![image](https://github.com/user-attachments/assets/a2e9ee09-9a4e-4b44-80e9-4459305323db)

![image](https://github.com/user-attachments/assets/7e4541ff-b5d3-4cca-8560-0db3732f953d)













# Inception of Layout and CMOS fabrication process

1. Creating Active regions:
   16 - mask process

   1. selecting the substrate
      Doping level of substrate should be less than the well doping
      ![image](https://github.com/user-attachments/assets/8ca88c14-da77-48f7-8e70-ac66723db926)

   2. Creating active regions
  
      16-mask cmos process
      Mask 1
      ![image](https://github.com/user-attachments/assets/0b2273cf-981a-4c0d-9b13-47e5f3cc6da6)

      depositing the layer of silicon oxide then a layer of silicon nitride
      deposit of layer of photoresist
      
      
      etching away the silicon nitrid
      growing SI02 ,LOCOS local oxidation of silicon
      ![image](https://github.com/user-attachments/assets/a0feb7f4-c322-424e-ab39-c4439b6def2a)
      etch out silicon nitride
      isolation regions present the 2 device from interfering in other;s function
      
   4. Nwell and P well
      Mask2
      ![image](https://github.com/user-attachments/assets/90e954de-325f-4b76-9e75-cca91696ec3e)
      Ion implantation using Boron or any other P type material
      ![image](https://github.com/user-attachments/assets/a521a19d-2bd0-478f-b8be-3508ddde9794)
      making n well using Phosphorous
      ![image](https://github.com/user-attachments/assets/57f006bf-a367-42b4-a836-d74a63bd6c5f)
      n-well and p well are created but we need to do diffusion twin well process to ave clear nwelll and well
      ![image](https://github.com/user-attachments/assets/86ffa298-9348-4cca-a438-7a7e1b2270c1)


   4. Formation of gate:
       ![image](https://github.com/user-attachments/assets/30d093d5-f3e1-46c9-a0ef-75f9fb0a689b)
      doping concentration and Cox are controlled to get the desired Vth for the mos
      ![image](https://github.com/user-attachments/assets/40dce2d9-f19d-4160-80f9-f326707c3e8d)
      deposition of polysilicon and doping it with more impurities
   
      ![image](https://github.com/user-attachments/assets/8bc42c90-053a-4c02-9f5f-47a71b62bbf1)
      ![image](https://github.com/user-attachments/assets/65943023-fdf3-4b9f-9fe9-bbbfac6ee326)
  
   5. Lightly doped drain LDD formation
      Readon of  P+, P-,N  & N+,N-,P doping profiles
      1. hot electron effect
      2. short channel effect

      when device size decreases the elctrical field increases,

      ![image](https://github.com/user-attachments/assets/abeb891b-b437-4fdd-9f82-f3eb55849d02)
      ![image](https://github.com/user-attachments/assets/4b7181f1-6d79-4c5f-b01e-8169a6ee472a)
      
   6. Source and drain formation
      a thin screen oxide is added to avoid channeling effects
      ![image](https://github.com/user-attachments/assets/e35766cd-101f-48b4-9a2f-91c844e0ae32)
      ![image](https://github.com/user-attachments/assets/40e986aa-6ec7-4050-88f7-0990bd332487)

   7. Steps to form contacts and interconnects
      Sputtering : using titanium on wafer surface.
      ![image](https://github.com/user-attachments/assets/0f3a395b-8792-4027-97b5-b5bd68830a97)

      Creating a contact
      Heating in nitrogen ambient
      ![image](https://github.com/user-attachments/assets/d8494b6a-62a7-478b-9b70-4e3d2bfdadd3)

   8. Higher metal level formation
      deposition of SiO2 with phosphotorous or boron
      Chemical mechanical polishing for planarizing wafer surface
      ![image](https://github.com/user-attachments/assets/164207f5-4927-4685-9094-3c83dad98012)



  # basic layers layout and LEF using inverter
  ![image](https://github.com/user-attachments/assets/bcdea3ea-d5c2-422a-9dc5-9ea72c17ee85)
   ![image](https://github.com/user-attachments/assets/994ecee1-7d59-484f-962d-b50b2eca2742)

# steps to create STD cell layout and extract spice netlist

1. Sky130 has a nomenclature of unithd with demension in microns  0.46 x 2.72(width X height) for sky_130fd_sc_hd PDK
2. invoke the magic tool using this command : magic -T sky130A.tech&
3. creating a bounding boc of with 1.38(3xwidth(unithd)) and height 2.72  commmand : property FIXED_BBOX {0 0 138 272}
4. press S and type box in the window
   ![image](https://github.com/user-attachments/assets/41433f48-ad1e-4f02-90d5-b61cf11aa841)
5.  n-substrate -<n substrate contact>- locali
    ![image](https://github.com/user-attachments/assets/4e160a1e-3c9f-41ee-859b-327ad8f14c71)
    ![image](https://github.com/user-attachments/assets/9107808a-8080-4f30-a3be-712eaa47ace5)

6. Extract the layout to ext file command extract all
   ![image](https://github.com/user-attachments/assets/6031181c-88eb-40d2-a1bd-3373c88195b7)

7. This ext file will be used to create a spice file  Command: ext2spice cthresh 0 rthresh 0
   ![image](https://github.com/user-attachments/assets/3df27c2c-418a-473e-b262-4cc8010a925d)

8.  Spice file
   ![image](https://github.com/user-attachments/assets/9caf1824-6600-423e-a770-e84973d6c456)




# Tech File Labs


1. Create final SPICE deck using sky130A tech
   ![image](https://github.com/user-attachments/assets/561ea95d-d040-4d59-b5fc-fec45760ac64)
![image](https://github.com/user-attachments/assets/a3ea89ab-ed1b-4ea2-84eb-03b811574b93)

Model files
![image](https://github.com/user-attachments/assets/30995339-677b-4735-a3aa-aacc98270e10)


Running the simulation using ngspice


    




