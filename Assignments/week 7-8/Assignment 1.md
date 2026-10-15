# W7-8 Assignment 1/5

## Car
``` java
public class Car {
    private int modelYear;
    // Declare purchasePrice data member (int)
    private int purchasePrice;
    private int currentValue;

    public void setModelYear(int userYear){
        modelYear = userYear;
    }

    public int getModelYear() {
        return modelYear;
    }

    // Define setPurchasePrice() method
    public void setPurchasePrice(int userPrice){
        purchasePrice = userPrice;
    }

    // Define getPurchasePrice() method
    public int getPurchasePrice() {
        return purchasePrice;
    }

    public void calcCurrentValue(int currentYear) {
        double depreciationRate = 0.15;
        int carAge = currentYear - modelYear;

        // Car depreciation formula
        currentValue = (int)
                Math.round(purchasePrice * Math.pow((1 - depreciationRate), carAge));
    }

    // Define printInfo() method to output modelYear, purchasePrice, and currentValue
    public void printInfo() {
        System.out.println("Car's information:");
        System.out.println("  Model year: " + modelYear);
        System.out.println("  Purchase price: $" + purchasePrice);
        System.out.println("  Current value: $" + currentValue);
    }
}
```
## CarValue
``` java
import java.util.Scanner;

public class CarValue {
    public static void main(String[] args) {
        Scanner scnr = new Scanner(System.in);

        Car myCar = new Car();

        System.out.print("Enter the car's model year: ");
        int userYear = scnr.nextInt();
        System.out.print("Enter the purchase price: ");
        int userPrice = scnr.nextInt();
        System.out.print("Enter the current year: ");
        int userCurrentYear = scnr.nextInt();

        myCar.setModelYear(userYear);
        myCar.setPurchasePrice(userPrice);
        myCar.calcCurrentValue(userCurrentYear);

        myCar.printInfo();
    }
}
```
