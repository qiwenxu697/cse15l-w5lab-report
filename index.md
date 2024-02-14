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

`-name pattern` searches for files and directories with a pattern and lists them out. `find ./technical -name "*.txt"` will search for files or directories with names ending in ".txt" in the `./technical` directory.

<img width="486" alt="截屏2024-02-13 下午9 42 55" src="https://github.com/qiwenxu697/cse15l-w5lab-report/assets/147675962/9b025875-8cce-4157-a2c9-d33da354202f">


* `find ./technical -name biomed`

`find ./technical -name biomed` will search for files or directories with the name "biomed" within the `./technical` directory.

<img width="487" alt="截屏2024-02-13 下午10 18 16" src="https://github.com/qiwenxu697/cse15l-w5lab-report/assets/147675962/8f33ce0b-6e0d-428f-971a-c556fd8a45ab">


* `find ./technical -type f`

`-type type` searches for a specific file type and lists them out. `-type f` searches for regular files.

<img width="487" alt="截屏2024-02-13 下午10 31 04" src="https://github.com/qiwenxu697/cse15l-w5lab-report/assets/147675962/2901837c-e955-45af-8353-310e2002b5f6">


* `find ./technical -type d`

`-type d` searches for directories.

<img width="482" alt="截屏2024-02-13 下午10 41 07" src="https://github.com/qiwenxu697/cse15l-w5lab-report/assets/147675962/85469c15-c567-4d64-9300-669415bca5c4">

* `find ./technical -size +20k`

`find ./technical -size n` searches for files with size n and list them out. The size are in bytes (c), kilobytes (k), megabytes (M), gigabytes (G). `find ./technical -size +20k` will search files with size 20 kilobytes. 

<img width="486" alt="截屏2024-02-13 下午10 39 33" src="https://github.com/qiwenxu697/cse15l-w5lab-report/assets/147675962/632fd5ad-080c-4925-8009-d392afbc93e9">

* `find ./technical -size +70k`

`find ./technical -size +20k` will search files with size 70 kilobytes. 

<img width="492" alt="截屏2024-02-13 下午10 46 12" src="https://github.com/qiwenxu697/cse15l-w5lab-report/assets/147675962/c20b0d1c-2d6e-4582-8524-fecb719fb4da">

* `find ./technical -mtime -7`

`find ./technical -mtime n` searches for files modified time. `-mtime n` will search files that is modified exactly n days ago.`-mtime -n` will search files that is modified more than n days ago. `-mtime +n` will search files that is modified less than n days ago. `find ./technical -mtime -7` will search files that is modified more than 7 days ago.

<img width="481" alt="截屏2024-02-13 下午11 09 02" src="https://github.com/qiwenxu697/cse15l-w5lab-report/assets/147675962/2faf2145-9cc0-4836-a1c7-9c4f9d73f124">


* `find ./technical -mtime +10`

`find ./technical -mtime +10` will search files that is modified less than 10 days ago.

<img width="486" alt="截屏2024-02-13 下午11 18 08" src="https://github.com/qiwenxu697/cse15l-w5lab-report/assets/147675962/76e1f83e-2578-4ea3-870f-c5bee82b327c">

Resource:
https://www.computerhope.com/unix/ufind.htm
ChatGPT:

Prompt: what are some find command-line options

Chatgpt output: 

The find command in Unix-like operating systems is a powerful tool for searching and locating files and directories. Here are some commonly used options for the find command:

Search by Name:

-name pattern: Search for files and directories with a specific name pattern.
-iname pattern: Case-insensitive version of -name.
Example:

bash
Copy code
find /path/to/search -name "*.txt"
Search by Type:

-type type: Search for a specific file type (e.g., f for regular files, d for directories).
Example:

bash
Copy code
find /path/to/search -type f
Search by Size:

-size n[cwbkMG]: Search for files based on size. You can specify the size in bytes (c), kilobytes (k), megabytes (M), gigabytes (G), etc.
Example:

bash
Copy code
find /path/to/search -size +10M
Search by Modification Time:

-mtime n: Search for files modified exactly n days ago.
-mtime -n: Search for files modified more than n days ago.
-mtime +n: Search for files modified less than n days ago.
Example:

bash
Copy code
find /path/to/search -mtime -7
Search by Permissions:

-perm mode: Search for files with specific permissions.
Example:

bash
Copy code
find /path/to/search -perm 644
Execute a Command:

-exec command {} \;: Execute a command on each found item.
Example:

bash
Copy code
find /path/to/search -name "*.log" -exec rm {} \;
Search for Empty Files or Directories:

-empty: Search for empty files and directories.
Example:

bash
Copy code
find /path/to/search -type d -empty
Combining Conditions:

-and, -or, -not: Combine multiple search conditions.
Example:

bash
Copy code
find /path/to/search -name "*.txt" -type f -mtime -7
These are just a few examples of the many options available with the find command. You can refer to the man page (man find) for more detailed information and options.

Change the `/path/to/search` to the directory I use for my examples. Change parameter to the parameter I use for my examples. 
