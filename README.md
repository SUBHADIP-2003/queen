#include <stdio.h>
#include <stdbool.h>

#define N 8  // Change this to solve for different board sizes

int board[N];

bool isSafe(int row, int col) {
    for (int i = 0; i < row; i++) {
        if (board[i] == col || 
            board[i] - i == col - row || 
            board[i] + i == col + row)
            return false;
    }
    return true;
}

void printSolution() {
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            if (board[i] == j)
                printf("Q ");
            else
                printf(". ");
        }
        printf("\n");
    }
    printf("\n");
}

void solve(int row) {
    if (row == N) {
        printSolution();
        return;
    }

    for (int col = 0; col < N; col++) {
        if (isSafe(row, col)) {
            board[row] = col;
            solve(row + 1);
        }
    }
}

int main() {
    solve(0);
    return 0;
}
