# week 5 lab report
## Part 1 - Bugs
One bug from week 4's lab: Array Methods
* A failure-inducing input
```
  @Test 
  public void testReverseInPlace() {
    int[] input1 = { 1, 2, 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3, 2, 1 }, input1);
  }
```
* An input that doesn't induce a failure
```
@Test 
  public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
  }
```
