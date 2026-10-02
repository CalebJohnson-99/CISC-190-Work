# Assignment 3
## Part 1-8
```java
import java.util.Scanner;

public class StoreSalesAnalyzer {

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        double[][] sales = new double[4][7];

        System.out.println("--- Enter Sales Data ---");

        for (int store = 0; store < sales.length; store++) {
            for (int day = 0; day < sales[store].length; day++) {
                double value = -1;

                while (value < 0) {
                    System.out.print("Enter sales for Store " + (store + 1) + ", Day " + (day + 1) + ": ");
                    if (input.hasNextDouble()) {
                        value = input.nextDouble();
                        if (value < 0) {
                            System.out.println("Invalid input. Sales cannot be negative. Try again.");
                        }
                    } else {
                        System.out.println("Invalid input. Please enter a valid number.");
                        input.next();
                    }
                }
                sales[store][day] = value;
            }
            System.out.println();
        }

        printSales(sales);
        System.out.println();
        printSummaryReport(sales);
        input.close();
    }

    public static void printSales(double[][] sales) {
        System.out.println("--- Weekly Store Sales Table ---");
        System.out.print("         ");
        for (int day = 0; day < sales[0].length; day++) {
            System.out.printf("Day %d     ", (day + 1));
        }

        for (int store = 0; store < sales.length; store++) {
            System.out.printf("Store %d: ", (store + 1));
            for (int day = 0; day < sales[store].length; day++) {
                System.out.printf("$%-8.2f", sales[store][day]);
            }
            System.out.println();
        }
    }

    public static double totalSales(double[][] sales) {
        double total = 0.0;
        for (int store = 0; store < sales.length; store++) {
            for (int day = 0; day < sales[store].length; day++) {
                total += sales[store][day];
            }
        }
        return total;
    }

    public static double rowTotal(double[][] sales, int row) {
        double total = 0.0;
        for (int day = 0; day < sales[row].length; day++) {
            total += sales[row][day];
        }
        return total;
    }

    public static double columnTotal(double[][] sales, int column) {
        double total = 0.0;
        for (int store = 0; store < sales.length; store++) {
            total += sales[store][column];
        }
        return total;
    }

    public static int bestStore(double[][] sales) {
        int bestRowIndex = 0;
        double maxRowTotal = rowTotal(sales, 0);

        for (int store = 1; store < sales.length; store++) {
            double currentTotal = rowTotal(sales, store);
            if (currentTotal > maxRowTotal) {
                maxRowTotal = currentTotal;
                bestRowIndex = store;
            }
        }
        return bestRowIndex;
    }

    public static double findMaximum(double[][] sales) {
        double maxVal = sales[0][0];
        for (int store = 0; store < sales.length; store++) {
            for (int day = 0; day < sales[store].length; day++) {
                if (sales[store][day] > maxVal) {
                    maxVal = sales[store][day];
                }
            }
        }
        return maxVal;
    }

    public static int[] findMaximumPosition(double[][] sales) {
        double maxVal = sales[0][0];
        int[] position = new int[2]; // index 0 -> row, index 1 -> column

        for (int store = 0; store < sales.length; store++) {
            for (int day = 0; day < sales[store].length; day++) {
                if (sales[store][day] > maxVal) {
                    maxVal = sales[store][day];
                    position[0] = store;
                    position[1] = day;
                }
            }
        }
        return position;
    }

    public static void printSummaryReport(double[][] sales) {
        System.out.println("--- Summary Report ---");

        double total = totalSales(sales);
        System.out.printf("Overall Sales: $%.2f\n", total);

        int totalEntries = sales.length * sales[0].length;
        double average = total / totalEntries;
        System.out.printf("Average Sale Per Entry: $%.2f\n", average);

        System.out.println("Store Totals:");
        for (int store = 0; store < sales.length; store++) {
            System.out.printf("  Store %d: $%.2f\n", (store + 1), rowTotal(sales, store));
        }

        System.out.println("Daily Totals:");
        for (int day = 0; day < sales[0].length; day++) {
            System.out.printf("  Day %d: $%.2f\n", (day + 1), columnTotal(sales, day));
        }

        int bestStoreIndex = bestStore(sales);
        System.out.printf("Best-Performing Store: Store %d (Total: $%.2f)\n", (bestStoreIndex + 1), rowTotal(sales, bestStoreIndex));

        double maxSale = findMaximum(sales);
        int[] maxPos = findMaximumPosition(sales);
        System.out.printf("Largest Individual Sale:  $%.2f (Store %d, Day %d)\n", maxSale, (maxPos[0] + 1), (maxPos[1] + 1));
    }
}
```

## Part 9
Using array[row].length is important for ragged arrays since each row can have a different amount of columns, and array[row].length focuses on the individual rows and finds the # of columns for each row.

