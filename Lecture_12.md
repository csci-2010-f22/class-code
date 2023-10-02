# Circular and Doubly Linked Lists

Doubly Linkedlist is a type of linkedlist that keeps track of forward and backward nodes.

`LinkedList.java`

```Java
package Doubly_LinkedList;

class Node
{
    public int data;
    public Node next;
    public Node previous;

    public Node(int data)
    {
        this.data = data;
    }
}


public class LinkedList {

    Node head, tail;

    LinkedList()
    {
        this.head = null;
        this.tail = null;
    }

    public void insertElement(int number)
    {
        Node node = new Node(number);

        if (this.head == null)
        {
            this.head = node;
            this.tail = head;
            this.head.next = null;
            this.head.previous = null;
        }
        else
        {
            Node currentNode = this.head;
            while (currentNode.next != null)
            {
                currentNode = currentNode.next;
            }
            tail = node;
            currentNode.next = tail;
            tail.previous = currentNode;
            tail.next = null;       
        }
    }
    public void printForward()
    {
        Node currentNode = this.head;

        if (this.head == null)
        {
            System.out.println("List is empty");
        }

        while (currentNode != null)
        {
            System.out.println(currentNode.data);
            currentNode = currentNode.next;
        }
    }
```

`Driver.java`
```Java
package Doubly_LinkedList;

public class Driver {
    public static void main(String[] args) {
        LinkedList list = new LinkedList();
        list.insertElement(2);
        list.insertElement(4);
        list.insertElement(6);
        list.insertElement(8);
        list.insertElement(10);

        list.printForward();
    }
}
```

One of the advantages of DoublyLinkedList is that you can traverse in the backward direction.
```Java
public void printBackward()
    {
        Node currentNode = this.tail;

        if (this.tail == null && this.head == null)
        {
            System.out.println("List is empty");
        }

        while (currentNode != null)
        {
            System.out.println(currentNode.data);
            currentNode = currentNode.previous;
        }
    }
```

Java has a built-in LinkedList class with some useful methods. Below is a simple LinkedList

`Driver.java`
```Java
package LinkedList_Class;

import java.util.LinkedList;

public class Driver {
    
    public static void main(String[] args) {
        LinkedList<Integer> list = new LinkedList<>();
        list.add(2);
        list.add(4);
        list.add(6);
        list.add(8);
        list.add(10);

        System.out.println(list);
    }
}
```
We can remove, add at specific index or modify elements of the linked list

Below will remove elements from a specific index in the list
`list.remove(2);`

Below will add element at a specific index in the list
`list.add(1, 5);`

Below will modify an element at a specific index
`list.set(1, 5);`

Below will help in iterating through the elements of LinkedList
```Java
for (int item : list)
{
        System.out.println(item);
}
```
LinkedList can be pretty handy in solving some mathematical problems like converting binary to decimal
```Java
public class Driver {

    public static int convert(LinkedList<Integer> list)
    {
        int result = list.getFirst();

        for (int i = 1; i< list.size(); i++)
        {
            result = result * 2 + list.get(i);
        }
        
        return result;
    }
    public static void main(String[] args) {
        LinkedList<Integer> list = new LinkedList<>();
        list.add(1);
        list.add(0);
        list.add(1);
        list.add(0);

        System.out.println(convert(list));
    }
}
```
To further practice, lets remove duplicates from the LinkedList but by implementing from scratch

`Driver.java`
```Java
package Remove_Duplicates;

class Node
{
    int value;
    Node next;

    Node(int value)
    {
        this.value = value;
    }

}

public class Driver {

    public static Node deleteDuplicates(Node head)
    {
        Node currentNode = head;

        while (currentNode != null && currentNode.next != null)
        {

            if (currentNode.value == currentNode.next.value)
            {
                currentNode.next = currentNode.next.next;
            }
            else
            {
                currentNode = currentNode.next;
            }

        }
        return head;
    }

    public static void print(Node node)
    {
        Node currentNode = node;

        while(currentNode != null)
        {
            System.out.println(currentNode.value);
            currentNode = currentNode.next;
        }
    }

    public static void main(String[] args) {
        Node head = new Node(1);
        head.next = new Node(1);
        head.next.next = new Node(2);
        head.next.next.next = new Node(2);
        deleteDuplicates(head);
        print(head);
        
    }
    
}
```