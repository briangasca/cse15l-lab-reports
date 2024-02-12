# Lab Report 3
by Brian Gasca

# Part 1
---

The buggy program I chose is the `reversed` method in week 4's lab. It's intended functinality is to return a new array 
with all the elements of the input array in reversed order, however it doesn't do that for all inputs.

**The Buggy Code:**

```Java
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

**Failure Inducing Input**

If we give the method a regular array, in this case `{3,4,5}`, it completely gets it wrong.

```Java
  @Test
  public void testReversed() {
    int[] input1 = {3,4,5};
    assertArrayEquals(new int[]{5,4,3}, ArrayExamples.reversed(input1));
  }
```

This test is supposed to receive an input integer array `{3,4,5}` from the reference `input1`. `assertArrayEquals` compares the expected, `{5,4,3}` to the returned. However, it fails, and we will go more in depth as to why later in the writing.

**Non-Failure Inducing Input**

If we give the method an empty array, `{}`, it gets it correct since there's nothing to reverse.

```Java
  @Test
  public void testReversed() {
    int[] input1 = {};
    assertArrayEquals(new int[]{}, ArrayExamples.reversed(input1));
  }
```

This test is extremely similar to the one above, the only thing changing is what `input` is referencing, which is an empty array now. Since the `newArray` variable in `reversed` is also empty,
then it's going to be the same. There's not really any reversing going on here since there's no elements.

**Symptom**

![Symptom-Image](https://github.com/briangasca/cse15l-lab-reports/blob/main/images/Screenshot%202024-02-12%20at%202.00.15%20PM.png?raw=true)

With a failure inducing input like `{3,4,5}`, we get a JUnit test failure with the message: `Expected [5] but was [0]`. This happens since
the returned value of `ArrayExamples.reversed(input1));` is actually `{0,0,0}`, since the `newArray` variabled in `reversed` method has the same length, but is not copying the same elements.

**Fixed Code**

- In order to fix this, we must make sure `newArray` is getting filled with `arr`'s existing elements in a backward order.

- **Before**

```Java
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

- **After**

```Java
int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - 1 - i]; // Changed
    }
    return newArray;
  }
```

Here, we are making an array `newArray` have a starting value of the ending element of `arr`, or `arr[arr.length - 1]`. Then we increment `arr[arr.length - 1 - i]` in order to traverse further toward the beginning of `arr`

## Part 2
---

For part 2, I chose the `grep` command.

* For the sake of simplicity, I have used `cd` to get into the `technical/` directory, so if I don't include the `technical/` directory in my responses, this is because it is assumed we are already inside it.

grep -r
grep -l
grep -L


`grep -c`
---

* `grep -c` is supposed to print the count of matching items for an input file you put into it.
* This only works on files and not directories!

>Examples:
>1:
> If we use `grep -c` in the `/technical/` directory, we can count how many times a word appears in a text file. For example,
>`grep -c the plos/journal.pbio.0020001.txt` will print out `147`, which is how many times the word "the" was written in that text file.
```
$ grep -c the plos/journal.pbio.0020001.txt
147
```
>
>2:
>We can also use `grep -c` on multiple files at once, or even all the files in a directory. By using the command `grep -c "the" techincal/plos/*.txt`, `grep` will search every `.txt` file in the
`technical/plos/` directory and return how many times it finds "the" per file.
> Like so:
> Note: We are already in the `technical/` directory, which is why the command call is only `plos/..` and the return is only `plos/..`
```
$ grep -c "the" plos/*.txt
...
plos/pmed.0020249.txt:266
plos/pmed.0020257.txt:22
plos/pmed.0020258.txt:22
plos/pmed.0020268.txt:33
plos/pmed.0020272.txt:40
...
```

* Here we can see, it returns the file and the amount of times "the" was found in the format `file : count`

`grep -r`
---

* `grep -r` recursively searches through directories and their subdirectories for a line that matches a given input. It prints out the lines where it finds the given input.
* This works on both files and directories!

> Examples:
> 1:
>  If we use `grep -r` to search for the word "the" in the `plos/` directory, we can write it as `grep -r "the" plos/`. This will search every file within the `plos/` directory and print out the line where it's found.
```
$ grep -r "the' plos/
...
plos/pmed.0020281.txt:        improve the status quo—be it in pharmaceutical marketing or managed-care decision
plos/pmed.0020281.txt:        success (I have adapted his comments for all of us who gathered in Washington in mid-May
plos/pmed.0020281.txt:        2005): “To leave the world a bit better, whether by a healthy child, a garden patch or a
plos/pmed.0020281.txt:        redeemed social condition; to know even one life breathed easier because you have lived;
...
```
>
> 2: If we use `grep -r` to search for the word "the" in a specific file within the `plos/` directory, we can also do that too. It will return the lines where it's found within the file.
```
$ grep -r "the" plos/pmed.0020281.txt
plos/pmed.0020281.txt:        Whistleblowers serve no function if they cannot tell their stories. The present story of
plos/pmed.0020281.txt:        PLoS Medicine —that involves the pharmaceutical industry, pharmaceutical
plos/pmed.0020281.txt:        benefit management corporations, the managed care industry, and the political and lobbying
...
```

`grep -l`
---

* `grep -l` displays the names of the files that have at least one line of a given input that I gave the command. It prints out the files it found.
* This only works on files and not directories!

> Examples:
> 1:
> If we use `grep -l` to find `.txt` files that contain the word "you" in them within the `plos/` directory, we can do that with this here. It will only print the file name where the input is located.
```
$ grep -l "you" plos/*.txt
plos/pmed.0020123.txt
plos/pmed.0020140.txt
plos/pmed.0020149.txt
...
```
>
> 2: We can also use `grep -l` to find ALL files that contain the word "you", not just `.txt` files. It will print out the file name where the input is located.
> In this case, the result is the same since there's only `.txt` files within the `plos/` directory.
```
$ grep -l "you" plos/*
plos/pmed.0020123.txt
plos/pmed.0020140.txt
plos/pmed.0020149.txt
...
```

`grep -L`

* `grep -L` is the opposite of `grep -l`. It prints out all files that do NOT have the specified input within it. It will only print out file names, not text within them.
* This only works on files and not directories!

> Examples:
> 1:
> If we use `grep -L` to find all `.txt` files not containing the word "hello" in them within the `plos/` directory, it will return all the files that DO NOT have "hello" inside them.
```
$ grep -L "hello" plos/*.txt
plos/pmed.0020258.txt
plos/pmed.0020268.txt
plos/pmed.0020272.txt
plos/pmed.0020273.txt
...
```
>
> 2: We can also use `grep -L` on multiple, specific files to find out if those specific files do not contain the given input. It will return the files that don't have the input.
```
$ grep -L "hello" plos/pmed.0020258.txt plos/journal.pbio.0020001.txt plos/pmed.0020272.txt
plos/pmed.0020258.txt
plos/journal.pbio.0020001.txt
plos/pmed.0020272.txt
```
Here, all 3 of them did not have the word "hello" inside of them.

**Sourced Used**

[Linux grep documentation](https://man7.org/linux/man-pages/man1/grep.1.html)







