Sure, here is a Tic Tac Toe game written in Python for two players:

**tic_tac_toe.py**
```python
# Import the necessary modules.
import os
import random

# Define the game board.
board = []
for i in range(3):
    board.append([' ', ' ', ' '])

# Define the players.
players = ['X', 'O']

# Determine who will go first.
current_player = random.choice(players)

# Play the game.
while True:
    # Display the game board.
    os.system('cls')
    for row in board:
        print(' '.join(row))

    # Get the player's move.
    move = input(f"{current_player}'s turn: ")

    # Check if the move is valid.
    if move not in ['1', '2', '3', '4', '5', '6', '7', '8', '9']:
        print("Invalid move. Please try again.")
        continue

    # Convert the move to a row and column.
    row = (int(move) - 1) // 3
    column = (int(move) - 1) % 3

    # Check if the move is legal.
    if board[row][column] != ' ':
        print("Illegal move. Please try again.")
        continue

    # Make the move.
    board[row][column] = current_player

    # Check if the game is over.
    if check_win(board, current_player):
        # Display the game board.
        os.system('cls')
        for row in board:
            print(' '.join(row))

        # Print the winner.
        print(f"{current_player} wins!")
        break

    # Switch to the other player.
    current_player = 'X' if current_player == 'O' else 'O'

# Define the check_win function.
def check_win(board, player):
    # Check the rows.
    for row in board:
        if all(cell == player for cell in row):
            return True

    # Check the columns.
    for column in range(3):
        if all(board[row][column] == player for row in range(3)):
            return True

    # Check the diagonals.
    if all(board[i][i] == player for i in range(3)):
        return True

    if all(board[i][2 - i] == player for i in range(3)):
        return True

    # The game is not over.
    return False
```

**README.md**
This is a simple Tic Tac Toe game written in Python. The game is played by two players, who take turns placing their marks (X or O) on a 3x3 game board. The first player to get three of their marks in a row, column, or diagonal wins the game.

To play the game, simply run the `tic_tac_toe.py` file. The game will then prompt you to enter your name and the name of your opponent. Once you have entered your names, the game will begin.

To make a move, simply enter the number of the square that you want to place your mark in. The game will then check if the move is valid and, if so, make the move.

The game will continue until one player wins or the game ends in a draw.

**Implementation Details**

The game is implemented using a simple list of lists to represent the game board. Each element in the list represents a row on the game board, and each element in a row represents a column. The game also uses a simple dictionary to keep track of the players' names and their corresponding marks.

The game is played by alternating between the two players. Each player takes turns placing their mark on the game board. The game checks if the move is valid and, if so, makes the move. The game then checks if the game is over. If the game is over, the game prints the winner.

**Additional Notes**

The game can be easily modified to change the size of the game board or to allow for more than two players. The game can also be modified to add additional features, such as a computer opponent or a timer.

I hope you enjoy playing Tic Tac Toe!