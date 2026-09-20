# Assignment 2 week 4

## part 1-6
```java
import java.util.Scanner;

public class NumericToolkit {
    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);
        int choice;

        do {
            displayMenu();
            choice = readChoice(input);

            switch (choice) {
                case 1 -> handleGcd(input);
                case 2 -> handlePrime(input);
                case 3 -> handleHexConversion(input);
                case 4 -> handleMaximum(input);
                case 5 -> System.out.println("Exiting the program. Goodbye!");
                default -> System.out.println("Invalid choice. Please try again.");
            }
        }
        while (choice != 5);

        input.close();
    }

    //displayMenu
    public static void displayMenu() {
        System.out.println("----- Numeric Toolkit -----");
        System.out.println("1. GCD");
        System.out.println("2. check Prime");
        System.out.println("3. Convert Hexadecimal to Decimal");
        System.out.println("4. Find Maximum Value");
        System.out.println("5. Exit");
        System.out.print("Enter your choice: ");
    }

    //readChoice
    static int readChoice(Scanner scanner) {
        while (!scanner.hasNextInt()) {
            System.out.print("Invalid input. Please enter a valid menu number: ");
            scanner.next();
        }
        return scanner.nextInt();
    }

    //handleGcd
    public static void handleGcd(Scanner scanner) {
        System.out.print("Enter first positive integer: ");
        int num1 = scanner.nextInt();
        System.out.print("Enter second positive integer: ");
        int num2 = scanner.nextInt();

        int result = gcd(num1, num2);
        System.out.println("The GCD of " + num1 + " and " + num2 + " is: " + result);
    }

    public static int gcd(int first, int second) {
        while (second != 0) {
            int temp = second;
            second = first % second;
            first = temp;
        }
        return first;
    }

    //handlePrime
    public static void handlePrime(Scanner scanner) {
        System.out.print("Enter an integer to check: ");
        int num = scanner.nextInt();

        if (isPrime(num)) {
            System.out.println(num + " is a prime number.");
        } else {
            System.out.println(num + " is NOT a prime number.");
        }
    }

    public static boolean isPrime(int number) {
        if (number <= 1) {
            return false;
        }

        for (int i = 2; i <= Math.sqrt(number); i++) {
            if (number % i == 0) {
                return false;
            }
        }

        return true;
    }

    //handleHexConversion
    public static void handleHexConversion(Scanner scanner) {
        System.out.print("Enter a hexadecimal string: ");
        String hex = scanner.next();

        int decimal = hexToDecimal(hex);
        System.out.println("The decimal value of \"" + hex + "\" is: " + decimal);
    }

    public static int hexToDecimal(String hex) {
        int decimalValue = 0;

        for (int i = 0; i < hex.length(); i++) {
            char hexChar = hex.charAt(i);
            int digitValue = hexDigitToDecimal(hexChar);
            decimalValue = decimalValue * 16 + digitValue;
        }

        return decimalValue;
    }

    public static int hexDigitToDecimal(char digit) {
        char upChar = Character.toUpperCase(digit);

        if (upChar >= '0' && upChar <= '9') {
            return upChar - '0';
        } else if (upChar >= 'A' && upChar <= 'F') {
            return upChar - 'A' + 10;
        } else {
            return 0;
        }
    }

    //handleMaximum
    public static void handleMaximum(Scanner scanner) {
        System.out.println("Choose an overload to test:");
        System.out.println("1. Max of two integers (int, int)");
        System.out.println("2. Max of two doubles (double, double)");
        System.out.println("3. Max of three integers (int, int, int)");
        System.out.print("Choice: ");
        int choice = scanner.nextInt();

        if (choice == 1) {
            System.out.print("Enter integer a: ");
            int a = scanner.nextInt();
            System.out.print("Enter integer b: ");
            int b = scanner.nextInt();
            System.out.println("Result: max(" + a + ", " + b + ") = " + max(a, b));
        } else if (choice == 2) {
            System.out.print("Enter double a: ");
            double a = scanner.nextDouble();
            System.out.print("Enter double b: ");
            double b = scanner.nextDouble();
            System.out.println("Result: max(" + a + ", " + b + ") = " + max(a, b));
        } else if (choice == 3) {
            System.out.print("Enter integer a: ");
            int a = scanner.nextInt();
            System.out.print("Enter integer b: ");
            int b = scanner.nextInt();
            System.out.print("Enter integer c: ");
            int c = scanner.nextInt();
            System.out.println("Result: max(" + a + ", " + b + ", " + c + ") = " + max(a, b, c));
        } else {
            System.out.println("Invalid test choice.");
        }
    }

    public static int max(int a, int b) {
        return (a > b) ? a : b;
    }

    public static double max(double a, double b) {
        return (a > b) ? a : b;
    }

    public static int max(int a, int b, int c) {
        return max(max(a, b), c);
    }
}
```

