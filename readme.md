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
1. Why the test failed at first?
1. Why you corrected the test that way?
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


- ANSWERS

1. What is the knowledge point of the test? Where is the official document to the knowledge point?

* 1. BooleanOperatorsTest

    * should_perform_logical_boolean_operations - To know what are the boolean results from the given actual value.
    * should_do_bitwise_and_boolean_operation - To know what are the result when the actual values are BITWISE AND.
    * should_do_bitwise_or_boolean_operation - To know what are the result when the actual values are BITWISE OR.
    * should_do_bitwise_not_operation - To know what are the result when the actual values are BITWISE NOT.

* 1. CharTypeTest

    * should_describe_escaped_chars - To know what are the escaped character values.

* 1. FloatingTypeTest

    * should_not_get_rounded_result_if_convert_floating_number_to_integer - To know how to get the NOT ROUNDED value when the given values are floating numbers.
    * should_judge_special_double_cases - To know how to use the existing functions, to get the expected result.
    * should_not_round_number_when_convert_to_integer - To know how to get the value when converting float values to integer values.
    * should_round_number - To know how to get the rounded number when converting float values to integer values.

* 1. IntegerTypeTest

    * should_get_range_of_primitive_int_type - To know how to get the range of primitive integer values.
    * should_get_range_of_primitive_short_type - To know how to get the range of primitive short values.
    * should_get_range_of_primitive_long_type - To know how to get the range of primitive long values.
    * should_get_range_of_primitive_byte_type - To know how to get the range of primitive byte values.
    * should_overflow_silently - To know how to pass the test when the values are greater than the MAX values depending on what data type.
    * should_underflow_silently - To know how to pass the test when the values are greater than the MIN values depending on what data type.
    * should_throw_exception_when_overflow - To know how to handle exception when the values are greater than the MAX values depending on what data type.
    * just_prevent_lazy_implementation - To know what are the result depending on what method is used.
    * should_take_care_of_number_type_when_doing_calculation - To know how to handle the calculation depending on what data type is used.
    * should_truncate_number_when_casting - To modify the actual values depending on what data type is used for expected values.
    * should_increment - To know how to use pre-increment values.
    * should_increment_2 - To know how to use post-increment values.

1. Why the test failed at first?

* 1. BooleanOperatorsTest

    * All of the test cases does have actual values, but expected values are 0 or null.

* 1. CharTypeTest

    * The expected values does not have any escaped character values.

* 1. FloatingTypeTest

    * should_not_get_rounded_result_if_convert_floating_number_to_integer - No expected values that should not round number when converting the float values to integer.
    * should_judge_special_double_cases - There are no handling of what should be the result in the functions that are being used.
    * should_not_round_number_when_convert_to_integer - No expected values that should not round number when converting the float values to integer.
    * should_round_number - No expected values that should get the rounded number when converting the float values to integer.

* 1. IntegerTypeTest

    * should_get_range_of_primitive_int_type - The expected values does not get the range of primitive integer type values.
    * should_get_range_of_primitive_short_type - The expected values does not get the range of primitive short type values.
    * should_get_range_of_primitive_long_type - The expected values does not get the range of primitive long type values.
    * should_get_range_of_primitive_byte_type - The expected values does not get the range of primitive byte type values.
    * should_overflow_silently - The expected values does not match the actual overflow values.
    * should_underflow_silently - The expected values does not match the actual underflow values.
    * should_throw_exception_when_overflow - No handling of exception on the function that is being used.
    * just_prevent_lazy_implementation - The function does not return any values.
    * should_take_care_of_number_type_when_doing_calculation - No expected values that should depend on what data type is being used on actual values.
    * should_truncate_number_when_casting - No expected values that should be equal to modified values.
    * should_increment - No expected values that should pre-increment.
    * should_increment_2 - No expected values that should post-increment.

1. Why you corrected the test that way?

* 1. BooleanOperatorsTest

    * Just modified the expected values depending on what are the values from the actual.

* 1. CharTypeTest

    * Searched for what are the proper values for the escaped characters, and modified the values from the expected variables.

* 1. FloatingTypeTest

    * should_not_get_rounded_result_if_convert_floating_number_to_integer - The result should not get the rounded number. Therefore, converting floating numbers to integer does not get the decimal point values.
    * should_judge_special_double_cases - Modified the functions that are being used on this test case, to create some conditions that should handle depending on what is the actual result.
    * should_not_round_number_when_convert_to_integer - The result should not get the rounded number. Therefore, converting floating numbers to integer does not get the decimal point values.
    * should_round_number - Used Math.round() method to get the rounded number values.

* 1. IntegerTypeTest

    * should_get_range_of_primitive_int_type - The result should be the MAX and MIN values of integer.
    * should_get_range_of_primitive_short_type - The result should be the MAX and MIN values of short.
    * should_get_range_of_primitive_long_type - The result should be the MAX and MIN values of long.
    * should_get_range_of_primitive_byte_type - The result should be the MAX and MIN values of byte.
    * should_overflow_silently - The result should be the values depending on what data type, are overflow values.
    * should_underflow_silently - The result should be the values depending on what data type, are underflow values.
    * should_throw_exception_when_overflow - No handling of exception on the function that is being used.
    * just_prevent_lazy_implementation - Modifying the function that is being used, to add the two integer numbers.
    * should_take_care_of_number_type_when_doing_calculation - Modified the expected values that should get the calculated result.
    * should_truncate_number_when_casting - Modified the expected values to get the smaller integer.
    * should_increment - Modified the expected value from the actual value that is being pre-incremented.
    * should_increment_2 - Modified the expected value from the actual value that is being post-incremented.

1. Do you have further questions on this knowledge point?

    * None.