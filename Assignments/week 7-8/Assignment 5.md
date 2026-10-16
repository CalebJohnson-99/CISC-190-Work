# W7-8 Assignment 5/5
## Book.java
```java
public class Book {
    private String title;
    private String author;
    private String publisher;
    private String publicationDate;

    public void setTitle(String title) {
        this.title = title;
    }
    public String getTitle() {
        return title;
    }

    public void setAuthor(String author) {
        this.author = author;
    }
    public String getAuthor() {
        return author;
    }

    public void setPublisher(String publisher) {
        this.publisher = publisher;
    }
    public String getPublisher() {
        return publisher;
    }

    public void setPublicationDate(String publicationDate) {
        this.publicationDate = publicationDate;
    }
    public String getPublicationDate() {
        return publicationDate;
    }

    public void printInfo() {
        System.out.println("Book Information:");
        System.out.println("   Book Title: " + title);
        System.out.println("   Author: " + author);
        System.out.println("   Publisher: " + publisher);
        System.out.println("   Publication Date: " + publicationDate);
    }
}
```
## Encyclopedia.java
```java
public class Encyclopedia extends Book {
    private String edition;
    private int numPages;

    public void setEdition(String edition) {
        this.edition = edition;
    }
    public String getEdition() {
        return edition;
    }

    public void setNumPages(int numPages) {
        this.numPages = numPages;
    }
    public int getNumPages() {
        return numPages;
    }

    @Override
    public void printInfo() {
        super.printInfo();
        System.out.println("   Edition: " + edition);
        System.out.println("   Number of Pages: " + numPages);
    }
}
```
## BookInfo.java
import java.util.Scanner;

public class BookInfo {
    public static void main(String[] args) {
        Scanner scnr = new Scanner(System.in);

        Book myBook = new Book();
        Encyclopedia myEncyclopedia = new Encyclopedia();

        String title = scnr.nextLine();
        String author = scnr.nextLine();
        String publisher = scnr.nextLine();
        String publicationDate = scnr.nextLine();

        String eTitle = scnr.nextLine();
        String eAuthor = scnr.nextLine();
        String ePublisher = scnr.nextLine();
        String ePublicationDate = scnr.nextLine();
        String edition = scnr.nextLine();
        int numPages = scnr.nextInt();

        myBook.setTitle(title);
        myBook.setAuthor(author);
        myBook.setPublisher(publisher);
        myBook.setPublicationDate(publicationDate);
        myBook.printInfo();

        myEncyclopedia.setTitle(eTitle);
        myEncyclopedia.setAuthor(eAuthor);
        myEncyclopedia.setPublisher(ePublisher);
        myEncyclopedia.setPublicationDate(ePublicationDate);
        myEncyclopedia.setEdition(edition);
        myEncyclopedia.setNumPages(numPages);
        myEncyclopedia.printInfo();
    }
}
```
