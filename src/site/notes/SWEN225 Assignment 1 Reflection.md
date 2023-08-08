---
{"dg-publish":true,"permalink":"/swen-225-assignment-1-reflection/"}
---

Related: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
Contents: [[SWEN225 MOC\|SWEN225 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN225_2023T2/CourseSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 07-08-2023
***

# Reflection

Individual Reflection

## Specifications and Assumptions

- Clearly justified any assumptions made regarding ambiguous or missing specification details. For example:
    - Assumed each estate occupies only 1 square on the board for simplicity.
    - Did not implement restrictions on players moving through walls, to focus on core game logic.

- Explained any major simplifications to the given specifications, and why they were made. For example:
    - Only implemented a simple text interface due to time constraints, instead of a graphical interface.
    - Did not incorporate rules around blocking other players' spaces, to simplify movement logic.

## Use of CRC Cards

- Thoroughly described how CRC cards were used during the design process. For example:
    - Created initial cards for key nouns like Player, Board, Weapon.
    - Identified cardinalities and relationships between classes.
    - Played out scenarios to validate responsibilities assigned to each class.
    - Iteratively refined cards as design was developed.

## Contributions and Challenges

- Listed specific design and code contributions, e.g.:
    - Designed the Board and Player classes.
    - Implemented movement logic and guess/refutation game rules.

- Discussed challenges faced and how they were resolved, e.g.:
    - Implementing refutation logic was complex, but CRC cards helped assign responsibilities.
    - Debugging concurrent player moves took time, but was fixed through proper synchronization.

## Suggestions for Improvement

- Provided constructive suggestions for improving design and code, e.g.:
    - Create common Guess and Solution classes to reduce duplication.
    - Use Java FX for a graphical interface.
    - Add JUnit tests to improve correctness.

In summary, this reflection template demonstrates an excellent understanding of the assignment and thoughtfully considers the required elements. It can be filled in with specific details and examples to create a high quality individual reflection.