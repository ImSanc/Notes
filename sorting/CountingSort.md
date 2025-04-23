# Counting sort
- Counting sort works best when:

   - You have n elements, AND
   - The values are in a small range, e.g., 1 to k.

- If k (the maximum number in the array) is not too big compared to n (say, k = 2n, 3n, etc.), then counting sort is efficient.
- Why? Because counting sort creates an extra array of size k to count occurrences.
  - If k becomes huge (say, k = 1,000,000 and n = 10), you're wasting a ton of memory for no good reason.

    - Say you have n = 1000 elements:

        O(n) → ~1000 steps

        O(n log n) → ~1000 * 10 = 10,000 steps
        O(n²) → ~1,000,000 steps 😬

That’s why we try to use O(n log n) sorts (like merge sort, quick sort, heap sort) instead of O(n²) ones (like bubble/selection/insertion) for large inputs.

## Important points :
- Not an comparison based algo.
- O( n + k) time
- O( n+ k ) space 
- Stable
- used as subroutine for radix sort 

✅ Counting Sort for Integers (Non-negative integers)
    public class CountingSort {
    public static void countingSort(int[] arr) {
    int max = arr[0];
    for (int num : arr) {
    if (num > max) max = num;
    }
    
            int[] count = new int[max + 1];
    
            // Count occurrences
            for (int num : arr) {
                count[num]++;
            }
    
            // Reconstruct sorted array
            int index = 0;
            for (int i = 0; i < count.length; i++) {
                while (count[i]-- > 0) {
                    arr[index++] = i;
                }
            }
        }
    
        public static void main(String[] args) {
            int[] arr = {4, 2, 2, 8, 3, 3, 1};
            countingSort(arr);
            System.out.println(Arrays.toString(arr));  // [1, 2, 2, 3, 3, 4, 8]
        }
    }

✅ Counting Sort (Handles negative integers too)

    public class CountingSortWithNegatives {
    public static void countingSort(int[] arr) {
    int min = arr[0], max = arr[0];
    for (int num : arr) {
    if (num < min) min = num;
    if (num > max) max = num;
    }
    
            int range = max - min + 1;
            int[] count = new int[range];
    
            // Count occurrences
            for (int num : arr) {
                count[num - min]++;
            }
    
            // Reconstruct sorted array
            int index = 0;
            for (int i = 0; i < range; i++) {
                while (count[i]-- > 0) {
                    arr[index++] = i + min;
                }
            }
        }
    
        public static void main(String[] args) {
            int[] arr = {4, -2, 2, -8, 3, 3, 1};
            countingSort(arr);
            System.out.println(Arrays.toString(arr));  // [-8, -2, 1, 2, 3, 3, 4]
        }
    }

