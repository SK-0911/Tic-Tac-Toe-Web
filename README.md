# Step-by-Step Guide to Building a Tic Tac Toe Game
### 1. Setting Up the HTML Structure
Start by creating the basic structure of the game. This includes the start screen, game board, and end game screen.
- **Start Screen**: Contains inputs for player names and a start button.
- **Game Board**: Where the game is played, with cells for Xs and Os.
- **End Game Screen**: Displays who won or if it's a draw, with an option to restart the game.

**Code Snippet:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- Meta tags, title, and CSS link -->
</head>
<body>
    <div class="container" id="gameStart">
        <!-- Player input fields and start button -->
    </div>

    <div class="container hide" id="gameBoard">
        <div id="playerTurn"></div>
        <div class="grid">
            <!-- 9 cells for the game -->
        </div>
        <button onclick="restartGame()">Restart Game</button>
    </div>

    <div id="gameEnd">
        <div class="container">
            <!-- Display winner and restart option -->
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>
```

### 2. Styling with CSS
Make the game visually appealing by adding styles. Focus on layout, colors, and interactivity.
- **Body**: Center the content and add a background color.
- **Containers**: Style the start screen, game board, and end screen.
- **Grid and Cells**: Create a grid layout for the game board.
- **Buttons and Inputs**: Style for better user experience.

**Code Snippet:**
```css
body {
    /* Flexbox layout and background styling */
}

.container {
    /* Styling for each container */
}

input[type="text"], button {
    /* Input and button styles */
}

.grid {
    /* Grid layout for game board */
}

.cell {
    /* Styling for each cell in the game board */
}
```

### 3. Adding JavaScript for Game Logic
Implement the game's functionality using JavaScript.

- **Starting the Game**: Capture player names and show the game board.
- **Playing the Game**: Handle player moves and update the board.
- **Checking for Win or Draw**: Determine the game's outcome after each move.
- **Ending the Game**: Show the winner and provide an option to restart.

**Code Snippet:**
```javascript
let currentPlayer = 'X';
let gameActive = true;
let gameState = ["", "", "", "", "", "", "", "", ""];
let players = {};

function startGame() {
    // Initialize game and display player turn
}

function makeMove(index) {
    // Update board on each move and check for win or draw
}

function checkResult() {
    // Check game state for a win or draw
}

function announceWinner(winner) {
    // Display winner or draw message
}

function restartGame() {
    // Reset the game to initial state
}

document.addEventListener('DOMContentLoaded', () => {
    restartGame(); // Reset the game when page loads
});
```
<hr/>

## Writing The Code -

### Step 1: HTML Structure for Tic Tac Toe Game

**Objective:** Create the basic structure of the Tic Tac Toe game, including the start screen, game board, and end game screen.

### A. Start Screen (`gameStart`) 
This is where players will enter their names and start the game.

**HTML Code:**
```html
<div class="container" id="gameStart">
    <h1>Tic Tac Toe</h1>
    <div class="input-group">
        <input type="text" id="player1" placeholder="Enter Player 1 Name" />
    </div>
    <div class="input-group">
        <input type="text" id="player2" placeholder="Enter Player 2 Name" />
    </div>
    <button onclick="startGame()">Start Game</button>
</div>
```

### B. Game Board (`gameBoard`)

This is the main game area where players will interact to play Tic Tac Toe.

**HTML Code:**
```html
<div class="container hide" id="gameBoard">
    <div id="playerTurn"></div>
    <div class="grid" id="grid">
        <div class="cell" onclick="makeMove(0)"></div>
        <!-- Repeat for cells 1 to 8 -->
    </div>
    <button onclick="restartGame()">Restart Game</button>
</div>
```

### C. End Game Screen(`gameEnd`)

This screen displays the winner or indicates a draw, and allows players to restart the game.

**HTML Code:**
```html
<div id="gameEnd">
    <div class="container">
        <h2 id="winner"></h2>
        <button onclick="restartGame()">Play Again</button>
    </div>
</div>
```

### Step 2: CSS Styling for the Game

**Objective:** Apply styles to the game elements for a visually appealing and user-friendly interface.

### A. General Styles

Style the body and set up the main container.

**CSS Code:**
```css
body {
    font-family: "Arial", sans-serif;
    background-color: #f4f4f4;
    display: flex;
    flex-direction: column;
    gap: 10px;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background-color: white;
    border-radius: 10px;
    box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
    padding: 20px;
    text-align: center;
    max-width: 400px;
    width: 100%;
}
```

### B. Styling Inputs and Buttons

Create a consistent and interactive look for inputs and buttons.

**CSS Code:**
```css
input[type="text"] {
    padding: 10px;
    margin: 10px 0;
    border: 1px solid #ddd;
    border-radius: 4px;
    width: calc(100% - 20px);
}

button {
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 4px;
    padding: 10px 20px;
    cursor: pointer;
    font-size: 1em;
    width: 100%;
    margin-top: 10px;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #0056b3;
}
```

### C. Game Board and Cells

Style the game board and individual cells for the Tic Tac Toe grid.

**CSS Code:**
```css
#gameBoard {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
}

.grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
}

.cell {
    background-color: #fff;
    border: 2px solid #007bff;
    border-radius: 4px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 2em;
    color: #333;
    width: 120px;
    height: 120px;
    cursor: pointer;
    user-select: none;
}

