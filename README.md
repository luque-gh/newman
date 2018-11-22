# Newman alternative
## Introduction 
The objective of this project is to **reproduce some claims made by Joseph Newman about his energy machine**.
This will be done in a **smaller scale** compared to the big machine Newman demonstrated.
The machine follows most of Newman's design described in his book.

However, it runs in a much lower voltage **(90-150 VDC)** compared to the one demonstrated by Newman (1500+ VDC).
This lower voltage makes possible to use **mosfet transistor and zener diodes** to replace the mechanical commutator.
**Duty cycle and frequency are adjustable** to optimize the performance through a **555 timer**.
Since **Newman's claims timing is very critical** for his invention, this gives much more flexibility to optimize compared to a mechanical commutator.

## Working
**Infrared emitter and sensor are used inhibit or activate the FIRING/BLANK/SHORT OUT cycle** depending on current rotor position.
This machine uses **a solid-state circuit with a 555 timer** to alternate between **FIRING (HIGH)** and **BLANK / SHORT OUT (LOW)**.

### FIRING/BLANK/SHORT OUT Cycle
The first phase is **FIRING** which enable both mosfets to energise the coil through the battery bank.
After that, the **BLANK** phase begins and cut the supply energy from the batteries, collapsing the field from the coil.
The **BLANK** phase only ends when the voltage difference in the coil is above the reverse zener voltage.
When this voltage is achieved, the **SHORT OUT** begins.
After that, a new **FIRING** phase begins reconnecting the battery bank to the coil.

## Schematic

Created using **Fritzing 0.9.3**.

Available in **/schematic**.

## Test Setup
* **~110V VDC** input voltage (twelve 9V zinc-carbon batteries).
* 9V zinc-cabon battery for circuit controller.
* 2-channels **Rigol DS1052E** Oscilloscope. 
	* Channel A (Yellow) - Batteries voltage
	* Channel B (Blue) - Voltage across 10Ohm resistor before ground (=Amps / 10).

## Results

### Full Cycle
![Image of Voltage in Full-Cycle](/results/Full-Cycle-V.png)

![Image of Voltage in Full-Cycle](/results/Full-Cycle-mA.png)

![Image of Voltage in Full-Cycle](/results/Full-Cycle-W.png)

### Motor Cycle
![Image of Voltage in Full-Cycle](/results/Motor-Cycle-V.png)

![Image of mAmps in Full-Cycle](/results/Motor-Cycle-mA.png)

### Feedback Cycle
![Image of Voltage in Full-Cycle](/results/Feedback-Cycle-V.png)

![Image of mAmps in Full-Cycle](/results/Feedback-Cycle-mA.png)

![Image of Voltage in Full-Cycle](/results/Feedback-Cycle-W.png)


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