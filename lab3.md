# Lab 3 Report

## Part 1 - Bugs

### **Buggy Program: `reverseInPlace`**

```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
}
```


### **JUnit test that fails:**
```
public void testReverseInPlace() {
    int[] input1 = {1, 2, 3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3, 2, 1}, input1);
}
```
The code inputs the `int` array of `{1, 2, 3}` that is failure inducing for the `reverseInPlace` method.

<br>

### **JUnit test that passes:**
```
public void testReverseInPlace() {
    int[] input1 = {3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3}, input1);
}
```
The input of an `int` array that is `{3}` does not induce a failure.

### **Symptoms:**
<br>
<img width="728" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/731c6459-19e5-4d06-8d0b-ba5020912df1">
<br>
In the image above, the failure inducing input, `{1, 2, 3}` was put through the JUnit test. The expexted output would be an array with values of `{3, 2, 1}`. However, the buggy program returned an output of `{3, 2, 3}`. They differed at the 2nd index of the array. This shows how the method did not reverse the array correctly. It starts out correct, but the array differs at certain point.

<br>
<br>

<img width="667" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/a44b157e-b971-45e0-9bb8-39c39a1a5091">

In the image above, the nonfailure inducing input passed. The input was an array of `{3}`, so its length was only one. Since the method passes, it shows that the method starts off correct in the beginning, but it starts to have bugs with longer arrays.

### **Fixing the bug:**

**Code before:**
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
}
```

**Code after:**
```
static void reverseInPlace(int[] arr) {
    int[] copy = new int[arr.length];

    for(int i = 0; i < arr.length; i++){
      copy[i] = arr[i];
    }

    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = copy[arr.length - i - 1];
    }
}
```

The code is fixed because a copy array of the original one was used when creating the reversed array to make sure the correct values are retrieved for each index. The code had a bug previously since it was overwritting values in the beginning indices before they were correctly put in the end of the array. This is why in the test case, the method returned `{3, 2, 3}` instead of `{3, 2, 1}`. The original 0 index with the value of `1` was replaced with `3`. When the array tried to retrieve the first index to get the value of `1`, it was already overwritten with `3`. By instead retriving the values with a copy of the original array, no values are overwritten and the method now works correctly.

## Part 2 - Researching Commands: `grep`
### `grep -r`
```
$ grep -r "base pair" technical/plos
technical/plos/journal.pbio.0020190.txt:        sequence, which is a specific series of eight base pairs in the DNA of the bacterial
technical/plos/journal.pbio.0020190.txt:        chromosomes, on the order of one or two thousand base pairs of DNA (or less—their length is
technical/plos/journal.pbio.0020223.txt:        Watson-Crick base pairing, the proximity of the synthetic reactive groups elevates their
```






