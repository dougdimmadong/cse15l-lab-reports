# Part 1
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
![Image](symptom.png)

## Before
```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
```

## After
```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    int counter = 0;
    for(double num: arr) {
      if(num != lowest) { 
        sum += num; 
        counter++;
      }
    }
    return sum / counter;
  }
```
Adding a counter for how many values aren't the lowest number in the array fixes the bug since it will correctly calculate the average of the numbers when there are multiple copies of the smallest number. Before,
the code would calculate the average by dividing the total sum of the numbers in the array by `arr.length - 1`, which only work if there is only one copy of the smallest number in the array. If there are multiple, this code will only account for the removal of one of them. The new code keeps track of the number of numbers that aren't the smallest and then calculate the average by dividing that by the amount of numbers actually summed. This way, the code correctly averages the numbers minus the smallest.
