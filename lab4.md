# **Lab 4**

This is what the folder looks like:

```bash
vishvansivanandan@Vishvans-MacBook-Pro/cse15l/lab7:
ListExamples.java  ListExamplesTests.java  lib  test.sh
```

##  `ieng6` login

The `ssh` command can be used to connect to the machine. In this case, `ieng6-201` is being connected to. No shortcuts can be used since `ieng6-201.ucsd.edu` is not a recognizable `bash` command. 

```bash
vishvansivanandan@Vishvans-MacBook-Pro ~ % ssh vsivanandan@ieng6.ucsd.edu
Last login: Tue Jan 30 19:14:40 2024 from 128.54.225.210


quota: Cannot resolve mountpoint path /home/linux/dsmlp/.snapshot/daily.2024-01-12_0010: Stale file handle
quota: Cannot resolve mountpoint path /home/linux/ieng6/cs120wi24/cs120wi24dx/.snapshot/hourly.2024-01-29_1201: Stale file handle
quota: Cannot resolve mountpoint path /home/linux/dsmlp/.snapshot/daily.2024-02-04_0010: Stale file handle
quota: Cannot resolve mountpoint path /home/linux/dsmlp/.snapshot/daily.2024-02-05_0010: Stale file handle
Hello vsivanandan, you are currently logged into ieng6-201.ucsd.edu

You are using 0% CPU on this system

Cluster Status 
Hostname     Time    #Users  Load  Averages  
ieng6-201   01:20:01   3  7.10,  8.37,  9.34
ieng6-202   01:20:01   3  1.20,  1.14,  1.15
ieng6-203   01:20:01   1  0.67,  0.28,  0.20

 

To begin work for one of your courses [ cs15lwi24 ], type its name 
at the command prompt.  (For example, "cs15lwi24", without the quotes).

To see all available software packages, type "prep -l" at the command prompt,
or "prep -h" for more options.
```

## Cloning the repository

`git clone` and then `ssh` URL of the forked repository is used to clone the repository onto the local machine. While `<tab>` can be pressed to autocomplete the word `clone`, a negligible amount of time would be saved.
Paste the URL into the terminal by simply right-clicking in the terminal window. `<enter>` is then pressed.

```bash
[vsivanandan@ieng6-201]:~:49$ git clone git@github.com:vishvannn/lab7.git
Cloning into 'lab7'...
remote: Enumerating objects: 58, done.
remote: Total 58 (delta 0), reused 0 (delta 0), pack-reused 58
Receiving objects: 100% (58/58), 469.36 KiB | 1.07 MiB/s, done.
Resolving deltas: 100% (21/21), done.
```

## Changing the working directory

`cd` can be used to change the working directory to `lab7`. `<tab>` can be pressed after typing `cd l` as there exist no other folders in `~/vsivanandan` that start with the letter `l`. This will then auto-complete the rest of the path. `<enter>` is then pressed.

```bash
[vsivanandan@ieng6-201]:~:52$ cd lab7/
```

## Compiling the tests 

The command `javac` compiles the `.java` files. However, it is necessary that the `classpath` is modified to include the Hamcrest core and JUnit `.jar` files in order for the program to compile successfully. The `classpath`, by default is the current directory 
which is also necessary to compile the files correctly. So, we specify the paths of the current directory and both the required `.jar` files separated by `:`. No shortcuts can be used while entering the paths here; however, the syntax `*.java` can be used to 
compile all the files in the present directory. `<enter>` is then pressed.

```bash
[vsivanandan@ieng6-201]:lab7:58$ javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
```

## Running the tests

The command `java` runs the compiled class files. It is once again necessary to modify the `classpath` in order to run the tests successfully. So, we can press `<up>` in order to recall the last command. The `<home>` key can then be pressed in order to return to the 
start of the line. `<Ctrl> + <right>` can then be pressed to seek to the end of the first word. Here, `<backspace>` can then be pressed in order to obtain the `java` command. `<end>` can then be pressed to return to the end of the line. Here, `<backspace>` can be pressed 5 times
to remove `*.java`. `org.jun` is then typed and `<tab>` pressed in order to autocomplete to `org.junit.`. `run` can then be typed and `<tab>` pressed to autocomplete to `org.junit.runner`. `.JU` can then be typed and `<tab>` pressed to autocomplete to `org.junit.runner.JUnitCo`. The 
rest of the word `JUnitCore` can then be entered manually. Finally, `List` can be typed and `<tab>` pressed to autocomplete to `ListExamples`. The rest of the filename can be entered manually. `<enter>` is then pressed.

```bash
[vsivanandan@ieng6-201]:lab7:61$ java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
JUnit version 4.13.2
..E
Time: 0.572
There was 1 failure:
1) testMerge2(ListExamplesTests)
org.junit.runners.model.TestTimedOutException: test timed out after 500 milliseconds
        at java.util.Arrays.copyOf(Arrays.java:3210)
        at java.util.Arrays.copyOf(Arrays.java:3181)
        at java.util.ArrayList.grow(ArrayList.java:267)
        at java.util.ArrayList.ensureExplicitCapacity(ArrayList.java:241)
        at java.util.ArrayList.ensureCapacityInternal(ArrayList.java:233)
        at java.util.ArrayList.add(ArrayList.java:464)
        at ListExamples.merge(ListExamples.java:42)
        at ListExamplesTests.testMerge2(ListExamplesTests.java:19)

FAILURES!!!
Tests run: 2,  Failures: 1
```

We can see that the test fails.

## Editing the code

`vim` can be used to edit the code. `vim List` can be typed and `<tab>` pressed to autocomplete the file name. The extension can then be entered manually.

```bash
[vsivanandan@ieng6-201]:lab7:183$ vim ListExamples.java
```
This opens the file in vim. Here, in normal mode, we can use `:set number` to enable line numbers. The same can be added to `~/.vimrc` to ensure that line numbers are enabled by default in the future.

We can now see that there is an error on line 44. In normal mode, `44G` can then be typed to reach line 44. `e` can then be pressed to reach the end of the line. `r` can then be pressed to replace the character directly under the cursor in place. In this case, the number `1` is to be changed to `2`.
`2` can then be entered to complete this operation. `:wq` can then be entered and `<enter>` pressed to quit out of vim.


## Recompiling and running the tests

`<up>` can be pressed twice in order to reach the `javac` command. `<enter>` can then be pressed. The tests are now compiled.
The same can be repeated once again in order to reach the `java` command. `<enter>` can then be pressed. The tests are now run without errors.

```bash
[vsivanandan@ieng6-201]:lab7:184$ javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
[vsivanandan@ieng6-201]:lab7:185$ java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
JUnit version 4.13.2
..
Time: 0.037

OK (2 tests)
```


## Committing and Pushing

`git commit -a` can be used to commit changes from all the files that were modified. This then opens a vim window wherein the commit message can then be entered. In order to save time, the `-m` flag can be used to enter the commit message within the command line.

```bash
[vsivanandan@ieng6-201]:lab7:186$ git commit -a -m "Fixed ListExamples.java"
[main 4e211d6] Fixed ListExamples.java
 Committer: Sriharsha Kavuri <skavuri@ieng6-201.ucsd.edu>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 1 file changed, 1 insertion(+), 1 deletion(-)
```

We can then use `git push` to push the committed changes to the origin. 

```bash
[vsivanandan@ieng6-201]:lab7:187$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 310 bytes | 310.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To github.com:vishvannn/lab7.git
   327ab1a..4e211d6  main -> main
```

The changes are now pushed to the fork of the repository.
