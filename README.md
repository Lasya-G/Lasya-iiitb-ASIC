### Table of Contents
- [Day 0 - Tools Installation](#day-0)
- [Day 1 - Introduction to Verilog RTL design and Synthesis](#day-1)
- [Day 2 - Timing libs, hierarchical vs flat synthesis and efficient flop coding styles](#day-2) 
- [Day 3 - Combinational and sequential optmizations](#day-3)
- [Day 4 - GLS, blocking vs non-blocking and Synthesis-Simulation mismatch](#day-4)
- [Day 5 -  If, case, for loop and for generate](#day-5)
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

### Day 3 
<details>
<summary>
3.1 Introduction to Logical Optimization
</summary>  
  
The combinational logic optimization is mainly to squeeze the logic to get most optimised design that is efficient in terms of power and area.  
The techniques used for combinational logic optimisation are:  

- Constant propagation : It is a direct optimisation technique.
- Boolean Logic Optimization

The techniques used for Sequential Logical Optimization are:

- Sequential constant propagation
- State Optimization : Optimization of unused states.
- Retiming
- Sequential logic cloning (Floor plan aware synthesis)

</details>

<details>
<summary>
3.2 Combinational Logic Optimizations
</summary>  
    
**opt_check**  
Invoke yosys and synthesize the opt files using the following commands:  
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog opt_check.v 
yosys> synth -top opt_check
yosys> opt_clean -purge 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
The output structure is as follows:
<img width="550" alt="Screenshot from 2023-08-14 19-52-15" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/d324cee9-4335-49f9-9312-73c52dca1815">  

**opt_check2**  
synthesize the opt files using the following commands:  
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog opt_check2.v 
yosys> synth -top opt_check2
yosys> opt_clean -purge 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
The output structure is as shown:
<img width="550" alt="Screenshot from 2023-08-14 19-54-22" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/768fd11d-893c-4e06-b880-97976ce800b8">  

**opt_check3**  
synthesize the opt files using the following commands:  
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog opt_check3.v 
yosys> synth -top opt_check3
yosys> opt_clean -purge 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
The output structure is as shown:
<img width="550" alt="Screenshot from 2023-08-14 19-57-58" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/b7a20ddd-b75d-4541-9640-1a634b9ad013">  

**opt_check4**  
synthesize the opt files using the following commands:  
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog opt_check4.v 
yosys> synth -top opt_check4
yosys> opt_clean -purge 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
The output structure is as shown:
<img width="550" alt="Screenshot from 2023-08-14 20-00-38" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/997be825-f7a0-464a-b8b7-f31facae071b">  

</details>

<details>
<summary>
    3.3 Sequential Logic Optimizations
</summary>  
Use the following commands to view the verilog files:   
    
```
 gvim dff_const1.v   
 ```
 The files are as follow:<img width="550" alt="Screenshot from 2023-08-14 22-06-16" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/9f78ac03-89b2-4675-ba30-f740a1bf61e7">  

 Run the dff_const1 verilog file with the help of the commands below:  
 ```
iverilog dff_const1.v tb_dff_const1.v
./a.out
gtkwave tb_dff_const1.vcd
```
The output is shown below:  
<img width="550" alt="Screenshot from 2023-08-14 22-09-08" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/e139452c-af5b-47e1-aaec-292a08e3867f">  

Run the dff_const2 verilog file using the below commands:  
```
iverilog dff_const2.v tb_dff_const2.v
./a.out
gtkwave tb_dff_const2.vcd
```

The output is as shown below:  
<img width="550" alt="Screenshot from 2023-08-14 22-12-42" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/cefe7fb5-f045-4f2a-84b6-a3c334417a70">  

Synthesize the above codes with yosys using the below commands:  
**dff_const1**
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog dff_const1.v 
yosys> synth -top dff_const1
yosys> dfflibmap ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
The structure of the output is shown below:
<img width="550" alt="Screenshot from 2023-08-14 22-17-00" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/183e0910-3602-404e-afe5-c8e4db962a35">  


**dff_const2**  
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog dff_const2.v 
yosys> synth -top dff_const2
yosys> dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
The output structure is as follows:
<img width="550" alt="Screenshot from 2023-08-14 22-20-27" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/bc99beb6-d51d-4c4f-acf0-e694c6abfbbd">  

**dff_const3**  
Use the following commands to obtain gtkwave:

```
iverilog dff_const3.v tb_dff_const3.v
./a.out
gtkwave tb_dff_const3.vcd
```
The following waveform is obtained: <img width="550" alt="Screenshot from 2023-08-14 22-26-40" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/81aef661-1dac-4ca1-b5c6-32af2e9e8c4c">  


Use the following commands to synthesize using yosys:
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog dff_const3.v 
yosys> synth -top dff_const3
yosys> dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```

The output structure is as follows: <img width="550" alt="Screenshot from 2023-08-14 22-27-48" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/811328cd-350d-4043-b6f8-ab44963785c0">  

**dff_const4**  
Use the following commands to obtain gtkwave:

```
iverilog dff_const4.v tb_dff_const4.v
./a.out
gtkwave tb_dff_const4.vcd
```
The output waveforn is shown below:
<img width="550" alt="Screenshot from 2023-08-14 22-33-00" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/7c78a1db-f5bd-4cd3-adda-9e4f1a66f0d2">  


Use the following commands to synthesize using yosys:
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog dff_const4.v 
yosys> synth -top dff_const4
yosys> dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
The output structure is shown below:  
<img width="550" alt="Screenshot from 2023-08-14 22-35-10" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/33216d13-8371-4220-95b4-96d899a3ec55">  

**dff_const5**  
Use the following commands to obtain gtkwave:

```
iverilog dff_const5.v tb_dff_const5.v
./a.out
gtkwave tb_dff_const5.vcd
```
The output waveforn is shown below:
<img width="550" alt="Screenshot from 2023-08-14 22-33-38" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/4704684e-5ec8-4357-9edc-fc92a2d37ff1">  


Use the following commands to synthesize using yosys:
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog dff_const5.v 
yosys> synth -top dff_const5
yosys> dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
The output structure is shown below:  
<img width="550" alt="Screenshot from 2023-08-14 22-36-19" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/b3d48358-0625-467a-9eff-afe93d29edb6">  

</details>

<details>
<summary>
3.4 Sequential Optimizations for unused outputs
</summary>

Let us view the verilog code using the command given below:  
```
gvim count_opt.v
```
The verilog code is opened: <img width="550" alt="Screenshot from 2023-08-14 22-42-00" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/431f70c3-0951-415f-9be7-da149f9daf4b">  


Now, let us synthesize the above code using yosys. Follow the below commands:  
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog count_opt.v 
yosys> synth -top count_opt
yosys> dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
The output structure is displayed like: <img width="550" alt="Screenshot from 2023-08-14 22-44-32" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/065693f1-ffe1-4830-ace9-736b33862e58">  
For a 3 counter we need to see 3 flops in the output but only 1 flop is structured.  

Let us make the following changes to the counte_opt verilog code and run synthesis on the modified file.
The modified code is shown below:
<img width="550" alt="Screenshot from 2023-08-14 22-51-45" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/2f428e30-41cc-402f-9a8f-226f3b72eccc">  
Let us synthesize using yosys:
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog count_opt.v 
yosys> synth -top count_opt
yosys> dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```
The output structure obtained is as shown: <img width="600" alt="Screenshot from 2023-08-14 22-53-1" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/975e565e-490a-446f-ab43-505a49d0ce43">  


</details>

### Day 4 

<details>
<summary>
4.1 GLS, Synthesis-Simulation mismatch and Blocking/Non-blocking statements    
</summary>

- **GLS**:  
  In GLS, we run test bench with netlist as the Design under test instead of the RTL code. Basically, Netlist is logically equal to RTL code as the netlist is obtained by converting RTL code into standard cell gates.  
  We will use GLS to verify the logical correctness of design after synthesis and also to ensure the timing of the design is met. (run with delay annotations.)
  <img width="550" alt="Screenshot from 2023-08-15 08-44-29" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/8cd33dbd-9663-4d0a-bfd9-5d3192050fe5">

**Synthesis Simulation Mismatch** can happen due to following reasons:  

- Missing Sensitivity List
- Blocking vs non-Blocking statemnets
- Non standard verilog coding


</details>

<details>
<summary>
4.2 Labs on GLS and Synthesis-simulation mismatch    
</summary>

Let us take a look at the files we use for this lab: <img width="550" alt="Screenshot from 2023-08-15 10-40-29" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/0bc520f0-4e90-40f0-80d1-b7320874e232">  

Let us simulate the ternary operator code using following commands:  
```
$ iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```
The output waveform is shown below:
<img width="550" alt="Screenshot from 2023-08-15 10-42-31" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/85491f18-f192-4b99-b5c6-9cf002f23582">  


Let us synthesize the same using yosys:
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog ternary_operator_mux.v 
yosys> synth -top ternary_operator_mux
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> write_verilog -noattr ternary_operator_mux_net.v
yosys> show
```
The output structure is as shown: <img width="550" alt="Screenshot from 2023-08-15 10-46-41" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/c890ebf1-64ee-40f0-afc3-720f50ae55aa"> 

**Bad_Mux**  
Let us simulate using following commands:  
```
iverilog bad_mux.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```
The output obtained is as shown: <img width="550" alt="Screenshot from 2023-08-15 10-52-12" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/b97396ed-8384-409e-ab7c-ada5130dcfbd">  

Let us simulate the same using following commands:
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog bad_mux.v 
yosys> synth -top bad_mux
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> write_verilog -noattr bad_mux_net.v
```
Now simulate the bad_mux file again:
```
iverilog ../my_lib/verilog_model/primitives.v  ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```
Let us observe the output waveform again: <img width="550" alt="Screenshot from 2023-08-15 10-58-28" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/26f8fb06-f7cf-4482-b01b-acf0d33f8a20">  
Now, the output correctly depicts the behaviour of a mux.  


</details>

<details>
<summary>
4.3 Labs on Synth sim mismatch for blocking statement    
</summary>  

We will now make use of the following verilog file:
```
gvim blocking_caveat.v
```
The following file opens: <img width="550" alt="Screenshot from 2023-08-15 19-09-45" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/53a6a261-c286-47ea-9ba5-12e127b72e0e">  

Now simulate the above code:
```
$ iverilog blocking_caveat.v tb_blocking_caveat.v 
$ ./a.out
$ gtkwave tb_blocking_caveat.vcd
```
The output is as follows: <img width="550" alt="Screenshot from 2023-08-15 19-11-23" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/8491efa4-327a-4c4a-a323-6d56755c4626">  

Synthesis the above file using yosys:  
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog blocking_caveat.v 
yosys> synth -top blocking_caveat
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> write_verilog -noattr blocking_caveat_net.v
yosys> show
```
The following structure is observed in output: <img width="550" alt="Screenshot from 2023-08-15 19-16-00" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/3429a182-6cc0-485a-8fe2-c3a2739aba19">  

Now, simulate the verilog file again using following commands:  
```
iverilog ../my_lib/verilog_model/primitives.v  ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```
The output is as follows: <img width="550" alt="Screenshot from 2023-08-15 19-20-41" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/c14cb78f-fec8-4d28-92f6-7e9ac1573b3d">  

</details>

### Day 5 

<details>
<summary>
5.1 If case constructs   
</summary>  

- **If constructs**: Mainly used to create the priority logic.In a nested if else construct, the conditions are given priority from top to bottom. Only if the condition is satisfied, if statement is executed and the compiler comes out of the block. If condition fails, it checks for next condition and so on.
- **Danger/Caution with if**: "Inferred latches" (Bad coding style-incomplete if)
- **Case constructs**: In case construct, the execution checks for all the case statements and whichever satisfies the statement, that particular statement is executed.If there is no match, the default statement is executed. But here unlike if construct, the execution doesn't stop once statement is satisfied, but it continues further.
- **Caveats in Case**: They occur due to two reasons- One is incomplete case statements and can be resolved by default case and the other is partial assignments in case statements. And also in case statements we should not have overlapping cases.
</details>

<details>
<summary>
5.2 Labs on "incomplete if case"
</summary>  

We will use the following files for this lab session. Use the below commands to view the required files:
```
gvim *incomp* -o
```
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/2cd2f881-9a08-4372-9457-4ccad8ed0853"> 

Simulate the verilog file incomp_if using following commands:  
```
$ iverilog incomp_if.v tb_incomp_if.v 
$ ./a.out
$ gtkwave tb_incomp_if.vcd
```
The output wave is as follows: <img width="550" alt="Screenshot from 2023-08-15 19-33-16" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/704f7c61-ddf2-457b-885e-902cff616d4d">  

Let us simulate the file and the output structure using the below commands:
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog incomp_if.v 
yosys> synth -top incomp_if
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> write_verilog -noattr incomp_if_net.v
yosys> show
```  
<img width="550" alt="Screenshot from 2023-08-15 19-37-04" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/321e1373-fa8b-4830-a3b7-125f12cd14b2">  


Simulate the verilog file incomp_if2 using following commands:  
```
$ iverilog incomp_if2.v tb_incomp_if2.v 
$ ./a.out
$ gtkwave tb_incomp_if2.vcd
```
The output wave is as follows: <img width="550" alt="Screenshot from 2023-08-15 19-41-46" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/7840b3f0-2469-4831-84e5-6de2ed83126d">   

Let us simulate the file and the output structure using the below commands:
```
yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog incomp_if2.v 
yosys> synth -top incomp_if2
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> write_verilog -noattr incomp_if2_net.v
yosys> show
```  
<img width="550" alt="Screenshot from 2023-08-15 19-43-39" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/4342965f-a162-4ac5-a9df-4f242ff66432">  

</details>

<details>
<summary>
5.3 Labs on "incomplete overlapping case"   
</summary>  
We will be using the following files for this lab:
<img width="550" alt="Screenshot from 2023-08-15 19-47-05" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/9706e42f-225b-48b2-823f-583206306c5b">  

Let us simulate the incomp_case file using following commands:
```
$ iverilog incomp_case.v tb_incomp_case.v 
$ ./a.out
$ gtkwave tb_incomp_case.vcd
```

The simulation output is as shown below:
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/59f87879-e0fb-43e5-bc72-c6b696f368c6">  

The systhesis output structure is as follows: <img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/39af17f8-2c84-4dbf-bbf5-7a787e6bfa78">  

Let us simulate the comp_case file using following commands:
```
$ iverilog comp_case.v tb_comp_case.v 
$ ./a.out
$ gtkwave tb_comp_case.vcd
```

The simulation output is as shown below:
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/beb9e35d-004f-4f88-a4d0-4ae8d3c77dc8">   

The systhesis output structure is as follows: <img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/1213c8c7-e625-4fea-8712-ac85560971a5">  

Let us simulate the partial_case_assign file using following commands:
```
$ iverilog partial_case_assign.v tb_partial_case_assign.v 
$ ./a.out
$ gtkwave tb_partial_case_assign.vcd
```

The simulation output is as shown below:
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/09497aca-d285-4285-8e87-c1e278195152">   


The systhesis output structure is as follows: <img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/06a1b06d-7443-4fe5-a88d-8ed2d5ccb6be">  



Let us simulate the bad_case file using following commands:
```
$ iverilog bad_case.v tb_bad_case.v 
$ ./a.out
$ gtkwave tb_bad_case.vcd
```

The simulation output is as shown below:
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/56589177-db4e-4976-b43d-04f2e2805a14">    

The systhesis output structure is as follows: <img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/dd62a012-e3b5-4f3e-ae08-fd7e50407e95">  


</details>

<details>
<summary>
5.4 for loop and for generate   
</summary>  

- **For Loop**:
  - For look is used in always block.
  - It is used for excecuting expressions alone.

- **Generate For loop**:
  - Generate for loop is used for instantaing hardware.
  - It should be used only outside always block.

</details>

<details>
<summary>
5.5 Labs on "for loop" and "for generate"   
</summary>  

We will be using the following file for this simulations and synthesis:
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/6d58a6e9-7755-4fd9-867a-0bd64f7adb0e">  

We will get the following simulation output:
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/8677737c-ab0e-42e2-8f20-b919759a45bd">  

The synthesis output structure is as follows:
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/2c25c88d-78a5-4f4b-9ad0-4c01ecec5e52">    

Now, let us resimulate the code and observe the output waveform:
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/89288bf0-c4e4-4d56-96b1-d995d2b247ed">  

We will be using the following file for this simulations and synthesis:
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/e631f10f-a650-46fa-bd20-5df2dfb81016">     

We will get the following simulation output:
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/47da29b3-507b-4d34-beeb-a84c87af731f">    

The synthesis output structure is as follows:
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/2845cb69-03cb-4aad-8522-45a7bc74ceb1">    

We will be using the following file for this simulations and synthesis:
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/40980898-84f0-4491-b4c4-5878709edd51">  

We will get the following simulation output:
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/8ec2a9eb-cfb3-4c63-ad7f-f74537cf5226">     

The synthesis output structure is as follows:
<img width="550" alt="image" src="https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/d2c9d2e9-cd11-4bf2-8ecb-c34710661638">   
</details>

## References
1. https://www.udemy.com/course/vsd-a-complete-guide-to-install-open-source-eda-tools/
2. https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
3. https://www.vsdiat.com/course_content?uniqueid=20220801054525 







