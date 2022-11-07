# Trees and Binary Search Trees
Binary Search Trees can be implemented using recursive and iterative approach. Below is the iterative approach

`BinarySearchTree.java`
```
class Node
{
    int value;
    Node left;
    Node right;

    Node(int value)
    {
        this.value = value;
    }
}

public class BinarySearchTree 
{
    Node root;

    public void insertNode(int value)
    {
        Node node = new Node(value);

        if (root == null)
        {
            root = node;
        }
        else
        {
            Node currentNode = root;
            Node parent;
            while (true)
            {
                parent = currentNode;
                if (value < currentNode.value)
                {
                    currentNode = currentNode.left;
                    if (currentNode == null)
                    {
                        parent.left = node;
                        return;
                    }
                }
                else
                {
                    currentNode = currentNode.right;
                    if (currentNode == null)
                    {
                        parent.right = node;
                        return;
                    }
                }
            }
        }

        // Time Complexity if O(n)
        // Space Complexity is O(n)
    }

    public void printNodes()
    {
        Stack<Node> stack = new Stack<>();
        Node currentNode = root;

        while (currentNode!=null || !stack.empty())
        {
            if (currentNode!=null)
            {
                stack.push(currentNode);
                currentNode = currentNode.left;
            }
            else
            {
                currentNode = stack.pop();
                System.out.println(currentNode.value);
                currentNode = currentNode.right;
            }
        }

        // Time Complexity if O(n)
        // Space Complexity is O(n)
    }

}
```
`Driver.java`
```
package BST;


public class Driver {


    public static void main(String[] args) {
        BinarySearchTree tree = new BinarySearchTree();
        tree.insertNode(5);
        tree.insertNode(10);
        tree.insertNode(2);
        tree.insertNode(11);
        tree.insertNode(1);
        tree.insertNode(3);
        tree.insertNode(20);
        tree.insertNode(15);
        tree.insertNode(90);

        tree.printNodes();
    }
}
```
Binary Search Trees are very efficient when it comes to searching
```
public Node search(int value)
    {
        Node currentNode = root;

        while (currentNode.value != value)
        {
            if (value < currentNode.value)
            {
                currentNode = currentNode.left;
            }
            else
            {
                currentNode = currentNode.right;
            }

            if (currentNode == null)
            {
                return null;
            }
        }
        return currentNode;

        // Time Complexity: O(logn)
        // Space Complexity: O(n)
    }
```
Recursion can be used to simplify the code for insertion as below:
```
public void insertion(int value)
    {
        root = insertNode_recursion(root, value);
    }

    public Node insertNode_recursion(Node root, int value)
    {
        if (root == null)
        {
            root = new Node(value);
            return root;
        }
        else if (value < root.value)
        {
            root.left = insertNode_recursion(root.left, value);
        }
        else
        {
            root.right = insertNode_recursion(root.right, value);
        }
        return root;
    }
```
Recursion can be used for Search as well
```
public Node search_recursion(Node root, int value)
    {
        if (root == null || root.value == value)
        {
            return root;
        }
        if (value < root.value)
        {
            return search_recursion(root.left, value);
        }
        else
        {
            return search_recursion(root.right, value);
        }
    }

    public void search_it(int value)
    {
        if (search_recursion(root, value) == null)
        {
            System.out.println("\nElement not found");
        }
        else
        {
            System.out.println("\nElement found");
        }
    }
```