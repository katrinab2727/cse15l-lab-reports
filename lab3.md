# Lab 3 Report

## Part 1 - Bugs

Buggy Program: `reverseInPlace`

```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
}
```
<br>

JUnit test that fails:
```
public void testReverseInPlace() {
    int[] input1 = {1, 2, 3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3, 2, 1}, input1);
}
```
The code inputs the `int` array of `{1, 2, 3}` that is failure inducing for the `reverseInPlace` method. The expexted output would be an array with values of `{3, 2, 1}`. However, the buggy program returned an output of `{3, 2, 3}`.
<br>

JUnit test that passes:
```
public void testReverseInPlace() {
    int[] input1 = {3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3}, input1);
}
```


