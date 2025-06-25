# Least Frequently Used (LFU)
- Least Frequently Used (LFU) is a type of cache algorithm used to manage memory within a computer.
- The standard characteristics of this method involve the system keeping track of the number of times a block is referenced in memory.
- When the cache is full and requires more room the system will purge the item with the lowest reference frequency.


## Implementation

- The simplest method to employ an LFU algorithm is to assign a counter to every block that is loaded into the cache.
- Each time a reference is made to that block the counter is increased by one.
- When the cache reaches capacity and has a new block waiting to be inserted the system will search for the block with 
the lowest counter and remove it from the cache, in case of a tie (i.e., two or more keys with the same frequency),
the Least Recently Used key would be invalidated.

## Problems
- While the LFU method may seem like an intuitive approach to memory management it is not without faults.
- Consider an item in memory which is referenced repeatedly for a short period of time and is not accessed again for an extended period of time.
- Due to how rapidly it was just accessed its counter has increased drastically even though it will not be used again for a decent amount of time.
- This leaves other blocks which may actually be used more frequently susceptible to purging simply because they were accessed through a different method.
- Due to major issues like these, an explicit LFU system is fairly uncommon; instead, there are hybrids that utilize LFU concepts.