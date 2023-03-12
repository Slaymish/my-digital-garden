---
{"dg-home":false,"dg-publish":true,"permalink":"/eeen-202/eeen-lab-prep-tasks/","dgPassFrontmatter":true}
---


Related: #practise 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 06-03-2023
***
[[EEEN202/EEEN Lab Prep Answers\|EEEN Lab Prep Answers]]
***
- [ ] Read through Sections 1a,b and c. 

- [ ] Draw truth tables for one of the four gates on each of the 74HCT00, 74HCT02 & 74HCT04 packages. Use data sheets to sketch the pin-outs for each of the devices. 

- [ ] Establish truth tables relating the inputs A and B to the output C for the circuits below. Summarize the truth tables with algebraic expressions which reflect the relevant theorems of Boolean algebra. 

$a~b>=\sqrt {160}=45$
 
- [ ] One-Bit Half Adder: Write down the truth table for a one-bit adder with inputs A, B, and outputs CARRY & SUM. Write expressions for the two outputs, and sketch the logic circuit that you will construct to implement this function. [^1]

$ ~$

- [ ] The 74HCT153 MUX: Get the data sheet of the above dual 4:1 MUX and study the operation of this device. Pay particular attention to the use of the ENABLE inputs. Explain what function this has in the operation of the IC. Now sketch in your lab book the logic levels that needs to be connected to the input lines in order to make this 4:1 MUX function as (i) a NAND gate (ii) an XOR gate. [^2] 

[^1]: The one-bit half adder takes two binary inputs A and B, and outputs their sum and carry as binary outputs. The expressions for the two outputs can be written as CARRY = A AND B, and SUM = A XOR B. The logic circuit can be implemented using a combination of logic gates such as AND, XOR, and OR gates.

[^2]: The 74HCT153 MUX is a digital multiplexer IC that can be used to select one of four possible input signals and route it to the output. The ENABLE inputs are used to enable/disable the operation of the device. To make the 4:1 MUX function as a NAND gate, the input signals must be connected in such a way that only one of the inputs is 1, and the output is inverted using a NOT gate. To make it function as an XOR gate, two of the input signals are connected to the two inputs of an XOR gate, and the other two inputs are inverted using NOT gates before being connected to the other input of the XOR gate.
