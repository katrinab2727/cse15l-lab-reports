# Lab 3 Report

## Part 1 - Bugs

Buggy Program:

```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
}
```
JUnit test that fails:
```
@Test 
public void testReverseInPlace() {
    int[] input1 = {1, 2, 3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3, 2, 1}, input1);
}
```
The code inputs the `int` array of `{1, 2, 3}` that is failure inducing for the `reverseInPlace` method.
