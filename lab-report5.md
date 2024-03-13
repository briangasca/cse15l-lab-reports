# Lab Report 5
---

# Part 1:

#### Student:

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

#### TA:

Excellent question! What do you think would be the leading cause to an element at the end of a list not being accessed, the for loop or the if-statement? I'd suggest changing one of the conditions to make sure it is accessed.

#### Student:

I changed the if-statement from `if(i <= list1.size() - 1)` to `if(i <= list1.size())`, however that resulted in an index out of bounds error.

![](https://i.imgur.com/JRZqf2c.png)

I reset everything and changed it back to the original, then I changed the for loops condition from `i < total_size - 1` to `i < total_size` and it worked!

![](https://i.imgur.com/A4D6SSH.png)

It seems that the bug was that the for loop was stopping right before accessing the last element of `list2` because of the `total_size - 1` in the for loop, so it was not added. Now, it can access every index.

## Summary:

The file and directory structure really didn't matter for this case, but we had to be in the `lab-report5` directory at the very least to access `test.sh` with `bash`.

![](https://i.imgur.com/TP3qfP7.png)

#### Before Fixing Bug:

- The `lib` directory just holds the contents of `JUnit` testing package, which we can't access since they are binary files.

- The `Main.java` file has the main method inside of it that we were testing.
The code inside is:

```
import java.util.ArrayList;
import java.util.List;

public class Main {

	public static List<String> merge(List<String> list1, List<String> list2){

		List<String> result = new ArrayList<>();

		int total_size = list1.size() + list2.size();

		for(int i = 0; i < total_size - 1; i++){
			if(i <= list1.size() - 1){
				result.add(list1.get(i));
			} else {
				result.add(list2.get( i - list2.size()));
			}
		}
		return result;
		
	}
}
```

- As stated above, `test.sh` is a script that runs the JUnit tests, it is as follows:

```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore Tester
```

- Finally, the file `Tester.java` is the JUnit test file for testing our method's functionality:

```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.*;
import java.util.ArrayList;


public class Tester {

	
	@Test
	public void testMainFunction(){
		List<String> list_1 = new ArrayList<String>(Arrays.asList("hello","hola","bonjour"));

		List<String> list_2 = new ArrayList<String>(Arrays.asList("hi","que pasa","hey"));


		assertArrayEquals(new String[]{"hello","hola","bonjour","hi","que pasa","hey"}, Main.merge(list_1,list_2).toArray());

		assertEquals(6, Main.merge(list_1, list_2).size());

	}

}
```

### How to trigger the bug:

- To trigger the bug, simply run the `bash test.sh` command to run the tests, which would promptly return with 1 failure out of 1 test.

![](https://i.imgur.com/6jvkgur.png)

### What to edit to fix:

We must change the for loop's condition on line `12` in `Main.java` from `for(int i = 0; i < total_size - 1; i++)` to `for(int i = 0; i < total_size; i++)`, getting rid of the ` - 1` part of the condition. This will now make it so we can access all of the `list2`'s indices and add them to `result`.

# Part 2:

I learned a lot about the text editor `vim` and how to use another text editor besides VSCode and Eclipse. Vim is extremely powerful and versatile however has a steep learning curve due to the odd syntax of its commands. However, it's extremely useful if you are on machines such as Linux where the terminal is your best friend. I felt like a programmer from one of those hacker movies while using it so that made it even more enjoyable to learn, even though I wasn't really doing anything special. I thoroughly enjoyed learning with my lab group and labs were my favorite part of this class and where I learned the most.








