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
    prep -design [!----file name--]
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


