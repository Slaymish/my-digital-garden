---
dg-home: false
dg-publish: true
---
Related: 
Contents: [[EEEN202 MOC]]
[[UNI MOC]]
Hamish Burke || 15-05-2023
***

# The System Stack

Why do we need it?
- When calling a subroutine (or servicing an interrupt) you need to preserve the return address
- We also need to preserve contents of other registers


<h2 align="center">

The stack is Last in first out (LIFO)

</h2>


- Max memory on the 8051 stack is **128 bytes**
- PUSH and POP are special instructions associated with the stack

## Example

```assembly
MOV SP, #50H // start the stack pointer at 50H
MOV A, #10H
MOV B, #20H 
PUSH ACC // pushes accumulator to stack
PUSH B // pushes contents of B register to stack

... (can do other code here)
...


// Get the B value from stack
POP B
POP ACC
```

## Calling a Subroutine

- Calling ACALL
	- Causes PC to increase by 2
	- Then push the 16-bit PC value onto the stack
	- Increments the stack pointer twice

### RET Instruction

- Pops the high and low byte address of PC from the stack
- decrements the SP by 2


***

# Interrupts

- Allows a system respond asynchronously to an event
- The sub program that deals with an interrupt is called a **interrupt service routine (ISR)** or **interrupt handler**

When an interrupt occurs, the main program temporarily stops and branches to the ISR


The ISR executes, performs the desired operation, then terminates with a 'return from interrupt' (RETI) instruction

8051 Interrupt sources:
- External interrupts
- Timer interrupts
- Serial port interrupts

- Each interrupt source has one or more associated interrupt-pending flag(s) located in an SFR
- 

When a peripheral or external sources meets a valid interrupt condition, the associated interrupt-pending flag is set to 1

<p align="center">
When system resets, all interrupts turn off
</p>

## Priority

- Each interrupt has an assigned priority
- A low priority interrupt routine can be interrupted by a higher priority interrupt

## Enabling/Disabling Interrupts

Two bits must be set to enable an interrupt (for most interrupts)
- The individual enable bit
- the global enable bit

The RESET interrupt (interrupt 0) can't be turned off and has the highest priority

## Interrupt Pending Flags

- Most are not cleared by the hardware, must be cleared by software before returning from the ISR

If the pending flag remains on after the CPU completes the RETI, a new interrupt request will be generated immediately after


