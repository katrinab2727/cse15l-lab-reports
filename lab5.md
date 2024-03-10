# Lab 5 Report

## Putting it All Together

### Part 1 - Debugging Scenario
### EdStem Post

#### Bug in my grade.sh &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; #389
Anonymous &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;80 views

My grade.sh is not printing the correct number of tests and is failing correct output.

<img width="746" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/18353f37-f1f5-48c5-ada8-85963b137008">

This is my file and directory structure:  
```
- list-examples-grader
    - lib  
      - hamcrest-core-1.3.jar  
      - junit-4.13.2.jar  
    - grading area  
    - student-submission
    - grade.sh
    - TestListExamples.java`
```

Here is my code for `grade.sh` before fixing the bug:
```
CPATH='..:..lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

rm -rf student-submission
rm -rf grading-area

mkdir grading-area

git clone $1 student-submission
echo 'Finished cloning'

if [[ -f student-submission/ListExamples.java ]] 
then
    cp student-submission/ListExamples.java grading-area/
    cp TestListExamples.java grading-area/
    cp -r lib grading-area
    echo "File found"
else
    echo "File ListExamples.java not found!"
    exit 1
fi 

cd grading-area
javac -cp $CPATH *.java

if [ $? -ne 0 ] 
then
    echo "Compilation error!"
    exit 1
fi


echo "Program complied successfully"


java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > junit-output.txt

lastline=$(cat junit-output.txt | tail -n 2 | head -n 1)
tests=$(echo $lastline | awk -F'[, ]' '{print $3}')
failures=$(echo $lastline | awk -F'[, ]' '{print $6}')
successes=$((tests - failures))
score=$((successes/tests))

echo "You passed $successes out of $tests tests"
echo "Your score is $score %"
```

Here is my code for `TestListExamples.java` before fixing the bug
```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.Arrays;
import java.util.List;

class IsMoon implements StringChecker {
  public boolean checkString(String s) {
    return s.equalsIgnoreCase("moon");
  }
}

public class TestListExamples {

  @Test
  public void testFilter() {
    List<String> list = Arrays.asList("apple", "banana", "orange", "moon", "sun");

    StringChecker moonChecker = new IsMoon();

    List<String> filteredList = ListExamples.filter(list, moonChecker);
    
    assertEquals(1, filteredList.size());
    assertEquals(true, filteredList.contains("moon"));
  }
  
  @Test(timeout = 500)
  public void testMergeRightEnd() {
    List<String> left = Arrays.asList("a", "b", "c");
    List<String> right = Arrays.asList("a", "d");
    List<String> merged = ListExamples.merge(left, right);
    List<String> expected = Arrays.asList("a", "a", "b", "c", "d");
    assertEquals(expected, merged);
  }
}
```

The full command line (or lines) I ran to trigger the bug:

`bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected`

I believe a part of my `grade.sh` is not working properly with the tests. Thanks for the help!

Comment ···  

#### 1 Answer  
Katrina Bosler <span style="font-size:0.5">STAFF</span>  
3 hours ago  






