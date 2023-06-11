Please help me solve a Sudoku.
This is the algorithm I want you to use:

1. I will provide you a digit to focus on.
2. Copy from the grid only the vacant cells and those that contain the digit.
3. Find the 3x3 subgrids that contain the digit. Remove the vacant cells that are in the same 3x3 subgrids as the digit.
4. Reconstruct the state from the modified subgrids.
5. Find the rows that contain the digit. Remove the vacant cells that are in the same rows as the digit.
6. Reconstruct the state from the modified rows.
7. Find the columns that contain the digits. Remove the vacant cells that are in the same columns as the digit.
8. Reconstruct the state from the modified columns.
9.  Reconstruct the detailed subgrids, identifying cells that must contain the digit.
10. Reproduce the new state of the Sudoku.
11. I will provide you with the next digit to focus on, and repeat the process until the Sudoku is solved.

## Example

This is an example Sudoku. 0 represents a vacant cell.

```
0 1 0 | 0 0 3 | 0 0 9
0 0 0 | 6 0 0 | 7 2 0 
9 7 0 | 0 0 0 | 0 0 0
- - - + - - - + - - - 
0 9 6 | 5 0 2 | 8 0 0
0 5 0 | 1 0 0 | 0 9 0 
0 0 7 | 3 6 9 | 1 4 0
- - - + - - - + - - - 
0 0 0 | 0 0 5 | 0 1 7
0 0 5 | 0 1 0 | 0 6 2
4 0 0 | 7 0 6 | 0 0 0
```

I will demonstrate the above algorithm the way I want you to do it. My demonstration will focus on the digit 2.

### Cells that are either vacant or contain a two:


```
0 . 0 | 0 0 . | 0 0 .
0 0 0 | . 0 0 | . 2 0 
. . 0 | 0 0 0 | 0 0 0
- - - + - - - + - - - 
0 . . | . 0 2 | . 0 0
0 . 0 | . 0 0 | 0 . 0 
0 0 . | . . . | . . 0
- - - + - - - + - - - 
0 0 0 | 0 0 . | 0 . .
0 0 . | 0 . 0 | 0 . 2
. 0 0 | . 0 . | 0 0 0
```

### Find the 3x3 subgrids that contain a 2, and remove their vacant cells:

Subgrid 1:

```
0 . 0
0 0 0
. . 0
```
Does not contain a 2.

Subgrid 2:

```
0 0 .
. 0 0
0 0 0
```
Does not contain a 2.

Subgrid 3:

```
0 0 .
. 2 0
0 0 0
```
Contains a 2. Without the vacant cells, it looks like this:

```
. . .
. 2 .
. . .
```

Subgrid 4:

```
0 . .
0 . 0
0 0 .
```
Does not contain a 2.

Subgrid 5:

```
. 0 2
. 0 0
. . .
```
Contains a 2. Without the vacant cells, it looks like this:

```
. . 2
. . .
. . .
```

Subgrid 6:

```
. 0 0
0 . 0
. . 0
```
Does not contain a 2.

Subgrid 7:

```
0 0 0
0 0 .
. 0 0
```
Does not contain a 2.

Subgrid 8:

```
0 0 .
0 . 0
. 0 .
```
Does not contain a 2.

Subgrid 9:

```
0 . .
0 . 2
0 0 0
```
Contains a 2. Without the vacant cells, it looks like this:

```
. . .
. . 2
. . .
```

### Reconstruct the state from the modified subgrids:

```
0 . 0 | 0 0 . | . . .
0 0 0 | . 0 0 | . 2 .
. . 0 | 0 0 0 | . . .
- - - + - - - + - - -
0 . . | . . 2 | . 0 0
0 . 0 | . . . | 0 . 0
0 0 . | . . . | . . 0
- - - + - - - + - - -
0 0 0 | 0 0 . | . . .
0 0 . | 0 . 0 | . . 2
. 0 0 | . 0 . | . . .
```

### Find the rows that contain a 2, and remove their vacant cells:

Row 1:

```
0 . 0 | 0 0 . | . . .
```
Does not contain a 2.

Row 2:

```
0 0 0 | . 0 0 | . 2 .
```
Contains a 2. Without the vacant cells, it looks like this:

```
. . . | . . . | . 2 .
```

Row 3:

```
. . 0 | 0 0 0 | . . .
```
Does not contain a 2.

Row 4:

```
0 . . | . . 2 | . 0 0
```
Contains a 2. Without the vacant cells, it looks like this:

```
. . . | . . 2 | . . .
```

Row 5:

```
0 . 0 | . . . | 0 . 0
```
Does not contain a 2.

Row 6:

```
0 0 . | . . . | . . 0
```
Does not contain a 2.

Row 7:

```
0 0 0 | 0 0 . | . . .
```
Does not contain a 2.

Row 8:

```
0 0 . | 0 . 0 | . . 2
```
Contains a 2. Without the vacant cells, it looks like this:

```
. . . | . . . | . . 2
```

Row 9:

```
. 0 0 | . 0 . | . . .
```
Does not contain a 2.

### Reconstruct the state from the modified rows:

