# Overview

This repository is a part of the Java language training plan. Please read the following guidelines before start.

# Getting Start

## Basic Principals

Each repository contains a gradle java project with a number of unit tests. The initial state of all unit tests are *FAILED*. So the aim is to correct the failed test. Please follow the following steps to get the best experience:

* Read the test code and try to understand what it says.
* Trying to fix the test **WITHOUT RUNNING**. This is very important. Because once you run the test, you may find the failure message of the test telling you the expected result. That means you may lose the chance to figure it out by yourself. Note that you should **ONLY** be able to modify code within the **TODO AREA**. The code outside the **TODO AREA** is **NOT** changable.
* Run the test to examine if the fix is correct.
* Answer the following 4 questions after the test is passed.

The 4 questions are:

1. What is the knowledge point of the test? Where is the offical document to the knowledge point?

BooleanOperator - To pass each test cases, where the two object should be equal.

CharTypeTest - To know what are the escaped characters to place in the variable.

FloatingTypeTest - To know how to modify some of the method to handle exceptions.

IntegerTypeTest - To know what are the MAX and MIN values of each number data types.

1. Why the test failed at first?

BooleanOperator - the test failed at first because the two objects are not equal, which should always return true.

CharTypeTest - The variables does not have values, and each value should be an escaped character.

FloatingTypeTest - Most of the test cases have final float value, and return in a different number data type. There are also some methods that only throws exception.

IntegerTypeTest - The actual variables are 0, which should be the MAX and MIN of each number data types.
1. Why you corrected the test that way?

BooleanOperator - To pass all the tests, two objects should always be equal. Therefore, the expected and actual values should be equal.

CharTypeTest - Since all the expected values should be an EscapedChars, the actual values should be also an escaped characters. Therefore, I searched what are the escaped characters, depending on what the variables are.

FloatingTypeTest - Some test cases have float given variable, and should be parsed to integer, to pass the test case. There are also some methods that should be modified to handle the exception occuring in some of the test cases.

IntegerTypeTest - Most actual values in test cases are the MAX and MIN values of each number data types. And other cases are using methods that should handle exceptions.
1. Do you have further questions on this knowledge point?

None.

## Example

Let's take a look at an example:

```java
@Test
void should_pass_by_value() {
  int value = 5;

  tryingToUpdateValue(value);

  // TODO: please modify the following code to pass the test
  // <--start
  final int expected = 0;
  // --end-->

  assertEquals(expected, value);
}
```

First, read the test. From the title and code we can know that the test what to examine the behavior when passing an argument. We are not sure what `tryingToUpdateValue` does, so we can jump into its implementation:

```java
private static void tryingToUpdateValue(int value) {
  value += 2;
}
```

Now we have got the full context of the test. The argument is passed by value so the integer will be copied when passing into `tryingToUpdateValue`. Thus the value from the caller site will not change.

Notice that the todo area is in the test method. So we can modify codes within the todo area to pass the test:

```java
  // TODO: please modify the following code to pass the test
  // <--start
  final int expected = 5;
  // --end-->
```

Please note that not all todo areas are located in test method. And some todo area may have further restrictions, for example:

```java
  // TODO: You should not write concrete number here. Please find a property or constant instead.
  // <!--start
  final int maximumSymbol = 0;
  final int minimumSymbol = 0;
  // --end-->
```

The hint indicates that we should not write concrete number here. So I should not write `3` or `0xffffffff`, but write symbol (e.g. `Integer.MAX_VALUE`).

## Running Test

You could run unit tests with the help of IntelliJ. But it is also possible to run unit test via command line: `./gradlew build`.

If you just want to build your code without running test. Please use `./gradlew build -x test
`
