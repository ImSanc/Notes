## Bubble sort
- we shift the biggest element to the last position, we keep on moving the biggest element to its correct position 
- Like bubbling it keeps on bubbling above and above
- stable sort
- O(n^2)

        public int[] sortArray(int[] nums) {
        
        int len = nums.length;

        for( int i = len-1 ; i>0 ; i--)
        {
            for( int j = 1 ; j <=i ; j++ )
            {
                if( nums[j-1]> nums[j] )
                {
                    swap( nums , j-1, j);
                }
            }
        }
        return nums;
      }


## Selection sort
- We swap the smallest element to its correct position.
- We only swap once for an element for its correct position.
- O(n^2)
- unstable sort

      public int[] sortArray(int[] nums) {

        int len = nums.length;

        for( int i = 0 ; i< len -1; i++)
        {
            int idx = i;
            for( int j = i+1 ; j < len ; j++ )
            {
                if( nums[j] < nums[idx])
                {
                    idx = j;
                }
            }
            swap(nums, i , idx);
        }
        return nums;
      }

## Insertion sort
- Insertion Sort is a simple, comparison-based sorting algorithm that builds the final sorted array one element at a time by inserting each element into its correct position in the already sorted part of the array.
- In-Place
- Stable


    public int[] sortArray(int[] nums) {

        int len = nums.length;
        for( int i = 1 ; i < len ; i++ )
        {
            int num = nums[i];
            int j = i-1;
            while( j>=0 && nums[j]> num)
            {
                nums[j+1] = nums[j];
                j--;
            }
            nums[j+1] = num;
        }
        return nums;

    }


## Merge Sort
- Merge Sort is a divide-and-conquer sorting algorithm that recursively divides an array into smaller subarrays, sorts them, and then merges them back together to produce a sorted array.
  - How Merge Sort Works:
    1.Divide: Recursively split the array into two halves until each subarray has only one element.
    2.Conquer: Recursively sort each half using Merge Sort.
    3.Merge: Merge the sorted halves back together in sorted order.

 - O(nlogn)
- Stable
- Not in-place: Requires extra space for merging.