## part 7
1. since (5, 5) are both applicable through numeric conversion. the compiler can't decide which to convert first and gives an error.
2.   you could add a .0 to one of the arguments.
3.   you could make it so it only takes integers or only takes decimals
   public static double combine(double a, double b) or public static double combine(int a, int b)

## Part 8
1. 1. the closing bracket in the if statement should be after the system.out.println statement.
2. 2. it begins at int result =
      and ends at the next closing bracket
3. ```java
   public static void scopeDemo() {
    int value = 10;

    if (value > 0) {
        int result = value * 2;
        System.out.println(result);
     }
   }

  ## Part 9-11
  ```java
import java.util.Scanner;

public class NumericToolkit {
    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);
        int choice;

        do {
            displayMenu();
            choice = readChoice(input);

            switch (choice) {
                case 1:
                    handleGcd(input);
                    break;
                case 2:
                    handlePrime(input);
                    break;
                case 3:
                    handleHexConversion(input);
                    break;
                case 4:
                    handleMaximum(input);
                    break;
                case 0:
                    System.out.println("Exiting.");
                    break;
                default:
                    System.out.println("Invalid choice.");
            }
        } while (choice != 0);
    }

    //displayMenu
    public static void displayMenu() {
        System.out.println("----- Numeric Toolkit -----");
        System.out.println("1. GCD");
        System.out.println("2. check Prime");
        System.out.println("3. Convert Hexadecimal to Decimal");
        System.out.println("4. Find Maximum Value");
        System.out.println("0. Exit");
    }

    //readChoice
    public static int readChoice(Scanner input) {
        System.out.print("Enter your choice: ");
        while (!input.hasNextInt()) {
            System.out.print("Invalid input. Please enter a valid number: ");
            input.next();
        }
        return input.nextInt();
    }

    //handleGcd
    public static void handleGcd(Scanner input) {
        System.out.print("Enter first positive integer: ");
        int num1 = input.nextInt();
        System.out.print("Enter second positive integer: ");
        int num2 = input.nextInt();

        int result = gcd(num1, num2);
        System.out.println("The GCD of " + num1 + " and " + num2 + " is: " + result);
    }

    public static int gcd(int first, int second) {
        while (second != 0) {
            int temp = second;
            second = first % second;
            first = temp;
        }
        return first;
    }

    //handlePrime
    public static void handlePrime(Scanner input) {
        System.out.print("Enter an integer to check: ");
        int num = input.nextInt();

        if (isPrime(num)) {
            System.out.println(num + " is a prime number.");
        } else {
            System.out.println(num + " is NOT a prime number.");
        }
    }

    public static boolean isPrime(int number) {
        if (number <= 1) {
            return false;
        }

        for (int i = 2; i <= Math.sqrt(number); i++) {
            if (number % i == 0) {
                return false;
            }
        }

        return true;
    }

    //handleHexConversion
    public static void handleHexConversion(Scanner input) {
        System.out.print("Enter a hexadecimal string: ");
        String hex = input.next();

        int decimal = hexToDecimal(hex);
        System.out.println("The decimal value of \"" + hex + "\" is: " + decimal);
    }

    public static int hexToDecimal(String hex) {
        int decimalValue = 0;

        for (int i = 0; i < hex.length(); i++) {
            char hexChar = hex.charAt(i);
            int digitValue = hexDigitToDecimal(hexChar);
            decimalValue = decimalValue * 16 + digitValue;
        }

        return decimalValue;
    }

    public static int hexDigitToDecimal(char digit) {
        char upChar = Character.toUpperCase(digit);

        if (upChar >= '0' && upChar <= '9') {
            return upChar - '0';
        } else if (upChar >= 'A' && upChar <= 'F') {
            return upChar - 'A' + 10;
        } else {
            return 0;
        }
    }

    //handleMaximum
    public static void handleMaximum(Scanner input) {
        System.out.println("Choose an overload to test:");
        System.out.println("1. Max of two integers (int, int)");
        System.out.println("2. Max of two doubles (double, double)");
        System.out.println("3. Max of three integers (int, int, int)");
        System.out.print("Choice: ");
        int choice = input.nextInt();

        if (choice == 1) {
            System.out.print("Enter integer a: ");
            int a = input.nextInt();
            System.out.print("Enter integer b: ");
            int b = input.nextInt();
            System.out.println("Result: max(" + a + ", " + b + ") = " + max(a, b));
        } else if (choice == 2) {
            System.out.print("Enter double a: ");
            double a = input.nextDouble();
            System.out.print("Enter double b: ");
            double b = input.nextDouble();
            System.out.println("Result: max(" + a + ", " + b + ") = " + max(a, b));
        } else if (choice == 3) {
            System.out.print("Enter integer a: ");
            int a = input.nextInt();
            System.out.print("Enter integer b: ");
            int b = input.nextInt();
            System.out.print("Enter integer c: ");
            int c = input.nextInt();
            System.out.println("Result: max(" + a + ", " + b + ", " + c + ") = " + max(a, b, c));
        } else {
            System.out.println("Invalid test choice.");
        }
    }

    public static int max(int a, int b) {
        return (a > b) ? a : b;
    }

    public static double max(double a, double b) {
        return (a > b) ? a : b;
    }

    public static int max(int a, int b, int c) {
        return max(max(a, b), c);
    }
}
```
## Part 12
For gcd the caller needs to know that when they give two numbers they get back the greatest common divisor.
they dont need to see the loop and the remainder math used to find it.

for isPrime the need to know that they give a number and get back true or false and that true means the number is prime and false means its not a prime number.
they dont need to see the loop that checks divisibility up to the square root of the number.

for hexToDecimal the caller needs to know that when they give a hex string it is converted to a normal number.
they dont need to see the formula and conversion steps.

for max they need to know how many numbers to give and that they'll get back the greatest value number given.
They dont need to see the code used to compare the numbers given.

The caller only needs to know how to use the program and what the outputs mean. They don't need to understand the ins and outs of the code to use it.

## Part 13-15
```java
import java.util.Scanner;

