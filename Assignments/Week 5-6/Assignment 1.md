# Assignment 1/5

```java
import java.util.Scanner;

public class AssessmentAnalyzer {

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        double[] scores = new double[10];

        System.out.println("Enter 10 scores (0 to 100):");

        for (int i = 0; i < scores.length; i++) {
            while (true) {
                System.out.print("Enter score " + (i + 1) + ": ");
                if (input.hasNextDouble()) {
                    double score = input.nextDouble();
                    if (score >= 0 && score <= 100) {
                        scores[i] = score;
                        break;
                    } else {
                        System.out.println("Invalid score.");
                    }
                } else {
                    System.out.println("Invalid input.");
                    input.next();
                }
            }
        }

        System.out.println("\n--- Assessment Summary ---");

        printScores(scores);

        double average = calculateAverage(scores);
        System.out.printf("\nAverage Score: %.2f\n", average);

        double min = findMinimum(scores);
        double max = findMaximum(scores);
        System.out.printf("Minimum Score: %.2f\n", min);
        System.out.printf("Maximum Score: %.2f\n", max);

        int countAbove = countAboveAverage(scores, average);
        System.out.println("Scores above average: " + countAbove);

        System.out.print("\nEnter a score to search for: ");
        while (!input.hasNextDouble()) {
            System.out.println("Invalid number.");
            input.next();
            System.out.print("Enter a score to search for: ");
        }
        double target = input.nextDouble();

        int searchResult = linearSearch(scores, target);
        if (searchResult != -1) {
            System.out.println("Score found at index: " + searchResult);
        } else {
            System.out.println("Score not found (-1).");
        }

        System.out.println("\n--- Independent Copy Demonstration ---");
        double[] independentCopy = copyArray(scores);

        System.out.println("Original scores before changing copy: " + scores[0]);
        independentCopy[0] = 99.9;
        System.out.println("Independent copy changed to: " + independentCopy[0]);
        System.out.println("Original score after copy: " + scores[0]);

        System.out.println("\n--- Circular Left Shift ---");
        System.out.println("Array BEFORE shift:");
        printScores(scores);

        shiftLeft(scores);

        System.out.println("\nArray AFTER shift:");
        printScores(scores);

        input.close();
    }

    public static void printScores(double[] scores) {
        for (int i = 0; i < scores.length; i++) {
            System.out.print("[" + i + "]:" + scores[i] + "  ");
        }
        System.out.println();
    }

    public static double calculateAverage(double[] scores) {
        double sum = 0;
        for (double score : scores) {
            sum += score;
        }
        return sum / scores.length;
    }

    public static double findMinimum(double[] scores) {
        double min = scores[0];
        for (int i = 1; i < scores.length; i++) {
            if (scores[i] < min) {
                min = scores[i];
            }
        }
        return min;
    }

    public static double findMaximum(double[] scores) {
        double max = scores[0];
        for (int i = 1; i < scores.length; i++) {
            if (scores[i] > max) {
                max = scores[i];
            }
        }
        return max;
    }

    public static int countAboveAverage(double[] scores, double average) {
        int count = 0;
        for (double score : scores) {
            if (score > average) {
                count++;
            }
        }
        return count;
    }

    public static int linearSearch(double[] scores, double target) {
        for (int i = 0; i < scores.length; i++) {
            if (scores[i] == target) {
                return i;
            }
        }
        return -1;
    }

    public static double[] copyArray(double[] source) {
        double[] target = new double[source.length];
        for (int i = 0; i < source.length; i++) {
            target[i] = source[i];
        }
        return target;
    }

    public static void shiftLeft(double[] scores) {
        if (scores.length == 0) return;

        double firstElement = scores[0];

        for (int i = 0; i < scores.length - 1; i++) {
            scores[i] = scores[i + 1];
        }

        scores[scores.length - 1] = firstElement;
    }
}
```
## part 7
second[0] also changes score[0] because second is a copy of score and both refer to the same array, so changing one also changes the other.
