# Arrays in Java

Just like C++, Java has collections and simplest of it is an array which is much like arrays in C++.
```
package Simple_Arrays;

/**
 * Driver
 */
public class Driver {

    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};

        for (int i = 0; i<numbers.length; i++)
        {
            System.out.println(numbers[i]);
        }
    }
}
```
Arrays can be passed to functions in Java
```
package Simple_Arrays;

/**
 * Driver
 */
public class Driver {

    public static void display(int[] numbers)
    {
        for (int i = 0; i<numbers.length; i++)
        {
            System.out.println(numbers[i]);
        }
        // Time Complexity = O(n) 
    }

    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};

        display(numbers);
    }
}
```
Arrays are passed by reference under the hood but you dont have to worry about that. It is done for you automatically.
```
package Simple_Arrays;

/**
 * Driver
 */
public class Driver {

    public static void modify(int[] numbers)
    {
        numbers[0] = 100;
    }
    public static void display(int[] numbers)
    {
        for (int i = 0; i<numbers.length; i++)
        {
            System.out.println(numbers[i]);
        }
    }

    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};

        display(numbers);
        modify(numbers);
        display(numbers);
    }
}
```
If an array in a method is assigned to another location then it would not change the original array.
```
package Simple_Arrays;

/**
 * Driver
 */
public class Driver {

    public static void modify(int[] numbers)
    {
        numbers[0] = 100;
    }
    public static void changeReference(int[] numbers)
    {
        numbers = new int[5];
        numbers[0] = 200;
    }
    public static void display(int[] numbers)
    {
        for (int i = 0; i<numbers.length; i++)
        {
            System.out.println(numbers[i]);
        }
    }

    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};

        display(numbers);
        changeReference(numbers);
        display(numbers);
    }
}
```
BTW, a variation of for loop can be used as well
```
    public static void display(int[] numbers)
    {
        for(int item: numbers)
        {
            System.out.println(item);
        }
    }

    public static void main(String[] args) {
        int numbers[] = {1, 2, 3, 4, 5};

        display(numbers);
    }
```
Getting size and elements from the user
```
package Simple_Arrays;

import java.util.Scanner;

/**
 * Driver
 */
public class Driver {

    public static void display(int[] numbers)
    {
        for(int item: numbers)
        {
            System.out.println(item);
        }
    }

    public static void getElements(int[] numbers)
    {
        Scanner scanner = new Scanner(System.in);
        
        for (int i= 0; i<numbers.length; i++)
        {
            System.out.printf("Element [%d]: ", i);
            numbers[i] = scanner.nextInt();
        }
        
        scanner.close();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("How many elements do you want to enter: ");
        int size = scanner.nextInt();

        int[] numbers = new int[size];
        getElements(numbers);

        scanner.close();

        display(numbers);
    }
}
```
Java offers other types of Arrays like String Arrays
```
package String_Arrays;

public class Driver {

    public static void display(String[] cities)
    {
        for(String city: cities)
        {
            System.out.println(city);
        }
        // Time Complexity = O(n) 
    }
    public static void main(String[] args) {
        String[] cities = new String[]{"Toronto", "New York", "Tokyo", "London"};
        display(cities);

    }
}
```
Arrays in Java offer all the traditional features like search and sort.
```
package String_Arrays;

public class Driver {

    public static void search(String[] cities)
    {
        String city_name = "Ottawa";

        for (String city: cities)
        {
            if (city.equals(city_name))
            {
                System.out.printf("%s found in the array.", city_name);
            }
        }
        // Time Complexity = O(n) 
    }

    public static void display(String[] cities)
    {
        for(String city: cities)
        {
            System.out.println(city);
        }
    }
    public static void main(String[] args) {
        String[] cities = new String[]{"Toronto", "New York", "Tokyo", "London"};
        search(cities);

    }
}
```
String has a function that allows comparison by ignoring the case
```
public static void search(String[] cities)
    {
        String city_name = "toronto";

        for (String city: cities)
        {
            if (city.equalsIgnoreCase(city_name))
            {
                System.out.printf("%s found in the array.", city_name);
            }
        }
    }

```
Just like C++, Java allows Arrays of Objects

