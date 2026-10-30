# Week 10 Assignment 1/1
```java
import java.util.Scanner;
import java.io.FileInputStream;
import java.io.IOException;

public class PhotoFileConverter {
    public static void main(String[] args) throws IOException {
        Scanner scnr = new Scanner(System.in);

        String fileName = scnr.nextLine();

        FileInputStream fileByteStream = new FileInputStream(fileName);
        Scanner fileScnr = new Scanner(fileByteStream);

        while (fileScnr.hasNextLine()) {
            String photoName = fileScnr.nextLine();

            String infoName = photoName.replace("_photo.jpg", "_info.txt");

            System.out.println(infoName);
        }

        fileByteStream.close();
        fileScnr.close();
    }
}
```
