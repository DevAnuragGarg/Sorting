# Sorting

Bubble Sort is the simplest sorting algorithm that works by iterating the input array from the first element to the last comparing each pair of elements and swapping them if needed. Bubble sort continues its iterations until no more swaps are needed. The algorithm gets its name from the way smaller elements "bubble" to top of the list.
Example: First Pass:
( 5 1 4 2 8 ) –> ( 1 5 4 2 8 ), Here, algorithm compares the first two elements, and swaps since 5 > 1.
( 1 5 4 2 8 ) –>  ( 1 4 5 2 8 ), Swap since 5 > 4
( 1 4 5 2 8 ) –>  ( 1 4 2 5 8 ), Swap since 5 > 2
( 1 4 2 5 8 ) –> ( 1 4 2 5 8 ), Now, since these elements are already in order (8 > 5), algorithm does not swap them.
Second Pass:
( 1 4 2 5 8 ) –> ( 1 4 2 5 8 )
( 1 4 2 5 8 ) –> ( 1 2 4 5 8 ), Swap since 4 > 2
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 )
( 1 2 4 5 8 ) –>  ( 1 2 4 5 8 )
Now, the array is already sorted, but our algorithm does not know if it is completed. The algorithm needs one whole pass without any swap to know it is sorted.
Third Pass:
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 )
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 )
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 )
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 )
Worst and Average Case Time Complexity: O(n*2). Worst case occurs when array is reverse sorted.
Best Case Time Complexity: O(n). Best case occurs when array is already sorted.
Auxiliary Space: O(1)

=======
Selection Sorting: The selection sort algorithm is an in place sorting algorithm. Selection sort works well for small files. It is used for sorting the files with large values and small keys. This is because selection is made based on keys and swaps are made only when required.
Following example explains the above steps:
arr[] = 64 25 12 22 11
// Find the minimum element in arr[0...4]
// and place it at beginning
11 25 12 22 64
// Find the minimum element in arr[1...4]
// and place it at beginning of arr[1...4]
11 12 25 22 64
// Find the minimum element in arr[2...4]
// and place it at beginning of arr[2...4]
11 12 22 25 64
// Find the minimum element in arr[3...4]
// and place it at beginning of arr[3...4]
11 12 22 25 64 
Time Complexity: O(n2) as there are two nested loops.
Auxiliary Space: O(1). The good thing about selection sort is it never makes more than O(n) swaps and can be useful when memory write is a costly operation.

=======
Insertion Sort is a simplest and efficient comparison sort. In this algorithm each iteration removes an element from the input data and inserts it into the correct position in the list being sorted. The choice of element being removed from input is random and process is repeated until all are sorted.
12, 11, 13, 5, 6
Let us loop for i = 1 (second element of the array) to 5 (Size of input array)
i = 1. Since 11 is smaller than 12, move 12 and insert 11 before 12
11, 12, 13, 5, 6
i = 2. 13 will remain at its position as all elements in A[0..I-1] are smaller than 13
11, 12, 13, 5, 6
i = 3. 5 will move to the beginning and all other elements from 11 to 13 will move one position ahead of their current position.
5, 11, 12, 13, 6
i = 4. 6 will move to position after 5, and elements from 11 to 13 will move one position ahead of their current position.
5, 6, 11, 12, 13
Time Complexity: O(n*n)
Auxiliary Space: O(1)
Boundary Cases: Insertion sort takes maximum time to sort if elements are sorted in reverse order. And it takes minimum time (Order of n) when elements are already sorted.