`Student.java`
```
package Object_Arrays;

public class Student {
    String name;
    int age;

    Student(String name, int age)
    {
        this.name = name;
        this.age = age;
    }

    public String toString()
    {
        return "Name: " + this.name + ", Age: " + this.age;
    }
}
```

`Driver.java`
```
package Object_Arrays;

public class Driver {
    
    public static void display(Student[] students)
    {
        for (Student student: students)
        {
            System.out.println(student.toString());
        }
        // Time Complexity = O(n) 
    }
    public static void main(String[] args) {
        Student[] students = new Student[] {
            new Student("Steve Jobs", 55),
            new Student("Bill Gates", 65),
            new Student("Elon Musk", 45),
            new Student("Jeff Bezos", 55),
        };

        display(students);
    }
}
```
This student array can be searched for a name as well
```
public static void searchStudents(Student[] students)
    {
        for (Student student: students){
            if (student.name.equalsIgnoreCase("elon"))
            {
                System.out.printf("%s found", student.name);
            }
        }
        // Time Complexity = O(n) 
    }
```
Arrays can be sorted in ascending or descending order
```
public static void sort_students(Student students[]) {
        int n = students.length;
        boolean swapped;
        
        do {
            swapped = false;
            for (int i = 0; i < n - 1; i++) {
                if (students[i].age > students[i + 1].age) {
                    Student temp = students[i];
                    students[i] = students[i + 1];
                    students[i + 1] = temp;
                    swapped = true;
                }
            }
        } while (swapped);
        
        // Time Complexity = O(n^2)
    }
```
Arrays.sort() method can be used to sort any collection but class has to implement Comparable

`Student.java`
```
public class Student implements Comparable<Student>{
    String name;
    int age;

    public Student(String name, int age)
    {
        this.name = name;
        this.age = age;
    }
    public String toString()
    {
        return this.name + ", " + this.age;
    }
    public int compareTo(Student otherStudent)
    {
        return Integer.compare(this.age, otherStudent.age);
    }
}
```
`Driver.java`
```
import java.lang.reflect.Array;
import java.util.Arrays;

public class Driver {
    
    public static void display(Student arr[])
    {
        for (Student item: arr)
        {
            System.out.println(item.toString());
        }
        System.out.println();
    }

    public static boolean search_student(Student students[], String name)
    {
        for (Student student: students)
        {
            if (student.name.equalsIgnoreCase(name))
            {
                return true;
            }
        }
        return false;
    }

    public static void sort_students(Student students[]) {
        int n = students.length;
        boolean swapped;
        
        do {
            swapped = false;
            for (int i = 0; i < n - 1; i++) {
                if (students[i].age > students[i + 1].age) {
                    Student temp = students[i];
                    students[i] = students[i + 1];
                    students[i + 1] = temp;
                    swapped = true;
                }
            }
        } while (swapped);
    }
    
    public static void main(String[] args) {
        Student students[] = new Student[]{
            new Student("Steve", 75),
            new Student("Bill", 55),
            new Student("Jeff", 65),
            new Student("Elon", 45),
            new Student("Warren", 85),
        };
        display(students);
        Arrays.sort(students); // O(nlogn)
        display(students);
    }
}
```

Implementing Comparable is not required and Comparator can be used directly in Arrays.sort as below
```
    public static void main(String[] args) {
        Student students[] = new Student[]{
            new Student("Steve", 75),
            new Student("Bill", 55),
            new Student("Jeff", 65),
            new Student("Elon", 45),
            new Student("Warren", 85),
        };
        display(students);
        Arrays.sort(students, new Comparator<Student>() 
        {
            public int compare(Student s1, Student s2)
            {
                return Integer.compare(s1.age, s2.age);
            }
        }); // O(nlogn)
        display(students);
    }
```

Names can be compared to sort based on alphabetical order

```
    public static void main(String[] args) {
        Student students[] = new Student[]{
            new Student("Steve", 75),
            new Student("Bill", 55),
            new Student("Jeff", 65),
            new Student("Elon", 45),
            new Student("Warren", 85),
        };
        display(students);
        Arrays.sort(students, new Comparator<Student>() 
        {
            public int compare(Student s1, Student s2)
            {
                return s1.name.compareToIgnoreCase(s2.name);
            }
        });
        display(students);
    }
```