horz_winner = False
vert_winner = False
diag_winner = False
unfinished_game = False
winning_tile = []

def createGame(final_board):
    print("-" * len(final_board))

    print("|", end=" ")
    for x in final_board[:3]:
        print(x , end=" ")
    print("|", end=" ")

    print("\n|", end=" ")
    for y in final_board[3:6]:
        print(y, end=" ")
    print("|", end=" ")
    print("\n|", end=" ")

    for y in final_board[6:9]:
        print(y, end=" ")
    print("|", end=" ")
    print(" ")

    print("-" * len(final_board), end=" ")

# TAKE USER INPUT AND COVERT TO STRING INDEX
def user_input_correct(user):
    global user_x
    global user_y

    try:
        user_x, user_y = [int(x) for x in user.split()]
    except ValueError:
        print("You should enter numbers!")
        return False

    if user_x > 3 or user_y > 3:
        print("Coordinates should be from 1 to 3!")
        return False


    return True

def convert_user(user_x, user_y):

    return (user_x - 1) + (3 * (3 - user_y))

def winHorizontal():
    global winning_tile, horz_winner
    win_horz_1 = (final[0] == final[1] == final[2] != " ")
    win_horz_2 = (final[3] == final[4] == final[5] != " ")
    win_horz_3 = (final[6] == final[7] == final[8] != " ")

    if win_horz_1 is True:
        horz_winner = True
        winning_tile.append(final[0])
    if win_horz_2 is True:
        horz_winner = True
        winning_tile.append(final[3])
    if win_horz_3 is True:
        horz_winner = True
        winning_tile.append(final[6])


def winVertical():
    global winning_tile, vert_winner
    win_vert_1 = (final[0] == final[3] == final[6] != " ")
    win_vert_2 = (final[1] == final[4] == final[7] != " ")
    win_vert_3 = (final[2] == final[5] == final[8] != " ")

    if win_vert_1 is True:
        vert_winner = True
        winning_tile.append(final[0])
    if win_vert_2 is True:
        vert_winner = True
        winning_tile.append(final[1])
    if win_vert_3 is True:
        vert_winner = True
        winning_tile.append(final[2])


def winDiagonal():
    global winning_tile, diag_winner
    win_diag_1 = (final[0] == final[4] == final[8] != " ")
    win_diag_2 = (final[2] == final[4] == final[6] != " ")

    if win_diag_1 is True:
        diag_winner = True
        winning_tile.append(final[0])
    if win_diag_2 is True:
        diag_winner = True
        winning_tile.append(final[2])



def validateGame():

    winHorizontal()
    winDiagonal()
    winVertical()
    

if __name__ == '__main__':
    final = list(" " * 9)
    player = ''
    x_counter = 0
    o_counter = 0

    user_x = 0
    user_y = 0

    player_x_turn = 1
    player_o_turn = 0

    #PRINT GAME
    createGame(final)


    while True:

        #GET INPUT AND CONVERT TO INDEX LOCATION and TEST USER INPUT IS CORRECT
        user = input("\nEnter the coordinates: ").upper()
        if user_input_correct(user):
            user = convert_user(user_x, user_y)
            if final[user] == 'X' or final[user] == 'O':
                print("This cell is occupied! Choose another one!")
                continue

        else:
            continue

        #SWITCHES TURNS BETWEEN PLAYERS and ADDS TO X/O COUNTER
        if player_x_turn > player_o_turn:
            player = 'X'
            player_o_turn += 2
            x_counter += 1
        elif player_o_turn > player_x_turn:
            player = 'O'
            player_x_turn += 2
            o_counter += 1


        # DISPLAY PLAYER TURN
        if final[user] == ' ':
            final[user] = player


        #TEST RESULTS AND UPDATE VALUES/BOOLEANS and REPRINT BOARD
        validateGame()
        createGame(final)


        if horz_winner and len(winning_tile) == 1:
            print("\n" + winning_tile[0] + " wins")
            break
        elif vert_winner and len(winning_tile) == 1:
            print("\n" + winning_tile[0] + " wins")
            break
        elif diag_winner and len(winning_tile) == 1:
            print("\n" + winning_tile[0] + " wins")
            break
        elif (x_counter + o_counter) == 9 and horz_winner is False and vert_winner is False and diag_winner is False:
                print('\nDraw')
                break
