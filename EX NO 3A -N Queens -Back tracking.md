
# EX 3A N Queens Problem - Backtracking Approach.
## AIM:
To Write a Java program for N queens using backtracking approach.
You are given an integer N. For a given N x N chessboard, find a way to place 'N' queens such that no queen can attack any other queen on the chessboard.
A queen can be attacked when it lies in the same row, column, or the same diagonal as any of the other queens. You have to print one such configuration.
Chess Board
<img width="241" height="209" alt="image" src="https://github.com/user-attachments/assets/96aacb61-4f34-423f-b324-5e34454e42b8" />


Note :

Get the input from the user for N . The value of N must be from 1 to 4

If solution exists Print a binary matrix as output that has 1s for the cells where queens are placed

If there is no solution to the problem  print  "Solution does not exist"

## Algorithm

1. Start the program and read the value of `N` (size of the chessboard) from the user.
2. Initialize an `N x N` board filled with zeros to represent an empty chessboard.
3. Use the `isSafe()` function to check if a queen can be safely placed at a given position (no other queen in the same row, column, or diagonal).
4. Use recursion (`solveNQUtil()`) to try placing queens column by column, backtracking if a conflict occurs.
5. If a solution is found, print the board with `1`s marking queen positions; otherwise, print **"Solution does not exist"**.


## Program:
```
/*
Program to implement Reverse a String
Developed by: Vignesh M
Register Number: 212223240176
*/
import java.util.Scanner;

public class NQueens {
    static int N;

    
    static void printSolution(int[][] board) {
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                System.out.print(board[i][j] + " ");
            }
            System.out.println();
        }
    }

    
    static boolean isSafe(int[][] board, int row, int col) {
        // Check left side of current row
        for (int i = 0; i < col; i++)
            if (board[row][i] == 1)
                return false;

       
        for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
            if (board[i][j] == 1)
                return false;

        
        for (int i = row, j = col; i < N && j >= 0; i++, j--)
            if (board[i][j] == 1)
                return false;

        return true;
    }

    // Recursive utility function to solve N-Queens
    static boolean solveNQUtil(int[][] board, int col) {
        //Add your code Here
        if(col>=N)
        {
            return true;
        }
        
        for (int i=0;i<N;i++)
        {
            if(isSafe(board, i,col))
            {
                board[i][col]=1;
            
            if(solveNQUtil(board,col+1))
            
               
                return true;
                board[i][col]=0;
            }
        }
        return false;
    }

    
    static boolean solveNQ() {
        int[][] board = new int[N][N];

        if (!solveNQUtil(board, 0)) {
            System.out.println("Solution does not exist");
            return false;
        }

        printSolution(board);
        return true;
    }

   
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        N = scanner.nextInt(); // Accept board size
        solveNQ();
    }
}

```

## Output:
<img width="633" height="261" alt="image" src="https://github.com/user-attachments/assets/3c079e15-3140-4737-866e-414cce15e0cd" />



## Result:
The program successfully implemented and the ouput is verified. 