.cell:hover {
    background-color: #e7e7e7;
}
```
### D. End Game Screen

Style the end game screen for displaying the game outcome.

**CSS Code:**
```css
#gameEnd {
    position: absolute;
    width: 100vw;
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
}
```

### Step 3: JavaScript for Tic Tac Toe Game

### A. Initial Setup and Variables

**Objective:** Define the essential variables for the game.

**Code:**
```javascript
let currentPlayer = 'X';
let gameActive = true;
let gameState = ["", "", "", "", "", "", "", "", ""];
let players = {};
```

**Explanation:**

- `currentPlayer`: Keeps track of who's turn it is. It starts with 'X'.
- `gameActive`: A boolean to determine if the game is ongoing.
- `gameState`: An array representing the state of each cell on the board.
- `players`: An object to store the names of the players.

### B. Starting the Game

**Objective:** Capture player names and display the game board.

**Code:**
```javascript
function startGame() {
    players.player1 = document.getElementById('player1').value || 'Player 1';
    players.player2 = document.getElementById('player2').value || 'Player 2';
    document.getElementById('gameStart').style.display = 'none';
    document.getElementById('gameBoard').style.display = 'block';
    document.getElementById('playerTurn').innerText = `${players.player1}'s Turn (X)`;
}
```
**Explanation:**

- This function is triggered when the "Start Game" button is clicked.
- It retrieves player names from the input fields. If a name is not entered, it defaults to 'Player 1' and 'Player 2'.
- It hides the start screen and reveals the game board.
- It updates the `playerTurn` element to show which player's turn it is.

### C. Making a Move

**Objective:** Handle player actions when they click on a cell in the game board.

**Code:**
```javascript
function makeMove(index) {
    if (gameState[index] !== "" || !gameActive) {
        return;
    }
    gameState[index] = currentPlayer;
    document.getElementsByClassName('cell')[index].innerText = currentPlayer;
    checkResult();
}
```

**Explanation:**

- The `makeMove` function is called when a cell is clicked, passing the cell's index as an argument.
- It first checks if the cell is already occupied (`gameState[index] !== ""`) or if the game is inactive (`!gameActive`). If either condition is true, it returns early, doing nothing.
- It updates the `gameState` array at the clicked cell's index with the current player's symbol ('X' or 'O').
- The cell's text is updated to display the current player's symbol.
- After each move, it calls `checkResult` to see if the game has been won or drawn.

### D. Checking the Game Result

**Objective:** Determine if the game has been won or if there's a draw after each move.

**Code:**
```javascript
function checkResult() {
    const winConditions = [
        [0, 1, 2], [3, 4, 5], [6, 7, 8],
        [0, 3, 6], [1, 4, 7], [2, 5, 8],
        [0, 4, 8], [2, 4, 6]
    ];

    let roundWon = false;
    for (let i = 0; i < winConditions.length; i++) {
        const winCondition = winConditions[i];
        let a = gameState[winCondition[0]];
        let b = gameState[winCondition[1]];
        let c = gameState[winCondition[2]];
        if (a === '' || b === '' || c === '') {
            continue;
        }
        if (a === b && b === c) {
            roundWon = true;
            break;
        }
    }

    if (roundWon) {
        announceWinner(currentPlayer === 'X' ? players.player1 : players.player2);
        gameActive = false;
        return;
    }

    let roundDraw = !gameState.includes("");
    if (roundDraw) {
        announceWinner('Draw');
        gameActive = false;
        return;
    }

    currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
    document.getElementById('playerTurn').innerText = `${currentPlayer === 'X' ? players.player1 : players.player2}'s Turn (${currentPlayer})`;
}
```

**Explanation:**

- `winConditions`: An array of winning combinations. Each sub-array represents a winning line on the game board.
- The function iterates over `winConditions` to check if any winning condition is met. If all cells in a winning condition have the same symbol (and are not empty), `roundWon` is set to `true`.
- If `roundWon` is true, it calls `announceWinner` with the name of the current player and sets `gameActive` to `false`.
- It checks for a draw if no empty cells are left (`!gameState.includes("")`) and calls `announceWinner` with 'Draw'.
- If the game is neither won nor drawn, it switches the current player.

### E. Announcing the Winner

**Objective:** Display the game's outcome – either the winning player or a draw.

**Code:**
```javascript
winners =[];

function announceWinner(winner) {
    document.getElementById('gameEnd').style.display = 'flex';
    document.getElementById('playerTurn').style.display = 'none';
    document.getElementById('winner').innerText = winner === 'Draw' ? 'Game Drawn!' : `Winner is ${winner}!`;

winners.push(winner);
}
```

**Explanation:**

- The `announceWinner` function is called when a player wins the game or when the game results in a draw.
- It makes the end game screen (`gameEnd`) visible by changing its display style to `flex`.
- The player turn indicator is hidden as the game is over.
- The function updates the text of the `winner` element to show either the winning player's name or a message indicating a draw.

### F. Restarting the Game

**Objective:** Reset the game to its initial state, allowing players to start a new game.

**Code:**
```javascript
function restartGame() {
    currentPlayer = 'X';
    gameState = ["", "", "", "", "", "", "", "", ""];
    gameActive = true;
    document.getElementById('gameBoard').style.display = 'none';
    document.getElementById('gameEnd').style.display = 'none';
    document.getElementById('gameStart').style.display = 'block';
    document.getElementById('playerTurn').style.display = 'block';
    document.querySelectorAll('.cell').forEach(cell => cell.innerText = '');
}
```

**Explanation:**

- The `restartGame` function resets all the game variables to their initial values.
- It hides the game board and end game screens, and shows the start screen again.
- The text in each cell of the game board is cleared.
- This function can be triggered by a button on either the game board or the end game screen, allowing players to start over.