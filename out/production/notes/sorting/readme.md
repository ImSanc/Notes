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

        private void mergeSort( int[] nums , int left ,int right)
        {
        if( left< right){
        int mid = left + ( right - left)/2;

              mergeSort( nums , left , mid );
              mergeSort( nums , mid+1 , right);
              merge( nums , left ,mid , right);
          }
        }
  
        private void merge( int[] nums , int left ,int mid , int right )
        {
            int[] arr1 = new int[ mid-left+1];
            int[] arr2 = new int[ right - mid];

          for( int i = 0 ; i < arr1.length ; i++ )
          {
              arr1[i] = nums[left+i];
          }

          for( int i = 0 ; i< arr2.length ; i++ )
          {
              arr2[i] = nums[mid+1 +i];
          }

          int len1 = arr1.length , len2 = arr2.length;
          int i = 0 , j= 0 , idx = left;

          while( i < len1 && j < len2 )
          {
              int num1 = arr1[i] , num2 = arr2[j];
              if( num1 < num2)
              {
                  nums[idx] = num1;
                  i++;
              }
              else
              {
                  nums[idx] = num2;
                  j++;
              }
              idx++;
          }

          while( i < len1 )
          {
              nums[idx++] = arr1[i++];
          }

          while( j < len2 )
          {
              nums[idx++] = arr2[j++];
          }
        }


## Quick sort

- Quick Sort is a divide-and-conquer sorting algorithm that works by selecting a pivot and partitioning the array into two halves such that:

- The left half contains elements smaller than the pivot.
- The right half contains elements greater than the pivot.
- It then recursively sorts both halves.
- O(N log N) worst O(N^2)
- Not stable

#### Partitioning Schemes

- Naive 
Stable but takes O(n^2)


- Lomuto Partitioning (Last Element as Pivot)
Selects the last element as the pivot.
Swaps elements to ensure the pivot is placed in its correct position.

- Hoare Partitioning (More Efficient)
Uses two pointers to swap elements and results in better-balanced partitions.

    
      //Lomuto partition
    private void quickSort( int[] nums, int low , int high)
    {
        if( low < high)
        {
            int p = partition(nums, low , high);
            quickSort(nums , low , p-1);
            quickSort( nums , p+1 , high);
        }
    }

    private int partition( int[] nums , int low , int high )
    {
        int pivot = nums[high];

        int i = low -1 ;

        while( low < high)
        {
            if( nums[low] < pivot )
            {
                i++;
                swap( nums , i , low);
            }
            low++;
        }
        swap(nums , high , ++i);
        return i;
    }


    //Hoare partition
    private void quickSort(int[] nums , int low , int high)
    {
        if( low < high)
        {
            int j = partition( nums, low , high);
            quickSort( nums, low , j);
            quickSort( nums, j+1 , high);
        }
    }
    private int partition( int[] nums , int low , int high)
    {
        int pivot = nums[low];
        int i = low-1 , j = high+1;

       while (true){ 
            do{
                i++;
            }while( i<=high &&  nums[i] < pivot);

            do{
                j--;
            }while( j>=low && nums[j]>pivot);

            if( i >=j){
                return j;
            }
            swap(nums,i , j);
        }
    }





