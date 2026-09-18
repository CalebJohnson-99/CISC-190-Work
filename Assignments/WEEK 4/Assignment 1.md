# Assignment 1 week 4

## Part 1-7
```java
import java.util.Scanner;

public class StudentGradeToolkit {

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        System.out.print("Enter student name: ");
        String name = input.nextLine();
        System.out.print("Enter first score (0-100): ");
        double score1 = input.nextDouble();
        System.out.print("Enter second score (0-100): ");
        double score2 = input.nextDouble();
        System.out.print("Enter third score (0-100): ");
        double score3 = input.nextDouble();

        if (!isValidScore(score1) || !isValidScore(score2) || !isValidScore(score3)) {
            System.out.println("Error: One or more scores are invalid.");
        } else
        {
            double average = calculateAverage(score1, score2, score3);
            char grade = determineGrade(average);
            boolean passing = isPassing(average);
            printReport(name, average, grade, passing);
        }
        input.close();
    }

    public static boolean isValidScore(double score) {
        return score >= 0 && score <= 100;
    }

    public static double calculateAverage(double score1, double score2, double score3) {
        return (score1 + score2 + score3) / 3.0;
    }

    public static char determineGrade(double average) {
        if (average >= 90) {
            return 'A';
        } else if (average >= 80) {
            return 'B';
        } else if (average >= 70) {
            return 'C';
        } else if (average >= 60) {
            return 'D';
        } else {
            return 'F';
        }
    }

    public static boolean isPassing(double average) {
        return average >= 60;
    }

    public static void printReport(String name, double average, char grade, boolean passing) {
        String statusStr = passing ? "Passing" : "Failing";

        System.out.println("----- Student Report -----");
        System.out.println("Name: " + name);
        System.out.printf("Average: %.2f\n", average);
        System.out.println("Grade: " + grade);
        System.out.println("Status: " + statusStr);
    }
}
```
## part 8
``` java
import java.util.Scanner;

public class StudentGradeToolkit {

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        double testScore = 80;
        addBonus(testScore);
        System.out.println(testScore);

        System.out.print("Enter student name: ");
        String name = input.nextLine();
        System.out.print("Enter first score (0-100): ");
        double score1 = input.nextDouble();
        System.out.print("Enter second score (0-100): ");
        double score2 = input.nextDouble();
        System.out.print("Enter third score (0-100): ");
        double score3 = input.nextDouble();

        if (!isValidScore(score1) || !isValidScore(score2) || !isValidScore(score3)) {
            System.out.println("Error: One or more scores are invalid.");
        } else
        {
            double average = calculateAverage(score1, score2, score3);
            char grade = determineGrade(average);
            boolean passing = isPassing(average);
            printReport(name, average, grade, passing);
        }
        input.close();
    }

    public static boolean isValidScore(double score) {
        return score >= 0 && score <= 100;
    }

    public static double calculateAverage(double score1, double score2, double score3) {
        return (score1 + score2 + score3) / 3.0;
    }

    public static char determineGrade(double average) {
        if (average >= 90) {
            return 'A';
        } else if (average >= 80) {
            return 'B';
        } else if (average >= 70) {
            return 'C';
        } else if (average >= 60) {
            return 'D';
        } else {
            return 'F';
        }
    }

    public static boolean isPassing(double average) {
        return average >= 60;
    }

    public static void printReport(String name, double average, char grade, boolean passing) {
        String statusStr = passing ? "Passing" : "Failing";

        System.out.println("----- Student Report -----");
        System.out.println("Name: " + name);
        System.out.printf("Average: %.2f\n", average);
        System.out.println("Grade: " + grade);
        System.out.println("Status: " + statusStr);
    }
    public static void addBonus(double score) {
        score += 5;
    }
}
```

1. 80.0
2. The original value does not change because the addBonus creates a copy that the +=5 affects and then the copy is deleted leaving the original
3.
```java
import java.util.Scanner;

public class StudentGradeToolkit {

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        double testScore = 80;
        testScore = addBonus(testScore);
        System.out.println(testScore);

        System.out.print("Enter student name: ");
        String name = input.nextLine();
        System.out.print("Enter first score (0-100): ");
        double score1 = input.nextDouble();
        System.out.print("Enter second score (0-100): ");
        double score2 = input.nextDouble();
        System.out.print("Enter third score (0-100): ");
        double score3 = input.nextDouble();

        if (!isValidScore(score1) || !isValidScore(score2) || !isValidScore(score3)) {
            System.out.println("Error: One or more scores are invalid.");
        } else
        {
            double average = calculateAverage(score1, score2, score3);
            char grade = determineGrade(average);
            boolean passing = isPassing(average);
            printReport(name, average, grade, passing);
        }
        input.close();
    }

    public static boolean isValidScore(double score) {
        return score >= 0 && score <= 100;
    }

    public static double calculateAverage(double score1, double score2, double score3) {
        return (score1 + score2 + score3) / 3.0;
    }

    public static char determineGrade(double average) {
        if (average >= 90) {
            return 'A';
        } else if (average >= 80) {
            return 'B';
        } else if (average >= 70) {
            return 'C';
        } else if (average >= 60) {
            return 'D';
        } else {
            return 'F';
        }
    }

    public static boolean isPassing(double average) {
        return average >= 60;
    }

    public static void printReport(String name, double average, char grade, boolean passing) {
        String statusStr = passing ? "Passing" : "Failing";

        System.out.println("----- Student Report -----");
        System.out.println("Name: " + name);
        System.out.printf("Average: %.2f\n", average);
        System.out.println("Grade: " + grade);
        System.out.println("Status: " + statusStr);
    }
    public static double addBonus(double score) {
        score += 5;
    return score;
    }
}
```

## part 11
1. if a is <= b there is no statement for it to return.
2. when a <= b
3. ``` java
   public static int larger(int a, int b) {
    if (a > b) {
        return a;
    } else {
        return b;
    }
}
```
