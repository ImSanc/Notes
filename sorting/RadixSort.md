# Radix sort 
- Radix Sort is a non-comparison-based sorting algorithm, like Counting Sort.
- It sorts numbers (or strings) digit by digit, starting from the least significant digit (LSD) to the most significant digit (MSD) — this is the LSD Radix Sort, which is the most common form.


    public class RadixSort {
    public static void radixSort(int[] arr) {
    int max = getMax(arr);
    
            // Do counting sort for every digit (1s, 10s, 100s, ...)
            for (int exp = 1; max / exp > 0; exp *= 10) {
                countingSortByDigit(arr, exp);
            }
        }
    
        private static int getMax(int[] arr) {
            int max = arr[0];
            for (int num : arr) {
                if (num > max) max = num;
            }
            return max;
        }
    
        private static void countingSortByDigit(int[] arr, int exp) {
            int[] output = new int[arr.length];
            int[] count = new int[10]; // digits 0-9
    
            // Count occurrences
            for (int num : arr) {
                int digit = (num / exp) % 10;
                count[digit]++;
            }
    
            // Cumulative count
            for (int i = 1; i < 10; i++) {
                count[i] += count[i - 1];
            }
    
            // Build output array (stable sort)
            for (int i = arr.length - 1; i >= 0; i--) {
                int digit = (arr[i] / exp) % 10;
                output[--count[digit]] = arr[i];
            }
    
            // Copy to original array
            System.arraycopy(output, 0, arr, 0, arr.length);
        }
    
        public static void main(String[] args) {
            int[] arr = {170, 45, 75, 90, 802, 24, 2, 66};
            radixSort(arr);
            System.out.println(Arrays.toString(arr));  // [2, 24, 45, 66, 75, 90, 170, 802]
        }
    }


