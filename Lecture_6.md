# Big O 

Constant time function is when the runtime does not increase with the increase in the size of the array
```Java
package Big_O;

public class Driver {

    public static int constant_function(int arr[])
    {
        int number = 0;  // O(1)
        return number;   // O(1)
	
	// total time = O(1) + O(1) = O(2) which is constant
    }
    public static void main(String[] args) {

        int arr[] = new int[5];
        constant_function(arr);
        
    }
    
}
```
Linear time function is when the runtime increases with the increase in the size of the array or size of the input
```java
    public static int linear_function(int arr[])
    {
        int sum = 0;  // O(1)
        for (int i=0; i<arr.length; i++)   // this runs n times
        {
            sum+=i;   // O(1)
        }
        return sum;   // O(1)

    // total time = O(1) + n x O(1) + O(1) = O(n)
    }
```
Even will multiple loops, we still get linear time
```java
    public static void sum_product(int arr[])
    {
        int sum = 0;  // O(1)
        for (int i=0; i<arr.length; i++)   // this runs n times
        {
            sum+=i;   // O(1)
        }
        System.out.println("Sum: " + sum);   // O(1)
        
        int product = 0;  // O(1)
        for (int i=0; i<arr.length; i++)   // this runs n times
        {
            product*=i;   // O(1)
        }
        System.out.println("Product: " + product);  // O(1)

        // total time = O(1) + n x O(1) + O(1) + O(1) + n x O(1) + O(1) = O(2n) = O(n)
    }
```
Quadratic Time is when nested loops come into play
```java
    public static void pairs(int arr[])
    {
        for (int i=0; i<arr.length; i++)  // this runs n times
        {
            for (int j=0; j<arr.length; j++)  // this runs n times
            {
                System.out.printf("(%d,%d)", arr[i], arr[j]); // O(1)
            }
        }
         // total time = O(n) x O(n) x O(1) = O(n^2)
    }
    public static void main(String[] args) {

        int arr[] = new int[]{1, 2, 3, 4, 5};
        pairs(arr); 
    }
```
Calculating time with two arrays of different sizes
```Java
public static void two_arrays(int arr1[], int arr2[])
    {
        for (int i=0; i<arr1.length; i++)  // this runs n times
        {
            for (int j=0; j<arr2.length; j++) // this runs m times
            {
                System.out.printf("(%d,%d)", arr1[i], arr2[j]);  //O(1)
            }
        }
        // total time = O(n) x O(m) x O(1) = O(nxm)
    }
    public static void main(String[] args) {

        int arr1[] = new int[]{1, 2, 3, 4, 5};
        int arr2[] = new int[]{6, 7, 8};
        two_arrays(arr1, arr2); 
    }
```