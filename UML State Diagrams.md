---
dg-home: false
dg-publish: true
---
Related: [[SWEN221 MOC]]
Contents: [[SWEN225 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN225_2023T2/CourseSchedule)
[[UNI MOC]]
Hamish Burke || 26-07-2023
***

# State Diagrams

- Used to specify the *states* exhibited by an object or system
- Determine the responses (state transitions) to outside stimuli (events)
- Concerned with *when* operations execute (rather than *what*)

## Events

- Make object/system transition between states
- Enabled/disabled, depending on *state*
	- EG pop on a stack is *disabled* when empty
- Yield different actions/transitions, depending on state

## Finite State Machines

Most primitive state machine (not [[UML]])

- Has States and Events
	- Can 'recognise' regular languages

Can also be represented as state transition **tables**

- Are **XOR** diagrams

***

## Harel StateCharts

- Are **OR** diagrams

Can determine if the program will terminate
Because it is a form of Petri Nets
- Not turing complete

- Multiple States
- Named after David Harel

A State could contains:
- State name (only required thing)
- State variable
	- Alter information
- Activity
	- Executed while state is active
	- Paired with some sort of event
- Entry Event
	- Fired when state is entered
- Internal Events
	- Execute actions without leaving/re-entering the state
 - Exit Event
	 - Fired every time state is left
- Event Guard 
	- If condition, only fires event if true

| Name           | Examples                     |
| -------------- | ---------------------------- |
| State Name     | PasswordMode                 |
| State Variable | `password: String = ""`      |
| Entry Event    | *entry* / set echo invisible |
|                | *do* / unsetCapsLock         |
|                | *help* / display help        |
|                | *exit* / set echo normal     |

## Transitions

- Have a **start state**
	- Black dot (where program starts)
 - Target thing is end state
	 - End states are unlimited

![[Pasted image 20230727114309.png]]

## Action

- Performed instantly
- During transition
- On arrow

## Activity

- Takes time to complete
- Performed in a state

***

# SuperState

- Reduces complexity by **hiding**

To lessen the amount of out/in lines for something
- The grey box is the superstate

![[Pasted image 20230727144902.png]]

# Concurrent Machines

- *Parallel Execution*
- Separates concurrent behaviour
- Each line is called a 'swim lane'
- Dotted line between the two, in a superstate
	- They don't interact (cross the dotted line)

- Total number of needed states is the **product** of both swim lanes

# Fork and Join

- Separate one arrow into two
- Both paths have to complete before it can terminate

![[Pasted image 20230727145902.png]]

## Linking

Can link with [[UML Class Diagram]]
- In state diagram, can reference the method that'll affect the state

```
lock / {report("unlocking dorr!");} -> Locked;
```