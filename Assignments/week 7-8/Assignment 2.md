# W7-8 Assignment 2/5
## FoodItem
```java
public class FoodItem {
    private String name;
    private double fat;
    private double carbs;
    private double protein;

    // Define default constructor
    public FoodItem() {
        name = "Water";
        fat = 0.0;
        carbs = 0.0;
        protein = 0.0;
    }

    // Define second constructor with parameters to initialize private fields
    public FoodItem(String userName, double userFatAmt, double userCarbAmt,
                    double userProteinAmt) {
        name = userName;
        fat = userFatAmt;
        carbs = userCarbAmt;
        protein = userProteinAmt;
    }

    public String getName() {
        return name;
    }

    public double getFat() {
        return fat;
    }

    public double getCarbs() {
        return carbs;
    }

    public double getProtein() {
        return protein;
    }

    public double getCalories(double numServings) {
        // Calorie formula
        double calories = ((fat * 9) + (carbs * 4) + (protein * 4)) * numServings;
        return calories;
    }

    public void printInfo() {
        System.out.println("Nutritional information per serving of " + name + ":");
        System.out.printf("  Fat: %.2f g\n", fat);
        System.out.printf("  Carbohydrates: %.2f g\n", carbs);
        System.out.printf("  Protein: %.2f g\n", protein);
    }
}
```
## NutritionalInfo
```java
import java.util.Scanner;

public class NutritionalInfo {
    public static void main(String[] args) {
        Scanner scnr = new Scanner(System.in);
        FoodItem foodItem;

        String itemName = scnr.next();

        if(itemName.equals("Water") || itemName.equals("water")) {
            foodItem = new FoodItem();

            foodItem.printInfo();
            System.out.printf("Number of calories for %.2f serving(s): %.2f\n", 1.0,
                    foodItem.getCalories(1.0));
        }

        else {
            double amountFat = scnr.nextDouble();
            double amountCarbs = scnr.nextDouble();
            double amountProtein = scnr.nextDouble();

            foodItem = new FoodItem(itemName, amountFat, amountCarbs, amountProtein);

            double numServings = scnr.nextDouble();

            foodItem.printInfo();
            System.out.printf("Number of calories for %.2f serving(s): %.2f\n", 1.0,
                    foodItem.getCalories(1.0));

            System.out.printf("Number of calories for %.2f serving(s): %.2f\n", numServings,
                    foodItem.getCalories(numServings));
        }
    }
}
```
