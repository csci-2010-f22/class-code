# Sorting in Java I
After Bubble Sort, selection sort is one of the simplest sorting algorithms.
```
package Selection_Sort;

import java.util.Arrays;

public class Driver {
    public static void selectionSort(int[] numbers)
    {
        int size = numbers.length;

        for (int i=0; i<size-1; i++)
        {
            int smallest = i;

            for (int j=i+1; j<size; j++)
            {
                if (numbers[smallest] > numbers[j])
                {
                    smallest = j;
                }
            }

            int temp = numbers[smallest];
            numbers[smallest] = numbers[i];
            numbers[i] = temp;
        }
    }
    public static void main(String[] args) {
        int[] numbers = new int[]{7, 10, 8, 1, 9, 2, 4, 3};
        System.out.println(Arrays.toString(numbers));
        selectionSort(numbers);
        System.out.println(Arrays.toString(numbers));
    }
}
```
Another approach to sort is using insertion sort
```
package Insertion_Sort;

import java.util.Arrays;

public class Driver {
    public static void insertionSort(int[] numbers)
    {
        int size = numbers.length;

        for (int i=1; i<size; i++)
        {
            int current = numbers[i];
            int j = i - 1;

            while (j >=0 && current<numbers[j])
            {
                numbers[j+1] = numbers[j];
                j--;
            }
            numbers[j+1] = current;
        }
    }
    public static void main(String[] args) {
        int[] numbers = new int[]{7, 10, 8, 1, 9, 2, 4, 3};
        System.out.println(Arrays.toString(numbers));
        insertionSort(numbers);
        System.out.println(Arrays.toString(numbers));
    }
}
```

Sorting LinkedLists using Selection Sort
```
package LinkedList_Selection_Sort;

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

    public static void selectionSort(Node head)
    {
        Node pointer = head;
    
        while (pointer != null) 
        {
            Node smallest = pointer;
            Node currentNode = pointer.next;
  
            while (currentNode != null) 
            {
                if (smallest.value > currentNode.value)
                {
                    smallest = currentNode;
                }
                  
                currentNode = currentNode.next;
            }
  
            int temp = pointer.value;
            pointer.value = smallest.value;
            smallest.value = temp;
            pointer = pointer.next;
        }
}

    public static void printList(Node head)
    {
        Node currentNode = head;
        while (currentNode != null) 
        {
            System.out.print(currentNode.value + " ");
            currentNode = currentNode.next;
        }
    }

    public static void main(String[] args) {

        Node head = new Node(5);
        head.next = new Node(1);
        head.next.next = new Node(7);
        head.next.next.next = new Node(3);
        head.next.next.next.next = new Node(4);

        printList(head);
        System.out.println();
        selectionSort(head);
        printList(head);
        
    }
}
```