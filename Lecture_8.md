# Collections and Array Optimizations
Java offers multi-dimensional arrays as well.
```
package MultiDim_Arrays;

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
The `ArrayList` class is a resizable array, which can be found in the `java.util package`. The difference between a built-in array and an `ArrayList` in Java, is that the size of an array cannot be modified (if you want to add or remove elements to/from an array, you have to create a new one). While elements can be added and removed from an `ArrayList` whenever you want.
```
package Array_List;

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
package Array_List;

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
`set` method cana be used to modify an element at a specific index in `ArrayList`
```
package Array_List;

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
Elements can be removed from `ArrayList` as well using remove method
```
package Array_List;

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
`ArrayList` can be used with other data types
```
package Array_List_Integers;

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
