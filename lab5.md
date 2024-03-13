# Part 1

Student Vishvan Sivanandan: I'm currently working on a very simple Java program that's supposed to print a greeting followed by any arguments passed to it. When I execute the program directly using java Greet Hello, 
it works as expected and prints Hello, Hello!. However, when I run it through a bash script named greet.sh, it just prints Hello, without repeating the argument.

### Greet.java

```
public class Greet {
    public static void main(String[] args) {
        if (args.length > 0) {
            System.out.println("Hello, " + args[0] + "!");
        } else {
            System.out.println("Hello, ");
        }
    }
}
```

### Terminal Output

```
$ ./test.sh Hello
Hello,
```

TA John Cena: t sounds like the issue might be related to how arguments are handled in your bash script. Could you please check if the bash script is correctly passing all arguments to your Java program?
You can do this by adding an echo statement before the java command in your script like so:
```
echo java Greet "$@"
```
Student Vishvan Sivanandan: Thank you for the help! After adding the echo command, here's what I got:
```
$ ./test.sh Hello
java Greet "$@"
Hello, Hello! 
```

### File Structure
```
/Users /vishvansivanandan /downloads /lab5 - Greet.java - test.sh
```
### Contents of Greet.java
```
public class Greet {
    public static void main(String[] args) {
        if (args.length > 0) {
            System.out.println("Hello, " + args[0] + "!");
        } else {
            System.out.println("Hello, ");
        }
    }
}
```
### Contents of test.sh (Before fixing)
```
java Greet  # Missing "$@"
```
### Contents of test.sh (After fixing)
```
java Greet "$@"
```

# Part 2 - Reflection
This quarter, my exploration into Vim profoundly impacted my coding efficiency and workflow. Initially, the modal editing concept and keyboard-centric interface seemed daunting, 
but dedicating time to learn Vim's keybindings and commands opened up a new realm of productivity. I was particularly fascinated by the composability of commands, which allows for 
executing complex editing tasks with minimal keystrokes. This not only sped up my coding process but also encouraged a deeper understanding of text manipulation and navigation. 










