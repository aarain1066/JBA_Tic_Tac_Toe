x_counter_and_winner = [0, False]
o_counter_and_winner = [0, False]
is_x_turn = True

def show_gameboard():
    print("---------")
    print(f"| {moves[0]} {moves[1]} {moves[2]} |")
    print(f"| {moves[3]} {moves[4]} {moves[5]} |")
    print(f"| {moves[6]} {moves[7]} {moves[8]} |")
    print("---------")


# def impossible_or_not_finished_check(moves):
"""Effectively not needed anymore"""
#     global x_counter_and_winner
#     global o_counter_and_winner
#     global is_game_valid
#     for char in range(len(moves)):
#         if moves[char] == "X":
#             x_counter_and_winner[0] += 1
#         elif moves[char] == "O":
#             o_counter_and_winner[0] += 1
#     if abs(x_counter_and_winner[0] - o_counter_and_winner[0]) >= 2:
#         is_game_valid = False
#     row_check(moves)
#     col_check(moves)
#     diag_check(moves)
#     if x_counter_and_winner[1] == True and o_counter_and_winner[1] == True:
#         is_game_valid = False
#     elif x_counter_and_winner[0] + o_counter_and_winner[0] < 9 and abs(x_counter_and_winner[0] - o_counter_and_winner[0]) < 2:
#         if x_counter_and_winner[1] == False and o_counter_and_winner[1] == False:
#             is_game_valid = False
#     return is_game_valid

       
def row_check(moves):
    """
    This function will take in `moves` as a string. This function will iterate through the string, searching
    for a pattern match that would correspond to a row-win. Note that the range logic starts at 0, then every
    third element.
    
    So the first iteration will be moves[0] + moves[0 + 1] + moves[0 + 2] (row 1)
    the second iteration will be moves[3] + moves[3 + 1] + moves[3 + 2] (row 2) and so on
    If any pattern is matched, return True for that player's winner array.
    """
    global x_counter_and_winner
    global o_counter_and_winner
    for row_elem in range(0, len(moves) - 1, 3):
        if moves[row_elem] + moves[row_elem + 1] + moves[row_elem + 2] == "XXX":
            x_counter_and_winner[1] = True
        elif moves[row_elem] + moves[row_elem + 1] + moves[row_elem + 2] == "OOO":
            o_counter_and_winner[1] = True
           
        
def col_check(moves):
    """
    This function will take in `moves` as a string. This function will iterate through the string, searching
    for a pattern match that would correspond to a column-win. Note that the range logic starts at 0, and only goes 
    up to the 4th element.
    
    So the first iteration will be moves[0] + moves[0 + 3] + moves[0 + 6] (col 1)
    the second iteration will be moves[1] + moves[1 + 3] + moves[1 + 6] (col 2) and so on
    If any pattern is matched, return True for that player's winner array.
    """
    global x_counter_and_winner
    global o_counter_and_winner
    for col_elem in range(0, len(moves[:3])):
        if moves[col_elem] + moves[col_elem + 3] + moves[col_elem + 6] == "XXX":
            x_counter_and_winner[1] = True
        elif moves[col_elem] + moves[col_elem + 3] + moves[col_elem + 6] == "OOO":
            o_counter_and_winner[1] = True
       
    
def diag_check(moves):
    """
    This function will take in `moves` as a string. This function will iterate through the string, searching
    for a pattern match that would correspond to a diagonal-win. The way the logic is built here, makes this check 
    independent of the order the array is read in. If there is a pattern match, return true for that corresponding 
    player array
    """
    global x_counter_and_winner
    global o_counter_and_winner
    if moves[0] + moves[4] + moves[8] == "XXX" or moves[2] + moves[4] + moves[6] == "XXX":
        x_counter_and_winner[1] = True
    elif moves[0] + moves[4] + moves[8] == "OOO" or moves[2] + moves[4] + moves[6] == "OOO":
        o_counter_and_winner[1] = True
        
        
def game_play():
    """
    Create an infinite loop (for optimal logic) where you first try to convert the player's chice into type int.
    If the conversion can't happen for either value, then prompt the user to enter integers. Repeat until the 
    user does so. 
    
    A step down in the logic does performs a similar check where we care to see if the player's choice, while 
    successfully being an int, is wihtin the boundires of the game board. 
    
    We then go on to verify that the spot the user has chosen, once input is verified, is not taken up by a piece already
    
    Go on to place the correspinding player's piece down and update the counter and turn values. The counter value
    Is required here to keep track of a draw scenario in later logic. The turn value helps to switch which piece is laid
    down.
    
    Perform all of the gameplay checks to see if there is a winner, if so, print that player wins and break the loop. 
    Else, go ahead and print the board, and restart the process until there is a winner or a draw.
    """
    global moves
    global is_x_turn
    while True:
            try:
                player_move = input("Enter the coordinates: ").split()
                for index,choice in enumerate(player_move, 0):
                    player_move[index] = int(choice)
            except ValueError:
                print("You should enter numbers!")
                continue
            # Is there a way to optimize this below code? using continue in a for loop for each element in
            # the `player_move` list doesn't go back to the while loop
            if player_move[0] < 1 or player_move[0] > 3:
                print("Coordinates should be from 1 to 3!")
                continue
            elif player_move[1] < 1 or player_move[1] > 3:
                print("Coordinates should be from 1 to 3!")
                continue
            if moves[(((player_move[0] - 1) * 3) + (player_move[1] + 2)) - 3] != " ":
                print("This cell is occupied! Choose another one!")
                continue
            else:
                if is_x_turn == True:
                # messy, consider using a loop to create a new string with the "X"
                    moves = moves[:(((player_move[0] - 1) * 3) + (player_move[1] + 2)) - 3] + "X" + moves[(((player_move[0] - 1) * 3) + (player_move[1] + 2)) - 2:]
                    x_counter_and_winner[0] += 1
                    is_x_turn = False
                else:
                    moves = moves[:(((player_move[0] - 1) * 3) + (player_move[1] + 2)) - 3] + "O" + moves[(((player_move[0] - 1) * 3) + (player_move[1] + 2)) - 2:]
                    o_counter_and_winner[0] += 1
                    is_x_turn = True
                # I tried setting this to equal board, so I don't repeat all of this, but board was not updating
                # with the moves. Look intp this
            row_check(moves)
            col_check(moves)
            diag_check(moves)
            if x_counter_and_winner[1] == True or o_counter_and_winner[1] == True:
                if x_counter_and_winner[1] == True:
                    show_gameboard()
                    print("X wins")
                    break
                else:
                    show_gameboard()
                    print("O wins")
                    break
            else:
                show_gameboard()
                break


moves = "         "
show_gameboard()

while x_counter_and_winner[1] == False and o_counter_and_winner[1] == False:
    game_play()
    if x_counter_and_winner[0] + o_counter_and_winner[0] == 9:
        if x_counter_and_winner[1] == False and o_counter_and_winner[1] == False:
            print("Draw")
            break
