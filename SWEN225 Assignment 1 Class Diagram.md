---
dg-home: false
dg-publish: true
---
Related: [[SWEN221 MOC]] [[SWEN225 Assignment 1]]
Contents: [[SWEN225 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN225_2023T2/CourseSchedule)
[[UNI MOC]]
Hamish Burke || 24-07-2023
***

# Hobby Detectives Class Diagram

## Potential Classes

- *Card*
	- Name
	- Location

- Player extends *Card*
	- canGuess
	- rollDice()

- Weapon extends *Card*

- Estate extends *Card*

- Cell
	- Color
	- Location

- Board
	- Cell : 2D array

- *MurderScenario*
	- Player
	- Weapon
	- Estate

- TheMurder extends *MurderScenario*

- Guess extends *MurderScenario*

- SolveAttempt extend *MurderScenario*
	- isSameAsMurder()

- Dice
	- rolledNum
