
# Experiment No. 8 – N-Queens Problem Using Backtracking

**Created By:** Krish Mhatre

## C Program

```c
#include <stdio.h>
#include <stdlib.h>

int n, pos[20], count = 0;

int safe(int row, int col) {
    for(int i = 0; i < row; i++) {
        if(pos[i] == col || abs(pos[i] - col) == abs(i - row))
            return 0;
    }
    return 1;
}

void solve(int row) {
    if(row == n) {
        printf("\nSolution %d:\n", ++count);

        for(int i = 0; i < n; i++) {
            for(int j = 0; j < n; j++)
                printf("%c ", pos[i] == j ? 'Q' : '.');
            printf("\n");
        }
        return;
    }

    for(int col = 0; col < n; col++) {
        if(safe(row, col)) {
            pos[row] = col;
            solve(row + 1);
        }
    }
}

int main() {
    printf("Enter number of queens: ");
    if(scanf("%d", &n) != 1 || n < 1 || n > 10) {
        printf("Enter a value from 1 to 10.\n");
        return 1;
    }

    solve(0);

    if(count == 0)
        printf("No solution found.\n");

    return 0;
}
```

## Output

```text
PS C:\AOA> gcc queen.c -o queen
PS C:\AOA> .\queen.exe

Enter number of queens: 4

Solution 1:
. Q . .
. . . Q
Q . . .
. . Q .

Solution 2:
. . Q .
Q . . .
. . . Q
. Q . .
```

## Aim
To implement the N-Queens Problem using Backtracking in C.

## Theory
The N-Queens Problem is solved using the Backtracking technique.

The goal is to place N queens on an N×N chessboard so that no two queens attack each other.

No two queens should be in the same row, column, or diagonal.

## Algorithm
1. Start the program.
2. Enter the number of queens.
3. Place a queen in a safe position.
4. Check rows, columns, and diagonals.
5. If the position is safe, place the queen.
6. If no safe position exists, backtrack.
7. Display all possible solutions.

## How to Run

**Step 1:** Save as `queen.c`.

**Step 2:** Compile:

```bash
gcc queen.c -o queen
```

**Step 3:** Run:

```powershell
.\queen.exe
```

## Time Complexity

- Worst Case: O(N!)
- Space Complexity: O(N)

## Conclusion
Successfully implemented the N-Queens Problem using Backtracking in C to find valid queen arrangements.
