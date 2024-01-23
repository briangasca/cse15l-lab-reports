# Lab Report 1

by Brian Gasca

***

The terminal has a lot of commands, 3 being `cd`, `ls`, and `cat`, each with their own functions.

***

# Using `cd`

**No Arguments**

> Using `cd` without arguments doesn't change the directory at all, since you are already at the `/home/` directory.
> 
> ![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.11.06%20PM.png)
> 
> However, if you are in another directory that is not home, i.e `/home/lecture1`, `cd` resets your current directory to the `/home/` directory.
> 
> ![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.19.39%20PM.png)
>

**Path to Directory**

> Using `cd` with a directory argument changes where the terminal is looking, now it's looking within the directory you gave.
> Now you are able to access files within that directory. In this case, the original working directory is `/home/`, however
> using `cd lecture1` we are now in the working directory `home/lecture1`.
> 
> ![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.22.59%20PM.png)
>

**Path to File**

> 
> Using `cd` with a file argument does not work and returns an error since `cd` can only work on directories. While we are in the
> directory `/home/lecture1`, attemping to access `/home/lecture1/Hello.java` with `cd` isn't possible since it's not a directory.
> 
> ![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.28.18%20PM.png)

***

# Using `ls`

**No Arguments**

> Using `ls` without arguments returns the files, or directories you can `cd` toward, that you have access to within the current directory you are in.
> When we use `ls` while we are in the `/home/` directory, it only displays `lecture1` as a file we have direct access to. However, if we were to
> `cd lecture1` and now have a current working directory of `/home/lecture1` when we perform `ls`, it gives us more files to choose from.
>
>![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.36.02%20PM.png)
>

**Path to Directory**

> Using `ls` with a directory as the argument will show you the files/directories that the directory specified has access to. Here we are in
> the `/home/` directory and have access to `/home/lecture1`, so we can see what files that directory has despite that not being the current
> working directory.
>
> ![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.39.24%20PM.png)
>
> However, it has restrictions, as you cannot use `ls` on a directory that you currently do not have access to in the current directory the terminal is located in.
> If we try to use `ls messages`, we can't because we don't have access to it from the current working directory, `/home/`. We would have to `cd` to `lecture1` in
> order to use `ls messages`.
>
> ![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.39.42%20PM.png)
>

**Path to File**

> Using `ls` with a file as the argument will just return you the file name you already specified. We are in the `/home/lecture1/messages` directory here,
> since that is where all our txt files are stored.
>
>![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.40.20%20PM.png)

***

# Using `cat`

**No Arguments**

> Using `cat` without arguments will result in you being able to type whatever and then the terminal returning exactly what you typed.
> Right now, we are just in the `/home/` directory and this effect happens regardless of the working directory.
>
>![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.45.51%20PM.png)
>

**Path to Directory**

> Using `cat` on a directory results in an error being returned because you cannot use `cat` on a directory. We are still in the
> `/home/` working directory and can't use `cat` on the `lecture1` directory despite having direct access to it.
>
>![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.47.06%20PM.png)
>
> 
**Path to File**

> Using `cat` on a file results in it returning what's inside that file. You can also use it on two separate files to return what they both contain.
> Right now we are in the `/home/lecture1/messages` directory since we have to be here to access the txt files.
>
>![Image](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-10%20at%203.47.52%20PM.png)
>


