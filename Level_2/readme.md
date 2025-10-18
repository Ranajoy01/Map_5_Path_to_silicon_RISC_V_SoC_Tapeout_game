[Go to Map List of the Game](https://github.com/Ranajoy01/Map_List_Path_to_silicon_RISC_V_SoC_Tapeout_game)

---

[Go to Level List of the Map-5](https://github.com/Ranajoy01/Map_5_Path_to_silicon_RISC_V_SoC_Tapeout_game)

---

[Go to the previous level](../Level_1/readme.md)

<div align="center">:star::star::star::star::star::star:</div> 

# Level-2: Velocity saturation and basics of CMOS inverter voltage transfer characteristics
## List of Objectives

- :microscope: <b>Practical Objective-1:</b> []()


 <div align="center">:star::star::star::star::star::star:</div> 

## :microscope: Velocity Saturation in lower nodes and comparision with longer nodes
### :zap: Introduction to lower node effects
- When channel length becomes lower than 250 nm, it is considered as short channel device.
- Current behaviour will not remain same as the long channel device.
- Current will saturate due to velocity saturation effect.

### :zap: Spice decks for Id vs Vds
#### Spice deck for higher node (NMOS W = 5000 nm and l =2000 nm, supply voltage = 1.8 v, input voltage = 1.8 v)
```spice
*Model Description
.param temp=27


*Including sky130 library files
.lib "sky130_fd_pr/models/sky130.lib.spice" tt


*Netlist Description



XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=5 l=2

R1 n1 in 55

Vdd vdd 0 1.8V
Vin in 0 1.8V

*simulation commands

.op
.dc Vdd 0 1.8 0.1 Vin 0 1.8 0.2

.control

run
display
setplot dc1

.endc

.end
```
#### Spice deck for lower node (NMOS W = 390 nm and l = 150 nm, supply voltage = 1.8 v, input voltage = 1.8 v)
```spice
*Model Description
.param temp=27


*Including sky130 library files
.lib "sky130_fd_pr/models/sky130.lib.spice" tt


*Netlist Description



XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=0.39 l=0.15

R1 n1 in 55

Vdd vdd 0 1.8V
Vin in 0 1.8V

*simulation commands

.op
.dc Vdd 0 1.8 0.1 Vin 0 1.8 0.2

.control

run
display
setplot dc1
.endc

.end
```

### :zap: Id vs Vds plot comparision for different nodes
#### Id vs Vds plot for higher node (NMOS W = 5000 nm and l =2000 nm, supply voltage = 1.8 v, input voltage = 1.8 v)

![Id_vds_h](images/Id_vds_h.png)

#### Id vs Vds plot for lower node (NMOS W = 390 nm and l = 150 nm, supply voltage = 1.8 v, input voltage = 1.8 v)

![Id_vds_l](images/Id_vds_l.png)

  


 <div align="center">:star::star::star::star::star::star:</div> 

 ## :trophy: Level Status: 

- All objectives completed.
- I have synthesized VSDBabySoC design, performed GLS Simulation and validated GLS with respect to functional simulation.
- 🔓 Next level unlocked 🔜 [Level-3: CMOS switching threshold and basic dynamic simulations](../Level_3/readme.md).
  
<div align="center">:star::star::star::star::star::star:</div> 


