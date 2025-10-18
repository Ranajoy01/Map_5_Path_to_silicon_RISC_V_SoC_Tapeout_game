[Go to Map List of the Game](https://github.com/Ranajoy01/Map_List_Path_to_silicon_RISC_V_SoC_Tapeout_game)

---

[Go to Level List of the Map-5](https://github.com/Ranajoy01/Map_5_Path_to_silicon_RISC_V_SoC_Tapeout_game)

---

[Go to the previous level](../Level_2/readme.md)

<div align="center">:star::star::star::star::star::star:</div> 

# Level-3: CMOS switching threshold and basic dynamic simulations

## :microscope: CMOS VTC spice simulation and switching threshold (Static simulation)

### :zap: Introduction to VTC of CMOS inverter for different W of PMOS and switching threshold
- VTC shifts with Width variation of PMOS in any technology node
- Switching threshold is the point in VTC where Vin = Vout.

### :zap: Spice deck 
```spice
*Model Description
.param temp=27


*Including sky130 library files
.lib "sky130_fd_pr/models/sky130.lib.spice" tt


*Netlist Description1


XM1 out1 in1 vdd1 vdd1 sky130_fd_pr__pfet_01v8 w=0.55 l=0.15
XM2 out1 in1 0 0 sky130_fd_pr__nfet_01v8 w=0.36 l=0.15


Cload1 out1 0 50fF

Vdd1 vdd1 0 1.8V
Vin1 in1 0 1.8V

*Netlist Description1


XM3 out2 in2 vdd2 vdd2 sky130_fd_pr__pfet_01v8 w=2.0 l=0.15
XM4 out2 in2 0 0 sky130_fd_pr__nfet_01v8 w=0.36 l=0.15


Cload2 out2 0 50fF

Vdd2 vdd2 0 1.8V
Vin2 in2 0 1.8V

*simulation command.72 1.08 1.44

.control
  dc Vin1 0 1.8 0.01
  dc Vin2 0 1.8 0.01
  plot dc1.out1 dc2.out2 xlabel "Vin" ylabel "Vout"
  
.endc
.end

```

### :zap: VTC plots for different PMOS width
![vtc_plot](images/vtc_plot.png)

### :zap: Analysis

- For PMOS width 550nm case dc1.out1 plot
- For PMOS width 2000nm case dc2.out2 plot
- Switching threshold(Vm) change
   |PMOS width|Vm|
   |---|---|
   |550nm|838mV|
   |2000nm|915mV|
- Switching threshold shifts to higher value for increase in PMOS width.
- Vm is a function of (Wp/Lp) and (Wn/Ln)
- Higher PMOS width means pull up circuit stronger as PMOS resistance (non-linear) less.

 <div align="center">:star::star::star::star::star::star:</div> 
 
 ## :microscope: Basic Dynamic simulation (Rise delays and fall delays)
 ### :zap: Introduction to rise delay and fall delay
 - Rise delay for inverter is considered for the case output changing low to high.
 - Rise delay signifies time duration between input signal 50 % level and output signal 50 % level in this case.
 - Fall delay for inverter is considered for the case output changing high to low.
 - Fall delay signifies time duration between input signal 50 % level and output signal 50 % level in this case.
 ### :zap: Spice deck
 ```spice
*Model Description
.param temp=27


*Including sky130 library files
.lib "sky130_fd_pr/models/sky130.lib.spice" tt


*Netlist Description1


XM1 out1 in1 vdd1 vdd1 sky130_fd_pr__pfet_01v8 w=0.55 l=0.15
XM2 out1 in1 0 0 sky130_fd_pr__nfet_01v8 w=0.36 l=0.15


Cload1 out1 0 50fF

Vdd1 vdd1 0 1.8V
Vin1 in1 0 PULSE(0V 1.8V 0 0.1ns 0.1ns 2ns 4ns)


*Netlist Description1


XM3 out2 in2 vdd2 vdd2 sky130_fd_pr__pfet_01v8 w=2.0 l=0.15
XM4 out2 in2 0 0 sky130_fd_pr__nfet_01v8 w=0.36 l=0.15


Cload2 out2 0 50fF

Vdd2 vdd2 0 1.8V
Vin2 in2 0 PULSE(0V 1.8V 0 0.1ns 0.1ns 2ns 4ns)


*simulation command.72 1.08 1.44

.control
   tran 1n 10n

   plot tran1.out1 tran1.out2 tran1.in1 xlabel "time" ylabel "Vout"
  
.endc
.end

 ```
 ### :zap: Analysis
 - Rise delay and fall delays from the plot are tabulated in the following table-
   |PMOS width|Rise Delay|Fall Delay|
   |---|---|---|
   |550nm|45ns|27ns|
   |2000nm|15ns|39ns|
 - With PMOS width increase rise delay decreased as PMOS become stronger.
 - Width PMOS width increase fall delay increased as PMOS become stronger and NMOS remains ame so discharging path requires more time.
 ### :zap: Use in STA
 - Based on the requirement of delay we should use technology node cell (fast, slow, typical)
 - Clk buffers and clk inverter should have same rise and fall delay so specific PMOS width is considered in a technology node.
 - Input signals and basic signals generally not that much concern about fall delay. So here PMOS width is not very specific.


 <div align="center">:star::star::star::star::star::star:</div> 

 ## :trophy: Level Status: 

- All objectives completed.
- I have synthesized VSDBabySoC design, performed GLS Simulation and validated GLS with respect to functional simulation.
- 🔓 Next level unlocked 🔜 [Level-4:  CMOS robustness ( Noise margin evaluation )](../Level_4/readme.md).
  
<div align="center">:star::star::star::star::star::star:</div> 


