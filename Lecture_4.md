# Abstraction, Exception Handling, Packages and Final

Java uses the concept of Abstract classes just like C++ except that it does not use virtual keyword and instead uses abstract keyword.

`Shape.java`
```Java
public abstract class Shape {
    double height, width;
    String name;

    Shape()
    {
        this.height = this.width = 0.0;
        this.name = "";
    }
    Shape(double height, double width, String name)
    {
        this.height = height;
        this.width = width;
        this.name = name;
    }

    abstract double calculateArea();
}
```

`Rectangle.java`
```Java
public class Rectangle extends Shape {
    
    Rectangle()
    {
        super();
    }

    Rectangle(double height, double width, String name)
    {
        super(height, width, name);
    }

    double calculateArea()
    {
        return height * width;
    }
}
```
`Triangle.java`
```Java
public class Triangle extends Shape{
    
    Triangle()
    {
        super();
    }

    Triangle(double height, double width, String name)
    {
        super(height, width, name);
    }

    double calculateArea()
    {
        return (height* width)/2;
    }
}
```

`Driver.java`
```Java
public class Driver {
    public static void main(String[] args) {
        
        Shape shapes[] = new Shape[4];
        shapes[0] = new Triangle(10.0, 5.0, "Triangle 1");
        shapes[1] = new Triangle(15.0, 15.0, "Triangle 2");
        shapes[2] = new Rectangle(10.0, 10.0, "Rectangle 1");
        shapes[3] = new Rectangle(20.0, 1.0, "Rectangle 2");

        for (int i = 0; i <4; i++)
        {
            System.out.println("Shape is " + shapes[i].name);
            System.out.println("Area is " + shapes[i].calculateArea());
        }
    }
}
```
In Java programming, it is sometimes helpful to define what a class must do but not how it will do it. It also helps in allowing unrelated classes to implement from it.

`Drawable.java`
```Java
public interface Drawable {
    public void draw();
}
```
`Car.java`
```Java
public class Car implements Drawable{
    public String name;

    public Car()
    {
        this.name = "";
    }
    public Car(String name)
    {
        this.name = name;
    }
    public void draw()
    {
        System.out.println("Drawing a design of a car");
    }
}
```
`Toy.java`
```Java
public class Toy implements Drawable{
    public String type;

    public Toy()
    {
        this.type = "";
    }
    public Toy(String type)
    {
        this.type = type;
    }
    public void draw()
    {
        System.out.println("Drawing a design of a toy");
    }
}
```
`Driver.java`
```Java
public class Driver {
    public static void main(String[] args) {
        Car car = new Car("Toyota");
        Toy toy = new Toy("Tank");
        car.draw();
        toy.draw();
    }
}
```
In programming, it is often helpful to group related pieces of a program together. In Java, this can be accomplished by using a package. With a subdirectory Library, we can write the following code

`Book.java`
```Java
package Library;

public class Book {
    String name, author;

    public Book(String name, String author)
    {
        this.name = name;
        this.author = author;
    }
    public String toString()
    {
        return this.name + ", " + this.author;
    }
}
```
`Journal.java`
```Java
package Library;

public class Journal {
    String type;

    public Journal(String type)
    {
        this.type = type;
    }
    public String toString()
    {
        return this.type;
    }
}
```
`Driver.java`
```Java
package Library;

public class Driver {
    public static void main(String[] args) {
        Book book = new Book("Java Programming", "Deitel");
        Journal journal = new Journal("Science");

        System.out.println(book.toString());
        System.out.println(journal.toString());
    }

}
```
Access modifiers work for packages as well. By default classes have package access which means they are visible to all classes within their package. However, this access can be change by changing access modifiers to private which would make that data member inaccessible outside the class.
```Java
package Packages;

public class Book {

    private String name;
    String author;

    Book(String name, String author)
    {
        this.name = name;
        this.author = author;
    }

    public String toString()
    {
        return "Name: " + this.name + " Author: " + this.author;
    }
}
```
A `final` is pretty handy keyword in java. It helps in avoiding accidentle change of values for a variable just like const in C++.  Below code will produce an error.
```java
Student.java

package Final_Keyword;

public class Student {
    String name;
    int age;
    final String student_type = "Undergraduate";

    void setType()
    {
        this.student_type = "Graduate";
    }
}
```
`final` keyword can also be used to avoid inheritance of classes. This code will produce an error.
```java
Student.java

package Final_Keyword;

public final class Student {
    String name;
    int age;

    Student(String name)
    {
        this.name = name;
    }
    
    public String toString()
    {
        return "Name: " + this.name;
    }

}
```
`Undergraduate.java`
```Java
package Final_Keyword;

public class Undergraduate extends Student{

    Undergraduate(String name)
    {
        super(name);
    }
    
}
```

