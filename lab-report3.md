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

This test is supposed to receive an input integer array `{3,4,5}` from the reference `input1`. `assertArrayEquals` compares the expected, `{5,4,3}` to the returned.
The returned value here is actually `{0,0,0}`, since the `newArray` variable in the `reversed` method has the same length as `arr`, but not the same elements.

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

![Symptom-Image]()

With a failure inducing input like `{3,4,5}`, we get a JUnit test failure with the message: `Expected [5] but was [0]`. This happens since
the returned value of `ArrayExamples.reversed(input1));` is actually `{0,0,0}`, since the `newArray` variabled in `reversed` method has the same length, but is not copying the same elements.

**Fixed Code**

- In order to fix this, we must make sure `newArray` is getting filled with `arr`'s existing elements.

- Before

```Java
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

- After

```Java
int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - 1 - i]; // Changed
    }
    return newArray;
  }
```

Here, we are making an array `newArray` have a starting value of the ending element of `arr`, or `arr[arr.length - 1]`. Then we increment `arr[arr.length - 1 - i]` in order to traverse further toward the beginning of `arr`





