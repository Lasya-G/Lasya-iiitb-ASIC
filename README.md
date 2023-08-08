# Day 0
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

![Screenshot from 2023-07-31 09-49-23](https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/c6031ebd-ee60-40c7-8327-88f82ef83f41)  
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
![Screenshot from 2023-07-31 09-50-00](https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/ac36da4e-6f33-47f0-8166-68141b26487f)  
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
![Screenshot from 2023-07-31 09-51-21](https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/865eae3a-149a-4fe6-89bf-9069cc70f48b)  

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
    ![Screenshot from 2023-08-08 17-12-55](https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/acb2abd2-75ff-4f01-985d-409e5dcc48df)

    
    
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
    ![Screenshot from 2023-08-08 15-53-55](https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/f7ac78ad-b6ca-4351-bf59-c0b64ba0cb9d)

    
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
![Screenshot from 2023-08-08 17-45-01](https://github.com/Lasya-G/Lasya-iiitb-ASIC/assets/140998582/d6732d99-4b05-4f93-9d77-4fdf6cf9a083)

</details>







