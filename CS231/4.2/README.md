Things that could be better explained:

**BIP**: every cache line is tagged as MRU or LRU with a probability during initialization. While deciding which to delete in the find victim function, you have to delete the least recently used line only among the LRUs. If suppose all lines are MRUs, swap all of them back to LRUs and then find the least recently used. If an existing cache line is a hit and it is an LRU, it is promoted to an MRU. But when it is a miss and you are filling a new memory address into the line, you should tag it as MRU/LRU with the probability. In either case, update the current time (clock cycle) the cache line is used, in order to delete the least recently used whenever required.

**ip_stride Prefetcher**: for ip_stride, the initiate_lookahead function is the one which decides which memory addresses are to be fetched, and puts the info inside the active lookahead variable. The advance_lookahead function is the one which is doing the actual fetching, it fetches addresses in an AP, with initial term as address+stride, common difference as stride, and no of terms as degree. This function doesn't need to be modified by us, as we also need to fetch consecutive addresses which is an AP as well.

**stream Prefetcher**: it is ok to use a vector to maintain all the monitoring regions, also maintain the last time any region was used. There are basically 3 things to do. 

- When we get a hit inside a monitoring region, update the latest time the region was used, for LRU purposes. 
- If we get a miss inside a monitoring region, follow whatever is given in the README itself, and update the time too.
- If we get a miss outside a monitoring region, we form new monitoring regions.