`Driver.java`
```Java
package Final_Keyword;

public class Driver {
    public static void main(String[] args) {
        Undergraduate ug = new Undergraduate("Steve Jobs");
        System.out.println(ug);
    }
}
```

`final` keyword can also be used to prevent overriding of methods display method in the code below cannot be overridden in child classes

`Student.java`
```Java
package Final_Keyword;

public class Student {
    String name;
    int age;

    Student(String name)
    {
        this.name = name;
    }
    
    public String toString()
    {
        return "Name: " + this.name;
    }

    final void display()
    {
        System.out.println("Name: " + this.name);
    }
}
```
There is an `Object` class in Java which is the parent class of all the classes. Even if no parent class is specified, that class would be extended from Object class. Parent of Student class below is Object class although it is not explicity mentioned.

`Student.java`
```Java
package Object_Class;

public class Student {
    String name;

    Student(String name)
    {
        this.name = name;
    }

    public String toString()
    {
        return this.name;
    }
}
```
The `toString()` method is basically a method in Object class which is overridden in child classes and hence requires public access.  

Exception handling streamlines error handling by allowing your program to define a block of code, called an exception handler, that is executed automatically when an error occurs.

`Driver.java`
```Java
package Exception_Handling;

public class Driver {
    public static void main(String[] args) {
        int nums[] = new int[4];
        try
        {
            nums[7] = 10;
        }
        catch(Exception e)
        {
            System.out.println("Array Index out of bound");
        }
        
    }
}
```
Exceptions can be generated in a separate method and can be caught in another method
```Java
package Exception_Handling;

public class Driver {

    void calculate()
    {
        int nums[] = new int[4];

        nums[7] = 10;

    }
    public static void main(String[] args) {
        Driver d = new Driver();
        try{
            d.calculate();
        }
        catch (ArrayIndexOutOfBoundsException e)
        {
            System.out.println("Array Index out of bound.");
        }
        
        
    }
}
```
**Series Exercise Solution**  

`Series.java`
```Java
package Interfaces;

public interface Series {
    int getNext();
    void reset();
    void setStart(int x);
}
```

`Ones.java`
```Java
package Interfaces;

public class Ones implements Series{
    int start;
    int value;

    Ones()
    {
        this.start = 0;
        this.value = 0;
    }
    public int getNext()
    {
        this.value += 1;
        return this.value;
    }
    public void reset()
    {
        this.value = 0;
    }
    public void setStart(int x)
    {
        this.start = x;
        this.value = x;
    }
}
```

`Twos.java`
```Java
package Interfaces;

public class Twos implements Series{
    int start;
    int value;

    Twos()
    {
        this.start = 0;
        this.value = 0;
    }
    public int getNext()
    {
        this.value += 2;
        return this.value;
    }
    public void reset()
    {
        this.value = 0;
    }
    public void setStart(int x)
    {
        this.start = x;
        this.value = x;
    }
}
```

`Driver.java`
```Java
package Interfaces;

public class Driver {
    public static void main(String[] args) {
        Ones ones = new Ones();
        
        for (int i =0; i<5; i++)
        {
            System.out.println("Next value: " + ones.getNext());
        }

        ones.setStart(100);
        for (int i =0; i<5; i++)
        {
            System.out.println("Next value: " + ones.getNext());
        }

        ones.reset();
        for (int i =0; i<5; i++)
        {
            System.out.println("Next value: " + ones.getNext());
        }

        Twos twos = new Twos();

        for (int i =0; i<5; i++)
        {
            System.out.println("Next value: " + twos.getNext());
        }
    }
}
```
