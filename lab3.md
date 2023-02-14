# `find` command
The find command is a handy command line tool to navigate files and directories. The command also involves many expressions that can further improve the uses of the command. In this lab report, I will be going over 4 expressions that help boost the functionality of the `find` command.

## Expression 1: `-type` in `find`
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

## Expression 2: `-size` in `find`
The second command line option I will be going over is the `-size` expression. This expression returns all files that are the same file size as you desire. You can also use `+/-` to specify whether you want to find more than or less than certain file sizes.

The command syntax for this expression:
```
$ find [pathname...] -size (+/-)[size]
```

Example 1:
```
$ find ./written_2 -size +100k
./written_2/non-fiction/OUP/Berk/ch2.txt
./written_2/non-fiction/OUP/Berk/CH4.txt
./written_2/travel_guides/berlitz1/WhereToIndia.txt
./written_2/travel_guides/berlitz1/WhereToItaly.txt
./written_2/travel_guides/berlitz1/WhereToMalaysia.txt
./written_2/travel_guides/berlitz1/WhereToJapan.txt
./written_2/travel_guides/berlitz1/WhereToFrance.txt
./written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt
./written_2/travel_guides/berlitz2/Canada-WhereToGo.txt
./written_2/travel_guides/berlitz2/China-WhereToGo.txt
```
The above example uses the `-size` expression with the size `+100k`, meaning it finds all files within the `./written_2` directory that are over 100 kilobytes. This command then outputs the corresponding files. This can be useful when you want to find files that are more than a certain size limit, which sometimes poses problems due to file storage constraints. 

Example 2:
```
$ find ./written_2 -size +80k -size -100k
./written_2/non-fiction/OUP/Berk/ch1.txt
./written_2/non-fiction/OUP/Kauffman/ch8.txt
./written_2/non-fiction/OUP/Kauffman/ch9.txt
./written_2/travel_guides/berlitz1/WhereToLakeDistrict.txt
./written_2/travel_guides/berlitz1/WhereToEgypt.txt
./written_2/travel_guides/berlitz1/WhereToIsrael.txt
./written_2/travel_guides/berlitz1/WhereToDublin.txt
./written_2/travel_guides/berlitz1/WhatToJamaica.txt
./written_2/travel_guides/berlitz1/WhereToIstanbul.txt
```
The above example uses the `-size` expression twice, once with `+80k` and another time with `-100k`. These two nested expressions essentially limit the file output to all files that are above 80 kilobytes but less than 100 kilobytes. This can be useful when you want to find files that are within a certain size range, in which you can then perform different operations on.

## Expression 3: `-mtime` in `find`
The third command line expression I will be going over is the `-mtime` expression. This expression returns all files that have been modified recently within a certain time frame. You are able to specify a number `n` which corresponds to the number of days the files have been recently modified.

The command syntax for this expression:
```
$ find [pathname...] -mtime -[n]
```

For the following examples, I decided to modify some files in the corresponding folder `./written_2/non-fiction/OUP/Castro` beforehand. This was to help test the functionality of the algorithm.

Example 1:
```
$ find ./written_2 -mtime -1 
./written_2/non-fiction/OUP/Castro/chA.txt
./written_2/non-fiction/OUP/Castro/chV.txt
./written_2/non-fiction/OUP/Castro/chZ.txt
./written_2/non-fiction/OUP/Castro/chO.txt
```
The above example runs the `mtime` expression based on one day. I recently modified the exact same files within the `./written_2/non-fiction/OUP/Castro` directory and have not touched any other files. This command is useful if you want to find out which files have been modified by a program. Although you have no knowledge of the modifications, you are able to find out what has been modified through this command.

Example 2:
```
$ find ./written_2 -mtime -12 -type d  
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
The above example runs the `mtime` expression based on the past 12 days and outputs all directories. I created this project around 12 days ago, so all the files were first modified thne and thus all directories have been outputted. This is useful if you want to find out which directories have been created within a certain amount of days and see what the recent changes are.

## Expression 4: `-maxdepth` in `find`
The fourth command line expression that I will be going over is the `-maxdepth` expression. This expression returns all files that are less than or equal to a certain depth `n`. Any directory or file within the target directory would have a depth of 1, their subdirectories and files would have a depth of 2, and so on.

The command syntax for this expression:
```
$ find [pathname...] -maxdepth [n]
```

Example 1:
```
$ find ./written_2 -maxdepth 2
./written_2
./written_2/non-fiction
./written_2/non-fiction/OUP
./written_2/travel_guides
./written_2/travel_guides/berlitz1
./written_2/travel_guides/berlitz2
```
The above example runs the `-maxdepth` expression with a depth of 2. All the files displayed are the ones that have a depth of 2 from the target directory. This can be useful when you only want the first few files of a directory and not the entire recursive list of files.

Example 2:
```
$ find ./written_2/non-fiction/OUP -maxdepth 2 -type f 
./written_2/non-fiction/OUP/Berk/ch2.txt
./written_2/non-fiction/OUP/Berk/ch1.txt
./written_2/non-fiction/OUP/Berk/CH4.txt
./written_2/non-fiction/OUP/Berk/ch7.txt
./written_2/non-fiction/OUP/Abernathy/ch2.txt
./written_2/non-fiction/OUP/Abernathy/ch3.txt
./written_2/non-fiction/OUP/Abernathy/ch1.txt
./written_2/non-fiction/OUP/Abernathy/ch7.txt
./written_2/non-fiction/OUP/Abernathy/ch6.txt
./written_2/non-fiction/OUP/Abernathy/ch8.txt
./written_2/non-fiction/OUP/Abernathy/ch9.txt
./written_2/non-fiction/OUP/Abernathy/ch15.txt
./written_2/non-fiction/OUP/Abernathy/ch14.txt
./written_2/non-fiction/OUP/Rybczynski/ch2.txt
./written_2/non-fiction/OUP/Rybczynski/ch3.txt
./written_2/non-fiction/OUP/Rybczynski/ch1.txt
./written_2/non-fiction/OUP/Kauffman/ch3.txt
./written_2/non-fiction/OUP/Kauffman/ch1.txt
./written_2/non-fiction/OUP/Kauffman/ch4.txt
./written_2/non-fiction/OUP/Kauffman/ch5.txt
./written_2/non-fiction/OUP/Kauffman/ch7.txt
./written_2/non-fiction/OUP/Kauffman/ch6.txt
./written_2/non-fiction/OUP/Kauffman/ch8.txt
./written_2/non-fiction/OUP/Kauffman/ch9.txt
./written_2/non-fiction/OUP/Kauffman/ch10.txt
./written_2/non-fiction/OUP/Fletcher/ch2.txt
./written_2/non-fiction/OUP/Fletcher/ch1.txt
./written_2/non-fiction/OUP/Fletcher/ch5.txt
./written_2/non-fiction/OUP/Fletcher/ch6.txt
./written_2/non-fiction/OUP/Fletcher/ch9.txt
./written_2/non-fiction/OUP/Fletcher/ch10.txt
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
The above example runs the `-maxdepth` expression with a depth 2 to find all the files within the `./written_2/non-fiction/OUP` subdirectory. All the files displayed are the ones that have a depth of 2 from the target directory. This shows how useful the -maxdepth expression can be, where we are able to select only the files from a certain directory.
