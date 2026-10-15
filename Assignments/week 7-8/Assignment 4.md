# W7-8 Assignment 4/5
## Course.java
```java
public class Course {
    private String courseNumber;
    private String courseTitle;

    public void setCourseNumber(String courseNumber) {
        this.courseNumber = courseNumber;
    }

    public String getCourseNumber() {
        return courseNumber;
    }

    public void setCourseTitle(String courseTitle) {
        this.courseTitle = courseTitle;
    }

    public String getCourseTitle() {
        return courseTitle;
    }

    public void PrintInfo() {
        System.out.println("Course Information:");
        System.out.println("   Course Number: " + courseNumber);
        System.out.println("   Course Title: " + courseTitle);
    }
}
```
## OfferedCourse.java
```java
public class OfferedCourse extends Course {
    private String instructorName;
    private String location;
    private String classTime;

    public void setInstructorName(String instructorName) {
        this.instructorName = instructorName;
    }

    public String getInstructorName() {
        return instructorName;
    }

    public void setLocation(String location) {
        this.location = location;
    }

    public String getLocation() {
        return location;
    }

    public void setClassTime(String classTime) {
        this.classTime = classTime;
    }

    public String getClassTime() {
        return classTime;
    }
}
```
## CourseInfo.Java
```java
import java.util.Scanner;

public class CourseInfo {
    public static void main(String[] args) {
        Scanner scnr = new Scanner(System.in);

        Course myCourse = new Course();
        OfferedCourse myOfferedCourse = new OfferedCourse();

        String courseNumber = scnr.nextLine();
        String courseTitle = scnr.nextLine();

        String oCourseNumber = scnr.nextLine();
        String oCourseTitle = scnr.nextLine();
        String instructorName = scnr.nextLine();
        String location = scnr.nextLine();
        String classTime = scnr.nextLine();

        myCourse.setCourseNumber(courseNumber);
        myCourse.setCourseTitle(courseTitle);

        myCourse.PrintInfo();

        myOfferedCourse.setCourseNumber(oCourseNumber);
        myOfferedCourse.setCourseTitle(oCourseTitle);
        myOfferedCourse.setInstructorName(instructorName);
        myOfferedCourse.setLocation(location);
        myOfferedCourse.setClassTime(classTime);

        myOfferedCourse.PrintInfo();

        System.out.println("   Instructor Name: " + myOfferedCourse.getInstructorName());
        System.out.println("   Location: " + myOfferedCourse.getLocation());
        System.out.println("   Class Time: " + myOfferedCourse.getClassTime());
    }
}
```
