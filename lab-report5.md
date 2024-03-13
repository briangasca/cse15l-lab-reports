## Lab Report 5
---

# Student:

Hello, my program that is supposed to merge two lists into one is not merging the last element of the 2nd list.

![Symptom](https://i.imgur.com/6jvkgur.png)

I believe this is due to the last index not being accessed, but I cannot find where the bug would be.

Here is my method:

![Method](https://i.imgur.com/anA0pxQ.png)

Also, `test.sh` is a script that runs JUnit. It is comprised of the commands:

```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore Tester
```

# TA:

Excellent question! What do you think would be the leading cause to an element at the end of a list not being accessed, the for loop or the if-statement? I'd suggest changing one of the conditions to make sure it is accessed.

# Student:

I changed the if-statement from `if(i <= list1.size() - 1)` to `if(i <= list1.size())`, however that resulted in an index out of bounds error.

![](https://imgur.com/JRZqf2c)

I reset everything and changed it back to the original, then I changed the for loops condition from `i < total_size - 1` to `i < total_size` and it worked!

![](https://i.imgur.com/A4D6SSH.png)

It seems that the bug was that the for loop was stopping right before accessing the last element of `list2` because of the `total_size - 1` in the for loop, so it was not added. Now, it can access every index.

# Summary:





