# What Is ARC?
- ARC (Adaptive Replacement Cache) is a self-tuning caching algorithm that dynamically balances between:
 - Recency (like LRU — least recently used)
 - Frequency (like LFU — least frequently used)
ARC learns from your workload and adapts to whether recently used or frequently used items are more valuable.

## 🚀 Why Was ARC Designed?
- LRU works well when recent items are reused, but fails when old items are reused frequently.
- LFU works well when hot items are reused often, but is slow to adapt to changing patterns.
- ARC gives you the best of both worlds, and self-adjusts over time.

## ⚙️ How ARC Works (High Level)
- ARC maintains four lists:

1. T1 (recent list)
   - Items that were used once recently 
   - Think of it like LRU

2. T2 (frequent list)
   - Items that were used multiple times 
   - Think of it like LFU

3. B1 (recently evicted from T1)
    - "Ghost list" to remember what used to be in T1
    - Contains only keys, no data

4. B2 (recently evicted from T2)
   - "Ghost list" to remember what used to be in T2
   - Also just keys


### 🧠 Smart Part: ARC learns from B1 and B2
- If items from B1 keep getting accessed again → workload favors recency → ARC increases space for T1
- If items from B2 keep getting accessed again → workload favors frequency → ARC increases space for T2

#### ✅ ARC dynamically adjusts how much space is given to recency vs. frequency
→ This means it adapts automatically to your workload.




