# Recursion in Java
Java offers recursion just like C++. The program below uses recursion to find factorial of a number
```Java
public class Driver {

    public static int factorial(int n)
    {
        if (n <= 1)
        {
            return 1;
        }
        else
        {
            return n * factorial(n - 1);
        }
            // f(4) = 4 x f(3)
            // f(3) = 3 x f(2)
            // f(2) = 2 x f(1)
            // f(1) = 1 x f(0)
            // f(0) = 1
            // f(4) = O(4 + 1) and for f(n) = O(n + 1) = O(n)
    }

    public static void main(String[] args) {

        System.out.println("Factorial: " + factorial(3));
        
    }
}
```

Recursive functions can be expensive when it comes to time complexity
```java
    public static int fibonacci(int n)
    {
        if (n <= 1)
        {
            return n;
        }
        else
        {
            return fibonacci(n - 1) + fibonacci(n - 2);
        }         
                //            f(4)           L1  = 1 node = 2^0
                //         /        \      
                //     f(3)        f(2)      L2  = 2 nodes = 2^1
                //    /    \       /   \     
                //  f(2)   f(1)   f(1) f(0)  L3  = 4 nodes = 2^2
               //  /   \   
               // f(1) f(0)                  L4  = 2 nodes because it reached base case so lets ignore this level
               //                            Time Complexity = O(2^n-1) = O(2^n)
    }
    public static void main(String[] args) {
        System.out.println("Fibonacci Number: " + fibonacci(4));
        
    }
```
Power function can also be solved using recursion.
```java
    public static int power(int base, int exp)
    {
        if (exp < 0)
        {
            return 0;
        }
        else if (exp == 0)
        {
            return 1;
        }
        else
        {
            return base * power(base, exp-1);
        }
        // p(2^4) = 2 x p(2^3)
        // p(2^3) = 2 x p(2^2)
        // p(2^2) = 2 x p(2^1)
        // p(2^1) = 1
        // O(4) = if exp is 4 and hence if exp is n time complexity will be O(n)
    }
    public static void main(String[] args) {

        System.out.println("Result: " + power(2, 3));
        
    }
```
Power function can be solved without recursion with O(n)
```java
    public static int power_simple(int base, int exp)
    {
        int result = 1;
        for (int i=0; i<exp; i++)
        {
            result = result*base;
        }
        return result;
        // Time complexity = O(n)
    }
```
Remove duplicates from LinkedList using Recursion
```Java
public static Node removeDuplicates(Node node, int value)
    {
        if (node == null)
        {
            return null;
        }

        if (node.value == value)
        {
            return removeDuplicates(node.next, value);
        }
        else
        {
            node.next =  removeDuplicates(node.next, value);
        }
        return node;
	// Time: O(n)
	// Space: O(n)
    }

    public static void print(Node node)
    {
        Node currentNode = node;

        while(currentNode != null)
        {
            System.out.print(currentNode.value + " ");
            currentNode = currentNode.next;
        }
    }

    public static void main(String[] args) {
        
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(3);
        head.next.next.next = new Node(2);
        head.next.next.next.next = new Node(4);

        print(head);
        System.out.println("\nAfter remove duplicates");
        print(removeDuplicates(head, 2));
    }
```
Function can be simplified as:
```Java
public static Node removeDuplicates(Node node, int value)
    {
        if (node == null)
        {
            return null;
        }

        node.next = removeDuplicates(node.next, value);
        
        if (node.value == value)
        {
            return node.next;
        }
        else
        {
           return node;
        }

    }
```