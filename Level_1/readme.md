[Go to Map List of the Game](https://github.com/Ranajoy01/Map_List_Path_to_silicon_RISC_V_SoC_Tapeout_game)

---

[Go to Level List of the Map-5](https://github.com/Ranajoy01/Map_5_Path_to_silicon_RISC_V_SoC_Tapeout_game)

<div align="center">:star::star::star::star::star::star:</div> 

# Level-1: Setup ngspice and basics of NMOS drain current vs drain to source voltage

## List of Objectives

- :microscope: <b>Practical Objective-1:</b> []()


 <div align="center">:star::star::star::star::star::star:</div> 

## :microscope: Setup Ngspice
### :zap: Download tarball from [https://sourceforge.net/projects/ngspice/files/ ](https://sourceforge.net/projects/ngspice/files/) to a local directory.
### :zap: Unpack it-
```bash
$ tar -zxvf ngspice-45.2.tar.gz
```
### :zap: Build release directory and configure-
```bash
$ cd ngspice-45.2
$ mkdir release
$ cd release
$ ../configure --with-x --with-readline=yes --disable-debug
```
### :zap: If xaw file error install the required package-
```bash
$ sudo apt install libxaw7-dev libxmu-dev libxt-dev libx11-dev libxpm-dev
```
### :zap: Install ngspice (system wide) -
```bash
$ make
$ sudo make install
```

![set_ngs](images/set_ngs.png)

:100: Ngspice installation successful

 <div align="center">:star::star::star::star::star::star:</div> 

 ## :book: What is the importance of Spice tool in VLSI?
 :rocket: Circuit design (in VLSI domain) includes combining of transistors in different manners to perform a certain function. But the importance of spice simulations are described below.

 - Spice tool is used for detailed characterization of transistors (PMOS and NMOS in case of CMOS) used in a circuit to analyze delay, load , power, noise margin, reliable working region etc.
  
 ![imp_sp_1](images/imp_sp_1.png)

 - This ciruit represent a two stage buffer.
 - Here, the input slew (transition delay) at each buffer input and corresponding buffer load capacitance causes different delays.
 - Delay tables are used for static timing analysis of this circuit.

   ![imp_sp_2](images/imp_sp_2.png)
   
 - Spice is used to make delay tables for circuits.
   

 <div align="center">:star::star::star::star::star::star:</div> 

 ## :trophy: Level Status: 

- All objectives completed.
- I have synthesized VSDBabySoC design, performed GLS Simulation and validated GLS with respect to functional simulation.
- 🔓 Next level unlocked 🔜 [Level-2: Velocity saturation and basics of CMOS inverter voltage transfer characteristics
](../Level_2/readme.md).
  
<div align="center">:star::star::star::star::star::star:</div> 


