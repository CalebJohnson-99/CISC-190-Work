# Assignment 2
```java
import java.util.Arrays;
import java.util.Scanner;

public class ArrayAlgorithmToolkit {

    public static void main(String[] args) {
        int size = 20;
        int min = 0;
        int max = 100;

        if (args.length > 0) {
            try {
                int inputSize = Integer.parseInt(args[0]);
                if (inputSize > 0) {
                    size = inputSize;
                }
            } catch (NumberFormatException e) {
            }
        }

        int[] myData = generateData(size, min, max);

        System.out.println("\n Automated Module Test");

        System.out.println("\nTest: Reverse");
        int[] reversed = reverse(myData);
        System.out.println("Original: " + Arrays.toString(myData));
        System.out.println("Reversed: " + Arrays.toString(reversed));

        System.out.println("\nTest: Reference Experiment]");
        System.out.println("Before Swap: " + Arrays.toString(myData));
        swapFirstTwo(myData);
        System.out.println("After Swap:  " + Arrays.toString(myData));

        System.out.println("\nTest: Variable-Length Arguments");
        System.out.println("average(4, 8, 12) -> " + average(4, 8, 12));
        System.out.println("average(10, 20, 30, 40, 50) -> " + average(10, 20, 30, 40, 50));

        System.out.println("\nTest: Duplicate Analysis");
        reportDuplicates(myData);

        runMenu(myData, min, max);
    }

    public static void runMenu(int[] data, int min, int max) {
        Scanner scanner = new Scanner(System.in);
        boolean running = true;

        while (running) {
            System.out.println("\n--- Array Algorithm Toolkit Menu ---");
            System.out.println("1. Display data");
            System.out.println("2. Reverse data");
            System.out.println("3. Sort using selection sort");
            System.out.println("4. Search using linear search");
            System.out.println("5. Search using binary search");
            System.out.println("6. Shuffle data");
            System.out.println("7. Regenerate data");
            System.out.println("8. Run Duplicate Analysis Report");
            System.out.println("0. Exit");
            System.out.print("Enter your choice: ");

            int choice = scanner.hasNextInt() ? scanner.nextInt() : -1;
            if (choice == -1) {
                scanner.next(); // Clear invalid scanner buffer token
            }

            switch (choice) {
                case 1:
                    System.out.print("Current Array Data: ");
                    printArray(data);
                    break;
                case 2:
                    data = reverse(data);
                    System.out.println("Reversed Array Data: ");
                    printArray(data);
                    break;
                case 3:
                    selectionSort(data);
                    System.out.println("Custom selection sort.");
                    printArray(data);
                    break;
                case 4:
                    System.out.print("Enter search key: ");
                    int linKey = scanner.nextInt();
                    int linIndex = linearSearch(data, linKey);
                    System.out.println(linIndex != -1 ? "Key found at index: " + linIndex : "Key not found.");
                    break;
                case 5:
                    System.out.print("Enter search key: ");
                    int binKey = scanner.nextInt();
                    int binIndex = binarySearch(data, binKey);
                    System.out.println(binIndex != -1 ? "Key found at index: " + binIndex : "Key not found.");
                    break;
                case 6:
                    shuffle(data);
                    System.out.println("Array items shuffled:");
                    printArray(data);
                    break;
                case 7:
                    data = generateData(data.length, min, max);
                    System.out.println("New data set generated:");
                    printArray(data);
                    break;
                case 8:
                    reportDuplicates(data);
                    break;
                case 0:
                    System.out.println("Exiting Toolkit Program.");
                    running = false;
                    break;
                default:
                    System.out.println("Invalid selection. Choose an option from 0 to 8.");
            }
        }
        scanner.close();
    }

    public static int[] generateData(int size, int min, int max) {
        int[] data = new int[size];
        for (int i = 0; i < data.length; i++) {
            data[i] = (int) (Math.random() * (max - min + 1)) + min;
        }
        return data;
    }

    public static void printArray(int[] values) {
        for (int val : values) {
            System.out.print(val + " ");
        }
        System.out.println();
    }

    public static int[] reverse(int[] values) {
        int[] reversed = new int[values.length];
        for (int i = 0; i < values.length; i++) {
            reversed[i] = values[values.length - 1 - i];
        }
        return reversed;
    }

    public static void selectionSort(int[] values) {
        for (int i = 0; i < values.length - 1; i++) {
            int minIndex = i;
            for (int j = i + 1; j < values.length; j++) {
                if (values[j] < values[minIndex]) {
                    minIndex = j;
                }
            }
            int temp = values[minIndex];
            values[minIndex] = values[i];
            values[i] = temp;
        }
    }

    public static int linearSearch(int[] values, int key) {
        int comparisons = 0;
        int foundIndex = -1;
        for (int i = 0; i < values.length; i++) {
            comparisons++;
            if (values[i] == key) {
                foundIndex = i;
                break;
            }
        }
        System.out.println("Linear Search Comparisons: " + comparisons);
        return foundIndex;
    }

    public static int binarySearch(int[] values, int key) {
        int low = 0;
        int high = values.length - 1;
        int comparisons = 0;

        while (low <= high) {
            int mid = low + (high - low) / 2;
            comparisons++;

            if (values[mid] == key) {
                System.out.println("Binary Search Comparisons: " + comparisons);
                return mid;
            } else if (values[mid] < key) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        System.out.println("Binary Search Comparisons: " + comparisons);
        return -1;
    }

    public static void shuffle(int[] values) {
        for (int i = values.length - 1; i > 0; i--) {
            int randomPos = (int) (Math.random() * (i + 1));
            int temp = values[i];
            values[i] = values[randomPos];
            values[randomPos] = temp;
        }
    }

    public static void swapFirstTwo(int[] values) {
        if (values.length >= 2) {
            int temp = values[0];
            values[0] = values[1];
            values[1] = temp;
        }
    }

    public static double average(int... values) {
        if (values == null || values.length == 0) {
            return 0.0;
        }
        double sum = 0;
        for (int val : values) {
            sum += val;
        }
        return sum / values.length;
    }

    public static int countOccurrences(int[] values, int key) {
        int count = 0;
        for (int val : values) {
            if (val == key) {
                count++;
            }
        }
        return count;
    }

    public static void reportDuplicates(int[] values) {
        int[] workingCopy = Arrays.copyOf(values, values.length);
        selectionSort(workingCopy);

        System.out.println("--- Duplicate Frequency Report ---");
        boolean foundAny = false;

        for (int i = 0; i < workingCopy.length; i++) {
            if (i < workingCopy.length - 1 && workingCopy[i] == workingCopy[i + 1]) {
                int duplicateKey = workingCopy[i];
                int occurrences = countOccurrences(values, duplicateKey);
                System.out.println("Value [" + duplicateKey + "] occurs " + occurrences + " times.");
                foundAny = true;

                while (i < workingCopy.length - 1 && workingCopy[i] == workingCopy[i + 1]) {
                    i++;
                }
            }
        }
                if (!foundAny) {
            System.out.println("No duplicate elements.");
        }
    }
}
```

## Part 6
The Array needs to be sorted before the binary search, since a binary search gets rid of half the elements with each search and will skip over elements that aren't in order.

## Part 9
The caller still sees the changed elements after Java used pass-by-value, because the reference is a copy of the location of the original array.
