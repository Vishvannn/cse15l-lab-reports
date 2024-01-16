# Lab Report 1 - CSE 15L

---

## cd
---
![Image](2.png)

- Working directory is /home/lecture1/ and is being changed into /home 
- When cd is used without an argument, the working directory is changed to /home. 
- If this is used within the context of a different user, the working directory would be set to that user’s home directory, i.e. /home/[your username here].

---

![Image](1.png)

- Working directory is /home and is being changed into /home/lecture1/ 
- When cd is usd with a folder as an argument, the working directory is changed to that folder. 
- This is intended behaviour and is the most common use case of cd, or “change directory”.



---

![Image](3.png)

- Working directory is /home/lecture1/ 
- When cd is used with a file as an argument, an error message is displayed. 
- This is displayed as cd, “change directory” is to be used with a directory as an argument. When it is used with a file, it returns an error as files cannot be switched into.

---

## ls

![Image](4.png)

- Working directory is /home 
- When ls is used with a folder as an argument, the contents of the folder are displayed. 
- ls stands for “list”. So, it lists all the files and directories within the specified folder.

---

![Image](5.png)

- Working directory is /home/lecture1/ 
- When ls is used with a file as an argument, the path of the file is displayed, as input in the argument. 
- This behavior is exhibited as ls cannot “list” the contents of a file. Since the file contains no files within itself, the file path, as given in the argument is displayed.

---

![Image](6.png)

- Working directory is /home/lecture1/ 
- When ls is used without any arguments, the contents of the working directory are displayed. 
- The default argument that ls takes when no other argument is explicitly specified is ./ or the present directory.

---

## cat
---

![Image](7.png)

- Working directory is /home/lecture1/ 
- When cat is used with a folder as an argument, an error message is displayed, identifying it as a directory. 
- This message is displayed as cat is to be used with files and it doesn’t know how directories are to be handled. 



---

![Image](8.png)

- Working directory is /home/lecture1/ 
- When cat is used with a file as an argument, the contents of the file are displayed. 
- It is important to note that cat does not insert newline characters at the end of a file. The contents of the files are concatenated end to end as they occur in the file itself.

---

![Image](9.png)

- Working directory is /home/lecture1/ 
- When cat is used with no argument, there is no initial response but the command is waiting for an input which it then prints out, this will continue indefinitely. it can be exited using ^C. 
- Since there is no file specified to be concatenated, cat, by default, displays the user input. The key combination Ctrl+C acts as an interrupt and breaks out of this loop.
