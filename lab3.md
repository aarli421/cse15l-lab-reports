## Part 1: `-type` expression in `find`
The first command line option for the `find` command I will be going over is the `-type` expression. This expression returns all files that are the same type as a specified type. These types are represented by a single letter and the most common ones are for directories and files:

* `d` - directory
* `f` - file

The command syntax for this expression:
```
$ find [pathname...] -type [t]
```

Example 1:
```
$ find ./written_2 -type d
./written_2
./written_2/non-fiction
./written_2/non-fiction/OUP
./written_2/non-fiction/OUP/Berk
./written_2/non-fiction/OUP/Abernathy
./written_2/non-fiction/OUP/Rybczynski
./written_2/non-fiction/OUP/Kauffman
./written_2/non-fiction/OUP/Fletcher
./written_2/non-fiction/OUP/Castro
./written_2/travel_guides
./written_2/travel_guides/berlitz1
./written_2/travel_guides/berlitz2
```
The above example uses the `-type` expression with the type `d` in the `./written_2` directory. This command extracts all of the directories within `./written_2` and outputs it. This can be useful when you want to know the number of directories within a folder, or when you want to execute a command on all possible directories in a folder.

Example 2:
```
$ find ./written_2/non-fiction/OUP/Castro -type f
./written_2/non-fiction/OUP/Castro/chR.txt
./written_2/non-fiction/OUP/Castro/chP.txt
./written_2/non-fiction/OUP/Castro/chQ.txt
./written_2/non-fiction/OUP/Castro/chB.txt
./written_2/non-fiction/OUP/Castro/chC.txt
./written_2/non-fiction/OUP/Castro/chA.txt
./written_2/non-fiction/OUP/Castro/chV.txt
./written_2/non-fiction/OUP/Castro/chW.txt
./written_2/non-fiction/OUP/Castro/chM.txt
./written_2/non-fiction/OUP/Castro/chZ.txt
./written_2/non-fiction/OUP/Castro/chL.txt
./written_2/non-fiction/OUP/Castro/chN.txt
./written_2/non-fiction/OUP/Castro/chY.txt
./written_2/non-fiction/OUP/Castro/chO.txt
```
The above example uses the `-type` expression with type `f` in the `./written_2/non-fiction/OUP/Castro` directory. This command then outputs all of the files in the specified directory. This can be useful when you want to know the number of files within a folder, or when you want to execute some command on all possible files in that folder. 
