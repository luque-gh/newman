# Newman alternative
## Introduction 
The objective of this project is to **reproduce some claims made by Joseph Newman about his energy machine**.
This will be done in a **smaller scale** compared to the big machine Newman demonstrated.
This machine follows most of Newman's design described in his book.

However, it runs in a much lower voltage **~190VDC** compared to the one demonstrated by Newman (1500+ VDC).
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

The cycle is activated in the range 135° to 225° and determined by the printed part **Commutator-Disc-90Deg**.
Each activation range requires an independent coil and circuit. In the test setup and videos, only one coil is used, but it is possibile to use two coils and activate in the range -45° to 45° as well.

## Schematic

Created using **Fritzing 0.9.3**.

Available in **/schematic**.

## Test Setup
* One coil activated in the range 135° to 225°.
* **~190V VDC** input voltage for the coil (20 x 9V zinc-carbon batteries).
* 9V zinc-cabon battery for the circuit controller.
* 2-channels **Rigol DS1052E** Oscilloscope. 
	* Channel A (Yellow) - Batteries voltage
	* Channel B (Blue) - Voltage across 10Ohm resistor before ground (=Amps / 10).

## Preliminary Results

![Image of cycle Fire/Blank](/results/FBS-Cycle-Batteries.png)

This scope shot show both battery voltage and current in the activation zone.
In the first part, there is energy consumption from the batteries because voltage goes down and current goes up.
However, this trend is averted by the induced current in the coil from the magnets. 
Current is reversed and voltage recovers and goes even above the batteries charged voltage. So, batteries are being charged in the middle part.
In the last part, the induced current decreases and energy consumption from the batteries is resumed until it leaves the activation zone.

![Image of Voltage in Full-Cycle](/results/FBS-Cycle-Batteries-V.png)



![Image of Voltage in Full-Cycle](/results/FBS-Cycle-Batteries-mA.png)

![Image of Voltage in Full-Cycle](/results/Batteries-Consumption-1-Closeup.png)

![Image of mAmps in Full-Cycle](/results/Batteries-Consumption-1-Closeup.png)

![Image of Voltage in Full-Cycle](/results/Batteries-Feedback-Closeup.png)


## Building Instructions

### Requirement
* 3D Printer
* Soldering tools

### Assembly itens
* 2 x 6000 Full Ceramic Bearing 10x26x8mm
* 2 x N52 45x45x20mm Block Magnet Strong Rare Earth Neodymium Magnet
* 5Kg AWG 28 Copper 
* 500g PLA or ABS 
* 22AWG Solid core wire

Print all STL files in the directory **/model**.
Put together **Coil.Inner and Coil.Outer** and insert in both holes **Coil.Lock**
Wind all AWG 28 Copper in the coil. There are holes in the coil for up to two coils.
It's recommended to fill the whole coil with copper wire. The more, the better.

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
* 1 x Breadboard or PCB
* 1 x 1nF Capacitor
* 1 x 10nF Capacitor
* 1 x 10uF Electrolytic Capacitor
* 1+ x IR TIL32
* 1+ x IR TIL78
* 13+ x 9V Zinc-Carbon Battery