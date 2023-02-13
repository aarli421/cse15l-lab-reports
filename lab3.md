## Part 1: `-type` expression in `find`
The first command line option for the `find` command I will be going over is the `-type` expression. This expression returns all files that are the same type as a specified type. These types are represented by a single letter and are defined as follows:

* b - block special
* c - character special
* d - directory
* f - file
* l - symbolic link
* p - FIFO
* s - socket

The command syntax for this expression:
```
$ find [pathname...] -type [t]
```
