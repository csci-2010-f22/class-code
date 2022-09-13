# Inner Classes, Inheritance and Polymorphism

Inner classes are allowed in Java as they can help in providing extra functionality in an organized manner.

`Student.java`
```
public class Student {
    String name;
    int age;

    Student(String name, int age)
    {
        this.name = name;
        this.age = age;
    }

    String getName()
    {
        return this.name;
    }

    int getAge()
    {
        return this.age;
    }

    void display()
    {
        System.out.println("Name: " + this.name + ", Age: " + this.age);
    }

    class StudentDetails
    {
        String getFirstName()
        {
            String firstName[];

            firstName = name.split(" ", 2);

            return firstName[0];
        }
    }
}
```
`Driver.java`
```
public class Driver {
    
    public static void main(String[] args) {
        Student student = new Student("Steve Jobs", 55);
        student.display();

        Student.StudentDetails details = student.new StudentDetails();
        System.out.println(details.getFirstName());
        
    }
}
```
Just like C++, Java offer Inheritance

`Vehicle.java`
```
package Inheritance;

public class Vehicle {
    String name;
    int kms;

    Vehicle()
    {
        this.name = "";
        this.kms = 0;
    }

    Vehicle(String name, int kms)
    {
        this.name = name;
        this.kms = kms;
    }

    void display()
    {
        System.out.println("Name: " + this.name + ", KMs: " + this.kms);
    }
}

```
`Car.java`
```
package Inheritance;

public class Car extends Vehicle {
    String type;

    Car()
    {
        this.type = "";
    }
    Car(String name, int kms, String type)
    {
        super(name, kms);
        this.type = type;
    }
    void display()
    {
        super.display();
        System.out.println("Type: " + type);
    }
}
```
`Driver.java`
```
package Inheritance;


public class Driver {
    
    public static void main(String[] args) {
        Car car  = new Car("Toyota Rav4", 1234, "SUV");
        car.display();
    }
}
```
Java does not offer multiple inheritance, however, it does offer multi-level-inheritance

`Phone.java`
```
package Multi_Level_Inheritance;

public class Phone {
    
    void makeCalls()
    {
        System.out.println("I can make calls");
    }
}
```

`SmartPhone.java`
```
package Multi_Level_Inheritance;

public class SmartPhone extends Phone {
    void browseInternet()
    {
        System.out.println("I can browse Internet");
    }

}
```
`Android.java`
```
package Multi_Level_Inheritance;

public class Android extends SmartPhone{
    
    void iAmAndroid()
    {
        System.out.println("I am Android");
    }
}
```

`Driver.java`
```
package Multi_Level_Inheritance;

public class Driver {
    
    public static void main(String[] args) {
        Android android = new Android();
        android.makeCalls();
        android.browseInternet();
        android.iAmAndroid();
    }
}
```

Java supports Polymorphism, e.g., An object of parent class can hold the reference of a child class.

`Driver.java`
```
package Polymorphism;

public class Driver {
    public static void main(String[] args) {

        Car car = new Car("Honda Civic", 45454, "Sedan");

        Vehicle v = car;
        v.display();
    }
}
```

Using Polymorphism at run time, Java knows which exact function to call based on the reference it has.

`Shape.java`
```
package Polymorphism_2;

public class Shape {
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

    double calculateArea()
    {
        return 0.0;
    }
}
```
`Rectangle.java`
```
package Polymorphism_2;

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

```
package Polymorphism_2;

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
```
package Polymorphism_2;

public class Driver {
    public static void main(String[] args) {
        
        Shape shapes[] = new Shape[5];
        shapes[0] = new Triangle(10.0, 5.0, "Triangle 1");
        shapes[1] = new Triangle(15.0, 15.0, "Triangle 2");
        shapes[2] = new Rectangle(10.0, 10.0, "Rectangle 1");
        shapes[3] = new Rectangle(20.0, 1.0, "Rectangle 2");
        shapes[4] = new Shape(10.0, 1.0, "General Shape");

        for (int i = 0; i <5; i++)
        {
            System.out.println("Shape is " + shapes[i].name);
            System.out.println("Area is " + shapes[i].calculateArea());
        }
    }
}
```
