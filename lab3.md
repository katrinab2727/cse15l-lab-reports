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

```
$ grep -r "high increase" technical/biomed
technical/biomed/1477-7827-1-13.txt:          from PT4 showed a high increase when compared to the PT4
```
The `grep -r` command reads all of the files recursively in the given path for the specified string. The `plos` and `biomed` directory files were searched for the specified string.

Source: https://man7.org/linux/man-pages/man1/grep.1.html

### `grep -i`
```
$ grep -i "Base Pair" technical/plos/journal.pbio.0020190.txt
        sequence, which is a specific series of eight base pairs in the DNA of the bacterial
        chromosomes, on the order of one or two thousand base pairs of DNA (or less—their length is
```

```
$ grep -i "hIgH inCreAse" technical/biomed/1477-7827-1-13.txt
          from PT4 showed a high increase when compared to the PT4
```
Combo: `grep -ri`
```
$ grep -ri "BASE PAIR" technical/plos
technical/plos/journal.pbio.0020190.txt:        sequence, which is a specific series of eight base pairs in the DNA of the bacterial
technical/plos/journal.pbio.0020190.txt:        chromosomes, on the order of one or two thousand base pairs of DNA (or less—their length is
technical/plos/journal.pbio.0020223.txt:        Watson-Crick base pairing, the proximity of the synthetic reactive groups elevates their
```
The `grep -i` command searches for a string with case insensitvity in the given file. You can also use `grep -ri` to search recursively with case insentivity, which is helpful since the string can be capitalized at the start of a sentence.

Source: https://www.geeksforgeeks.org/grep-command-in-unixlinux/

### `grep -v`
```
$ grep -v "the" technical/plos/pmed.0020191.txt





        The excellent article by Jordan Paradise, Lori B. Andrews, and colleagues, “Ethics.
        biohistorical research; instead, it points out that such investigations are currently
        taking place without guidelines—ethical, scientific, moral, or religious. The question
        remains: if such guidelines were to be established, what individuals, institutions,
        governments, medical examiners, family members, or intrepid biographers are to be given
```
$ grep -v "a" technical/biomed/1471-2490-3-2.txt






        Methods
        to the lower border of symphysis pubis using 5 mm


        Results


        Discussion
        on this subject.


        Conclusion
        diverticulitis.


        Competing interests


        Authors' contribution
        writing
```
The `grep -v` command is an inverted version of `grep` since it only returns non-matching lines. It searches the given file and excludes any successful matches.

Source: https://www.redhat.com/sysadmin/how-to-use-grep











