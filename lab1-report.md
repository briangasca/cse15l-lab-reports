# Lab Report 1

The terminal has a lot of commands, 3 being `cd`, `ls`, and `cat`, each with their own functions.

***

# Using `cd`

**No Arguments**
> Using `cd` without arguments doesn't change the directory at all at first
> 
> ![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.11.06%20PM.png)
> 
> However, if you are in a path, `cd` resets your current path to the home path.
> 
> ![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.19.39%20PM.png)
> 
**Path to Directory**

> Using `cd` with a directory argument changes where the terminal is looking, now it's looking within the directory you gave.
> Now you are able to access files within that directory
> 
> ![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.22.59%20PM.png)
> 
**Path to File**
> 
> Using `cd` with a file argument does not work, `cd` can only work on directories.
> 
> ![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.28.18%20PM.png)

***

# Using `ls`

**No Arguments**
>Using `ls` without arguments returns the files, or directories you can `cd` toward, that you have access to within the current directory you are in
>
>![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.36.02%20PM.png)
>
**Path to Directory**
> Using `ls` with a directory as the argument will show you the files/directories that the directory specified has access to.
>
> ![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.39.24%20PM.png)
>
> However, it has restrictions, as you cannot use `ls` on a directory that you currently do not have access to in the current directory the terminal is located in.
>
> ![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.39.42%20PM.png)
>
**Path to File**
>Using `ls` with a file as the argument will just return you the file name you already specified.
>
>![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.40.20%20PM.png)

***

# Using `cat`

**No Arguments**
