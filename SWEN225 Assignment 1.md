---
dg-home: false
dg-publish: true
---
Related: [[SWEN221 MOC]]
Contents: [[SWEN225 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN225_2023T2/CourseSchedule)
[[UNI MOC]]
Hamish Burke || 24-07-2023
***

# Hobby Detectives

Due on 7th

[[SWEN225 Assignment 1 Class Diagram]]


- 3-4 players
	- Lucilla
	- Bert
	- Malina
	- Percy
 - 5 weapons
	 - Broom
	 - Scissors
	 - Knife
	 - Shovel
	 - iPad
- 5 estates
	- Each one is a single square
- 24 x 24 square area

## UI

- Text based
	- Only using `System.in/System.out`
- **Starts** by asking how many players
- One player selected to start at random
- Once a player has rolled (and moved)
	- They have the option to make a guess or solve attempt
- Repeats the above steps until a players won
	- Or all players lost (by making a wrong solve attempt)
- Must print instructions on which player to pass the 'tablet' to
	- Like Spy (mobile game)

## Objective

- Murder can happen in any of 5 estates
- Deduce the murder circumstances
	- Who the murderer was
	- What weapon was used
	- Which estate the murder happened in

## Start-up

- Each weapon placed in a estate at random (one for each)
- One character/weapon/estate card are selected at random
	- That's the murder cards
- Remaining cards (of all types) are then combined and distributed at random to players
	- One player may end up with one more card (that's ok)

## Gameplay

- Player rolls two dice
- Move their player the sum of the roll
	- No diagonal movement
	- No square can be used twice *in one turn*

**If a player enters an estate on their turn**
- They don't need to use any remaining moves left
- They can then make a *guess* about the character and weapon
	- Using the estate they are in
- The said weapon/character are then teleported to the estate


**After a guess has been made**
- Each player attempts to refute by producing a card that matches one of the suggested murder circumstances
	- Must be made if able to
	- Using *order* Lucilla, Bert, Malina, Percy (starting person is one player after the player making the guess)
- A refutation card to the guess is only revealed to the person who guessed it
- If no one can refute, that *Guess* can be used to make a *solve attempt* later
	- By any player


**A solve attempt**
- Contains a character, weapon, and an estate
- If matches murder exactly, the player wins
- Otherwise, player is excluded from making further guesses or solve attempts
	- Can't win anymore, but will continue to refute guesses by others



