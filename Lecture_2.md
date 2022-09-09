# Data Types and Type Casting in Java

Java uses various data types just like C and C++.
```
public class Student {
    
    public static void main(String[] args) {
        String name = "Steve Jobs";
        int age = 55;
        float cgpa = 2.95f;
        boolean active = true;
        double height = 5.11;

        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("CGPA: " + cgpa);
        System.out.println("Active: " + active);
        System.out.println("Height: " + height);
    }
}
```
`printf` is another way of printing in Java much like C and C++.
```
public class Student {
    
    public static void main(String[] args) {
        String name = "Steve Jobs";
        int age = 55;
        float cgpa = 2.95f;
        boolean active = true;
        double height = 5.11;

        System.out.printf("Name: %s \nAge: %d \nCGPA: %.2f \nActive: %s \nHeight: %.2f", name, age, cgpa, active, height);
    }
}
```
Instance members (variables) are used in Java much like member functions. More than 1 can be created. An instance of the class is required to access these variables inside a static method.
```
public class Student {
    String name = "Steve Jobs";
    int age = 55;
    float cgpa = 2.95f;
    boolean active = true;
    double height = 5.11;

    public static void main(String[] args) {

        Student student = new Student();
        System.out.printf("Name: %s \nAge: %d \nCGPA: %.2f \nActive: %s \nHeight: %.2f", student.name, student.age, student.cgpa, student.active, student.height);
    }
}
```
Member functions can access instance variables without creating an instance of a class. However, to call a member function in a static function, an instance is required for that class.

```
public class Student {
    String name = "Steve Jobs";
    int age = 55;
    float cgpa = 2.95f;
    boolean active = true;
    double height = 5.11;


    public void display()
    {
        System.out.printf("Name: %s \nAge: %d \nCGPA: %.2f \nActive: %s \nHeight: %.2f", name, age, cgpa, active, height);
    }

    public static void main(String[] args) {
        Student student = new Student();
        student.display();
        
    }
}
```
Conditional statements in Java are similar to C and C++.
```
public class Student {
    String name = "Steve Jobs";
    int age = 55;
    float cgpa = 3.95f;
    boolean active = true;
    double height = 5.11;

    void calculateGrade()
    {
        if (cgpa > 3.5f && cgpa <=4.0f)
        {
            System.out.println("A");
        }
        else if (cgpa > 3.0f && cgpa <=3.5f)
        {
            System.out.println("B");
        }
        else if (cgpa > 2.5f && cgpa <=3.0f)
        {
            System.out.println("C");
        }
        else if (cgpa > 2.0f && cgpa <=2.5f)
        {
            System.out.println("D");
        }
        else
        {
            System.out.println("F");
        }
    }

    public void display()
    {
        System.out.printf("Name: %s \nAge: %d \nCGPA: %.2f \nActive: %s \nHeight: %.2f \n", name, age, cgpa, active, height);
    }

    public static void main(String[] args) {
        Student student = new Student();
        student.display();
        student.calculateGrade();
        
    }
}
```
Java has loops similar to C and C++.
```
    void progress()
    {
        int i = 1;
        while (i<=8)
        {
            System.out.printf("Semester: %d , CGPA: %.2f ", i, cgpa );
            cgpa = cgpa - 0.25f;
            i++;
        }
    }
```
Java functions can return results based on various data types.
```
public class Numbers {

    public static double power(int base, int exponent)
    {
        double result = 1;

        for (int i=0; i<exponent; i++)
        {
            result *= base;
        }

        return result;
    }
    public static void main(String[] args) {
        
        double result = power(5, 2);
        System.out.println("Result: " + result);
    }
}
```
Java allows casting from one data type to another. Java allows implicit casting as well as explicit casting.
```
// Implicit Casting

    public static void casting(int number)
    {
        int i = 10;
        double d = i;
        float f = i;

        System.out.println("Integer : " + i);
        System.out.println("Double : " + d);
        System.out.println("Float : " + f);

    }
```
Narrow casting would result in an error as we need lose precision. Below will produce an error
```
    public static void casting(int number)
    {
        double d = 10.5;
        int i = d;

        System.out.println("Integer : " + i);
        System.out.println("Double : " + d);

    }
```
```
// Explicit Casting

public static void casting(int number)
{
        int i = 10;
        double d = (double) i;
        System.out.println("Integer : " + i);
        System.out.println("Double : " + d);

}
```
Narrow casting is allowed using explicit casting
```
public static void casting(int number)
    {
        double d = 10.5;
        int i = (int) d;
        System.out.println("Integer : " + i);
        System.out.println("Double : " + d);

    }
```