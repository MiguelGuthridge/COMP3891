To speed up system performance, caching can be used to keep [[block]] data in memory, which improves the speed of repeated access to [[file|files]].

Buffers and cache should be shared to avoid wasted memory.

## UNIX buffer cache
On read:
- hash the device number and block number
- Check if there's a match in the cache
- If so, use the in-memory copy
- Otherwise, load the block into the buffer cache

## Cache replacement
If there isn't enough memory, elements of the cache should be removed
- Using first-in, first-out is a bad idea -- what if the first file cached is also the most-requested one?
- Clearing the least recently-used one sounds good but there are other factors too.
- We want to write important elements first (eg disk blocks)

# Alternative - write-through cache
Write all changes to the disk as well as caching them.
- Temporary files will be written
- Multiple updates not combined

This is useful on devices such as USB drives, which could be removed unexpectedly.
