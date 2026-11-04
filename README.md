
# Experiment No. 8 – N-Queens Using Backtracking

**Created By:** Krish Mhatre

## C Program

```c
#include <stdio.h>
#include <stdlib.h>

int n, pos[20], count = 0;

int safe(int row, int col) {
    for(int i = 0; i < row; i++) {
        if(pos[i] == col ||
           abs(pos[i] - col) == abs(i - row))
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
    scanf("%d", &n);

    if(n < 1 || n > 10) {
        printf("Invalid number of queens.\n");
        return 1;
    }

    solve(0);

    if(count == 0)
        printf("No solution found.\n");

    return 0;
}
```

## Terminal Input (Copy and Paste)

```text
4
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
The N-Queens Problem involves placing N queens on an N×N chessboard so that no two queens attack each other.

Backtracking is used to try possible positions and remove a queen when a conflict occurs.

## Algorithm
1. Enter the number of queens.
2. Place a queen in a safe position.
3. Check columns and diagonals.
4. If safe, move to the next row.
5. If not safe, backtrack.
6. Display all valid solutions.

## How to Run

Save as `queen.c`.

Compile:

```bash
gcc queen.c -o queen
```

Run:

```powershell
.\queen.exe
```

Paste the input from the Terminal Input section.

## Time Complexity

- Time Complexity: O(N!) (commonly quoted search bound)
- Auxiliary Space Complexity: O(N)

## Conclusion
Successfully implemented the N-Queens Problem using Backtracking in C.
