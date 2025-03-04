# Lomuto partition
- The Lomuto partition scheme is a partitioning algorithm used in QuickSort.
- It works by selecting a pivot (typically the last element of the array) and rearranging the array so that all elements smaller than or equal to the pivot are on its left, and all greater elements are on its right.

#### Steps of Lomuto Partition:
- Choose the pivot as the last element of the array.

- Initialize an index (i) to keep track of the position where elements smaller than the pivot should be placed.

- Traverse the array from the left to the second last element:

- If an element is smaller than or equal to the pivot, swap it with the element at index i and increment i.

- Swap the pivot with the element at index i to place it in its correct position.

- Return the index of the pivot after partitioning.


    public static int partition(int[] arr, int low, int high) {
          int pivot = arr[high]; // Choosing the last element as pivot
          int i = low - 1; // Index for smaller elements
    
            for (int j = low; j < high; j++) {
                if (arr[j] <= pivot) { // If current element is <= pivot
                    i++;
                    swap(arr, i, j);
                }
            }

        // Place pivot in its correct position
        swap(arr, i + 1, high);
        return i + 1; // Return partition index
    }