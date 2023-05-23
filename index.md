Step 4: Log into ieng6
For this step, I pasted the `ssh` command followed by my username from my Lab 1 notes.


```
`⌘v`
```
No password was required and login was successful.

<img width="772" alt="ss1" src="https://github.com/pameza/cse15l-lab-reports/assets/130017007/8acc1eab-7115-4690-a54f-79a0436c7c0b">



Step 5: Clone your fork of the repository from your Github account
Since I previously forked this repository `https://github.com/ucsd-cse15l-s23/lab7` 
I can now clone the forked repository by typing 
```
`git clone https://github.com/pameza/lab7.git`
```
And now we have a directory named `lab7`, we can check this by running `ls`.

<img width="564" alt="ss2" src="https://github.com/pameza/cse15l-lab-reports/assets/130017007/1987bde3-f424-41f0-be26-b17a320a562b">
<img width="474" alt="ss3" src="https://github.com/pameza/cse15l-lab-reports/assets/130017007/cd59e6fd-9d2e-4c13-9dcb-e093a091cb2f">

	

Step 6: Run the tests, demonstrating that they fail
To run these tests I had to compile and run. To do this, I used JUnit to run javac and then again to run java.

```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java

java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ...
```
I can compile with no issue, however, I get a failed test when I run it. 
<img width="860" alt="ss4" src="https://github.com/pameza/cse15l-lab-reports/assets/130017007/8f667b95-4fb1-48a2-9b79-63af6a3d13d4">



Step 7: Edit the code file ListExamples.java to fix the failing test
To edit the faulty java file, I entered vim by typing  
```
vim ListExamples.java 
```
From there, I proceed to edit the file with the following keystrokes:
```
`/ index1` // the `/` helps me find the string that follows it
[<enter>]  // by entering this command, the cursor is placed at the start of the first time that string appears
`nnnn` // `n` skips to the next instance of that string
`er2` // `e` places the cursor at the end of the string, `r` replaces the character selected and `2` is the replacement character
[<esc>] // exits –INSERT – mode
`: wq` // Saves and exits vim
```
These commands change that one number like shown in the image below.
<img width="571" alt="Screen Shot 2023-05-22 at 11 22 39 PM" src="https://github.com/pameza/cse15l-lab-reports/assets/130017007/ca3a60da-8016-4830-b798-5ace76747288">


Step 8: Run the tests, demonstrating that they now succeed
<img width="643" alt="Screen Shot 2023-05-22 at 11 55 11 PM" src="https://github.com/pameza/cse15l-lab-reports/assets/130017007/963f5dd4-ffde-4ec1-97ba-bf7b5840af36">





