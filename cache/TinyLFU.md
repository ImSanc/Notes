# 🧠 What Is TinyLFU?
- TinyLFU (Tiny Least Frequently Used) is a probabilistic LFU algorithm that tracks how often items are used,
but in a space-efficient way using approximate counters (not full counters per item).
- It's called "Tiny" because:
   - It doesn't store exact access counts
   - It uses compact data structures like count-min sketch (a space-saving frequency estimator)

## ⚙️ How TinyLFU Works (Simplified)
 ### Key Components:
    Frequency Sketch (Count-Min Sketch)
    → Like a lightweight map that counts frequency of recently seen items
    → Can be very large but uses fixed, small memory

 ### Admittor
    → When cache is full, TinyLFU asks:
    
    “Is this new item more popular than something already in cache?”
    → If yes → admit it (evict old one)
    → If no → reject it

### Eviction Policy (e.g., LRU or Segmented LRU)
    → Decides which item to evict, often based on recency
    → TinyLFU just helps decide whether to admit the new item


### 🧃 Imagine This Story
- You're running a tiny juice bar with limited fridge space (your cache). You want to stock juices people will ask for again, and toss the ones that don’t sell.
#### Here's what you do:
- Every time someone asks for a juice (mango, orange, etc.), you increase its popularity score

#### If the fridge is full and someone wants a new juice:
- You compare the new juice’s popularity to the least popular juice in the fridge
- If the new juice is more popular, toss out the least popular one and add it
- Otherwise, reject it

#### You don’t need to know exact counts, just a good enough idea of what’s popular.

👉 That’s TinyLFU.

### 🧠 Key Idea (in Plain Terms)
- Only let frequently requested items into the cache. If something is rarely accessed, don’t let it waste space.
- Unlike traditional caches (which admit everything and later evict), TinyLFU is picky from the start:
- "Prove you’re useful before I let you in."


### 📦 Where TinyLFU Is Used
- Caffeine (Java) – industry-leading local cache
- Redis (from v4) – approximate LFU mode
- Go's Ristretto – high-performance TinyLFU implementation
- CDNs & Databases – for smarter eviction

