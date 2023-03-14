# Grading Script
## Making of the Script
For the making of the grading script, I started with the code that was given. I first decided to plan out my bash file. I realized that I would need to first clone the repository, then check if the tested file exists, copy the file over, check for errors in compilation, and lastly check for errors while running. 
```
ROOT='student-submission'
FILE='ListExamples.java'

rm -rf $ROOT
rm $FILE
git clone $1 $ROOT
echo 'Finished cloning...'
```
The above code is to clone the repository over. As you can see I defined variables for both the root folder of the repository and the file that we want to run which in this case is `ListExamples.java`.
```
if [[ -f $ROOT/$FILE ]]
then
    echo 'Found submission file...'
else
    echo 'Submission file not found!'
    exit
fi
```
The above code is to check if the file exists. I used the `-f` condition that checks if the file exists and if it doesn't I will then exit the program right away because that means I cannot continue.
```
CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'
COMPILE='compile.txt'
RUN='run.txt'

cp student-submission/$FILE ./
javac -cp $CPATH *.java 2> $COMPILE
```
The above code is to compile the file. As you can see I compile the corresponding files with Junit and make sure to redirect all the error outputs into a separate file.
```
if [[ $? -eq 0 ]]
then
    echo 'Compiled successfully...'
else
    echo 'Compilation failed!'
    exit
fi
```
The above code is to check if the compilation is successful. As you can see I use the `$?` flag in order to check if the run code of the compilation was successful. If the exit code is 0 that means the compilation was successful and we can continue with the program.
```
java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > $RUN
if [[ $? -eq 0 ]]
then
    echo 'All tests ran successfully!'
    
    OUTPUT=`grep 'OK' run.txt | cut -d ' ' -f 2`
    OUTPUT=${OUTPUT:1}

    echo $OUTPUT/$OUTPUT correct!
```
The above code if the run is successful. We use the cut command in order to get the number of testcases from the `run.txt` file that we use to output all of the run results. We use the expression `OUTPUT=${OUTPUT:1}` to get rid of the first character of the expression and find the total testcases.
```
else
    echo 'Some tests failed!'
    
    OUTPUT=`grep 'Tests run' run.txt`
    TOTAL=`echo $OUTPUT | cut -d ' ' -f 3 | rev`
    WRONG=`echo $OUTPUT | cut -d ' ' -f 5`
    TOTAL=${TOTAL:1}
    TOTAL=`echo $TOTAL | rev`

    echo $WRONG/$TOTAL incorrect!
    exit
fi
```
The above code is if the run is not successful and there are some errors. We use the cut command again to get both the total amount of testcases and the incorrect testcases. We then use the same expression as the previous part, `TOTAL=${TOTAL:1}`, to get rid of the first character and leave only the number. Through this, we are able to parse the output to get the number of total and incorrect testcases.

## Testing With Different Submissions
I then tested my bash script on different versions of the list methods. The following screenshot is when I used the corrected version. Since it is a corrected version, it should input that it is all correct which is exactly what it outputs.
![Screenshot 2023-03-13 at 9 07 12 PM](https://user-images.githubusercontent.com/35825663/224890646-f59988d1-aaf7-4de5-97db-3539317d5f26.png)
The following screenshot is when I used the incorrect version. Since it was the incorrect version and would cause an infinite loop, it should output an error for the testcase, which it does correctly.
![Screenshot 2023-03-13 at 9 10 19 PM](https://user-images.githubusercontent.com/35825663/224891000-65c49b37-3643-43ec-a5ad-95b146d53e0a.png)
Lastly, I wanted to test the compilation error part of the grading script. I forked the repository and made my own program that had syntax errors. My grading script automatically picked up on this and gave an error in the correct place.
![Screenshot 2023-03-13 at 9 10 41 PM](https://user-images.githubusercontent.com/35825663/224891046-94c9be66-08a9-43f2-a000-952a3072b456.png)
