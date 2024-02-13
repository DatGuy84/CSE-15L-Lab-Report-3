# Lab Report 3 - Bugs and Commands

## Bugs


Bug Before Fix:
```
static void reverseInPLace(int[] arr){
  for(int i = 0; i < arr.length; i+=1){
    arr[i] = arr[arr.length - i - 1];
  }
}
```

Failure Inducing Input:
```
@Test
public void testReverseInPlace(){
  int[] input1 = {1,2,3,4};
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{4,3,2,1}, input1);
}
```

Non-failure Inducing Input:
```
@Test
public void testReverseInPlace(){
  int[] input1 = {1,2,3,4};
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{4,3,3,4}, input1);
}
```
Output of running the tests:
![Image](https://github.com/DatGuy84/CSE-15L-Lab-Report-3/blob/main/output%20of%20tests%20pre-fix.png?raw=true)

Bug After Fix:
```
static void reverseInPlace(int[] arr){
  int[] temp = new int[arr.length];
  for(int i = 0; i < arr.length; i++){
    temp = arr[arr.length - i - 1];
  }
  for(int y = 0; y < arr.length; y++){
    arr[y] = temp[y];
  }
}
```

In order to fix the bug, a new array called temp was created and takes in the the values of arr starting
from the end to the beginning of arr.  Once the reverse values of arr are stored in temp, arr's values
are changed to match temp.  This fixes the bug since the original array would overwrite the beginning values
instead of creating a reversed array.

## Researching Commands - Find

4 Different Find Commands:

* -type
  ```
  $ find technical -type d
  technical
  technical/911report
  technical/biomed
  technical/government
  technical/government/About_LSC
  technical/government/Alcohol_Problems
  technical/government/Env_Prot_Agen
  technical/government/Gen_Account_Office
  technical/government/Media
  technical/government/Post_Rate_Comm
  technical/plos
  ```
  ```
  $ find technical/911report -type f
  technical/911report/chapter-1.txt
  technical/911report/chapter-10.txt
  technical/911report/chapter-11.txt
  technical/911report/chapter-12.txt
  technical/911report/chapter-13.1.txt
  technical/911report/chapter-13.2.txt
  technical/911report/chapter-13.3.txt
  technical/911report/chapter-13.4.txt
  technical/911report/chapter-13.5.txt
  technical/911report/chapter-2.txt
  technical/911report/chapter-3.txt
  technical/911report/chapter-5.txt
  technical/911report/chapter-6.txt
  technical/911report/chapter-7.txt
  technical/911report/chapter-8.txt
  technical/911report/chapter-9.txt
  technical/911report/preface.txt
  ```
*
