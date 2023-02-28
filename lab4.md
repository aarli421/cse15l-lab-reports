# Lab Report 4: "Done Quick"

## Step 4: Log into ieng6
Keys pressed: 
* `Ctrl+R` `ssh` `<enter>`

<img width="681" alt="Screenshot 2023-02-27 at 9 23 20 PM" src="https://user-images.githubusercontent.com/35825663/221761617-2f2abfa4-e620-4286-8c97-0de4d891cecf.png">

The `ssh cs15lwi23atw@ieng6.ucsd.edu` command is accessible within bash history, so I used the `Ctrl+R` command to access it. After typing `ssh`, it was unique enough to access my last ssh command which was the one I wanted. As depicted, I successfully enter the ieng6 machine using the ssh command.

## Step 5: Clone fork of Github repository
Keys pressed: 
* `Ctrl+R` `git cl` `<enter>`
* `cd` `l` `<tab>` `<enter>`

<img width="523" alt="Screenshot 2023-02-27 at 9 26 13 PM" src="https://user-images.githubusercontent.com/35825663/221762040-02fe1837-1e5e-4828-843f-e6fc34ac3ebd.png">

The `git clone git@github.com:aarli421/lab7.git` command is accessible within bash history, so I used the `Ctrl+R` command to access it. After typing `git cl`, it was unique enough to access my last git clone command which was the one I wanted. After cloning the repository, I then entered the github working directory. I did this by using the `<tab>` autocomplete after typing `l` allowing me to enter the working folder. As depicted, I successfully clone and enter the github repository.

## Step 6: Run tests
Keys pressed: 
* `Ctrl+R` `javac` `<enter>`
* `Ctrl+R` `java ` `<enter>`

<img width="971" alt="Screenshot 2023-02-27 at 9 28 27 PM" src="https://user-images.githubusercontent.com/35825663/221762334-77e4baea-3e6b-4263-b478-20795482b06a.png">

The `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.jav` command is accessible within bash history, so I used the `Ctrl+R` command to access it. After typing `javac`, it was unique enough to access my last compile command which was the one I wanted. I then wanted to run the java files. The `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` command was also accessible within bash history, so I used the `Ctrl+R` command to access it. After typing `java `, it was unique enough to access my last run command which was the one I wanted. As depicted, I compile and run the java files which shows an error within the ListExamples.java file.

## Step 7: Edit code
Keys pressed: 
* `nano` `L` `<tab>` `.j` `<tab>` `<enter>`
* `Ctrl+Shift+-` `43, 13` `<enter>`
* `<backspace>` `2`
* `Ctrl+X` `y` `<enter>`

<img width="776" alt="Screenshot 2023-02-27 at 9 34 59 PM" src="https://user-images.githubusercontent.com/35825663/221763309-51b878cd-afa9-4e89-b483-1e92cba6208e.png">

I want to edit the ListExamples.java file, so I access it using the command `nano`. I use `<tab>` to autocomplete the file name allowing me to enter ListExamples.java with just 5 keypresses. I then want to locate the error, which is approximately at row 43 column 13. I then access this through `nano`'s `Ctrl+Shift+-` command allowing me to go to the exact space I want. I then edit this file by changing the 1 to a 2. Finally, I exit nano using `Ctrl+X` and I save the file accordingly.

## Step 8: Run tests
Keys pressed: 
* `<up>` `<up>` `<up>` `<enter>`
* `<up>` `<up>` `<up>` `<enter>`

<img width="975" alt="Screenshot 2023-02-27 at 9 36 17 PM" src="https://user-images.githubusercontent.com/35825663/221763491-de8242df-2f2e-4f4b-9b32-c8ccb61279fe.png">

I want to compile and run the files again using the `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.jav` and `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` commands. Hence, I use the `<up>` keys to access the previously used commands in Step 6. I access it and run both commands. As depicted, there is no more error from the Junit tests.

## Step 9: Commit and push changes
Keys pressed: 
* `Ctrl+R` `git a` `<enter>`
* `Ctrl+R` `git co` `<enter>`
* `Ctrl+R` `git p` `<enter>`

<img width="501" alt="Screenshot 2023-02-27 at 9 43 05 PM" src="https://user-images.githubusercontent.com/35825663/221764526-6e78a3dd-ad32-4062-9ae9-404fbca64ab0.png">
<img width="721" alt="Screenshot 2023-02-27 at 9 43 51 PM" src="https://user-images.githubusercontent.com/35825663/221764648-e02ca0bf-e24b-49db-94c7-ceda58a9be97.png">

I want to run the `git add .` command, which is accessible within bash history, so I used the `Ctrl+R` command to access it. After typing `git a`, my prompt was unique enough to get the command I wanted. Similarly, I use the `Ctrl+R` command to access the `git commit -m "Fixed bug"` command within bash history. I am able to get this query with the unique prompt `git co`. Finally, I use the `Ctrl+R` command once again to get the `git push` command from bash history. I am able to get this query with the unique prompt `git p`. As depicted, I successfully push my changes to the repository.
