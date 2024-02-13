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
