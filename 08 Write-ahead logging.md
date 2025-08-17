# Design Pattern (Software Architecture and Design, Refactoring)

### Write-ahead logging

In a system using **WAL (write-ahead logging)**, all modifications are written to a log before they are applied. Usually both redo and undo information is stored in the log.

Example. Imagine a program that is in the middle of performing some operation when the machine it is running on loses power. Upon restart, that program might need to know whether the operation it was performing succeeded, succeeded partially, or failed. If a write-ahead log is used, the program can check this log and compare what it was supposed to be doing when it unexpectedly lost power to what was actually done. On the basis of this comparison, the program could decide to undo what it had started, complete what it had started, or keep things as they are.


