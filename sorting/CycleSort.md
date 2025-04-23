## Cycle sort
1. A worst case O(n^2) sorting algo.
2. Does minimum memory writes and can be useful for cases where memory writes are costly.
3. In-place and not stable.
4. Useful to solve questions like find minimum swap to make an array sorted


#### For distinct element
        public int[] sortArray(int[] nums) {
        int len = nums.length;

            for( int i = 0 ; i < len ; i++ )
            {
                int item = nums[i];
                int pos = i;
    
                for( int j = i+1 ; j < len ; j++ ){
                    if( item > nums[j]){
                        pos++;
                    }
                }
    
                if( pos != i ){
                    swap(nums, i , pos);
                }
    
                while( i != pos){
                    pos = i ;
                    item = nums[pos];
    
                    for( int j = pos+1 ; j < len ; j++ ){
                        if( item > nums[j]){
                            pos++;
                        }
                    }
    
                    if( pos != i ){
                        swap(nums, i , pos);
                    }
    
                }
            }
            return nums;
        }
    
        private void swap( int[] nums , int i , int j){
            int temp = nums[i];
            nums[i] = nums[j];
            nums[j] = temp;
        }
