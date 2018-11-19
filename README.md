# Introduction 
The objective of this project is to reproduce and validate some claims made by Joseph Newman about his energy machine.
However, this will be done in a smaller scale compared to the big machine Newman demonstrated.
This design follow Newman's base idea to maximize de amount of copper as possible in the coil.
No mechanical commutator is used and this machine runs in a much lower voltage (90-150 VDC) compared to the one demonstrated by newman (1500+ VDC).
So, it became possible to use mosfet transistor as switch instead and commutation based on infrared emitter / sensor.
The duty cycle and frequency can be adjusted using 555 timer to optimize the performance of the machine.
Since Newman's claims timing is very critical for his invention, this gives much more flexibility to optimize compared to a mechanical commutator.

# Working
This machine runs using a solid-state circuit with a 555 timer to alternate between FIRING (HIGH) and BLANK / SHORT OUT (LOW).
The first phase is FIRING and open both mosfets to energise the coil using the battery bank.
After that, the BLANK phase begins and cut the supply energy from the batteries, collapsing the field from the coil.
The BLANK phase only ends when the voltage difference in the coil is above the reverse zener voltage.
When this voltage is achieved, the SHORT OUT begins.
After that, a new FIRING phase begins reconnecting the battery bank to the coil.

## Test Setup
Twelve 9V zinc-carbon batteries were used for input voltage for the coil.
One 9V zinc-cabon battery were used for the circuit input.
Two channels from Rigol DS1052E Oscilloscope was used to measure both input voltage (yellow) and current (blue).
A 10Ohm resistor was added before ground in other to measure the current across the resistor.

## Results

![Image of Voltage in Full-Cycle](/results/Feedback-Cycle-V.png)

![Image of mAmps in Full-Cycle](/results/Feedback-Cycle-mA.png)


## Building

### Requirement
* 3D Printer
* Soldering tools

### Assembly itens
* 2 x 6000 Full Ceramic Bearing 10x26x8mm
* 2 x N52 45x45x20mm Block Magnet Strong Rare Earth Neodymium Magnet
* 5Kg AWG 28 Copper 
* 500g PLA or ABS 
* 22AWG Solid core wire

### Circuit itens
* 1 x 555 CI
* 1 x 2N2222
* 1 x 2N3906
* 2 x IRF830
* 2 x 1N5388
* 1 x Linear Potentiometer 50K
* 1 x 470k Resistor
* 1 x 47k Resistor
* 1 x 4.7k Resistor
* 1 x 1k Resistor
* 1 x 680 Resistor
* 1 x 4.7 Resistor
* 1 x Breadboard
* 1 x 1nF Capacitor
* 1 x 10nF Capacitor
* 1 x 10uF Electrolytic Capacitor
* 1+ x IR TIL32
* 1+ x IR TIL78
* 13+ x 9V Zinc-Carbon Battery


