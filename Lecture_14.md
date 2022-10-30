# Divide and Conquer Algorithm

Divide and Conquer is a technique that is used to split a problem into smaller problems.

Merge Sort is one of such applications that uses Divide and Conquer
```
package MergeSort;

import java.util.Arrays;

public class Driver {

    public static void mergeSort(int[] numbers)
    {
        int size = numbers.length;

        if (size < 2)
        {
            return;
        }

        int mid = size / 2;

        int[] s1 = new int[mid];
        int[] s2 = new int[size - mid];

        // fill in left side array
        for (int i =0; i<mid; i++)
        {
            s1[i] = numbers[i];
        }

        // fill in right side array
        for (int i = mid; i<size; i++)
        {
            s2[i - mid] = numbers[i];
        }

        mergeSort(s1);
        mergeSort(s2);

        merge(numbers, s1, s2);

        // Time Complexity = O(nlogn)
    }

    public static void merge(int numbers[], int s1[], int s2[])
    {
        int s1_size = s1.length;
        int s2_size = s2.length;

        int i = 0, j = 0, k = 0;

        while (i < s1_size && j <s2_size)
        {
            if (s1[i]<=s2[j])
            {
                numbers[k] = s1[i];
                i++;
            }
            else
            {
                numbers[k] = s2[j];
                j++;
            }
            k++;
        }

        while (i < s1_size)
        {
            numbers[k] = s1[i];
            k++;
            i++;
        }
        while (j <s2_size)
        {
            numbers[k] = s2[j];
            k++;
            j++;
        }
    }
    public static void main(String[] args) {
        int[] numbers = new int[] {7, 10, 8, 1, 9, 2, 4, 3};
        System.out.println(Arrays.toString(numbers));
        mergeSort(numbers);
        System.out.println(Arrays.toString(numbers));
    }
}
```
Find Min and Max from array can also be solved using Divide and Conquer
```
package MinMax;

import java.util.Arrays;

public class Driver {

    public static int[] findMinMax(int A[], int start, int end)
    {
        int max;
        int min;
        if ( start == end )
        {
            max = A[start];
            min = A[start];
        }
        else if ( start + 1 == end )
        {
            if ( A[start] < A[end] )
            {
                max = A[end];
                min = A[start];
            }
            else
            {
                max = A[start];
                min = A[end];
            }
        }
        else
        {
            int mid = start + (end - start)/2;
            int left[] = findMinMax(A, start, mid);
            int right[] = findMinMax(A, mid+1, end);
            
            if ( left[0] > right[0] )
                max = left[0];
            else
                max = right[0];
            if ( left[1] < right[1] )
                min = left[1];
            else
                min = right[1];
        }
        int ans[] = {max, min};
        return ans;
    }
    
    public static void main(String[] args) {

        int numbers[] = new int[]{7, 10, 8, 1, 9, 2, 4, 3};

        System.out.println(Arrays.toString(findMinMax(numbers, 0, numbers.length-1)));
        
    }
}
```