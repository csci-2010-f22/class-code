# Stacks and Queues

Java has a built-in class for Stack under java.util package.
```
package Stack_Class;

import java.util.Scanner;
import java.util.Stack;

public class Driver {
    
    public static void pushElements(Stack<Integer> stack)
    {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the size of the stack: ");
        int size = scanner.nextInt();

        for (int i=0; i<size; i++)
        {
            System.out.print("Enter element: ");
            stack.push(scanner.nextInt());
        }

        scanner.close();    
    }

    public static void popElements(Stack<Integer> stack)
    {
        while(!stack.isEmpty())
        {
            System.out.println("Element " + stack.pop() + " popped");
        }
    }

    public static void searchElement(Stack<Integer> stack, int number)
    {
        int pos = stack.search(number);

        if (pos == -1)
        {
            System.out.println("Item not found!");
        }
        else
        {
            System.out.println("Item found at index " + pos);
        }
    }
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();
        pushElements(stack);
        searchElement(stack, 5);
        //popElements(stack);
        
    }
}
```

Stacks can help in validating an equation. Assume an equation in the form of a string which has characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
```
package Valid_Parenthesis;

import java.util.Stack;

public class Driver {

    public static boolean isValid(String str) 
    {
        Stack<Character> stack = new Stack<>();

        for (char c: str.toCharArray())
        {
            if (c == '(' || c == '{'|| c == '[')
            {
                stack.push(c);
            }
            else if (stack.empty())
            {
                return false;
            }
            else if ((c == ')' && stack.pop() != '(' ) || (c == '}' && stack.pop() != '{') || (c == ']' && stack.pop() != '['))
            {
                return false;
            }

        }
        return stack.empty();
    }

    public static void main(String[] args) 
    {
        System.out.println(isValid("()"));  
    }
}
```

Remove all the consecutive duplicates from the string using stack.
```
package Remove_Duplicates;

import java.util.Stack;

public class Driver {
    
    public static String removeDuplicates(String str) 
    {
        Stack<Character> stack = new Stack<>();
        StringBuilder result = new StringBuilder();

        for (char c: str.toCharArray())
        {
            if (!(stack.isEmpty()) && stack.peek() == c )
            {
                stack.pop();
            }
            else
            {
                stack.push(c);
            }
        }

        while (!stack.isEmpty())
        {
            result.append(stack.pop());
        }

        return result.reverse().toString();
        
    }
    public static void main(String[] args) {

        System.out.println(removeDuplicates("abccbz"));
        
    }
}
```

Java has some built-in classes and intefaces for queue as well. PriorityQueue is one of them.

`Driver.java`
```
package PriorityQueue_Class;

import java.util.PriorityQueue;
import java.util.Scanner;

public class Driver {

    public static void pushElements(PriorityQueue<Integer> queue)
    {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the size of the queue: ");
        int size = scanner.nextInt();

        for (int i=0; i<size; i++)
        {
            System.out.print("Enter element to push: ");
            queue.add(scanner.nextInt());
        }
        scanner.close();
    }

    public static void print(PriorityQueue<Integer> queue)
    {
        System.out.println(queue);
        // while (!queue.isEmpty())
        // {
        //     System.out.println(queue.element());
        //     queue.poll();
        // }
    }
    public static void main(String[] args) {
        PriorityQueue<Integer> queue = new PriorityQueue<>();

        pushElements(queue);
        print(queue);
    }
}
```


A java program that returns the max. product of 2 elements from an array using PriorityQueue.
```
package Maximum_Product;

import java.util.Collections;
import java.util.PriorityQueue;

public class Driver {

    public static int max_product(int[] numbers)
    {
        PriorityQueue<Integer> queue = new PriorityQueue<>(Collections.reverseOrder());

        for (int number: numbers)
        {
            queue.add(number);
        }
        
        // while(!queue.isEmpty())
        // {
        //     System.out.println(queue.poll());
        // }
        int result = queue.poll() * queue.poll();
        return result;

    }
    
    public static void main(String[] args) {
        
        int[] numbers = new int[]{5, 2, 1, 8, 10};
        System.out.println("Max Product: " + max_product(numbers));
    }
}
```