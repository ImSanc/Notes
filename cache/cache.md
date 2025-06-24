# Cache replacement policies
- <b>Cache replacement policies (also known as cache replacement algorithms or cache algorithms)</b> are optimizing instructions or algorithms which a computer program or hardware-maintained structure can utilize to manage a cache of information.


# There’s a Magic Formula:
 <b>T = m × Tₘ + Tₕ + E</b>

This is a formula for average memory access time. Let’s break it down:

#### What Do These Letters Mean?
 - T = how long it takes on average to get data from memory

 - m = miss ratio → how often we don’t find what we want in the fast memory
(like when you open your toy box and the toy isn’t there)
 
- Tₘ = how long it takes to go get it from the slow place (like the attic)

- Tₕ = how long it takes to check the fast place (your toy box)

- E = extra time that might happen if there’s waiting (like your brother is using the toy)

 So, the computer first checks the fast memory:

If the thing is there = it's a "hit" = fast

If the thing is not there = it's a "miss" = slow, have to go look in bigger memory

#### 📦 Cache Has Two Superpowers:
- Hit ratio – how often it finds things in the fast memory (more is better!)

 - Latency – how fast it can find things (less is better!)