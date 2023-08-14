### Table of Contents
- [Day 0](#day-0)
- [Day 1](#day-1)
- [Day 2](#day-2)
- [Day 3](#day-3)
- [Day 4](#day-4)
- [Day 5](#day-5)
- [References](#references)

### Day 0
<details>  
<summary>  
Yosys  
    
</summary>  

    
I installed Yosys using following commands:  

```
$ git clone https://github.com/YosysHQ/yosys.git  
$ cd yosys-master   
$ sudo apt install make (If make is not installed please install it)  
$ sudo apt-get install build-essential clang bison flex \  
    libreadline-dev gawk tcl-dev libffi-dev git \  
    graphviz xdot pkg-config python3 libboost-system-dev \  
    libboost-python-dev libboost-filesystem-dev zlib1g-dev  
$ make config-gcc  
$ make   
$ sudo make install
```

Below is the screenshot showing successful installation and launch:  

<img width="550" alt="Screenshot from 2023-07-31 09-49-23" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/c6031ebd-ee60-40c7-8327-88f82ef83f41">  

</details>

<details>
<summary>  
Iverilog  
</summary>  

I installed verilog using following command: 
```
sudo apt-get install iverilog  
```
Below is the screenhot showing successful installation and launch:  
<img width="550" alt="Screenshot from 2023-07-31 09-50-00" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/ac36da4e-6f33-47f0-8166-68141b26487f)">  

</details> 

<details>
<summary>  
    Gtkwave
</summary>
    
I installed gtkwave using following commands: 
```
sudo apt install gtkwave  
```
Below is the screenshot showing successful installation and launch:  
<img width="550" alt="Screenshot from 2023-07-31 09-51-21" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/865eae3a-149a-4fe6-89bf-9069cc70f48b">  


</details>    

<details>
<summary>
        NgSpice        
</summary> 

    
Download the tarball from https://sourceforge.net/projects/ngspice/files/ to a local directory.  
Now, use the following commands to unpack and install it:

```
$ tar -zxvf ngspice-40.tar.gz  
$ cd ngspice-40  
$ mkdir release  
$ cd release  
$ ../configure  --with-x --with-readline=yes --disable-debug  
$ make  
$ sudo make install
```

The screenshot of successful installation is shown below:  

<img width="550" alt="Screenshot from 2023-08-08 17-12-55" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/acb2abd2-75ff-4f01-985d-409e5dcc48df">  
    
    
</details>

<details>
<summary>
        magic
</summary>

    
I have used the following commands for the installation of magic:
    
```
sudo apt-get install m4
sudo apt-get install tcsh
sudo apt-get install csh
sudo apt-get install libx11-dev
sudo apt-get install tcl-dev tk-dev
sudo apt-get install libcairo2-dev
sudo apt-get install mesa-common-dev libglu1-mesa-dev
sudo apt-get install libncurses-dev
git clone https://github.com/RTimothyEdwards/magic
cd magic
./configure
make
sudo make install
```
The screenshot of successful installation is attatched below:  

<img width="550" alt="Screenshot from 2023-08-08 15-53-55" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/f7ac78ad-b6ca-4351-bf59-c0b64ba0cb9d">  


    
</details>

<details>
<summary>
    OpenSTA
</summary>
I have used following commands to install OpenSTA:   
    
```
git clone https://github.com/The-OpenROAD-Project/OpenSTA.git
cd OpenSTA
mkdir build
cd build
cmake ..
make
sudo make install
```

The screenshot of successful installation is shown below:  

<img width="550" alt="Screenshot from 2023-08-08 17-45-01" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/d6732d99-4b05-4f93-9d77-4fdf6cf9a083">  


</details>


### Day 1
<details>
<summary>
1.1 Introduction to iverilog design testbench
</summary>
  
**Simulator:**
It is a tool used for simulating the design. In this course, we will be using **iverilog** simulation tool.  
The simulator always looks for the changes in input signals. Upon change of input signal, the output is evaluated.  
**Design:**
It is the actual verilog code or set of verilog codes which has the intended functionality to meet with the required specifications.  
**Testbench:**
It is the setup to apply stimulus(test_vectors) to the design to check it's functionality.  

<img width="550" alt="Screenshot from 2023-08-08 22-12-13" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/5b2ba389-6dbd-4d1b-9ae2-1dfc81deabd3">  

<img width="550" alt="Screenshot from 2023-08-08 22-25-09" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/bbf0f254-9f81-41d6-9977-a4063eef6867">


</details>

<details>
<summary>
1.2 Labs using iverilog and gtkwave
</summary>
    
Clone into the github repository https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git by using the following command:
    
```
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
```

This consists of all the necessary files required for the entire lab sessions/workshop.  
Today, we will be executing the 2:1 mux (good_mux.v) by using the iverilog simulator, which creates a vcd file and view the output with the help of gtkwave. Use the following commands to simulate the verilog file and dump the generated vcd file into gtkwave:
```
iverilog good_mux.v tb_good_mux.v
./a.out
gtkwave tb_good_mux.vcd
```
The output generated is as follows:  
<img width="600" alt="Screenshot from 2023-08-08 21-29-10" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/7d520c61-869f-4087-944c-1808c7a5ff89">


</details>

<details>
<summary>
1.3 Introduction to yosys and logic synthesis
</summary>
    
**Yosys:**
The synthesizer tool we use in this lab session is **yosys**.  
<img width="550" alt="Screenshot from 2023-08-08 22-47-16" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/1b146fd0-a7a3-4fd2-a8e9-590261400b3c)">  
The synthesis output is said to be correct if the output observed during the RTL simulation is same as that of during the simulation of design testbench.  
We can use the same testbench for both the simulations.  

**Logic synthesis:**  
It is process of converting RTL design into gate level. The RTL design is converted into gates and connection is made between gates. The output file generated is called **netlist.**


</details>

<details>
<summary>
1.4 Labs using yosys and Sky130 pdks
</summary>

Invoke yosys and use the following commands to synthesize the design:  
```
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> read_verilog good_mux.v
yosys> synth -top good_mux

```
The synthesizer output is shown below:  
<img width="600" alt="Screenshot from 2023-08-08 21-36-50]" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/2c3a3b54-a0ae-47ff-91f5-976a794fe119)">  
 

The commands to creating and viewing the netlist are listed below:  

```
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
yosys> write_verilog good_mux_netlist.v 
yosys> !gvim good_mux_netlist.v
```
The information regarding the number of cells used is here: <img width="500" alt="Screenshot from 2023-08-08 21-36-05" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/e4e1c537-025b-4453-9ec8-df287422f73d">  

The netlist files is as shown below:  
<img width="600" alt="Screenshot from 2023-08-08 21-40-27" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/77ff5e8e-be1f-4681-8093-46ccad36a6e5)">  


</details>

### Day 2

<details>
<summary>    
2.1 Introduction to timing.libs
</summary>
Use the following commands to open the lib file:  
    
```
$ gvim ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Below is the screenshot of the library file:  
<img width="550" alt="Screenshot from 2023-08-11 15-34-52" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/a4c05c75-fd39-42cf-a870-bdf025f213f6">  
We have 3 important factors which determines the working of a semiconductor. They are: "**P**", "**V**", "**T**" which stands for Power, Voltage and Temperature respectively which forms the pillar for the working of a design.  

- The Process will have many variations due to fabrication of the transistors.
- The change in Voltage will effect the behaviour of the circuit.
- As semiconductors sre sensitive to Temperature, even a minimal temperature change may effect the working parameters of the components.

The libraries are mainly characterized to model these variations.  

</details>

<details>
<summary>
2.2 Hierarchical vs Flat synthesis  
</summary>

    
</details>

## References
1. https://www.udemy.com/course/vsd-a-complete-guide-to-install-open-source-eda-tools/
2. https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
3. https://www.vsdiat.com/course_content?uniqueid=20220801054525 







