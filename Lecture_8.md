# Collections and Array Optimizations

**5-Step Process For Algorithm Analysis**

public static void display(int numbers[])
{
//Step 1: Identify Time complexity of each statemen
//            O(1)        O(n)           O(n)
        for (int i=1; i<numbers.length; i++)
        {
            System.out.println(numbers[i]); // O(1)
        }

        // Step 2: Form an equation = O(1) + O(n)*{1} + O(n) + O(1)
        // Step 3: Simplify the equation = O(2) + O(n) + O(n) = O(2) + O(2n)
        // Step 4: Identify significantly growing term = O(2n)
        // Step 5: Remove constants = O(n)
}

Java offers multi-dimensional arrays as well.
```
public class Driver {
    
    public static void display(int[][] numbers)
    {
        for (int i =0; i<numbers.length; i++)
        {
            for (int j=0; j<numbers[i].length; j++)
            {
                System.out.println(numbers[i][j]);
            }
        }
    }
    public static void main(String[] args) {
        int[][] numbers = new int[][]{{1,2,3}, {4, 5, 6}};
        display(numbers);

    }
}
```
The `ArrayList` class is a resizable array, which can be found in the java.util package. The difference between a built-in array and an ArrayList in Java, is that the size of an array cannot be modified (if you want to add or remove elements to/from an array, you have to create a new one). While elements can be added and removed from an ArrayList whenever you want.

```
import java.util.ArrayList;

public class Driver {

    public static void main(String[] args) {
        ArrayList<String> fruits = new ArrayList<String>();
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Orange");
        fruits.add("Grapes");  

        System.out.println(fruits);

    }
}
```
`ArrayList` has built-in methods like add and get to insert or get the elements.
```
import java.util.ArrayList;

public class Driver {

    public static void display(ArrayList<String> fruits)
    {
        for(int i=0; i<fruits.size(); i++)
        {
            System.out.println(fruits.get(i));
        }
    }
    public static void main(String[] args) {
        ArrayList<String> fruits = new ArrayList<String>();
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Orange");
        fruits.add("Grapes");  

        display(fruits);

    }
}
```
`set` method can be used to modify an element at a specific index in ArrayList

```
import java.util.ArrayList;

public class Driver {

    public static void modify(ArrayList<String> fruits)
    {
        fruits.set(0, "Pine Apple");
    }

    public static void display(ArrayList<String> fruits)
    {
        for(int i=0; i<fruits.size(); i++)
        {
            System.out.println(fruits.get(i));
        }
    }
    public static void main(String[] args) {
        ArrayList<String> fruits = new ArrayList<String>();
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Orange");
        fruits.add("Grapes");  

        display(fruits);
        modify(fruits);
        display(fruits);

    }
}
```
Elements can be removed from ArrayList as well using remove method

```
import java.util.ArrayList;

public class Driver {

    public static void removeByName(ArrayList<String> fruits)
    {
        fruits.remove("Apple");
        System.out.println(fruits.size());
    }
    
    public static void display(ArrayList<String> fruits)
    {
        for(int i=0; i<fruits.size(); i++)
        {
            System.out.println(fruits.get(i));
        }
    }
    public static void main(String[] args) {
        ArrayList<String> fruits = new ArrayList<String>();
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Orange");
        fruits.add("Grapes");  

        display(fruits);
        removeByName(fruits);
        display(fruits);

    }
}
```
`ArrayList`` can be used with other data types

```
import java.util.ArrayList;
import java.util.Collections;

public class Driver {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<Integer>();
        numbers.add(2);
        numbers.add(10);
        numbers.add(20);
        numbers.add(12);
        numbers.add(7);
        numbers.add(6);

        Collections.sort(numbers);

        System.out.println(numbers);
    }
}
```
Can be sorted in descending order by changing the above one line to

```
Collections.sort(numbers, Comparator.reverseOrder());
```

Comparing Strings can be done using ArrayList of Strings
```
public static boolean compareStringArrays(ArrayList<String> str1, ArrayList<String> str2)
    {
        boolean flag = true;

        for (int i =0; i <str1.size(); i++)
        {
            if (str1.get(i) != str2.get(i))
            {
                flag = false;
            }
        }
        return flag;
    }

    public static boolean compareStringArrays_better(ArrayList<String> str1, ArrayList<String> str2)
    {
        return String.join("",str1).equals(String.join("",str2));
    }
    public static void main(String[] args) {
        ArrayList<String> str1 = new ArrayList<>();
        str1.add("Toronto");
        str1.add("Ottawa");
        str1.add("Oshawa");

        ArrayList<String> str2 = new ArrayList<>();
        str2.add("Toronto");
        str2.add("Ottawa");
        str2.add("Oshawa");

        if (compareStringArrays_better(str1, str2))
        {
            System.out.println("String arrays are equal");
        }
        else{
            System.out.println("String arrays are not equal");
        }

    }
```
Similarly, we can use ArrayList for objects of classes as well and use sorting on data members of those objects as below:
```
class Student
{
    String name;
    int age;

    Student(String name, int age)
    {
        this.name = name;
        this.age = age;
    }
    public String toString()
    {
        return this.name + ", " + this.age;
    }
}

public class Driver {

    public static void main(String[] args) {
        ArrayList<Student> students = new ArrayList<Student>();
        students.add(new Student("Steve", 55));
        students.add(new Student("Bill", 65));
        students.add(new Student("Jeff", 45));
        students.add(new Student("Warren", 85));

        Collections.sort(students, new Comparator<Student>() {
            public int compare(Student s1, Student s2)
            {
                return Integer.compare(s1.age, s2.age);
            }
        });
        System.out.println(students);
    }
}
```
**Space Complexity**  
Besides Time complexity it is also important to look at the space complexity. Consider the program below which takes the running sum of the elements of an array:

```
public class Driver {

    public static int[] runningSum(int[] numbers) 
    {
        int[] result = new int[numbers.length];
        
        result[0] = numbers[0];
        for (int i = 1; i < numbers.length; i++) {
            result[i] = result[i - 1] + numbers[i];
        }

        return result;
    }

    public static void main(String[] args) {
        int[] numbers = new int[] {1,2,3,4};

        for(int number : runningSum(numbers))
        {
            System.out.println(number);
        }
    }
}
```
The space complexity of this algorithm is `O(n)` since it creates a new array of the same size as the original to store the result. This can be optimized by using the original array as a resulting array as well that would reduce the space complexity to `O(1)`:
```
public static void running_sum(int numbers[])
{
        for (int i=1; i<numbers.length; i++)
        {
            numbers[i]+= numbers[i - 1];
        }
}
```
