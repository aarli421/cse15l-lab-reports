## Part 1: Installing VSCode
Please go to <a href="https://code.visualstudio.com/download">this link</a> and download your corresponding visual studio code version. For instance, if you have mac you will download the Mac version listed, and if Windows you will download the Windows version listed. Once downloaded, be sure to click the downloaded application to install it to your computer. For Windows, you might need to allow the application to change your computer, and on Mac you might need to drag it into your applications folder. Once installed, open visual studio code and voila, you have begun your coding journey.

<img width="1711" alt="VSCode ss" src="https://user-images.githubusercontent.com/35825663/212194737-65667f71-85ae-4825-9087-9fed584e8539.png">

## Part 2: Remotely Connecting
Please search up your username on the <a href="https://sdacs.ucsd.edu/~icc/index.php">UCSD username searching engine</a>. If this is your first time accessing your account or you need to change your password, there is a change password option that allows you to change your password to a new one. After you have successfully obtained both your username and password, proceed to your command line and remotely connect by typing

```
ssh cs15lwi23XXX@ieng6.ucsd.edu
```

where you replace XXX with your own username. You will then get prompted with a password prompt where you can enter your password and successfully login.

<img width="509" alt="Screenshot 2023-01-12 at 2 31 38 PM" src="https://user-images.githubusercontent.com/35825663/212195447-11701dc6-82f9-4171-890a-adc5f472c203.png">

## Part 3: Trying Some Commands
Please proceed with testing different command line commands. To enter a command, you type in the command and then press enter. Some example commands include:
* cd: outputs nothing, but changes current working directory 
* ls: outputs lots of files which seem to be the files in the working directory
* cp /home/linux/ieng6/cs15lwi23/public/hello.txt ~/: outputs nothing, but seems to copy a hello.txt file to home folder
* cat hello.txt: outputs "Hello! Welcome to CSE 15L" which seems to be the contents of the hello.txt file

Flags can be added to these commands in order to show more or less info. For instance, try
* ls -lat: each file has its own row with different parameters displayed such as permissions, user, and group
* ls -a: all files are listed, including previously hidden files

<img width="1330" alt="Screenshot 2023-01-12 at 2 37 06 PM" src="https://user-images.githubusercontent.com/35825663/212196187-9b3da6d9-850a-471e-8b2f-0958a193091d.png">
