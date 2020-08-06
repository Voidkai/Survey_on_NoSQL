# Database Management System

## Storage Hierarchy

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