=========
Mergesort is a fast, recursive, stable sort algorithm which works by the divide and conquer principle. This is used for sorting the linked list. The algorithm has a complexity of O(n log (n)). Similar to Quicksort the list of elements which should be sorted is divided into two lists. These lists are sorted independently and then combined. During the combination of the lists the elements are inserted (or merged) on the correct place in the list. Merge can be implemented in several ways.
The simplest way of merge is the following :
1) Assume the size of the left array is k, the size of the right array is m and the size of the total array is n=k+m.
2) Create a helper array with the size n
3) Copy the elements of the left array into the left part of the helper array. This is position 0 until k-1.
4) Copy the elements of the right array into the right part of the helper array. This is position k until m-1.
5) Create an index variable i=0; and j=k+1
6) Loop over the left and the right part of the array and copy always the smallest value back into the original array. Once i=k all values have been copied back the original array. The values of the right array are already in place.
Compared to quicksort the mergesort algorithm puts less effort in dividing the list but more into the merging of the solution. Standard mergesort does require a copy of the array although there are (complex) implementations of mergesort which allow to avoid this copying.
MergeSort(arr[], l,  r)
If r > l
     1. Find the middle point to divide the array into two halves:  
             middle m = (l+r)/2
     2. Call mergeSort for first half:   
             Call mergeSort(arr, l, m)
     3. Call mergeSort for second half:
             Call mergeSort(arr, m+1, r)
     4. Merge the two halves sorted in step 2 and 3:
             Call merge(arr, l, m, r)
             
private void mergeParts(int lowerIndex, int middle, int higherIndex) {
    for (int i = lowerIndex; i <= higherIndex; i++) {
        tempMergArr[i] = array[i];
    }
    int i = lowerIndex;
    int j = middle + 1;
    int k = lowerIndex;
    while (i <= middle && j <= higherIndex) {
        if (tempMergArr[i] <= tempMergArr[j]) {
            array[k] = tempMergArr[i];
            i++;
        } else {
            array[k] = tempMergArr[j];
            j++;
        }
        k++;
    }
    while (i <= middle) {
        array[k] = tempMergArr[i];
        k++;
        i++;
    }
}
Time Complexity: O(nlogn)
Auxiliary Space: O(n)

========
Heap sort: It is a comparison-based sorting algorithm. Checkout in Trees section.

========
Quicksort: is a fast, recursive, non-stable sort algorithm which works by the divide and conquer principle. It has in average O(n log (n)) and in the worst case O(n2) complexity. Quicksort selects first a pivot elements. It then divides the elements of the list into two lists based on this pivot element. Every element which is smaller than the pivot element is placed in the left list and every element which is larger is placed in the right list. If an element is equal to the pivot element then it can go in any list. After this sorting the algorithm is then called recursively for the left and right list. If a list contains only one (or zero) elements then it sorted. Quicksort does not copy any data it just exchanges the values in the array therefore it does not consume a lot of memory (only on the call stack for the recursive call of the function. The disadvantages of Quicksort is that it does not work well on already sorted lists or an lists with lots of similar values.
public class Quicksort {
    private int[] numbers;
    private int number;
    public void sort(int[] values) {
        this.numbers = values;
        number = values.length;
        quicksort(0, number - 1);
    }
    private void quicksort(int low, int high) {
        int i = low, j = high;
        // Get the pivot element from the middle of the list
        int pivot = numbers[(low + high) / 2];

        // Divide into two lists
        while (i <= j) {
            // If the current value from the left list is smaller then the pivot
            // element then get the next element from the left list
            while (numbers[i] < pivot) {
                i++;
            }
            // If the current value from the right list is larger then the pivot
            // element then get the next element from the right list
            while (numbers[j] > pivot) {
                j--;
            }

            // If we have found a values in the left list which is larger then
            // the pivot element and if we have found a value in the right list
            // which is smaller then the pivot element then we exchange the
            // values.
            if (i <= j) {
                exchange(i, j);
                i++;
                j--;
            }
        }
        // Recursion
        if (low < j)
            quicksort(low, j);
        if (i < high)
            quicksort(i, high);
    }

    private void exchange(int i, int j) {
        int temp = numbers[i];
        numbers[i] = numbers[j];
        numbers[j] = temp;
    }
}
