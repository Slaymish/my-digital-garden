---
dg-publish: true
---
Name: Hamish Burke
Lab Partner: Seb Collis

# Design Exercise Report

## 1. Introduction

This project involves the design and development of a system that can measure the distance traveled by a rover and display it on a set of seven-segment displays. The primary goal of this report is to document the design process for each of the sub-systems involved in creating the final system and provide a clear description of how they work together. The project is separated into five sub-systems: the clock, odometer, odometer display, motor control, and grey code generator. The clock is responsible for generating a square wave signal with a frequency of 2Hz. The odometer measures every time the wheel does a full rotation and counts up to a total distance of 64 meters of travel. The odometer display uses the odometer output to display the distance traveled on two seven-segment displays. The motor control system generates a stop signal after the rover has traveled 50m and stops the clock signal, and it generates a battery charged signal to enable the clock again. Finally, the grey code generator generates a 3-bit grey code pattern that counts either up or down, depending on the direction bit. This report will describe the design process for each sub-system and provide well-labeled circuit diagrams. Furthermore, we will discuss the testing and operation of the system, including any glitches we discovered and how we solved them.

## 2. Odometer:

The odometer subsystem is designed to measure the distance traveled by the rover. It counts every time the wheel does a full rotation, and since the wheel covers one meter with every full revolution, the counter counts up to a maximum of 64, which means the rover has traveled 64 meters. However, the travel is limited to 50 meters to ensure the batteries can recharge. Therefore, the odometer subsystem outputs a stop signal after 50 meters. The counter counts either pulses from the clock signal or uses the output from the grey code generator. When the odometer reaches 50 meters, it starts the motor control system and shuts down the clock. The output of the odometer is in binary encoded decimal (BCD), which is sent to the odometer display.

I first thought to create the counter with 6 J-K Flip Flops, this is because each FF is one bit, so $2^n=64$, which means $n$ would have to be 6 to have enough bits to count up to 64. We decided on using the 74HCT390 IC, which is a dual decade ripple counter. This means one IC has two independent 4-bit decade counters, triggered on the negative going transition (NGT). We choose to use this IC because it already counted in BCD, which meant we would not need any additional ICs or circuitry to get the BCD output for the 7-segment display. Because it also had two counters, we could use just one IC for the counting components. To achieve this, we connected $1QD$ (pin 7) to 2CLKA (pin 15). This created an 8-bit BCD counter, with 2QD being the MSB, and 1QA being the LSB.

The next step was to generate a stop signal that occurred at the 50th state. To do this, I connected all outputs $1QA-1QD$ and $2QA-2QD$ that were high at the 50th state into an AND gate. These outputs were $2QC$ and $2QA$. To accomplish this, we used the 74HCT08 IC, which outputs a high signal only when all its inputs are high. This was used as our stop signal at 50m. To implement this, we connected $2QA$ of the counter to $1A$ (pin 1) of the IC, and $2QD$ to $1B$ (pin 2) of the IC.


![300](https://i.imgur.com/NiBdEo2.png)


***

## 3. Odometer Display:

Since the counter we used outputted the count in binary coded decimal (BCD), we did not need to add anything to make it work correctly with the odometer display. We plugged 1QA-2QD into the display inputs. However, we encountered a problem as one of the segments was always remaining on. We discovered that this was due to the 7-segment display being slightly broken. To ensure that the counter was working correctly, we connected all the outputs to the LED diodes and confirmed that it was functioning properly. As a result, we decided to keep the outputs of the counter connected to the LEDs, as those were the only ones working.

Here is how I connected my Odometer to the 7-segment displays:

![300](https://i.imgur.com/5kaZreG.png)

## 4. Motor Control:

We've already got our stop signal for 50m (the 50th state) from the counter, so to stop the CLK signal when that is HI we used a NOR Gate Latch. We constructed this with the 74HCT02 IC (Quad 2-input NOR gate). It has two inputs, Set (S) and Clear (C), and outputs $Q$ and $\neg Q$. The SR NOR latch can be used to stop the CLK signal when the stop signal for 50m (50th state) is reached.

Construction of NOR latch:
![300](https://i.imgur.com/tcndEy8.png)

To implement this, connect the stop signal for 50m to the Set input of the NOR latch. We then connected the CLEAR input to a button so we could pulse that HI when we wanted the CLK to continue. The output Q of the SR NOR latch will go high when the 50th state is reached. Connect this Q output to an AND gate (74HCT08) along with the original CLK signal as its other input. This will ensure that when Q is high, indicating that 50th state has been reached, the output of the AND gate will be low regardless of the CLK signal. The output of the AND gate is the new clock signal that stops when 50m is reached. 

![300](https://i.imgur.com/wJ5zTkP.png)


***

## 5. Grey Code Generator:

We used three D Flip-flops, and connected them synchronously by connecting the CLK to all three. We then added the combinatorial logic for each of the D inputs. They were as follows:

$D_0 = \neg B \neg C + BC$
$D_1 = A \neg C + \neg A B$
$D_2 = AC + \neg A B$

To make the combinatorial logic components for each FF input, we created logic diagrams from them. From those we figured out what gates we would need for the logic to work. For all of the combinatorial logic, we need to use OR gates, as well as AND gates. We used 74HCT08 (Quad 2-input AND gate) and 74HCT32 (Quad 2-input OR gate). 

This was a lot of IC's, so it took us most of the second lab to complete it. As the grey-code code was intended to signify the turning of the wheel, we'd want the odometer system to increment once the rover has gone '1m'. We did this by combing $Q_0 - Q_2$ (outputs of the three D FF's) into a NOR gate (we used 74HCT02). This means that when the system reaches the state were all output are LO, then the NOR gate will output a HI signal. We connected this as the CLK input for the odometer, so that it would increment once the rover had travelled one meter. This would happen when the grey code generator goes to the state after 0,0,0. This is because the counter we used is triggered on the negative going transition. 

We did not manage to get the direction bit working in the lab time, though if we were to continue, we won't add it as a switch input, and use that in the combinatorial logic of the grey code counter.

Grey-code counter circuit diagram:
![300](https://i.imgur.com/oEVVXIa.png)

## 6. System Integration and Testing:

In conclusion, this report presents the design and development process of a system that measures the distance traveled by a rover and displays it on a set of seven-segment displays. The system is composed of five sub-systems: the clock, odometer, odometer display, motor control, and grey code generator. Each sub-system was designed and tested individually before integrating them to create the final system.

During the integration process, we encountered several challenges such as noise in the circuit due to ungrounded inputs and a broken segment in the seven-segment display. If we were to continue working on this project, we could address these issues by grounding all unused inputs and using a different set of 7-segment displays.

The final system was tested to ensure that it worked as intended. Although there were some minor glitches discovered during testing, we were able to find the reasons for most of them. The only remaining issue is the direction bit for the grey code generator, which could be addressed in future work. I'd do this by implementing the direction input as a switch in the combinatorial logic elements of the grey code generator. 

Overall, this project demonstrates how different sub-systems can be designed and integrated to create a functional system that achieves its intended purpose. It also highlights the importance of thorough testing throughout the development process to identify potential issues and make improvements accordingly. Future work could involve refining the grey code generator's direction bit functionality and getting it to work more reliably.
