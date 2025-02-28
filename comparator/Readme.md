# Comparable 

- if we use compareTo method to compare what happens? 
- 5 is the number we need to compare with and this is the array {0,5,10,-50,50 }
- 
Output :
    
    5 > 0: compareTo = 1 
    5 == 5: compareTo = 0 
    5 < 10: compareTo = -1
    5 < -50: compareTo = 1
    5 < 50: compareTo = -1

#### what it represents?
1. -1 when the value is less than the value it is being compared with
2. 0 when its equal to the value it is compared with
3. 1 when the value is equal to the value it is being compared with

If you want to use Comparable with an anonymous class, it's not possible in the usual way because Comparable must be implemented inside the class itself
. However, if you don't want to modify the class directly, you must use Comparator instead.

But if you're asking whether you can sort an anonymous class that implements Comparable, then yes, you can create an anonymous inner class that implements Comparable<T> on the fly.