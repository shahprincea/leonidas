---
title: "Tic Tac Toe isValid"
tags: [matrix]
---

## Find winner in tic tac toe game 

Idea here is to use +1 for X and -1 for 0. Also, we will keep track of row sum, column sum and two diagonals sum in an array. 

- <strong>Algo</strong> : o(n^2) 
- <strong>Time complexity</strong> : O(n) since you r storing stats of rows, cols and diagonals. 
- <strong>Space Complexity</strong> : O(n) 



```java
public static boolean validTicTacToe(String[] board) {
        int n = board[0].length();
        int[] rowCount = new int[n];
        int[] colCount = new int[n];
        int[] diagonals = new int[2];

        int xCount  = 0;
        int oCount = 0;
        int rowIndex = 0;
        for(String row : board) {
            for(int col = 0; col < n; col++) {
                int box = row.charAt(col);
                if(box == ' ')
                    continue;
                else if(box == 'X') {
                    rowCount[rowIndex]++;
                    if(rowIndex == col) {
                        diagonals[0]++;
                    } else if(n - 1 - rowIndex  == col) {
                        diagonals[1]++;
                    }
                    xCount++;
                } else if(box == 'O') {
                    colCount[col]--;
                    if(rowIndex == col) {
                        diagonals[0]--;
                    } else if(n - 1 - rowIndex  == col) {
                        diagonals[1]--;
                    }
                    oCount++;
                }
            }
            rowIndex++;
        }
        for(int r : rowCount)
            if(Math.abs(r) == 3)
                return true;

        for(int c : colCount)
            if(Math.abs(c) == 3)
                return true;

        if(Math.abs(diagonals[0]) == 3 || Math.abs(diagonals[1]) == 3 )
            return true;

        return false;
    }
```