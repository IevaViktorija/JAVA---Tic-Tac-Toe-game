# JAVA---Tic-Tac-Toe-game
Tic, Tac Toe game for 2 players
```java
import java.util.Scanner;

public class TicTacToe {
    char[][] board = new char[3][3];
    char currentPlayer = 'X';
    
    public TicTacToe() {
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                board[i][j] = ' ';
            }
        }
    }

    public void printBoard() {
        
        System.out.println("  1 2 3 ");
        for (int i = 0; i < 3; i++) {
            System.out.print(i + 1 + " ");
            for (int j = 0; j < 3; j++) {
                System.out.print(board[i][j] + " ");
            }
            System.out.println();
        }
    }

    public void makeMove(int row, int col) {
        if (row >= 1 && row <= 3 && col >= 1 && col <= 3 && board[row - 1][col - 1] == ' ') {
            board[row - 1][col - 1] = currentPlayer;
            if (checkWin()) {
                System.out.println("Player " + currentPlayer + " wins. Congratulations!");
                printBoard();
                System.exit(0);
            }
            if (currentPlayer == 'X') {
                currentPlayer = 'O';
            } else {
                currentPlayer = 'X';
            }
        } else {
            System.out.println("Invalid move. Try again.");
        }
    }

    public boolean checkWin() {
        for (int i = 0; i < 3; i++) {
            if (board[i][0] != ' ' && board[i][0] == board[i][1] && board[i][1] == board[i][2]) {
                return true;
            }
            if (board[0][i] != ' ' && board[0][i] == board[1][i] && board[1][i] == board[2][i]) {
                return true;
            }
        }
        if (board[0][0] != ' ' && board[0][0] == board[1][1] && board[1][1] == board[2][2]) {
            return true;
        }
        if (board[0][2] != ' ' && board[0][2] == board[1][1] && board[1][1] == board[2][0]) {
            return true;
        }
        return false;
    }

    public static void main(String[] args) {
        System.out.println("Let's play Tic, Tac, Toe game! One, two, three... START!");
        TicTacToe game = new TicTacToe();
        Scanner scanner = new Scanner(System.in);
        while (true) {
            game.printBoard();
            System.out.print("Player " + game.currentPlayer + ", please enter your move (row column): ");
            int row = scanner.nextInt();
            int col = scanner.nextInt();
            game.makeMove(row, col);
        }
    }
}
```
