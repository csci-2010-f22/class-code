# Hashing - HashMap

Hashmaps are used to improve efficiency while searching

`HashMap.java`
```Java
package HashMaps;

class Node
{
    int key;
    int value;
    Node next;

    Node(int key, int value)
    {
        this.key = key;
        this.value = value;
    }
    int getValue()
    {
        return this.value;
    }
    int getKey()
    {
        return this.key;
    }
    void setValue(int value)
    {
        this.value = value;
    }
}

public class HashMap {

    Node table[];
    int size;

    HashMap(int size)
    {
        this.size = size;
        table = new Node[size];
    }

    void put(int key, int value)
    {
        int hash = key % size;

        Node node = table[hash];

        if (node == null)
        {
            table[hash] = new Node(key, value);
        }
        else
        {
            while (node.next != null)
            {
                // update the value of the key
                if (node.getKey() == key)
                {
                    node.setValue(value);
                    return;
                }
                node = node.next;
            }

            if (node.getKey() == key)
            {
                node.setValue(value);
                return;
            }
            node.next = new Node(key, value);
        }
    }
    
    int get(int key)
    {
        int hash = key % size;
        Node node = table[hash];

        if (node == null)
        {
            return -1;
        }

        while (node != null)
        {
            if (node.getKey() == key)
            {
                return node.getValue();
            }
            node = node.next;
        }
        return -1;
    }
    
}
```

`Driver.java`
```Java
package HashMaps;

public class Driver {
    public static void main(String[] args) {
        HashMap map = new HashMap(10);
        map.put(1, 25);
        map.put(2, 38);
        map.put(3, 46);
        map.put(4, 59);
        map.put(5, 94);
        map.put(1, 98);
        int value = 381;
        int key = 6;

        
        if ((value = map.get(key)) == -1)
        {
            System.out.println("No value found at that key");
        }
        else
        {
            System.out.printf("Value at %d: %d", key, value);
        }
    }
}
```
Java has a built in HashMap as well.
```Java
package HashMaps_Java;

import java.util.HashMap;

public class Driver {
    public static void main(String[] args) {
        HashMap<Integer, String> map = new HashMap<>();
        map.put(1, "Steve Jobs");
        map.put(2, "Bill Gates");
        map.put(3, "Elon Musk");
        map.put(4, "Jeff Bezos");
        
        System.out.println(map);

        System.out.println(map.get(2));

        System.out.println(map.containsValue("Bill Gates"));
        

    }
}
```

Find occurrences of characters in a string
```Java
package Good_String;

import java.util.HashMap;

public class Driver {

    public static boolean areOccurrencesEqual(String s) 
    {
        HashMap<Character, Integer> map = new HashMap<>();

        for (char ch: s.toCharArray())
        {
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        }

        for (char key: map.keySet())
        {
            if (map.get(key) != map.get(s.charAt(0)))
            {
                return false;
            }
        }
        return true;
    }
    public static void main(String[] args) {
        String string = new String("abbaccd");

        if (areOccurrencesEqual(string))
        {
            System.out.println("Good String");
        }
        else
        {
            System.out.println("Bad String");
        }
    }
}
```

Find at least one occurrence of each English alphabet in a string
```java
import java.util.HashSet;

public class Driver {

    public static boolean isPangram(String sentence) {
        HashSet<Character> set = new HashSet<>();
        for (char c : sentence.toCharArray()) {
            if (Character.isLetter(c)) {
                char lowercaseC = Character.toLowerCase(c);
                set.add(lowercaseC);
            }
        }
        return set.size() == 26;
    }

    public static void main(String[] args) {
        String sentence = "thequickbrownfoxjumpsoverthelazydog";
        boolean result = isPangram(sentence);
        System.out.println(result);
    }
}
```
