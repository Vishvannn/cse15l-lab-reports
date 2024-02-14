# Lab Report 3

The layout of the folders is shown below:

```
/home/gram/cse15l:
f1  f10  f2

/home/gram/cse15l/folder1:
f3  f4  f5  f6  f7  f8  f9

```

The above files hold text that is irrelevant for this report. Relevant text is displayed in codeblocks when necessary.

## Bugs

```
// Returns a *new* array with all the elements of the input array in reversed
// order
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
  }
  return arr;
}

```

The errors can be identified using Junit Tests.

```
@Test
public void testReversed() {
  int[] input1 = { };
  assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
}
```

```
vishvansivanandan@Vishvans-MacBook-Pro:~/$ java -cp .:./lib/hamcrest-core-1.3.jar:./lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
.
Time: 0.016

OK (1 test)
```

The program has a flaw, but this particular test doesn't reveal any issues. We anticipate that the reverse function should output a new array mirroring the order of elements in the original array, but in reverse. 
However, in this scenario, we're evaluating the function with an empty array. Given that it has no elements, potential errors remain undetected, allowing the test to succeed.

The following changes can be used to solve this:

```
-- int[] input1 = { };
++ int[] input1 = {1, 2, 3};
-- assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
++ assertArrayEquals(new int[]{3, 2, 1}, ArrayExamples.reversed(input1));
```

After these edits, the failures can be observed.

```
vishvansivanandan@Vishvans-MacBook-Pro:~/$ java -cp .:./lib/hamcrest-core-1.3.jar:./lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
.E
Time: 0.027
There was 1 failure:
1) testReversed(ArrayTests)
arrays first differed at element [0]; expected:<3> but was:<0>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReversed(ArrayTests.java:8)
        ... 30 trimmed
Caused by: java.lang.AssertionError: expected:<3> but was:<0>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 36 more

FAILURES!!!
Tests run: 1,  Failures: 1
```

The output indicates that the first element should have been 3 but turned out to be 0. To identify the mistake, we should examine the code segment responsible for populating the new array. 
In the expression `arr[i] = newArray[arr.length - i - 1];,` elements are incorrectly assigned from the new array to the original array, contrary to our intention. 
The correction involves reversing the assignment direction, which can be achieved by modifying the code to `newArray[arr.length - i - 1] = arr[i];`.

This does not however fix the error completely as seen below
```
vishvansivanandan@Vishvans-MacBook-Pro:~/$ java -cp .:./lib/hamcrest-core-1.3.jar:./lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
.E
Time: 0.02
There was 1 failure:
1) testReversed(ArrayTests)
arrays first differed at element [0]; expected:<3> but was:<1>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReversed(ArrayTests.java:8)
        ... 30 trimmed
Caused by: java.lang.AssertionError: expected:<3> but was:<1>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 36 more

FAILURES!!!
Tests run: 1,  Failures: 1
```
This time, the expected element is 3 but the actual element was 1. This matches the elements in the original array. So, we identify whether we are returning the correct array. 
In the return statement, we can see that we are returning `arr` and not `newArray`. So, we change the line to `return newArray;`. After making this change, we can see that all the tests pass.

```
vishvansivanandan@Vishvans-MacBook-Pro:~/$ java -cp .:./lib/hamcrest-core-1.3.jar:./lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
.
Time: 0.014

OK (1 test)
```

The complete code is shown below

```
// Returns a *new* array with all the elements of the input array in reversed
// order
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    newArray[arr.length - i - 1] = arr[i];
  }
  return newArray;
}
```

## `grep`
The source for all the commands listed in this section is the man grep command.

The command `grep`, finds files that display a certain string pattern. Certain options can be enabled by using different "flags"

### Recursive

The `-r` flag can be used to search for patterns recursively i.e. within sub-directories of the specified directory.


```
vishvansivanandan@Vishvans-MacBook-Pro:~/cse15l/lr3$ grep -r "text" ./
./f10:text
./folder1/f3:text
./folder1/f5:text
./folder1/f4:text
```
> `f10` is a file in the current directory. `f3`, `f4`, `f5` are in the sub-directory folder1. All of these files contain the word text.


### Ignore

> The -i flag can be used to enable case-insensitive search in grep.

```
vishvansivanandan@Vishvans-MacBook-Pro:~/cse15l/lr3$ grep -i "text" ./*
./f1:Text
./f10:text
./f2:tExT
```

### Line Number
The -n flag prints the line number of the matched line for each file.

```
vishvansivanandan@Vishvans-MacBook-Pro:~/cse15l/lr3/folder1$ grep -n "text" ./*
./f3:1:text
./f4:2:text
./f5:3:text
```

> `f3` contains the word `text` on line 1, `f4` contains the word on line 2 and `f5` contains the word on line 3.

### Context

The `-C` flag followed by a positive integer n, prints n number of lines before and after the matched line.

```
vishvansivanandan@Vishvans-MacBook-Pro:~/cse15l/lr3/folder1$ grep -C 2 "context" ./f6
l2
l3
context
l4
l5
```

> 2 lines before and after the matched line are printed