public class NumericToolkit {
    public static void main(String[] args) {

        System.out.println(gcd(24, 36));
        System.out.println(isPrime(29));
        System.out.println(hexToDecimal("1F"));
        System.out.println(max(5, 8));
        System.out.println(max(4.5, 2.7));
        System.out.println(max(5, 8, 3));

        Scanner input = new Scanner(System.in);
        int choice;

        do {
            displayMenu();
            choice = readChoice(input);

            switch (choice) {
                case 1:
                    handleGcd(input);
                    break;
                case 2:
                    handlePrime(input);
                    break;
                case 3:
                    handleHexConversion(input);
                    break;
                case 4:
                    handleMaximum(input);
                    break;
                case 0:
                    System.out.println("Exiting.");
                    break;
                default:
                    System.out.println("Invalid choice.");
            }
        } while (choice != 0);
    }

    //displayMenu
    public static void displayMenu() {
        System.out.println("----- Numeric Toolkit -----");
        System.out.println("1. GCD");
        System.out.println("2. check Prime");
        System.out.println("3. Convert Hexadecimal to Decimal");
        System.out.println("4. Find Maximum Value");
        System.out.println("0. Exit");
    }

    //readChoice
    public static int readChoice(Scanner input) {
        System.out.print("Enter your choice: ");
        while (!input.hasNextInt()) {
            System.out.print("Invalid input. Please enter a valid number: ");
            input.next();
        }
        return input.nextInt();
    }

