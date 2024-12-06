# Lab 5 Heap Manager

There are 3 parts to this lab, two of which are optional. The first part is mm.c, which is an implementation of C's malloc and free functions, which allocate a given amount of bytes in the processes heap and deallocate the block pointed to by the given pointer respectively. The first optional part is mm-realloc.c, a reimplementation of C's realloc function, which copies the data in the given block to a new block of the given size (the new block can be in the same place as the old if there is enough space). Finally, there is mm-gc.c, a mark and sweep garbage collector similar to that in java.

- mm.c:
  - mm_malloc: We were provided most of the lower level functions for this, so we only had to implement it on a high level. First I properly sanitize the size input, adding 8 bytes for the header, aligning it to an 8 byte (1 word) address, and ensuring it was of minimum size. Then, I searched the free list for a large enough block. If one wasn't found I requested more heap space and searched again and then removed the found block from the free list. Next I checked if the block was large enough to be split, if so I create a new free block filling the unused space with the proper tag bits and a footer, adding to the free list afterward. If the block is just the right size we can simply set the prec_used tag of the next block to a 1 and move on to initializing the newly used block by setting the size to the required size and the used and prec_used tags to 1. Finally, we just return the pointer to our newly allocated block plus 8 so the pointer is to the payload instead of the header
  - mm_free: TBD
- mm-realloc: TBD
- mm-gc: TBD
