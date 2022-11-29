# Coding Exercises Solution (Week 13)

Q1: Hashmap
```
package HashMap;

import java.util.Arrays;
import java.util.Collections;
import java.util.HashMap;

public class Driver {

    public static String[] sortByWins(String[] players, Integer[] wins)
    {
        HashMap<Integer, String> map = new HashMap<>();

        for (int i=0; i<players.length; i++)
        {
            map.put(wins[i], players[i]);
        }
        Arrays.sort(wins, Collections.reverseOrder());
        String[] result = new String[wins.length];
        for (int i=0; i<wins.length; i++)
        {
            result[i] = map.get(wins[i]);
            result[i] = result[i] + ": " + wins[i];
        }
        return result;
        // Time Complexity: O(nlogn)
        // Space Complexity: O(n)
    }

    public static void main(String[] args) {
        String[] players = new String[]{
            "Pete Sampras", "Novak Djokovic", "Roger Federer", "Roy Emerson", "Rafael Nadal", "Bjorn Borg"
        };

        Integer[] wins = new Integer[]{
            14, 21, 20, 12, 22, 11
        };

        for (String result: sortByWins(players, wins))
        {
            System.out.println(result);
        }
        
    }
}
```
Q2: Linked List
```
package LinkedList;

class Node
{
    String value;
    Node next;

    Node()
    {
        this.value = "";
    }

    Node(String value)
    {
        this.value = value;
    }
}

public class Driver {

    public static Node removeCitiesWithO(Node head)
    {
        if (head == null)
        {
            return null;
        }

        Node temp = new Node();
        temp.next = head;
        Node currentNode = temp;

        while (currentNode.next != null)
        {
            if (currentNode.next.value.contains("O") || currentNode.next.value.contains("o"))
            {
                currentNode.next = currentNode.next.next;
            }
            else
            {
                currentNode = currentNode.next;
            }
        }
        return temp.next;
        // Time Complexity = O(n^2)
        // Space Complexity = O(1)
    }

    public static void printList(Node head)
    {
        Node currentNode = head;
        while (currentNode!=null)
        {
            System.out.print(currentNode.value + " | ");
            currentNode = currentNode.next;
        }
        // Time Complexity = O(n)
        // Space Complexity = O(1)
    }
    public static void main(String[] args) 
    {
        Node head = new Node("Toronto");
        head.next = new Node("Oshawa");
        head.next.next = new Node("Ajax");
        head.next.next.next = new Node("Whitby");
        head.next.next.next.next = new Node("Markham");

        System.out.println("\nOriginal Linked List...");
        printList(head);

        System.out.println("\n\nModified Linked List...");
        printList(removeCitiesWithO(head));
        
    }
}
```

Q3: Trees
```
package Trees;

class Student
{
    String name;
    int marks;

    Student(String name, int marks)
    {
        this.name = name;
        this.marks = marks;
    }
    public String toString()
    {
        return this.name + ": " + this.marks;
    }
}

class Node
{
    Student student;
    Node left;
    Node right;

    Node(Student student)
    {
        this.student = student;
    }
    Node(Student student, Node left, Node right)
    {
        this.student = student;
        this.left = left;
        this.right = right;
    }
}

public class Driver {

    public static Node updateMarks(Node root_A, Node root_B)
    {
        if (root_A == null)
        {
            return root_B;
        }
        if (root_B == null)
        {
            return root_A;
        }

        if (root_A.student.marks < root_B.student.marks)
        {
            root_A.student.marks = root_B.student.marks;
        }
        root_A.left = updateMarks(root_A.left, root_B.left);
        root_A.right = updateMarks(root_A.right, root_B.right);
        return root_A;

        // Time Complexity: O(n)
        // Space Complexity: O(n)
    }

    public static void preOrder(Node root)
    {
        if (root == null)
        {
            return;
        }
        System.out.println(root.student.toString());
        preOrder(root.left);
        preOrder(root.right);

        // Time Complexity: O(n)
        // Space Complexity: O(n)
    }
    public static void main(String[] args) {
        Node quiz_A = new Node(new Student("Steve", 85));
        quiz_A.left = new Node(new Student("Bill", 65));
        quiz_A.right = new Node(new Student("Elon", 90));
        quiz_A.left.left = new Node(new Student("Jeff", 55));
        
        Node quiz_B = new Node(new Student("Steve", 88));
        quiz_B.left = new Node(new Student("Bill", 75));
        quiz_B.right = new Node(new Student("Elon", 90));
        quiz_B.left.right = new Node(new Student("Lizzy", 80));
        quiz_B.right.right = new Node(new Student("Sheena", 95));

        System.out.println("\nQuiz A...");
        preOrder(quiz_A);

        System.out.println("\nQuiz B...");
        preOrder(quiz_B);

        System.out.println("\nResultant Tree");
        preOrder(updateMarks(quiz_A, quiz_B));
    }
}
```

