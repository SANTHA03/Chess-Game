#include <iostream>
#include <vector>
#include <string>

class ChessGame {
private:
    std::vector<std::vector<char>> board;

public:
    ChessGame() {
        // Initialize the board with empty spaces
        board.resize(8, std::vector<char>(8, '.'));
        
        // Setup pieces using simple characters
        // Black pieces
        std::string black_pawns(8, 'p');
        std::string black_pieces = "rnbqkbnr";
        // White pieces
        std::string white_pawns(8, 'P');
        std::string white_pieces = "RNBQKBNR";

        // Place black pieces
        for (int i = 0; i < 8; ++i) {
            board[0][i] = black_pieces[i];
            board[1][i] = black_pawns[i];
        }

        // Place white pieces
        for (int i = 0; i < 8; ++i) {
            board[7][i] = white_pieces[i];
            board[6][i] = white_pawns[i];
        }
    }

    void printBoard() {
        for (int i = 0; i < 8; ++i) {
            for (int j = 0; j < 8; ++j) {
                std::cout << board[i][j] << " ";
            }
            std::cout << "\n";
        }
    }

    void movePiece(int startRow, int startCol, int endRow, int endCol) {
        // Simple move validation
        if (board[startRow][startCol] != '.' && board[endRow][endCol] == '.') {
            board[endRow][endCol] = board[startRow][startCol];
            board[startRow][startCol] = '.';
        } else {
            std::cout << "Invalid move!\n";
        }
    }
};

int main() {
    ChessGame game;
    game.printBoard();
    
    int startRow, startCol, endRow, endCol;
    
    while (true) {
        std::cout << "Enter move (startRow startCol endRow endCol): ";
        std::cin >> startRow >> startCol >> endRow >> endCol;
        
        game.movePiece(startRow, startCol, endRow, endCol);
        game.printBoard();
    }

    return 0;
}
