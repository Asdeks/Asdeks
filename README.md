# Cross_and_zeroes

Welcome to **Cross_and_zeroes**, a simple yet classic console game of Tic-Tac-Toe implemented in C++. This project serves as a great example of basic game logic and console-based user interaction.

## Features

- **Classic 3X3 Grid:** Play the traditional Tic-Tac-Toe game on a 3x3 board.
- **Two-Player Mode:** Alternate turns between two players, `X` and `O`.
- **Automatic Win Check:** The game automatically checks for a win condition or a draw after each move.
- **Random First Player:** Randomly select which player goes first at the beginning of each game.
- **Game Statistics:** Track the number of wins for each player and the number of draws.

## How to Play

1. **Start the Game:** Run the executable to start the game.
2. **Input Coordinates:** Players take turns inputting the coordinate of the cell where they want to place their mark (`X` or `O`).
3. **Win or Draw:** The game will declare a winner if three of the same marks align horizontally, vertically, or diagonally. If all cells are filled without a winner, the game ends in a draw.
4. **Play Again:** After each game, you have the option to play again, with the win statistics being updated accordingly.

## Code Overview

The main logic of the game is encapsulated within the `Game` class:

- **Attributes:**
  - `Board[3][3]`: The game board.
  - `X`: The current player’s mark (either 'X' or 'O').
  - `Result`: Indicates the result of the game (1 for X win, 2 for O win, 0 for draw).

- **Methods:**
  - `ShowBoard()`: Displays the current state of the game board.
  - `GetCoord()`: Prompts the current player to input a coordinate for their move.
  - `EmptySquare(char)`: Checks if the selected cell is empty.
  - `Check()`: Checks if there's a winning condition on the board.
  - `swapX()`: Switches the current player.
  - `NewGame()`: Initializes a new game session.

### Code Snippet

```cpp
void Game::ShowBoard() {
    system("CLS");
    for (int i = 0; i<3; i++) {
        for (int j = 0; j<3; j++) {
            cout << "|" << Board[i][j] << "|";
        }
        cout << "\n";
    }
    Check();
}

void Game::GetCoord() {
    char ch = '1';
    cout << "Input COORD(" << X << "): ";
    cin >> ch;

    while (!EmptySquare(ch)) {
        cout << "Input COORD(" << X << "): ";
        cin >> ch;
    }

    Board[0][ch - '0' - 1] = X;
    swapX();
    ShowBoard();
}

bool Game::EmptySquare(char x) {
    return (Board[0][x - '0' - 1] == x);
}
g++ -o Cross_and_zeroes Cross_and_zeroes.cpp
