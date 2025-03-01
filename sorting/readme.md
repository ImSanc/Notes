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

