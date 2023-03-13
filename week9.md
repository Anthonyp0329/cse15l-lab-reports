# Week 9 Lab Report
Today's topic: Becoming the Done Quick Champion, but with a bash script!

Week 7's lab was definitely my favorite - I loved the competition and trying to figure out the fastest ways to do the tasks! The search for the ```sed```
option was the most memorable part, as my lab tutor, Bryan, had hinted you can edit files with a command, and finding this option was so rewarding!
For this lab report, I'll be revisiting this lab, and figure out how run all the tasks with only one command, using bash scripts!

## My First Attempt

For this attempt, I simply thought you could just put the ssh command, then the rest of the commands, into a bash script and simply run this script from
the terminal. I expected the program to execute the ssh login, then upon successful login, run the commands after it in the script. This is the bash script
I made, which consisted of the log-in command then the commands to execute all the steps I had come up with in lab 7: 

```
ssh cs15lwi23amo@ieng6.ucsd.edu

git clone git@github.com:Anthonyp0329/lab7.git

cd lab7/

javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java

java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests

sed -i '43 s/index1/index2/' ListExamples.java

javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java

java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests

git add ListExamples.java

git commit -m “yay”

git push origin main
```

However, this is the output I got when I ran the script using bash: 
![Wrong Script](wrong_script.png)

None of the commands after the ```ssh``` actually ran, and only ran once I exited the remote server! This made me realize I had to specify that the 
commands had to be run on the remote connection, which led me to the solution.

## Automation Central!

Here's how I made the commands able to run inside the remote connection. After a quick Google search, I realized I could run commands inside the remote 
connection by formatting my ```ssh``` command like so: 
```ssh cs15lwi23amo@ieng6.ucsd.edu "[commands I want to run]"```

I didn't want to paste all my commands inside the quotations, as I was skeptical this would work and too lazy to Google search a way to do this.
Instead, I realized I could make a bash script in my account on the ieng6 server with all the commands I wanted to run, and simply run it as well 
as the ssh login by doing: 
```ssh cs15lwi23amo@ieng6.ucsd.edu "[script_name].sh"```

So then, I logged into my account, and made a file called **run_all.sh**, the contents of which are:

```
git clone git@github.com:Anthonyp0329/lab7.git

cd lab7/

javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java

java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests

sed -i '43 s/index1/index2/' ListExamples.java

javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java

java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests

git add ListExamples.java

git commit -m “yay”

git push origin main
```

I then went back to my own terminal, and made a script called **fast_script.sh** which just contained: 
```
ssh cs15lwi23amo@ieng6.ucsd.edu "run_all.sh"
```



