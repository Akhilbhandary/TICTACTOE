##TIC TAC TOE ####

VIDEO:
https://github.com/user-attachments/assets/cfcc2971-c9ad-421c-a36f-a17c36d233c2

CODE 
#THE CODE TO PRINT TIC TAC TOE GAME 
def print_board(board):
    print(f"{board[0]} | {board[1]} | {board[2]}") # THESE PRINT STATEMENTS ARE USED TO PRINT THE COLLUMNS AND ROWS OF TIC YAC TOE 
    print("--+---+--")
    print(f"{board[3]} | {board[4]} | {board[5]}")
    print("--+---+--")
    print(f"{board[6]} | {board[7]} | {board[8]}")

# Function to check for a win or draw
def check_winner(board, player):
    # Winning combinations
    win_conditions = [(0, 1, 2), (3, 4, 5), (6, 7, 8),  # Rows
                      (0, 3, 6), (1, 4, 7), (2, 5, 8),  # Columns
                      (0, 4, 8), (2, 4, 6)]             # Diagonals

    for condition in win_conditions:
        if board[condition[0]] == board[condition[1]] == board[condition[2]] == player:
            return True
    return False

# Function to check if the board is full (draw condition)
def check_draw(board):
    return all([spot == 'X' or spot == 'O' for spot in board])

# Function to handle player moves
def player_move(board, player):
    while True:
        try:
            move = int(input(f"Player {player}, enter your move (1-9): ")) - 1
            if board[move] not in ['X', 'O']:
                board[move] = player
                break
            else:
                print("This spot is already taken.")
        except (ValueError, IndexError):
            print("Invalid move. Please try again.")

# Main game loop
def tic_tac_toe():
    board = [str(i + 1) for i in range(9)]  # Initial board setup
    current_player = 'X'  # Starting player

    while True:
        print_board(board)  # Display the current board
        player_move(board, current_player)  # Player makes a move

        # Check for a win
        if check_winner(board, current_player):
            print_board(board)
            print(f"Player {current_player} wins!")
            break

        # Check for a draw
        if check_draw(board):
            print_board(board)
            print("It's a draw!")
            break

        # Switch player
        current_player = 'O' if current_player == 'X' else 'X'

# Start the game
tic_tac_toe()
