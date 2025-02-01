# Introduction
You all have used simple electronic appliances like washing machines, refrigerators, microwaves, ovens etc. and also some smart appliances and other products like laptops and mobiles. Many of the appliances are able to perform one task and some to perform one task more eficiently and some are to perform multiple tasks. But, what is common among all of these products, that is its processing unit, its core. That is its chip!
ssd 
Chip design is a very interesting (and comlex) medium in chip design we can create everything that we want for our use and th euse of the world or it can be a way to do so.
# OpenLane
Here we are talking about an open source package desigened to create *GDSII* file while we put input of *RTL* and *PDK* files. These files are very complicated to understand in one view. But we are not here about that all file task. We will just understand about, What comes under OpenLANE Package.<br>
1. Synthesis
2. Floor planning and Power Planning
3. Placement
4. Clock tree synthesis
5. Routing
6. Sign off
<br>

### Before moving directly towards the first step, that is synthesis, we will take a look how to setup the OpenLANE package.
First of all, we will be using Ubuntu 18.04 operating system for using OpenLANE Package. <br>
![Screenshot 2025-01-29 192055](https://github.com/user-attachments/assets/ebea5fab-e6fe-44ac-864a-a6f23edf28cc)
<br>
To run OpenLANE, we have to open the file which contains complete package of OpenLANE applications and designs and then right click it to open it in terminal. And then enter:- <br>
```
    docker
```
After that the promot symbol will change into some numericals *bash-4.2$* then enter:-
```
   ./flow.tcl -interactive
```
![Screenshot 2025-01-29 195945](https://github.com/user-attachments/assets/fdc066a3-371a-43a2-923c-f0ee2119c7d9)

We will require the package <i>openlane 0.9</i>, hence we will import that package by typing the code:-
```
    package require openlane 0.9
```
Then we have to look for the design on which we will work and start the preperation of the design before going to the process of synthesis. In my case the design is "picorv32a" :-
```
    prep -design [!---file name---]
```
![Screenshot 2025-01-27 215540](https://github.com/user-attachments/assets/df5ef9c5-7184-427d-9d5c-48ec9bc5cf2d)

After preperation, we will run the synthesis process:-
```
    run_synthesis
```
![Screenshot 2025-01-27 220919](https://github.com/user-attachments/assets/63bd6252-8e16-4bb4-88c4-341d6cedc50d) <br>
<i>Flop Flop ratio = 11.0446356547459</i> <br>
After the process of synthesis we will run the process of **floorplan**. In floorplan process the dimensions of the base of the chip is designed according to the components of the netlist. 
```
   run_floorplan
```
![Screenshot 2025-01-29 213803](https://github.com/user-attachments/assets/e575ddfd-8f3c-40cf-bd61-a85b62bd3ba9)


After completing the process of floorplan we can view it in the another open source application called ***Magic***. Magic is an open source programme and another part of openlane package. To review our floorplan layout in magic, we first have to open a new tab in terminal and type the following syntax:
```
  magic -T [!---path of 'lef' file---] read [!---path of 'def' file---] .def $
```
![Screenshot 2025-01-29 222756](https://github.com/user-attachments/assets/811db2b9-7f80-4550-a956-12006bd61538) <br>
And if we had to zoom to a particular cell of the floorplan layout, we will see the following. <br>
![Screenshot 2025-01-31 204657](https://github.com/user-attachments/assets/c1bf6149-8ae0-458f-955c-db8dd38d6f8f) <br>

After the floorplan, we will have another process called cell placement, here the term cell refers to the gates that we will be puting in our chip. These gates and other components are present in the shape of box, that is why they are called as cells. In openlane the process of cell placement occures in two stages, one is **GLOBAL PLACEMENT**and another is **DETAILED PLACEMENT**. In global placement it is ensured that cells in the design are placed in a position that the space between the two cells is least and in this case, cells can even overlap each other, and in the detailed placement, as the name suggests the detailing will be more precise and cells do not over lap each other. And once again, the syntax is:
```
  run_placement
```
In placement, like in floorplan, we can fiew the layout in magic by the same code but the *.lef* and *.def* should be assosiated with cell placement, you yust have to cahange *.def* file, *.lef* file will be the same.
```
  magic -T [!---path of 'lef' file---] read [!---path of 'def' file---] .def $
```
### And you willget the output: 
![Screenshot 2025-01-30 213205](https://github.com/user-attachments/assets/18d5ab10-0f2a-42bd-b70a-686c7e411404)

# Spice deck file
In this file, we can see the input and output state of the design, and it is a quite long process. First of all, type this line in the terminal of openlane folder 
```
  git clone https://github.com/nickson-jose/vsdstdcelldesign.git 
```
This will create a new folder inside your openlane folder named *vsdstdcelldesign*. Before opening that folder, we have to copy *sky130A.tech* which is present inside magic folder, to the new file that is created just now and enter the code 
```
  magic -T sky130A.tech sky130_inv.mag $
```
### And you will see the following layout: 
![Screenshot 2025-02-01 123016](https://github.com/user-attachments/assets/dc2b2641-955c-43f4-99b8-412a35803c8f)

After that we have to write *extract all* in the other window that opens with the  magic tool.
![Screenshot 2025-02-01 152931](https://github.com/user-attachments/assets/937a337a-c011-48d5-9bf6-8e7f79a17066)

This will create an another file in the *vsdstdcelldesign* as *sky130_inv.ext*. Then once again open the same window and enter *ext2spice cthresh 0 rthresh 0* and in the next promot, type  *ext2spice* and once again open the folder *vsdstdcelldesign* and there will be one more file named *sky130_inv.spice*. And to read the file, in the terminal enter *vim sky130_inv.spice*, and it will redirect you to this page 👇:
![Screenshot 2025-02-01 155305](https://github.com/user-attachments/assets/b2bfbcc8-9474-4140-ae36-8df2c37ba2c8) <br> 

And you have to make some changes like this in that file: <br> 
![Screenshot 2025-02-01 160601](https://github.com/user-attachments/assets/d05166ca-2827-4d10-a95a-74d25462e364)

> Ok time is over now




