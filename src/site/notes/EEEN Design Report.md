---
{"dg-publish":true,"permalink":"/eeen-design-report/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 04-05-2023
***

# Report

## ==1. Introduction==

-   Briefly introduce the project and the purpose of the report.
-   Provide an overview of the sub-systems that you will be discussing.

This project involves the design and development of a system that can measure the distance traveled by a rover and display it on a set of seven-segment displays. The primary goal of this report is to document the design process for each of the sub-systems involved in creating the final system and provide a clear description of how they work together. The project is separated into five sub-systems: the clock, odometer, odometer display, motor control, and grey code generator. The clock is responsible for generating a square wave signal with a frequency of 2Hz. The odometer measures every time the wheel does a full rotation and counts up to a total distance of 64 meters of travel. The odometer display uses the odometer output to display the distance traveled on two seven-segment displays. The motor control system generates a stop signal after the rover has traveled 50m and stops the clock signal, and it generates a battery charged signal to enable the clock again. Finally, the grey code generator generates a 3-bit grey code pattern that counts either up or down, depending on the direction bit. This report will describe the design process for each sub-system and provide well-labeled circuit diagrams. Furthermore, we will discuss the testing and operation of the system, including any glitches we discovered and how we solved them.

## ==2. Odometer:==

-   Provide a detailed description of the design process for the odometer sub-system.
-   Discuss any challenges that you encountered during the design process and how you overcame them.
-   Include a circuit diagram for the odometer sub-system.


The odometer subsystem is designed to measure the distance traveled by the rover. It counts every time the wheel does a full rotation, and since the wheel covers one meter with every full revolution, the counter counts up to a maximum of 64, which means the rover has traveled 64 meters. However, the travel is limited to 50 meters to ensure the batteries can recharge. Therefore, the odometer subsystem outputs a stop signal after 50 meters. The counter counts either pulses from the clock signal or uses the output from the grey code generator. When the odometer reaches 50 meters, it starts the motor control system and shuts down the clock. The output of the odometer is in binary encoded decimal (BCD), which is sent to the odometer display.

I first thought to create the counter with 6 J-K Flip Flops, this is because each FF is one bit, so $2^n=64$, which means $n$ would have to be 6 to have enough bits to count up to 64. We decided on using the ==74HCT390== IC, which is a dual decade ripple counter.  This means one IC has two independent 4-bit decade counters, triggered on the negative going transition (NGT). We choose to use this IC because it already counted in BCD, which meant we would not need any additional ICs or circuitry to get the BCD output for the 7-segment display. Because it also had two counters, we could use just one IC for the counting components. To achieve this, we connected $1QD$ (pin 7) to 2CLKA (pin 15). This created an 8-bit BCD counter, with 2QD being the MSB, and 1QA being the LSB.

The next step was to generate the stop signal that occurred at the 50th state. To do this, I connected all outputs $1QA-1QD$ and $2QA-2QD$ that were HI at the 50th state into an AND gate. The resulting outputs were $2QC$ and $2QA$. For this, we used the 74HCT86 IC, which outputs a high signal only when all its inputs are HI. This was used as our stop signal at 50m.

## ==3. Odometer Display:==

-   Provide a detailed description of the design process for the odometer display sub-system.
-   Discuss any challenges that you encountered during the design process and how you overcame them.
-   Include a circuit diagram for the odometer display sub-system.

Since the counter we used outputted the count in binary coded decimal (BCD), we did not need to add anything to make it work correctly with the odometer display. We plugged 1QA-2QD into the display inputs. However, we encountered a problem as one of the segments was always remaining on. We discovered that this was due to the 7-segment display being slightly broken. To ensure that the counter was working correctly, we connected all the outputs to the LED diodes and confirmed that it was functioning properly. As a result, we decided to keep the outputs of the counter connected to the LEDs, as those were the only ones working.

## ==4. Motor Control:==

-   Provide a detailed description of the design process for the motor control sub-system.
-   Discuss any challenges that you encountered during the design process and how you overcame them.
-   Include a circuit diagram for the motor control sub-system.


Should stop the CLK signal 
Generate a 'battery charged' signal that will enable CLK again
	- Off counter?




We've already got our stop signal for 50m (the 50th state) from the counter, so to stop the CLK signal when that was HI we used that in a SC NOR Latch. A NOR latch is a useful logic circuit that can be used to store one bit of information. It consists of two inputs (S and R) and two outputs (Q and Q'). The latch is set when S is high and R is low, and it is reset when R is high and S is low. When both inputs are low, the latch maintains its previous state.

In your case, you want to stop the CLK signal when the counter reaches 50. To do this, you can use a NOR latch to control the CLK signal.

Here's how you can connect the components:

1. Connect the output of your 50m detector (the stop signal) to the S input of the NOR latch.
2. Connect the CLK signal to one input of an AND gate.
3. Connect the Q output of the NOR latch to another input of the AND gate.
4. The output of the AND gate will now be your new "stopped" CLK signal that stops when 50m is reached.

When your counter reaches 50 states, it will send a HI signal to set the NOR latch. This will cause Q to become HI as well, which in turn blocks any further CLK signals from passing through the AND gate.

To reset everything back to its initial state after reaching 50 states, you can add a reset button connected to R input on your NOR latch. Pressing this button will unset/reset your NOR latch, allowing clock signals pass through again until another 50 states are reached.

This way, you've effectively stopped the CLK signal when it reaches 50m using an SC (Set-Reset) nor Latch in combination with an AND gate for controlling clock signals based on counter output.



## ==5. Grey Code Generator:==

-   Provide a detailed description of the design process for the grey code generator sub-system.
-   Discuss any challenges that you encountered during the design process and how you overcame them.
-   Include a circuit diagram for the grey code generator sub-system.

- Generate a 3-bit gray code pattern
- Should contain a direction bit D that'll allow it to count UP (D=1) or DOWN (D=0) in grey code.
	- Rest of system will assume only forwards
- G2G1G0
- Only one bit changes at a time
- Minimises risk of errors
- *D FF's and MUXes might be easiest*

We used three D Flip-flops, and connected them synchronously by connecting the CLK to all three. We then added the combinatorial logic for each of the D inputs. They were as follows:

==i believe these are in my book==
$D_1 = xxxxx$
$D_2 = xxxxx$
$D_3 = xxxxx$

The output of this was a greycode counter that start at 000, and went up in grey code by 1 at every clock pulse.
We did not manage to get the direction bit working. 

## ==6. System Integration and Testing:==

-   Describe how you integrated the sub-systems to create the final system.
-   Discuss any challenges that you encountered during the integration process and how you overcame them.
-   Describe how you tested the system to ensure that it works as desired.
-   Include a discussion of any glitches that you discovered during testing and how you propose to solve them.

## ==7. Conclusion:==

-   Summarise the main points of the report.
-   Discuss any future work that could be done to improve the system.

Most things worked, though because we had not grounded quite a few inputs, there was a lot of noise in the circuit, which main it not stable enough to function properly.

8.  Circuit Diagrams:

-   Include circuit diagrams for each of the sub-systems in an appendix at the end of the report.