```java
import java.util.Scanner;

public class StoreSalesAnalyzer {

    public static void main(String[] args) {
        double[][] irregularSales = {
                {120.0, 145.0, 160.0},
                {90.0, 105.0},
                {200.0, 210.0, 220.0, 230.0},
                {75.0}
        };

        printSales(irregularSales);
        System.out.println();
        printSummaryReport(irregularSales);
    }

    public static void printSales(double[][] sales) {
        System.out.println("--- Weekly Store Sales Table ---");
        System.out.print("         ");

        int maxDays = 0;
        for (int store = 0; store < sales.length; store++) {
            if (sales[store].length > maxDays) {
                maxDays = sales[store].length;
            }
        }

        for (int day = 0; day < maxDays; day++) {
            System.out.printf("Day %d     ", (day + 1));
        }
        System.out.println();

        for (int store = 0; store < sales.length; store++) {
            System.out.printf("Store %d: ", (store + 1));
            for (int day = 0; day < sales[store].length; day++) {
                System.out.printf("$%-8.2f", sales[store][day]);
            }
            System.out.println();
        }
    }

    public static double totalSales(double[][] sales) {
        double total = 0.0;
        for (int store = 0; store < sales.length; store++) {
            for (int day = 0; day < sales[store].length; day++) {
                total += sales[store][day];
            }
        }
        return total;
    }

    public static double rowTotal(double[][] sales, int row) {
        double total = 0.0;
        for (int day = 0; day < sales[row].length; day++) {
            total += sales[row][day];
        }
        return total;
    }

    public static double columnTotal(double[][] sales, int column) {
        double total = 0.0;
        for (int store = 0; store < sales.length; store++) {
            if (column < sales[store].length) {
                total += sales[store][column];
            }
        }
        return total;
    }

    public static int bestStore(double[][] sales) {
        int bestRowIndex = 0;
        double maxRowTotal = rowTotal(sales, 0);

        for (int store = 1; store < sales.length; store++) {
            double currentTotal = rowTotal(sales, store);
            if (currentTotal > maxRowTotal) {
                maxRowTotal = currentTotal;
                bestRowIndex = store;
            }
        }
        return bestRowIndex;
    }

    public static double findMaximum(double[][] sales) {
        double maxVal = sales[0][0];
        for (int store = 0; store < sales.length; store++) {
            for (int day = 0; day < sales[store].length; day++) {
                if (sales[store][day] > maxVal) {
                    maxVal = sales[store][day];
                }
            }
        }
        return maxVal;
    }

    public static int[] findMaximumPosition(double[][] sales) {
        double maxVal = sales[0][0];
        int[] position = new int[2];

        for (int store = 0; store < sales.length; store++) {
            for (int day = 0; day < sales[store].length; day++) {
                if (sales[store][day] > maxVal) {
                    maxVal = sales[store][day];
                    position[0] = store;
                    position[1] = day;
                }
            }
        }
        return position;
    }

    public static void printSummaryReport(double[][] sales) {
        System.out.println("--- Summary Report ---");

        double total = totalSales(sales);
        System.out.printf("Overall Sales: $%.2f\n", total);

        int totalEntries = 0;
        for (int store = 0; store < sales.length; store++) {
            totalEntries += sales[store].length;
        }

        double average = total / totalEntries;
        System.out.printf("Average Sale Per Entry: $%.2f\n", average);

        System.out.println("Store Totals:");
        for (int store = 0; store < sales.length; store++) {
            System.out.printf("  Store %d: $%.2f\n", (store + 1), rowTotal(sales, store));
        }

        int maxDays = 0;
        for (int store = 0; store < sales.length; store++) {
            if (sales[store].length > maxDays) {
                maxDays = sales[store].length;
            }
        }

        System.out.println("Daily Totals:");
        for (int day = 0; day < maxDays; day++) {
            System.out.printf("  Day %d: $%.2f\n", (day + 1), columnTotal(sales, day));
        }

        int bestStoreIndex = bestStore(sales);
        System.out.printf("Best-Performing Store: Store %d (Total: $%.2f)\n", (bestStoreIndex + 1), rowTotal(sales, bestStoreIndex));

        double maxSale = findMaximum(sales);
        int[] maxPos = findMaximumPosition(sales);
        System.out.printf("Largest Individual Sale:  $%.2f (Store %d, Day %d)\n", maxSale, (maxPos[0] + 1), (maxPos[1] + 1));
    }
}
```
## Part 10
1. The inner loop assumes the matrix is a square.
2. if there are ragged arrays it could cause the loop to fail. if there are more rows than columns it will try to access columns that do not exist, and if there are more columns than rows it will ignore the extra columns.
3. ```java
   for (int row = 0; row < sales.length; row++) {
    for (int column = 0; column < sales[row].length; column++) {
        System.out.println(sales[row][column]);
    }
}
```
