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

# Hoare Partition

- The Hoare partition scheme is another partitioning algorithm used in QuickSort.
- It is more efficient than the Lomuto partition in many cases because it reduces the number of swaps.

Steps of Hoare Partitioning:
1. Choose a pivot (usually the first element).

2. Use two pointers:

 - i starts from the left.

 - j starts from the right.

- Move i forward until an element greater than or equal to the pivot is found.

- Move j backward until an element smaller than or equal to the pivot is found.

- Swap arr[i] and arr[j] to ensure elements smaller than the pivot are on the left and larger ones are on the right.

- Repeat the process until i and j cross each other.

- Return j (partition index).


    public static int partition(int[] arr, int low, int high) {
        int pivot = arr[low]; // Choosing the first element as pivot
        int i = low - 1, j = high + 1;

        while (true) {
            do {
                i++; // Move i forward to find an element >= pivot
            } while (arr[i] < pivot);

            do {
                j--; // Move j backward to find an element <= pivot
            } while (arr[j] > pivot);

            if (i >= j) // If indices cross, return partition index
                return j;

            // Swap elements at i and j
            swap(arr, i, j);
        }
    }


Key Differences Between Hoare and Lomuto:

Feature             	Hoare Partition             	Lomuto Partition
Pivot Choice	    Usually first element	            Usually last element
Swaps	                    Fewer swaps	                More swaps
Efficiency	            Faster (fewer swaps)	        Slower in some cases
Partition Index	        Returns j	                    Returns i+1


#### What Happens with the Pivot in Hoare Partition?
- In Hoare's Partition Scheme, the pivot does not necessarily end up in its final sorted position after partitioning. Instead, it ensures that:

- Elements smaller than or equal to the pivot are on the left.

- Elements greater than or equal to the pivot are on the right.