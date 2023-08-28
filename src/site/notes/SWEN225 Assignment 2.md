---
{"dg-publish":true,"permalink":"/swen-225-assignment-2/"}
---

Related: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
Contents: [[SWEN225 MOC\|SWEN225 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN225_2023T2/CourseSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 28-08-2023
***

# Reflection

Individual Reflection [82 marks]

For the individual reflection, marks will be awarded on an individual basis as follows: 

- GUI Discussion (25 marks). Marks will be awarded for how well the individual reflection conveys aspects of the GUI design of your implementation, i.e., which Swing components were used where (conceptually and within the code) for what purpose and why a particular component type was chosen. 

```
Followed MVC architecture, created GameView and Gamecontroller classes. I set up and intialised the buttons/jpanels in GameView. Added the action listeners to GameController.

Swing Components used:

- **KeyListener**: Listens for key events and performs actions based on the key pressed.
    - `keyPressed(KeyEvent e)`: Handles various key events like creating a new game, quitting, guessing, and solving.
- **MouseListener**: Listens for mouse events.
    - `mouseClicked(MouseEvent e)`: Handles cell clicks on the GUI board.
- **JPanel**: Used as the base class for the controller.
    - `GameController extends JPanel`: Inherits JPanel to make use of its functionalities.
- **JFrame**: The main window of the application.
    - `GameView extends JFrame`: Inherits JFrame to create the main application window.
- **JPanel**: Used for various parts of the UI.
    - `boardPanel`: Displays the game board.
    - `infoArea`: Displays player information or game messages.
    - `cardPanel`: Displays player cards.
- **JLabel**: Used for displaying text.
    - `boardTitle`: Displays the title of the board.
- **JTextArea**: Used for displaying multi-line text.
    - `infoAreaText`: Displays game messages or player information.
- **JMenuBar, JMenu, JMenuItem**: Used for the menu bar and its items.
    - `NewGameItem`: Creates a new game.
    - `quitItem`: Quits the game.
- JOptionPane
	- pops up asking the user if they're sure they want to close
- **JButton**: Used for various actions.
    - `Roll Dice`: Rolls the dice.
    - `Guess Murder`: Makes a guess about the murder.
    - `Solve Attempt`: Attempts to solve the murder.
    - `End Turn`: Ends the current player's turn.
    - 'new game': Creates a new game (resets everything)
    - 'quit': Brings up JOptionPane to confirm quit
- **JRadioButton**: Used for selecting the number of players.
    - `threePlayers`: Sets up a game for 3 players.
    - `fourPlayers`: Sets up a game for 4 players.
- **ButtonGroup**: Groups radio buttons.
    - `playerNumRadioButtons`: Groups `threePlayers` and `fourPlayers` radio buttons.
```

- Design Discussion (27 marks). Marks will be awarded for how well the individual reflection explains the challenges in modifying the previous code to feature a GUI, rather than textual input/output. In particular the reflection should elaborate on how a good design supports changes like adding a GUI, e.g., what properties of the original code made it hard or easy to change the textual UI to a GUI. 

```
Patterns used:
- Made Game, GameView, and GameController follow the singleton pattern. This is allowed to more easily call methods from other classes (eg from GameController to GameView to update the GUI for the next player)

We found quite hard in some places to change our original design to meet the new specifications. For example in the game class, we hardcoded the user inputs inside all the methods that are used to play the game (eg for guess or solve), which meant it was difficult to use those methods at all, and required us to rewrite them. One place where our design made it easy to switch to a GUI was with the board and cells. This is because we 

Main way I updated the GUI was with the upateView() method in GameView. This used a switch to change what was displayed in GameView based on the GameState. These states were an enum in Game and were: 
PlayerToMove,  
WaitingForPlayerToMove,  
PlayerCanSolve,  
PlayerCanGuessAndSolve,  
PlayerWon,  
PlayersLost,  
GameSetup

For the buttons, I wanted it to be easy to add more buttons at any time, and to dynamically decide what buttons to show at any point. So I created a map of buttons, that changes what buttons to display based on the gamestate. (eg `PlayerToMove` shows the Roll dice button, `PlayerToGuess` shows the Guess button, and End Turn button). This meant I could call setContextButtons(<buttons to display>) (eg in GameView.updateView()) and it will update accordingly.
```

- State Diagram Discussion (25 marks). Marks will be awarded for how well the individual reflection describes the states that the software may be in, including details such as which information may be associated with a state, and which state transitions are supported/prohibited. There is no need to be comprehensive; only important key points need to be mentioned. The state diagram submitted as part of the group work should be referenced in this part.

```

```