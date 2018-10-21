# Database Management Systems - Chapter 9 Solutions

### Exercise 9.1
What is the most important difference behveen a disk and a tape?
#### `Answer`

***
### Exercise 9.2
Explain the terms seek time, rotational delay, and transfer time.
#### `Answer`

***
### Exercise 9.3
Both disks and main memory support direct access to any desired location (page). On average, main memory accesses are faster, of course. That is the other important
difference (from the perspective of the time required to access a desired page)?
#### `Answer`

***
### Exercise 9.4
If you have a large file that is frequently scanned sequentially, explain how you would store the pages in the file on a disk.

#### `Answer`

***
### Exercise 9.5
Consider a disk with a sector size of 512 bytes, 2000 tracks per surface, 50 sectors per track, five double-sided platters, and average seek time of 10 msec.
1. What is the capacity of a track in bytes? What is the capacity of each surface? What is the capacity of the disk?
2. How many cylinders does the disk have? Give examples of valid block sizes. Is 256 bytes a valid block size? 2048? 51,200?
4. If the disk platters rotate at 5400 rpm (revolutions per minute), what is the maximum rotational delay?
5. If one track of data can be transferred per revolution, what is the transfer rate?
#### `Answer`

***
### Exercise 9.6
Consider again the disk specifications from Exercise 9.5 and suppose that a
block size of 1024 bytes is chosen. Suppose that a file containing 100,000 records of 100 bytes
each is to be stored on such a disk and that no record is allowed to span two blocks.
1. How many records fit onto a block?
2. How many blocks are required to store the entire file? If the file is arranged sequentially
on disk, how many surfaces are needed? How many records of 100 bytes each can be stored using this disk?
4. If pages are stored sequentially on disk, with page 1 on block 1 of track 1, what page is stored on block 1 of track 1 on the next disk surface? How would your answer change if the disk were capable of reading and writing from all heads in parallel?
5. What time is required to read a file containing 100,000 records of 100 bytes each sequentially? Again, how would your answer change if the disk were capable of reading/writing from all heads in parallel (and the data was arranged optimally)?
6. What is the time required to read a file containing 100,000 records of 100 bytes each in a
random order? To read a record, the block containing the record has to be fetched from
disk. Assume that each block request incurs the average seek time and rotational delay.

#### `Answer`

***
### Exercise 9.7
Explain what the buffer manager must do to process a read request for a page. What happens if the requested page is in the pool but not pinned?

#### `Answer`

***
### Exercise 9.8
When does a buffer manager write a page to disk?

#### `Answer`

***
### Exercise 9.9
What does it mean to say that a page is pinned in the buffer pool? Who is responsible for pinning pages? Who is responsible for unpinning pages?

#### `Answer`

***
### Exercise 9.10
When a page in the buffer pool is modified, how does the DBMS ensure that this change is propagated to disk? (Explain the role of the buffer manager as well as the modifier of the page.)
Exercise 9.11 What happens if a page is requested when all pages in the buffer pool are dirty?

#### `Answer`

***
### Exercise 9.12
What is sequential flooding of the buffer pool?

#### `Answer`

***
### Exercise 9.13
Name an important capability of a DBMS buffer manager that is not supported by a typical operating system's buffer manager.

#### `Answer`

***
### Exercise 9.14
Explain the term prefetching. Why is it important?

#### `Answer`

***
### Exercise 9.15
Modern disks often have their own main memory caches, typically about 1 MB, and use this to prefetch pages. The rationale for this technique is the empirical observation that, if a disk page is requested by some (not necessarily database!) application,
80% of the time the next page is requested as well. So the disk gambles by reading ahead.
1. Give a nontechnical reason that a DBMS may not want to rely on prefetching controlled
by the disk.
2. Explain the impact on the disk's cache of several queries running concurrently, each
scanning a different file.
3. Is this problem addressed by the DBMS buffer manager prefetching pages? Explain.
4. Modern disks support segmented caches, with about four to six segments, each of which is used to cache pages from a different file. Does this technique help, with respect to the preceding problem? Given this technique, does it matter whether the DBMS buffer manager also does prefetching?

#### `Answer`

***
### Exercise 9.16
Describe two possible record formats. What are the trade-offs between them?

#### `Answer`

***
### Exercise 9.17
Describe two possible page formats. What are the trade-offs between them?

#### `Answer`

***
### Exercise 9.18
Consider the page format for variable-length records that uses a slot directory.
1. One approach to managing the slot directory is to use a maximum size (i.e., a maximum number of slots) and allocate the directory array when the page is created. Discuss the pros and cons of this approach with respect to the approach discussed in the text.
2. Suggest a modification to this page format that would allow us to sort records (according to the value in some field) without moving records and without changing the record ids. Exercise 9.19 Consider the two internal organizations for heap files (using lists of pages and a directory of pages) discussed in the text.
1. Describe them briefly and explain the trade-offs. Which organization would you choose if records are variable in length?
2. Can you suggest a single page format to implement both internal file organizations?

#### `Answer`

***
### Exercise 9.20
Consider a list-based organization of the pages in a heap file in which two lists are maintained: a list of all pages in the file and a list of all pages with free space. In
contrast, the list-based organization discussed in the text maintains a list of full pages and a
list of pages with free space.


1. What are the trade-offs, if any'? Is one of them clearly superior?
2. For each of these organizations, describe a suitable page format.

#### `Answer`

***
### Exercise 9.21
Modern disk drives store more sectors on the outer tracks than the inner tracks. Since the rotation speed is constant, the sequential data transfer rate is also higher on
the outer tracks. The seek time and rotational delay are unchanged. Given this information,
explain good strategies for placing files with the following kinds of access patterns:
1. Frequent, random accesses to a small file (e.g., catalog relations).
2. Sequential scans of a large file (e.g., selection from a relation with no index).
3. Random accesses to a large file via an index (e.g., selection from a relation via the index).
4. Sequential scans of a small file.

#### `Answer`

***
### Exercise 9.22
Why do frames in the buffer pool have a pin count instead of a pin flag?

#### `Answer`

***
