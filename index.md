# week 5 lab report
## Part 1 - Bugs
One bug from week 4's lab: Array Methods
* A failure-inducing input
```
  @Test
  public void testReversed() {
    int[] input1 = { 1 };
    assertArrayEquals(new int[]{ 1 }, ArrayExamples.reversed(input1));
  }
```
* An input that doesn't induce a failure
```
  @Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```
* Symptom
The output of an int array input will be an array filled with 0 with same length of input. 
![Image](截屏2024-02-13 上午10.40.39.png)

![Image](截屏2024-02-13 上午10.41.46.png)

*Bug
Before fixing
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
After fixing 
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```