```
0 . 0 | 0 0 . | . . .
. . . | . . . | . 2 .
. . 0 | 0 0 0 | . . .
- - - + - - - + - - -
. . . | . . 2 | . . .
0 . 0 | . . . | 0 . 0
0 0 . | . . . | . . 0
- - - + - - - + - - -
0 0 0 | 0 0 . | . . .
. . . | . . . | . . 2
. 0 0 | . 0 . | . . .
```

### Find the columns that contain a 2, and remove their vacant cells:

Column 1:

```
0
.
.
-
.
0
0
-
0
.
.
```
Does not contain a 2.

Column 2:

```
.
.
.
-
.
.
0
-
0
.
0
```
Does not contain a 2.

Column 3:

```
0
.
0
-
.
0
.
-
0
.
0
```
Does not contain a 2.

Column 4:

```
0
.
0
-
.
.
.
-
0
.
.
```
Does not contain a 2.

Column 5:

```
0
.
0
-
.
.
.
-
0
.
0
```
Does not contain a 2.

Column 6:

```
.
.
0
-
2
.
.
-
.
.
.
```
Contains a 2. Without the vacant cells, it looks like this:

```
.
.
.
-
2
.
.
-
.
.
.
```

Column 7:

```
.
.
.
-
.
0
.
-
.
.
.
```
Does not contain a 2.

Column 8:

```
.
2
.
-
.
.
.
-
.
.
.
```
Contains a 2. Without the vacant cells, it looks like this:

```
.
2
.
-
.
.
.
-
.
.
.
```

Column 9:

```
.
.
.
-
.
0
0
-
.
2
.
```
Contains a 2. Without the vacant cells, it looks like this:

```
.
.
.
-
.
.
.
-
.
2
.
```

### Reconstruct the state from the modified columns:

```
0 . 0 | 0 0 . | . . .
. . . | . . . | . 2 .
. . 0 | 0 0 . | . . .
- - - + - - - + - - -
. . . | . . 2 | . . .
0 . 0 | . . . | 0 . .
0 0 . | . . . | . . .
- - - + - - - + - - -
0 0 0 | 0 0 . | . . .
. . . | . . . | . . 2
. 0 0 | . 0 . | . . .
```

### Reconstruct the detailed subgrids, identifying cells that must contain a 2:

Subgrid 1:

```
0 . 0
. . .
. . 0
```
Has more than one viable vacant cell, so it is unmodified:

```
0 1 0
0 0 0
9 7 0
```

Subgrid 2:

```
0 0 .
. . .
0 0 .
```
Has more than one viable vacant cell, so it is unmodified:

```
0 0 3
6 0 0
0 0 0
```

Subgrid 3:

```
. . .
. 2 .
. . .
```
Already had a 2, so it is unmodified:

```
0 0 9
7 2 0
0 0 0
```

Subgrid 4:

```
. . .
0 . 0
0 0 .
```
Has more than one viable vacant cell, so it is unmodified:

```
0 9 6
0 5 0
0 0 7
```

Subgrid 5:

```
. . 2
. . .
. . .
```
Already had a 2, so it is unmodified:

```
5 0 2
1 0 0
3 6 9
```

Subgrid 6:

```
. . .
0 . .
. . .
```
Only has one viable vacant cell, so it is modified:

```
8 0 0
2 9 0
1 4 0
```

Subgrid 7:

```
0 0 0
. . .
. 0 0
```
Has more than one viable vacant cell, so it is unmodified:

```
0 0 0
0 0 5
4 0 0
```

Subgrid 8:

```
0 0 .
. . .
. 0 .
```
Has more than one viable vacant cell, so it is unmodified:

```
0 0 5
0 1 0
7 0 6
```

Subgrid 9:

```
. . .
. . 2
. . .
```
Already had a 2, so it is unmodified:

```
0 1 7
0 6 2
0 0 0
```

### New state of the Sudoku:

```
0 1 0 | 0 0 3 | 0 0 9
0 0 0 | 6 0 0 | 7 2 0 
9 7 0 | 0 0 0 | 0 0 0
- - - + - - - + - - - 
0 9 6 | 5 0 2 | 8 0 0
0 5 0 | 1 0 0 | 2 9 0 
0 0 7 | 3 6 9 | 1 4 0
- - - + - - - + - - - 
0 0 0 | 0 0 5 | 0 1 7
0 0 5 | 0 1 0 | 0 6 2
4 0 0 | 7 0 6 | 0 0 0
```

At this point I would give you a new digit to focus on, and you would repeat the process.

Please use the algorithm above to solve the Sudoku below. The first digit to focus on is 1.

```
0 5 7 | 2 0 0 | 0 0 9
0 0 4 | 0 1 6 | 8 0 0 
3 8 1 | 4 0 0 | 7 0 6
- - - + - - - + - - -
0 0 3 | 0 0 0 | 6 0 7
0 0 9 | 0 0 7 | 4 5 8
0 0 0 | 8 6 0 | 0 0 0
- - - + - - - + - - -
0 0 0 | 0 4 0 | 0 0 0
7 0 6 | 0 0 1 | 0 0 4
1 4 2 | 9 0 0 | 5 0 3
```
