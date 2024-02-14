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
  The command "type" lists all files of the file's type.  This is useful when the user wants to find files
  of a specific type like txt, directories, or symbolic links.
  Source: https://tecadmin.net/linux-find-command-with-examples/
  
* -size
  ```
  $ find technical -size -1k
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
  $ find technical -size +100k
  technical/911report/chapter-1.txt
  technical/911report/chapter-12.txt
  technical/911report/chapter-13.2.txt
  technical/911report/chapter-13.3.txt
  technical/911report/chapter-13.4.txt
  technical/911report/chapter-13.5.txt
  technical/911report/chapter-3.txt
  technical/911report/chapter-6.txt
  technical/911report/chapter-7.txt
  technical/911report/chapter-9.txt
  technical/biomed/1471-2105-3-2.txt
  techincal/government/About_LSC/comission_report.txt
  techincal/government/About_LSC/State_Planning_Report.txt
  technical/government/Env_Prot_Agen/bill.txt
  technical/government/Env_Prot_Agen/ctm4-10.txt
  technical/government/Env_Prot_Agen/multi102902.txt
  technical/government/Env_Prot_Agen/tech_adden.txt
  ```
  The size command lists all files according to the size provided in the argument.  This is useful to
  know which files are a certain size or if they are above or below a size.
  Source: https://tecadmin.net/linux-find-command-with-examples/ 

* -mtime
  ```
  $ find technical -mtime -1
  ```

  ```
  $find technical -mtime -6
  technical/plos/pmed.0020212.txt
  technical/plos/pmed.0020216.txt
  technical/plos/pmed.0020226.txt
  technical/plos/pmed.0020231.txt
  technical/plos/pmed.0020232.txt
  technical/plos/pmed.0020235.txt
  technical/plos/pmed.0020236.txt
  technical/plos/pmed.0020237.txt
  technical/plos/pmed.0020238.txt
  technical/plos/pmed.0020239.txt
  technical/plos/pmed.0020242.txt
  technical/plos/pmed.0020246.txt
  technical/plos/pmed.0020247.txt
  technical/plos/pmed.0020249.txt
  ```
  The mtime command lists the files that were modified in the past certain amount of days.  This
  is useful to know which files were changed on certain days.
  Source: https://tecadmin.net/linux-find-command-with-examples/ 

*-user
```
$ find technical/911report -user sinji
.
./chapter-1.txt
./chapter-10.txt
./chapter-11.txt
./chapter-12.txt
./chapter-13.1.txt
./chapter-13.2.txt
./chapter-13.3.txt
./chapter-13.4.txt
./chapter-13.5.txt
./chapter-2.txt
./chapter-3.txt
./chapter-5.txt
./chapter-6.txt
./chapter-7.txt
./chapter-8.txt
./chapter-9.txt
./preface.txt
```

```
$ find government/Post_Rate_Comm -user sinji
government/Post_Rate_Comm
government/Post_Rate_Comm/Cohenetal_comparison.txt
government/Post_Rate_Comm/Cohenetal_Cost_Function.txt
government/Post_Rate_Comm/Cohenetal_CreamSkimming.txt
government/Post_Rate_Comm/Cohenetal_DeliveryCost.txt
government/Post_Rate_Comm/Cohenetal_RuralDelivery.txt
government/Post_Rate_Comm/Cohenetal_Scale.txt
government/Post_Rate_Comm/Gleiman_EMASpeech.txt
government/Post_Rate_Comm/Gleiman_gca2000.txt
government/Post_Rate_Comm/Mitchell_6-17-Mit.txt
government/Post_Rate_Comm/Mitchell_RMVancouver.txt
government/Post_Rate_Comm/Mitchell_spyros-first-class.txt
government/Post_Rate_Comm/Redacted_Study.txt
government/Post_Rate_Comm/ReportToCongress2002WEB.txt
government/Post_Rate_Comm/WolakSpeech_usps.txt
```

The command user list all the files in the directory that are owned by the specified user.
This is important when working in a group setting with multiple people working on a project
and can search files based on other group members.
Source: https://tecadmin.net/linux-find-command-with-examples/ 
