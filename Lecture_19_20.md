# AVL Trees (Balanced Trees)
AVL trees help solving worst case scenario of Binary Search Trees

`AVL_Tree.java`
```
package AVL_Tree;

class Node
{
    int value;
    int height;
    Node left;
    Node right;

    Node(int value)
    {
        this.value = value;
        height = 1;
    }
}

public class AVL {
    
    Node root;

    void insertion(int value)
    {
        root = insertNode(root, value);
    }

    Node insertNode(Node node, int value)
    {
        if (node == null)
        {
            return new Node(value);
        }
        if (value < node.value)
        {
            node.left = insertNode(node.left, value);
        }
        else if (value > node.value)
        {
            node.right = insertNode(node.right, value);
        }
        else
        {
            return node;
        }
        node.height = getMax(getHeight(node.left), getHeight(node.right)) + 1;
        int balanceFactor = getBalanceFactor(node);

        if (balanceFactor > 1)
        {
            if (value < node.left.value)
            {
                return rightRotate(node);
            }
            else
            {
                node.left = leftRotate(node.left);
                return rightRotate(node);
            }
        }
        if (balanceFactor < -1)
        {
            if (value > node.right.value)
            {
                return leftRotate(node);
            }
            else
            {
                node.right = rightRotate(node.right);
                return leftRotate(node);
            }
        }
        return node;
    }
    Node rightRotate(Node node)
    {
        Node newRoot = node.left;
        node.left = newRoot.right;
        newRoot.right = node;
        node.height = getMax(getHeight(node.left), getHeight(node.right)) + 1;
        newRoot.height = getMax(getHeight(newRoot.left), getHeight(newRoot.right)) + 1;
        return newRoot;
    }
    Node leftRotate(Node node)
    {
        Node newRoot = node.right;
        node.right = newRoot.left;
        newRoot.left = node;
        node.height = getMax(getHeight(node.left), getHeight(node.right)) + 1;
        newRoot.height = getMax(getHeight(newRoot.left), getHeight(newRoot.right)) + 1;
        return newRoot;
    }
    int getHeight(Node node)
    {
        if (node == null)
        {
            return 0;
        }
        return node.height;
    }
    int getMax(int a, int b)
    {
        return (a > b) ? a : b;
    }
    int getBalanceFactor(Node node)
    {
        if (node == null)
        {
            return 0;
        }
        return getHeight(node.left) - getHeight(node.right);
    }
    void preOrder(Node node)
    {
        if (node == null)
        {
            return;
        }
        else
        {
            System.out.println(node.value + " ");
            preOrder(node.left);
            preOrder(node.right);
        }
    }
    
}
```
`Driver.java`
```
package AVL_Tree;

public class Driver {
    public static void main(String[] args) {
        AVL tree = new AVL();
        tree.insertion(10);
        tree.insertion(20);
        tree.insertion(30);
        tree.insertion(40);
        tree.insertion(50);
        tree.insertion(25);
        tree.preOrder(tree.root);
    }
}
```
