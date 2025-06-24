# Time-aware, least-recently used
- Time-aware, least-recently-used (TLRU) is a variant of LRU designed for when the contents of a cache have a valid lifetime.
- The algorithm is suitable for network cache applications such as information-centric networking (ICN), 
content delivery networks (CDNs) and distributed networks in general. 
- TLRU introduces a term: TTU (time to use), a timestamp of content (or a page) which stipulates the usability time
for the content based on its locality and the content publisher.
- TTU provides more control to a local administrator in regulating network storage.

- When content subject to TLRU arrives, a cache node calculates the local TTU based on the TTU assigned by the content publisher.
- The local TTU value is calculated with a locally-defined function.
- When the local TTU value is calculated, content replacement is performed on a subset of the total content of the cache node. 
- TLRU ensures that less-popular and short-lived content is replaced with incoming content.
  
## 🏗 How It Works (Step-by-Step)
### Publisher assigns TTU:
 - When some content (like a video or a file) is published, the creator gives it a TTU value.

### Local TTU is computed:
- When the content reaches a cache node (e.g., a CDN server):

- The cache calculates a local TTU

- This may adjust the original TTU based on local rules or network conditions
(e.g., local popularity, bandwidth, load)

### TLRU eviction:

 - The cache will consider both:

 - How recently content was used (like LRU)

 - Whether the content is still valid (i.e., not expired based on TTU)

- Content is only kept if it’s popular AND still valid

### Eviction happens in a subset:

 - Instead of scanning the whole cache,

 - TLRU only looks at a subset (e.g., items about to expire or less popular)

This improves speed and keeps important content longer

