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
<br>
<br>
First of all, we will be using Ubuntu 18.04 operating system for using OpenLANE Package. <br>
[https://github.com/user-attachments/assets/0a259704-b994-448b-a5bb-f720af99302b]
<br>
<p4>To run OpenLANE, we have to open the file which contains complete package of OpenLANE applications and design. And then enter:-</p4> <br>
<pre id="code-block">
  <code>
    docker
  </code>
</pre>
After that the promot symbol will change into some numericals "bash-4.2$" then enter:-
<pre id="code-block">
  <code>
   ./flow.tcl -interactive
  </code>
</pre>
(https://github.com/user-attachments/assets/3f957826-72d7-4783-8ab0-249eb1a354c5) <br>
We will require the package <i>openlane 0.9</i>, hence we will import that package by typing the code:-
<pre id-"code-block">
  <code>
    package require openlane 0.9
  </code>
</pre>
Then we have to look for the design on which we will work and start the preperation of the design before going to the process of synthesis. In my case the design is "picorv32a" :-
<pre id-"code-block">
  <code>
    prep -design [!----file name--]
  </code>
</pre>
(https://github.com/user-attachments/assets/7a7d5fd8-3c10-467f-8249-4a6a805b9c89) <br>
After preperation, we will run the synthesis process:-
<pre id-"code-block">
  <code>
    run_synthesis
  </code>
</pre>
![Screenshot 2025-01-27 220919](https://github.com/user-attachments/assets/63bd6252-8e16-4bb4-88c4-341d6cedc50d) <br>
<i>Flop Flop ratio = 11.0446356547459</i> <br>
After the process of synthesis we will 

