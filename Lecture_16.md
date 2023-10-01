# Advanced Sorting in Java
One of quickest ways of sorting is Quick Sort that uses pivot for sorting. It is also an example of Divide and Conquer where collections are first partitioned into smaller collections and then they are recursively sorted.
```Java
package Quick_Sort;

import java.util.Arrays;

public class Driver {

    public static void swap(int[] numbers, int i, int j)
    {
        int temp = numbers[i];
        numbers[i] = numbers[j];
        numbers[j] = temp;
    }
    public static int partition(int[] numbers, int start, int end)
    {
        int pivot = numbers[end];
        int i = start - 1;

        for (int j=start; j<end; j++)
        {
            if (numbers[j] < pivot)
            {
                i++;
                // Swapping numbers smaller than pivot
                int temp = numbers[i];
                numbers[i] = numbers[j];
                numbers[j] = temp;
            }
        }
        i++;
        //Swapping pivot with the last number next to smaller numbers
        int temp = numbers[i];
        numbers[i] = pivot;
        numbers[end] = temp;
        return i;
    }

    public static void quickSort(int[] numbers, int start, int end)
    {
        if (start < end)
        {
            int pivotIndex = partition(numbers, start, end);
            quickSort(numbers, start, pivotIndex - 1);
            quickSort(numbers, pivotIndex + 1, end);
        }
    }
    public static void main(String[] args) {
        int[] numbers = new int[]{8, 2, 7, 3, 10, 15, 6};
        System.out.println(Arrays.toString(numbers));
        quickSort(numbers, 0, numbers.length-1);
        System.out.println(Arrays.toString(numbers));
    }
}
```
Sorting String using Quick Sort
```Java
import java.util.Arrays;

public class Driver {

    public static int partition(String[] strings, int start, int end)
    {
        String pivot = strings[end];
        int i = start - 1;

        for (int j=start; j<end; j++)
        {
            if (strings[j].compareTo(pivot) < 0)
            {
                i++;
                // Swapping numbers smaller than pivot
                String temp = strings[i];
                strings[i] = strings[j];
                strings[j] = temp;
            }
        }
        i++;
        //Swapping pivot with the last number next to smaller numbers
        String temp = strings[i];
        strings[i] = pivot;
        strings[end] = temp;
        return i;
    }

    public static void quickSort(String[] strings, int start, int end)
    {
        if (start < end)
        {
            int pivotIndex = partition(strings, start, end);
            quickSort(strings, start, pivotIndex - 1);
            quickSort(strings, pivotIndex + 1, end);
        }
    }
    public static void main(String[] args) {

        String[] strings = new String[]{"Toronto", "Ottawa", "Oshawa", "Whitby", "Ajax"};
        System.out.println(Arrays.toString(strings));
        quickSort(strings, 0, strings.length-1);
        System.out.println(Arrays.toString(strings));
        
    }
}
```
Sorting string by length using Quick Sort
```Java
public class Driver {

    public static int partition(String[] strings, int start, int end)
    {
        String pivot = strings[end];
        int i = start - 1;

        for (int j=start; j<end; j++)
        {
            if (strings[j].length() < pivot.length())
            {
                i++;
                // Swapping numbers smaller than pivot
                String temp = strings[i];
                strings[i] = strings[j];
                strings[j] = temp;
            }
        }
        i++;
        //Swapping pivot with the last number next to smaller numbers
        String temp = strings[i];
        strings[i] = pivot;
        strings[end] = temp;
        return i;
    }

    public static void quickSort(String[] strings, int start, int end)
    {
        if (start < end)
        {
            int pivotIndex = partition(strings, start, end);
            quickSort(strings, start, pivotIndex - 1);
            quickSort(strings, pivotIndex + 1, end);
        }
    }
    public static void main(String[] args) {

        String[] strings = new String[]{"abcd", "ab", "abc", "abcde", "a"};
        System.out.println(Arrays.toString(strings));
        quickSort(strings, 0, strings.length-1);
        System.out.println(Arrays.toString(strings));
        
    }
}
```
Sort a String Sentence
```Java
package Sort_Sentence;

public class Driver {

    public static String sortSentence(String sentence)
    {
        String[] words = sentence.split(" ");
        String[] answer = new String[words.length];

        for (String word: words)
        {
            int i = word.length() - 1;
            int index = word.charAt(i) - '0';
            answer[index-1] = word.substring(0, i);
        }
        return String.join(" ", answer);
    }
    public static void main(String[] args) {
        System.out.println(sortSentence("is2 sentence4 This1 a3"));
    }
}
```