    //handleGcd
    public static void handleGcd(Scanner input) {
        System.out.print("Enter first positive integer: ");
        int num1 = input.nextInt();
        System.out.print("Enter second positive integer: ");
        int num2 = input.nextInt();

        int result = gcd(num1, num2);
        System.out.println("The GCD of " + num1 + " and " + num2 + " is: " + result);
    }

    public static int gcd(int first, int second) {
        while (second != 0) {
            int temp = second;
            second = first % second;
            first = temp;
        }
        return first;
    }

    //handlePrime
    public static void handlePrime(Scanner input) {
        System.out.print("Enter an integer to check: ");
        int num = input.nextInt();

        if (isPrime(num)) {
            System.out.println(num + " is a prime number.");
        } else {
            System.out.println(num + " is NOT a prime number.");
        }
    }

    public static boolean isPrime(int number) {
        if (number <= 1) {
            return false;
        }

        for (int i = 2; i <= Math.sqrt(number); i++) {
            if (number % i == 0) {
                return false;
            }
        }

        return true;
    }

    //handleHexConversion
    public static void handleHexConversion(Scanner input) {
        System.out.println("Hex conversion selected.");
    }

    public static int hexToDecimal(String hex) {
        int decimalValue = 0;

        for (int i = 0; i < hex.length(); i++) {
            char hexChar = hex.charAt(i);
            int digitValue = hexDigitToDecimal(hexChar);
            decimalValue = decimalValue * 16 + digitValue;
        }

        return decimalValue;
    }

    public static int hexDigitToDecimal(char digit) {
        char upChar = Character.toUpperCase(digit);

        if (upChar >= '0' && upChar <= '9') {
            return upChar - '0';
        } else if (upChar >= 'A' && upChar <= 'F') {
            return upChar - 'A' + 10;
        } else {
            return 0;
        }
    }

    //handleMaximum
    public static void handleMaximum(Scanner input) {
        System.out.println("Choose an overload to test:");
        System.out.println("1. Max of two integers (int, int)");
        System.out.println("2. Max of two doubles (double, double)");
        System.out.println("3. Max of three integers (int, int, int)");
        System.out.print("Choice: ");
        int choice = input.nextInt();

        if (choice == 1) {
            System.out.print("Enter integer a: ");
            int a = input.nextInt();
            System.out.print("Enter integer b: ");
            int b = input.nextInt();
            System.out.println("Result: max(" + a + ", " + b + ") = " + max(a, b));
        } else if (choice == 2) {
            System.out.print("Enter double a: ");
            double a = input.nextDouble();
            System.out.print("Enter double b: ");
            double b = input.nextDouble();
            System.out.println("Result: max(" + a + ", " + b + ") = " + max(a, b));
        } else if (choice == 3) {
            System.out.print("Enter integer a: ");
            int a = input.nextInt();
            System.out.print("Enter integer b: ");
            int b = input.nextInt();
            System.out.print("Enter integer c: ");
            int c = input.nextInt();
            System.out.println("Result: max(" + a + ", " + b + ", " + c + ") = " + max(a, b, c));
        } else {
            System.out.println("Invalid test choice.");
        }
    }

    public static int max(int a, int b) {
        return (a > b) ? a : b;
    }

    public static double max(double a, double b) {
        return (a > b) ? a : b;
    }

    public static int max(int a, int b, int c) {
        return max(max(a, b), c);
    }
    //randomCharacter
    public static char randomCharacter(char first, char last) {
        int range = last - first + 1;
        return (char) (first + Math.random() * range);
    }
    public static char randomLowercaseLetter() {
        return randomCharacter('a', 'z');
    }
    public static char randomUppercaseLetter() {
        return randomCharacter('A', 'Z');
    }
    public static char randomDigit() {
        return randomCharacter('0', '9');
    }
}
```
