# Database Management System

## I. Storage Hierarchy

1. CPU Registers(  Faster Smaller Expensive)
2. CPU Caches
3. DRAM
4. SSD
5. HDD
6. Network Storage(slower bigger cheaper)

from register to DRAM is Volatile:

1. Random Access 
2. Byte-Address(字节寻址)

from SSD to Network Storage is Non-volatile:

1. Sequential Access
2. Block-Address(块寻址)

There is another Storage called Non-volatile Memory between DRAM and SSD.

## Two Problems

1. How the DBMS represents the database in files on disk.
2. How the DBMS managers its memory and move data back-and-forth from disk.

## II. the DBMS represents the database in files on disk

### 1. File Storage

The DBMS stores a database as one or more files on disk but OS doesn't know anything about the contents of these files.

#### 1.1 Storage Manager

The SM is responsible for maintaining a database's files

It organized the files as a collection of pages

- Tracks data read/written to pages.
- Tracks the available space.

#### 1.2 Database pages

A page is a fixed-size block of data.

- It can contain tuples, meta-data, indexes, log records...
- Most systems do not mix page types
- Some systems require a page to be self-contained.

Each page is given a unique identifier: Page ID

- The DBMS uses an indirection layer to map page ids to physical locations.

Three different notions of pages:

1. Hardware Page 4KB
2. OS Pages 4KB
3. Database Page (512B-16KB)

#### 1.3 Database Heap

: an unordered collection of pages, need meta-data to keep track of what pages exist and which have free space. And there are two ways to represent a heap file : **Linked list and Page Directory**.

##### 1.3.1 Linked List

Maintain a header page includes the head of the free page list and the head of the data page list. Each page keeps track of the number of free slots in itself.

##### 1.3.2 Page Directory

The DBMS maintains special pages that tracks the location of data pages in the database files

The directory also records the number of free slots per page.

### 2. Page layout

### 2.1 Page Header

Page Header includes :

1. page size
2. Checksum
3. DBMS Version
4. Transaction Visibility
5. Compression Information

### 2.2 Page Layout

Only storing tuples: There are two approaches:

1. Tuple-oriented
2. Log-structured



#### Slotted Pages

The most common layout scheme is called slotted pages,

 the slot array maps "slots" to the tuple's starting position offsets.

![slot_page](C:\Users\I533777\repos\Survey_on_NoSQL\slot_page.png)



###  3. Tuple layout

A tuple is a sequence of bytes

Tuple includes header and attribute data.

1. header contains meta-data about it
   1. Visibility info (concurrency control)
   2. Bit map for NULL values.
2. We don't need to store meta-data about the schema.





## III. DBMS managers its memory and move data back-and-forth from disk

