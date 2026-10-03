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

## Part 12
```java
public class ClosestPointAnalyzer {

    public static void main(String[] args) {
        double[][] points = {
                {-1, 3},
                {-1, -1},
                {1, 1},
                {2, 0.5},
                {2, -1},
                {3, 3},
                {4, 2},
                {4, -0.5}
        };

        double minDistance = Double.MAX_VALUE;
        int point1Index = -1;
        int point2Index = -1;

        for (int i = 0; i < points.length; i++) {
            for (int j = i + 1; j < points.length; j++) {
                double currentDistance = distance(points[i], points[j]);

                if (currentDistance < minDistance) {
                    minDistance = currentDistance;
                    point1Index = i;
                    point2Index = j;
                }
            }
        }

        System.out.println("--- Closest Point ---");
        System.out.printf("Point 1: (%s, %s)\n", points[point1Index][0], points[point1Index][1]);
        System.out.printf("Point 2: (%s, %s)\n", points[point2Index][0], points[point2Index][1]);
        System.out.printf("Minimum Distance: %.2f\n", minDistance);
    }

    public static double distance(double[] p1, double[] p2) {
        double deltaX = p2[0] - p1[0];
        double deltaY = p2[1] - p1[1];
        return Math.sqrt((deltaX * deltaX) + (deltaY * deltaY));
    }
}
```

## Part 13-14
```java
public class ThreeDimensionalArrayExtension {

    public static void main(String[] args) {
        double[][][] scores = {
                // Student 1
                {
                        {80.0, 75.0}, // Exam 1
                        {90.0, 70.0}, // Exam 2
                        {75.0, 89.0}  // Exam 3
                },
                // Student 2
                {
                        {60.0, 65.0}, // Exam 1
                        {85.0, 95.0}, // Exam 2
                        {80.0, 85.0}  // Exam 3
                },
                // Student 3
                {
                        {75.0, 75.0}, // Exam 1
                        {80.0, 80.0}, // Exam 2
                        {65.0, 75.0}  // Exam 3
                },
                // Student 4
                {
                        {70.0, 85.0}, // Exam 1
                        {90.0, 85.0}, // Exam 2
                        {70.0, 65.0}  // Exam 3
                }
        };

        System.out.println("--- Student Total Score ---");

        for (int student = 0; student < scores.length; student++) {
            // Modified: Call the refactored method instead of nested loops here
            double totalScore = studentTotal(scores, student);
            System.out.printf("Total Score for Student %d: %.2f\n", (student + 1), totalScore);
        }
    }

    public static double studentTotal(double[][][] scores, int student) {
        double total = 0.0;

        for (int exam = 0; exam < scores[student].length; exam++) {
            for (int component = 0; component < scores[student][exam].length; component++) {
                total += scores[student][exam][component];
            }
        }

        return total;
    }
```
