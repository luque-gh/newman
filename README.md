# Newman alternative - Small scale without mechanical commutator 
## Introduction 
The objective of this project is to **reproduce some claims made by Joseph Newman about his energy machine**.
This will be done in a **smaller scale** compared to the big machine Newman demonstrated.
This machine follows most of Newman's design described in his book.

However, it runs in a much lower voltage **~190VDC** compared to the one demonstrated by Newman (1500+ VDC).
This lower voltage makes possible to use **mosfet transistor and zener diodes** instead of a mechanical commutator.
**Duty cycle and frequency are adjustable** to optimize the performance through a **555 timer**.
Since **Newman's claims timing is very critical** for his invention, this gives much more flexibility to optimize compared to a mechanical commutator.

## Working
**Infrared emitter and sensor are used inhibit or activate the FIRING/BLANK/SHORT OUT cycle** depending on current rotor position.
This machine uses **a solid-state circuit with a 555 timer** to alternate between **FIRING (HIGH)** and **BLANK / SHORT OUT (LOW)**.

### FIRING/BLANK/SHORT OUT Cycle
The first phase is **FIRING** which enable both mosfets to energise the coil through the battery bank.
After that, the **BLANK** phase begins and cut the supply energy from the batteries, collapsing the field from the coil.
The **BLANK** phase only ends when the voltage difference in the coil is above the reverse zener voltage (>400V).
When this voltage is achieved, the **SHORT OUT** begins.
After that, a new **FIRING** phase begins reconnecting the battery bank to the coil again.

The cycle is activated in the range 135° to 225° and determined by the printed part **Commutator-Disc-90Deg**.
Each activation range requires an independent coil and circuit. In the test setup and videos, only one coil is used, but it is possibile to use two coils and activate in the range -45° to 45° as well.

## Schematic

Created using **Fritzing 0.9.3**.

Available in **/schematic**.

## Test Setup
* One coil activated in the range 135° to 225°.
* **~190V VDC** input voltage for the coil (20 x 9V zinc-carbon batteries **OUT OF WARRANTY, BUT NOT DEPLETED**).
* 9V zinc-cabon battery for the circuit controller.
* 555 Duty+ for FIRING is ~82.1%.
* 555 Frequency is ~17.24Khz.
* 2-channels **Rigol DS1052E** Oscilloscope. 
	* Channel A (Yellow) - Batteries voltage
	* Channel B (Blue) - Voltage across 10Ohm resistor before ground (=Amps / 10).

## Preliminary Results

![Image of cycle Fire/Blank](/results/FBS-Cycle-Batteries.png)

This scope shot show both battery voltage (yellow) and current (blue) in the activation zone.
In the first part, there is energy consumption from the batteries because voltage goes down and current goes up.
However, this trend is averted by **the induced current in the coil from the magnets and from the collapsing magnet field around the coil**.
Current is reversed and voltage recovers and goes even above the batteries charged voltage. So, batteries are being charged in the middle part.
Notice how important is the geometry, because in other machines like the Bedini's SSG, the current induced by the collapsing magnet field goes against the induced current by the magnes, slowing down the machine.
In the last part, the induced current decreases and energy consumption from the batteries is resumed until it leaves the activation zone.

![Image of Voltage in Full-Cycle](/results/FBS-Cycle-Batteries-V.png)

When energy is consumed, batteries voltages goes down to 178V.
When recharge process takes place, batteries voltage goes up to 200V.

![Image of Voltage in Full-Cycle](/results/FBS-Cycle-Batteries-mA.png)

Likewise, current goes up to 19.6mA in the consumption and reverse to -15.2mA in the recharge phase
(current must be divided by 10 because we are using 10 Ohm resistor).

![Image of Voltage in Full-Cycle](/results/Batteries-Consumption.png)

![Image of mAmps in Full-Cycle](/results/Batteries-Consumption-V.png)

Closeup view to batteries in consumption phase.
Notice the 555 frequency is 17.24Khz which is much higher compared to frequency used by Newman is his experiments.

![Image of Voltage in Full-Cycle](/results/Batteries-Recharge.png)

![Image of Voltage in Full-Cycle](/results/Batteries-Recharge-V.png)

Closeup view to batteries in recharge phase. Frequency still the same as expected.

Although this is preliminary results, frequency seems to don't matter much except when lower frequencies are used that makes the back emf becames too strong for the rotor to overcome.
On the other hand, duty cycle affects a lot, affecting both the energy consumption, recharge and rpm.
Increasing duty for the FIRING phase increases consumption, recharge and speedup the rotor but not at the same rate. 
So, the exact sweet spot that gives the maximum recharge and rpm and minimum consumption is unknown.

## Conclusions so far...

Although there are too many input variables to deal with:
* Coil's input voltage
* 555's frequency and duty cycle
* Range of the activation zone
* Wire diameter and length
* Magnet size and strength

**It's clear that Newman's invention does recharge the batteries when running**.
Although I am using a solid state circuit instead of a mechanical commutator, it tries to mimic the working of the mechanical commutator described by Newman.
So far, the results that I have achieved are not overunity, but they are at least interesting and they can be improved.

## Things to do in future...

* More tests with different input parameters
* Analyse relation among input and output parameters
* Measure RPM
* Running test with low farad capacitor as input voltage for the coil
* PMBO 2018 using improved geometry

## Building Instructions

### Requirement
* 3D Printer
* Soldering tools
* Hot glue gun

### Assembly itens
* 2 x 6000 Full Ceramic Bearing 10x26x8mm
* 2 x N52 45x45x20mm Block Magnet Strong Rare Earth Neodymium Magnet
* ~5Kg AWG 28 Copper
* ~500g PLA or ABS 
* 22AWG solid core wire for soldering the IR

Print all STL files in the directory **/model**.
Put together **Coil.Inner and Coil.Outer** and insert in both holes **Coil.Lock**
Wind all AWG 28 Copper in the coil. There are holes in the coil for up to two coils. It's recommended to fill the whole coil with copper wire. The more, the better.
22AWG must be solderd in IR sensors and emitters (only a par is required for this test). IR sensor and emmiter must be put in **Coil.BL-4xLR** in any spot facing each other. Glue the IR Sensor with hot glue.

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