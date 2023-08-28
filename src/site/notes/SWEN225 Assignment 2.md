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

[[SWEN225 Assignment 2 Final\|SWEN225 Assignment 2 Final]]

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


Whenever I updated something in the UI, I wrapped that method in swingutilities.invokelater(). This makes each change executed in the Event Dispatch Thread, making the updates thread-safe.
```

In our transition to a GUI-based game, adhering to the Model-View-Controller (MVC) architecture provided a structured approach, ensuring clean separation of concerns. We utilized Java's Swing library for GUI components, offering a mature and well-documented toolkit for this implementation.

**Swing Components and Their Functionalities**

- **JFrame**: The main application window was constructed using `JFrame` by extending it in the `GameView` class. `JFrame` provides a comprehensive framework for adding various UI components, making it an ideal choice for the primary window.
    
- **JPanel**: Used extensively in different segments of the UI, `JPanel` serves as the container for components like `boardPanel`, `infoArea`, and `cardPanel`.
    
- **JLabel & JTextArea**: For displaying static and multi-line text, we employed `JLabel` for the board title (`boardTitle`) and `JTextArea` for showing game messages (`infoAreaText`). The flexibility of `JTextArea` in displaying multi-line, non-editable text made it particularly useful.
    
- **JMenuBar, JMenu, JMenuItem**: These components composed the menu bar, featuring options such as `NewGameItem` for starting a new game and `quitItem` for exiting.
    
- **JButton**: Chosen for triggering game actions like rolling dice and making guesses, `JButton` was used for its straightforward implementation and ease in attaching action listeners.
    
- **JRadioButton & ButtonGroup**: `JRadioButton` allowed players to select the number of participants, and a `ButtonGroup` ensured that only one radio button could be active at a given time.
    
- **JOptionPane**: Employed for verification dialogs, like confirming the user's intent to exit the game.
    
- **Key and Mouse Listeners**: `KeyListener` and `MouseListener` were integrated for advanced interactivity. For example, `KeyListener` managed actions like quitting and making a guess, while `MouseListener` detected cell clicks on the board.
    

**Thread Safety**

To ensure thread safety, UI update methods were wrapped in `SwingUtilities.invokeLater()`, thereby executing them in the Event Dispatch Thread. This precaution avoids potential inconsistencies in the UI due to multi-threading.


- [ ] Design Discussion (27 marks). Marks will be awarded for how well the individual reflection explains the challenges in modifying the previous code to feature a GUI, rather than textual input/output. In particular the reflection should elaborate on how a good design supports changes like adding a GUI, e.g., what properties of the original code made it hard or easy to change the textual UI to a GUI. 

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

In the process of transitioning from a text-based interface to a GUI for our game, we encountered several design challenges and opportunities that offer valuable lessons in software architecture. One of the initial decisions made was to apply the Singleton pattern to the `Game`, `GameView`, and `GameController` classes. This design choice simplified the interaction between these central components, making it easier to invoke methods across them, such as updating the GUI when the game state changes. However, Singleton patterns, while convenient, can introduce global state issues that may complicate debugging and testing in more complex projects.

A significant challenge was the embedded user inputs within the `Game` class. Initially, methods governing gameplay (e.g., making guesses or solving puzzles) contained hardcoded textual inputs, making them tightly coupled with the text-based presentation layer. This coupling violated the principle of separation of concerns, one of the cornerstones of robust software design. Because the game logic was intertwined with the input/output mechanisms, adapting the class to a GUI setting required significant refactoring. This experience emphasized the importance of separating the core logic from its presentation, facilitating future interface changes without affecting the underlying mechanics.

On the brighter side, the modularity of our original board and cells design made the transition to a GUI smoother. This aspect of the code adhered well to principles of good software design, notably modularity and flexibility. Such modular design allows different system components to be updated or replaced independently, making it easier to introduce changes like a new interface.

The GUI implementation used a state machine model, handled by the `updateView()` method in `GameView`. This method, relying on an enum for different game states (`GameState`), streamlined the GUI updates, ensuring that the interface always accurately reflected the current game condition. This design choice offered a clean and understandable way to manage the various GUI elements based on the game's state.

To further enhance our GUI's adaptability, we introduced dynamic button management. Using a method like `setContextButtons()`, the displayed buttons change according to the current game state. This dynamic approach affords high flexibility, aligning with the evolving requirements of the gameplay, and enabling quick and easy adjustments to the GUI in the future.

In summary, this exercise in transitioning from a text-based interface to a GUI elucidated key principles of effective software design. It highlighted the need for modularity, separation of concerns, and flexibility. Challenges like hardcoded user inputs served as a lesson in what not to do, whereas successes in areas like board design and dynamic button management underscored the importance of forward-thinking, adaptable architecture.

- [ ] State Diagram Discussion (25 marks). Marks will be awarded for how well the individual reflection describes the states that the software may be in, including details such as which information may be associated with a state, and which state transitions are supported/prohibited. There is no need to be comprehensive; only important key points need to be mentioned. The state diagram submitted as part of the group work should be referenced in this part.

```
The game starts in GameSetup, which is where the user selects how many players they want to play. Once they select that, the state changes to PlayerToMove. It shows the player the Roll Dice button, and once they click that, they know how far they can move, and the state changes to WaitingForPlayerToMove. This state waits for them to select a cell, and checks if the player has enough moves to go there. The states fork here, depending on whether the player landed in an estate (by selecting a door cell). If they did, the state changes to PlayerCanGuessAndSolve, otherwise PlayerCanSolve. Both these states bring up guess/solve buttons repectiviley, as well as a end turn button. When this is pressed. The currentPlayerNumber is incremented and the state is set back to PlayerToMove. It is now the next players turn. This continues until someone solves the murder correctly, which changes the state to PlayerWon. If every attempts to solve but fails, the state changes to PlayersLost.
```

In the development of our game, the state diagram serves as a critical guide for defining the game's behaviour at various stages. The game starts in the "GameSetup" state, wherein the primary objective is to initialise the number of players. This information becomes crucial as it sets the stage for the game's entire flow. From "GameSetup," the state transitions to "PlayerToMove," where the focus is on the current player and their decision to roll the dice.

The next stage, "WaitingForPlayerToMove," is invoked after the dice roll. This state encapsulates not just waiting, but also validating the player's moves by associating the number of available moves with the dice outcome. Depending on whether the player ends up in an "estate" or not, the state diverges into either "PlayerCanGuessAndSolve" or "PlayerCanSolve." These states incorporate player actions such as making guesses or attempting to solve the murder, while also offering an "End Turn" option.

These transitions are carefully controlled. For example, a player cannot skip from "PlayerToMove" to the solving states without first going through "WaitingForPlayerToMove," ensuring gameplay integrity. Moreover, the states "PlayerWon" and "PlayersLost" act as terminus states, sealing the game's outcome. These terminal states are reached only when a player successfully solves the murder or when all players fail in doing so, respectively.

Prohibited transitions also add rigidity to the game design. One cannot jump from the initial "GameSetup" to the terminal states like "PlayerWon" or "PlayersLost" without actual gameplay, preserving the game's logical flow.

The state diagram therefore serves as both a conceptual and a practical roadmap. It helps in organising the code, thanks to the clear transitions and associated information with each state. In essence, the diagram acts as the backbone of the game's logical structure, providing clear rules and boundaries.