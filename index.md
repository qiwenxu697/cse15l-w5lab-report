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
The `reversed` method creates a `newArray`. The length of `newArray` is same with `arr`. Java will assign the default value 0 to each element of the int array. The for loop assigns each element in `arr` to be the element in `newArray` from the backward direction. It makes the elements in `arr` to be the default value 0. 

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
In order to fix it, we need to assign each element in `newArray` to be the element in `arr` from the backward direction. Last, we return `newArray` which is the reversed version of `arr`.
## Part 2 - Researching Commands: find
* `find ./technical -name "*.txt"`

`-name` searches for files and directories with a pattern. `find ./technical -name "*.txt"` will search for files or directories with names ending in ".txt" in the `./technical` directory.

<img width="486" alt="截屏2024-02-13 下午9 42 55" src="https://github.com/qiwenxu697/cse15l-w5lab-report/assets/147675962/9b025875-8cce-4157-a2c9-d33da354202f">

* `find ./technical -name biomed`

`find ./technical -name biomed` will search for files or directories with the name "biomed" within the `./technical` directory.

<img width="487" alt="截屏2024-02-13 下午10 18 16" src="https://github.com/qiwenxu697/cse15l-w5lab-report/assets/147675962/8f33ce0b-6e0d-428f-971a-c556fd8a45ab">

* `find ./technical -type f`

<img width="487" alt="截屏2024-02-13 下午10 31 04" src="https://github.com/qiwenxu697/cse15l-w5lab-report/assets/147675962/2901837c-e955-45af-8353-310e2002b5f6">

* `find ./technical -type d`


<img width="482" alt="截屏2024-02-13 下午10 41 07" src="https://github.com/qiwenxu697/cse15l-w5lab-report/assets/147675962/85469c15-c567-4d64-9300-669415bca5c4">

* `find ./technical -size +20k`

<img width="486" alt="截屏2024-02-13 下午10 39 33" src="https://github.com/qiwenxu697/cse15l-w5lab-report/assets/147675962/632fd5ad-080c-4925-8009-d392afbc93e9">

* `find ./technical -size +70k`

<img width="492" alt="截屏2024-02-13 下午10 46 12" src="https://github.com/qiwenxu697/cse15l-w5lab-report/assets/147675962/c20b0d1c-2d6e-4582-8524-fecb719fb4da">

