// Tic-tac-toe-game
//TIC-TAC-TOE GAME USING C++

#include <iostream>
#include <vector>

using namespace std;

vector<vector<char>> board = {{'1', '2', '3'}, {'4', '5', '6'}, {'7', '8', '9'}};

void displayBoard() {
  for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
      cout << board[i][j] << " ";
    }
    cout << "\n";
  }
}

void playerMove(char symbol) {
  int move;
  cout << "Enter your move (1-9): ";
  cin >> move;

  int row = (move - 1) / 3;
  int col = (move - 1) % 3;

  if (board[row][col] != 'X' && board[row][col] != 'O') {
    board[row][col] = symbol;
  } else {
    cout << "Invalid move! Try again.\n";
    playerMove(symbol);
  }
}

bool checkWin(char symbol) {
  for (int i = 0; i < 3; i++) {
    if (board[i][0] == symbol && board[i][1] == symbol && board[i][2] == symbol) {
      return true;
    }
    if (board[0][i] == symbol && board[1][i] == symbol && board[2][i] == symbol) {
      return true;
    }
  }
  if (board[0][0] == symbol && board[1][1] == symbol && board[2][2] == symbol) {
    return true;
  }
  if (board[0][2] == symbol && board[1][1] == symbol && board[2][0] == symbol) {
    return true;
  }
  return false;
}

int main() {
  int turn = 0;

  while (true) {
    displayBoard();
    playerMove((turn % 2 == 0) ? 'X' : 'O');
    if (checkWin((turn % 2 == 0) ? 'X' : 'O')) {
      displayBoard();
      cout << "Player " << ((turn % 2 == 0) ? "X" : "O") << " wins!\n";
      break;
    }
    turn++;
    if (turn == 9) {
      displayBoard();
      cout << "It's a draw!\n";
      break;
    }
  }

  return 0;
}
