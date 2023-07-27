---
{"dg-publish":true,"permalink":"/uml-state-diagrams/"}
---

Related: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
Contents: [[SWEN225 MOC\|SWEN225 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN225_2023T2/CourseSchedule)
[[UNI MOC\|UNI MOC]]
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

Most primitive state machine (not [[UML\|UML]])

- Has States and Events
	- Can 'recognise' regular languages

Can also be represented as state transition **tables**

***

## Harel StateCharts

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

![Pasted image 20230727114309.png](/img/user/Pasted%20image%2020230727114309.png)

## Action

- Performed instantly
- During transition
- On arrow

## Activity

- Takes time to complete
- Performed in a state

***

# SuperState

To lessen the amount of out/in lines for something

The grey box is the superstate

![Pasted image 20230727144902.png](/img/user/Pasted%20image%2020230727144902.png)

