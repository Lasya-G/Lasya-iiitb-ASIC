### Table of Contents
- [Day 0 - Tools Installation](#day-0---tools-installation)
- [Day 1 - Introduction to Verilog RTL design and Synthesis](#day-1---introduction-to-verilog-rtl-design-and-synthesis)
- [Day 2 - Timing libs, hierarchical vs flat synthesis and efficient flop coding styles](#day-2-timing-libs,-hierarchical-vs-flat-synthesis-and-efficient-flop-coding-styles) 
- [Day 3 - Combinational and sequential optmizations](#day-3-combinational-and-sequential-optmizations)
- [Day 4](#day-4)
- [Day 5](#day-5)
- [References](#references)

### Day 0 - Tools Installation
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


### Day 1 - Introduction to Verilog RTL design and Synthesis
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

### Day 2 - Timing libs, hierarchical vs flat synthesis and efficient flop coding styles

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
.lib file is a bucket of all the standard cells that are available or required for the model.  
A cell consists of the details of the leakage power of all the input conbinations of the cells and the delay, area occupied and some other features like pin details, timing information etc.  

Observe the following image:  
<img width="550" alt="Screenshot from 2023-08-14 14-18-06" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/8d5a0273-3d13-460b-9b40-7b50c5fe7aec">  
From the above image, we can depict that the larger means that the cell employs wider transistors which leads to faster performance.

</details>

<details>
<summary>
2.2 Hierarchical vs Flat synthesis  
</summary>  

Open the verilog file using the following command:  
```
$ gvim multiple_modules.v
```
This is the verilog file:<img width="550" alt="Screenshot from 2023-08-14 14-37-03" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/7a06bb18-2134-4256-b152-b9546cc96497">  
Now, launch yosys and use following commands:  
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> read_verilog multiple_modules.v
yosys> synth -top multiple_modules
```
The following report will be generated:<img width="600" alt="Screenshot from 2023-08-14 14-47-09" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/62ba86c2-101c-48ac-9f5a-c82f84aa73c5">  
Read the design to the library using following command:  
```
yosys> abc -liberty  ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
```
Now, when we give the command "**show**", we expect to see the following structure:<img width="550" alt="IMG_0028" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/935948d5-c8f5-4f91-bed5-b17cde43a969">  
But the following will be displayed:<img width="550" alt="Screenshot from 2023-08-14 15-13-14" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/02edb451-f891-4202-8015-2b4897e264b9">  
Generate netlist using the following commands:  
```
yosys> write_verilog -noattr multiple_modules_hier.v  
yosys> !gvim multiple_modules_hier.v
```
The netlist is as follows:  
<img width="550" alt="Screenshot from 2023-08-14 15-19-31" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/c9b27065-f882-48f6-aff5-ff7760414461">  

The netlist generated is a hierarchial netlist.  

We use the following command to write the flat netlist:  
```
yosys> flatten
yosys> write_verilog -noattr multiple_modules_flat.v
yosys> !gvim multiple_modules_flat.v
```
The following flat netlist will be generated:  
<img width="550" alt="Screenshot from 2023-08-14 15-24-11" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/aad73976-d1c2-4626-99da-7b608a2278af">  
In this flattened netlist we can see the instantiation of or gate. We can view the flattened structure using the following command:  
```
yosys> show
```
The structure is as follows: <img width="550" alt="Screenshot from 2023-08-14 15-26-29" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/ff8fccb8-5319-477d-b4da-418cbc64a303">  

We can also do the entire process/synthesis even for a single submodule using the following command:  
```
yosys> synth -top sub_module1
```
</details>
<details>
<summary>
2.3 Various Flop coding styles and Optimization
</summary>

For any circuit in digital design, the output is going to change only after the propagation delay after applying inputs.Due to this delay, there is going to be a glitch in the output.  
The more number of corcuits, the more glitches we going to experience. Inorder to avoid and fix this glitch, we use **Flops**.  
The output of the flop will change only on the edge of the clock. Due to this, the glitch will not be propagated to the output. Therefore, The flop will act as a shield and make sure the output is stable.  
We can code the flop as synchronous, asynchronous or both.  


Let us take a look at the aynchronous reset flop. Use the following commands:  
```
$ iverilog dff_asyncres.v tb_dff_asyncres.v
$ ./a.out
$ gtkwave tb_dff_asyncres.vcd
```
We obtain the following output:  
<img width="550" alt="Screenshot from 2023-08-14 16-53-59" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/56151b22-ddef-4183-b008-5d2bc44b9389">  

Now, let us observe the asynchronous set flop. Use the following commands:  
```
$ iverilog dff_async_set.v tb_dff_async_set.v
$ ./a.out
$ gtkwave tb_dff_async_set.vcd
```
The output is shown below:
<img width="550" alt="Screenshot from 2023-08-14 16-58-03" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/30ef54f2-d786-431e-8a2d-be3f01aa81e1">  

Now, let us synthesize the Flop circuits using yosys.  

**Asynchronous reset flop**  

Use the commands given below:  
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog dff_asyncres.v 
yosys> synth -top dff_asyncres
yosys> dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
We obtain the following structure of Flop: <img width="550" alt="Screenshot from 2023-08-14 17-22-38" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/44e67c75-6bd4-4220-8ae2-7ecab5e3f3a4">  

**Asynchronous Set Flop**  
Use the following commands:  
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog dff_async_set.v 
yosys> synth -top dff_async_set
yosys> dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
 We obtain the asynchronous set flop structure as shown: <img width="550" alt="Screenshot from 2023-08-14 17-27-12" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/4ef7e1c6-c813-4181-9fb3-4de3919ed799">  

 **Synchronous Reset Flop**  
 Use the following commands:  
 ```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog dff_syncres.v 
yosys> synth -top dff_syncres
yosys> dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
The output structure of synchronous reset flop is as follows: 
<img width="550" alt="Screenshot from 2023-08-14 17-31-38" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/69539c25-f597-4358-b69d-fb94568a7c7a">   


Open the mult files using following command:
```
$ gvim mult_*.v -o
```
The screen pops up as shown: <img width="550" alt="Screenshot from 2023-08-14 18-57-13" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/c51fb467-794f-4b92-8b7f-8d6567dd5017">  

Now synthesis using yosys. Use the below commands:
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog mult_2.v 
yosys> synth -top mul2
yosys> dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
Thw following structure shows up: <img width="550" alt="Screenshot from 2023-08-14 19-05-40" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/cc072a2c-6b6f-45ad-96a8-780066791835">  

Let us generate the netlist using the following commands:
```
yosys> write_verilog -noattr mul2_net.v
yosys> !gvim mul2_net.v
```
The netlist is as follows: <img width="550" alt="Screenshot from 2023-08-14 19-07-34" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/4e96bc86-eb8c-4450-b6ef-577f5f02feb8">  

Let us now synthesize mult_8 using following commands:
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog mult_8.v 
yosys> synth -top mult8
yosys> dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
The ouput structure is shown below: 
<img width="550" alt="Screenshot from 2023-08-14 19-12-20" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/357a914e-244d-4499-955b-1ae52fc5bf13">  

Generate netlist using following commands:  
```
yosys> write_verilog -noattr mult8_net.v
yosys> !gvim mult8_net.v
```
The netlist is as follows: <img width="550" alt="Screenshot from 2023-08-14 19-13-53" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/5de4c6a3-6386-41d5-a278-e07e8c499709">  


</details>

### Day 3 - Combinational and sequential optmizations

### Day 4  


### Day 5  


## References
1. https://www.udemy.com/course/vsd-a-complete-guide-to-install-open-source-eda-tools/
2. https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
3. https://www.vsdiat.com/course_content?uniqueid=20220801054525 







