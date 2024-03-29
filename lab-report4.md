## Lab Report 4
by Brian Gasca
---
- This is steps 4-9 of Lab7.

## Step 4:

- **Log into ieng6**
  
I typed: `s` `s` `h` `<space>`  `b` `g` `a` `s` `c` `a` `@` `i` `e` `n` `g` `6` `-` `2` `0` `1` `.` `u` `c` `s` `d` `.` `e` `d` `u` `<enter>` in order to log into ieng6. I picked `ieng6-201` because apparently the other servers don't have jdk installed.

![Logging into ieng6](https://i.imgur.com/6Lxn12x.png)

- For this step, I ran the command `ssh` into the server `bgasca@ieng6-201.ucsd.edu` to connect my terminal to the remote ieng6 server. 

## Step 5: 

- **Clone the forked repository from Github account using SSH URL**

I typed: `g` `i` `t` `<space>`  `c` `l` `o` `n` `e` `<space>`  `<CTRL+V>` `<enter>`

The SSH URL was on my clipboard, so I simply used the paste command.

![Step 5](https://i.imgur.com/mmhLeZ1.png)

- For this step, I ran the command `git clone` to clone the repository into `ieng6`. This let me edit the repository within ieng6 so I could do my repository editing remotely.

## Step 6:

- **Run tests and demonstrate that they fail**

First I typed: `l` `s` `<enter>` to view the files and directories, then i typed `c` `d` `<space>` `l` `a` `b` `<enter>` to change my current directory to the `lab7` one.
I typed `l` `s` `<enter>` again to view files and directories, then typed `b` `a` `s` `h` `<space>`  `t` `e` `s` `t` `.` `s` `h` `<enter>` to run the `JUnit` test.

![](https://i.imgur.com/ejZDyzw.png)

- For this step, I used the `ls` commands to see files that I could traverse to. I used `cd` to change directories, and `bash` to run a script that would run the JUnit tests.

## Step 7:

- **Edit the code file to fix the failing test**

I typed `v` `i` `m` `<space>` `L` `i` `s` `t` `E` `x` `a` `m` `p` `l` `e` `s` `.` `j` `a` `v` `a` `<enter>` in order to open the code editor `vim` so i could change the functionality.

![](https://i.imgur.com/K86b3YU.png)

I typed `j` and held it in order to scroll down and get to where I needed in the code editor to fix the problem.

![](https://cdn.discordapp.com/attachments/461005479792082944/1212250776890642442/image.png?ex=65f12783&is=65deb283&hm=c7baebf63ce5052c85433facbff762b08af0ef1b6c5caa330f5ab34b86ac83ad&)

I pressed `h` `h` `h` `h` `h` (h 5 times) in order to get to the proper place to edit the code

![](https://i.imgur.com/HEmGg1F.png)

I pressed `i` `<backspace>` `2` `<esc>` in order to change `index1` to `index2`

![](https://i.imgur.com/uAicgTk.png)

Finally, I exit and save by typing `:` `w` `q`

![](https://i.imgur.com/npWPZNv.png)

- For this step, I used the `vim` command to open the file `ListExamples.java` inside the `vim` code editor so I could change the code inside the file. The effect of the keypress `j` here was a scrolling effect, then `h` as to turn my cursor to the left, `i` was to instert characters, and `<esc>` was to exit out of the insertion. Finally, `:wq` was used to save and quit the vim editor.

## Step 8:

- **Run the tests demonstrating that they now succeed.**

I typed `<up>` `<up>` `<up>` to get back to `bash test.sh`

![](https://i.imgur.com/mmhM8aB.png)

Then i pressed `<enter>`

![](https://i.imgur.com/S71INaG.png)

- For this step, using `<up>` each time would go back one command I used previously. In this case, `bash test.sh` was 3 away so I had to press it twice.

## Step 9:

- **Commit and push the resulting change**

First I typed `g` `i` `t` `<space>`  `a` `d` `d` `<space>`  `L` `i` `s` `t` `E` `x` `a` `m``p` `l` `e` `s` `.` `j` `a` `v` `a` `<enter>` to add my changes to be committed.

Then i typed `g` `i` `t` `<space>`  `c` `o` `m` `m` `i` `t` `<space>`  `-` `m` `<space>`  `"` `F` `i` `x` `e` `d` `<space>`  `F` `u` `n` `c` `t` `i` `o` `n` `a` `l` `i` `t` `y` `"` `<enter>` to commit my changes.

![](https://i.imgur.com/Fr1SVYl.png)

Finally, `g` `i` `t` `<space>`  `p` `u` `s` `h` to push to the repository.

![](https://i.imgur.com/EI3mAnT.png)

- For this step, `git add` is used to add changes to be commited, `git commit` solidifes those changes, and `git push` pushes those changes to the repository.
