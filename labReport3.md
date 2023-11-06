## Part 1
```
 @Test
  public void meanTest() {
    double[] input1 = {3,3,3,3,2,2};
    double output = ArrayExamples.averageWithoutLowest(input1);
    assertEquals(3.0, output, 0.01);
  }
```

```
@Test
public void workingTest() {
    double[] input1 = {1,3,4,2};
    double output = ArrayExamples.averageWithoutLowest(input1);
    assertEquals(3.0, output, 0.01);
  }
```
