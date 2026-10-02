# Assignment 4

## Part 1-11
```java
public class GridValidator {

    public static void main(String[] args) {
        // Grid has to be a Sudoku grid in order to be valid in all cases.
        int[][] testGrid = {
                {5, 3, 4, 6, 7, 8, 9, 1, 2}, // row 0
                {6, 7, 2, 1, 9, 5, 3, 4, 8}, // row 1
                {1, 9, 8, 3, 4, 2, 5, 6, 7}, // row 2
                {8, 5, 9, 7, 6, 1, 4, 2, 3}, // row 3
                {4, 2, 6, 8, 5, 3, 7, 9, 1}, // row 4
                {7, 1, 3, 9, 2, 4, 8, 5, 6}, // row 5
                {9, 6, 1, 5, 3, 7, 2, 8, 4}, // row 6
                {2, 8, 7, 4, 1, 9, 6, 3, 5}, // row 7
                {3, 4, 5, 2, 8, 6, 1, 7, 9}  // row 8
        };

        System.out.println("--- Starting Grid Validation Engine ---");
        boolean finalResult = isValidGrid(testGrid);
        System.out.println("Overall Grid Validity: " + finalResult);
    }

    public static boolean isValidGrid(int[][] grid) {
        if (grid == null || grid.length != 9) {
            System.out.println("Invalid grid dimensions: Must have exactly 9 rows.");
            return false;
        }
        for (int row = 0; row < grid.length; row++) {
            if (grid[row].length != 9) {
                System.out.println("Invalid grid dimensions: Row " + row + " does not have 9 columns.");
                return false;
            }
        }

        if (!valuesInRange(grid)) {
            return false;
        }

        if (!areRowsValid(grid)) {
            return false;
        }

        if (!areColumnsValid(grid)) {
            return false;
        }

        if (!areRegionsValid(grid)) {
            return false;
        }

        System.out.println("Grid is entirely valid!");
        return true;
    }

    public static boolean valuesInRange(int[][] grid) {
        for (int row = 0; row < grid.length; row++) {
            for (int col = 0; col < grid[row].length; col++) {
                if (grid[row][col] < 1 || grid[row][col] > 9) {
                    System.out.println("Invalid value at row " + row + ", column " + col);
                    return false;
                }
            }
        }
        return true;
    }

    public static boolean isRowValid(int[][] grid, int row) {
        boolean[] seen = new boolean[10];
        for (int col = 0; col < grid[row].length; col++) {
            int value = grid[row][col];
            if (seen[value]) {
                System.out.println("Duplicate detected in row " + row);
                return false;
            }
            seen[value] = true;
        }
        return true;
    }

    public static boolean areRowsValid(int[][] grid) {
        for (int row = 0; row < grid.length; row++) {
            if (!isRowValid(grid, row)) {
                return false;
            }
        }
        return true;
    }

    public static boolean isColumnValid(int[][] grid, int column) {
        boolean[] seen = new boolean[10];
        for (int row = 0; row < grid.length; row++) {
            int value = grid[row][column];
            if (seen[value]) {
                System.out.println("Duplicate detected in column " + column);
                return false;
            }
            seen[value] = true;
        }
        return true;
    }

    public static boolean areColumnsValid(int[][] grid) {
        for (int col = 0; col < grid.length; col++) {
            if (!isColumnValid(grid, col)) {
                return false;
            }
        }
        return true;
    }

    public static boolean isRegionValid(int[][] grid, int startRow, int startColumn) {
        boolean[] seen = new boolean[10];
        for (int r = startRow; r < startRow + 3; r++) {
            for (int c = startColumn; c < startColumn + 3; c++) {
                int value = grid[r][c];
                if (seen[value]) {
                    System.out.println("Invalid 3x3 region beginning at row " + startRow + ", column " + startColumn);
                    return false;
                }
                seen[value] = true;
            }
        }
        return true;
    }

    public static boolean areRegionsValid(int[][] grid) {
        for (int startRow = 0; startRow < grid.length; startRow += 3) {
            for (int startColumn = 0; startColumn < grid[startRow].length; startColumn += 3) {
                if (!isRegionValid(grid, startRow, startColumn)) {
                    return false;
                }
            }
        }
        return true;
    }
}
```

## Part 12-
