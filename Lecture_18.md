# Binary Tree Traversals

Tree traversals can be level wise which is also called Breadth First Traversals
```Java
public static void levelOrder(Node root)
    {
        LinkedList<Node> list = new LinkedList<>();
        list.add(root);

        while (!list.isEmpty())
        {
            Node currentNode = list.poll();
            System.out.print(currentNode.value + " ");

            if (currentNode.left != null)
            {
                list.add(currentNode.left);
            }
            if (currentNode.right != null)
            {
                list.add(currentNode.right);
            }
        }
    }
```
Traversals can be Depth First as well which are pre-order, in-order and post-order
```Java
public static void preOrder(Node root)
    {
        if (root == null)
        {
            return;
        }
        System.out.print(root.value + " ");
        preOrder(root.left);
        preOrder(root.right);
    }

    public static void inOrder(Node root)
    {
        if (root == null)
        {
            return;
        }
        inOrder(root.left);
        System.out.print(root.value + " ");
        inOrder(root.right);
    }

    public static void postOrder(Node root)
    {
        if (root == null)
        {
            return;
        }
        postOrder(root.left);
        postOrder(root.right);
        System.out.print(root.value + " ");

    }
```
Above functions can be used with the following main method
```Java
public static void main(String[] args) {

        Node root = new Node(5);
        root.left = new Node(3);
        root.right = new Node(15);
        root.left.left = new Node(2);
        root.left.right = new Node(4);
        root.right.left = new Node(12);
        root.right.right = new Node(25);

        System.out.println("Level Order Traversal");
        levelOrder(root);

        System.out.println("\nPre Order traversal:");
        preOrder(root);
        
        System.out.println("\nIn Order traversal:");
        inOrder(root);

        System.out.println("\nIn Post traversal:");
        postOrder(root);

    }
}
```
Deleting a node from the tree is pretty complicated. Deleting a node with no children is the easiest.
```Java
public static boolean delete(Node root, int value)
    {
        Node currentNode = root;
        Node parent = root;
        boolean isLeft = false;

        while (currentNode.value != value)
        {
            parent = currentNode;
            if (value < currentNode.value)
            {
                isLeft = true;
                currentNode = currentNode.left;
            }
            else
            {
                isLeft = false;
                currentNode = currentNode.right;
            }
            if (currentNode == null)
            {
                return false;
            }
        }

        if (currentNode.left == null && currentNode.right == null)
        {
            if (currentNode == root)
            {
                root = null;
            }
            else 
            {
                if (isLeft)
                {
                    parent.left = null;
                }
                else
                {
                    parent.right = null;
                }
            }
        }
        return true;
    }
```
All above examples use following Node class
```Java
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
```