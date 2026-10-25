# Week 9 assignment 1/1
```java
import java.util.Scanner;

public class StepsToMiles {

    public static double stepsToMiles(int steps) throws Exception {
        if (steps < 0) {
            throw new Exception("Exception: Negative step count entered.");
        }

        return steps / 2000.0;
    }

    public static void main(String[] args) {
        Scanner scnr = new Scanner(System.in);
        int userSteps;

        userSteps = scnr.nextInt();

        try {
            double miles = stepsToMiles(userSteps);

            System.out.printf("%.2f\n", miles);
        }
        catch (Exception e) {
            System.out.println(e.getMessage());
        }
    }
}
```
