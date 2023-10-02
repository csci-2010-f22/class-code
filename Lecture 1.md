# Introduction to Java

Java uses classes to create a program
```Java
public class HelloWorld
{
    public static void main(String[] args)
    {
        System.out.println("Hello World");
    }
}

```
In order to show something on the console, a static object System.out is used with functions like print() and println()
```Java
public class HelloWorld
{
    public static void main(String[] args)
    {
        System.out.print("Hello World");
        System.out.print("Ontario Tech");
    }
}
```

Word `static` means it is a class level function and not an object/instance level function. So you can access this function without creating an object of a class. You can create more than one static function in a class.
```Java
public class HelloWorld
{
    public static void main(String[] args)
    {
        System.out.println("Hello World");
        test();
    }

    public static void test()
    {
        System.out.println("This is another static function");
    }
}
```
Member functions can also be used in Java that would require you to create an object/instance of a class to access them. These functions cannot be accessed without an object. So the following code will produce an error.
```Java
public class Testing {


    public void test()
    {
        System.out.println("This is a member function");
    }
    public static void main(String[] args) {
        test();
    }
    
}
```
In order to fix the above code, an instance of the class is required. Below is the correct code.
```Java
public class Testing {


    public void test()
    {
        System.out.println("This is a member function");
    }
    public static void main(String[] args) {
        Testing testing = new Testing();
        testing.test();
    }
    
}
```
More than 1 member function can be created inside a class like C++
```Java
public class Testing {


    public void test()
    {
        System.out.println("This is a member function");
    }

    public void test_2()
    {
        System.out.println("This is another member function");
    }
    public static void main(String[] args) {
        Testing testing = new Testing();
        testing.test();
        testing.test_2();
    }
    
}
```