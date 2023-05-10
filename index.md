#Lab 3

## Part 1
For the portion that I wrote, I used the methods `getPath` and `equals` to check if the url gives the instruction to add text. I also used `split` to separate 
what comes after the equals sign. This seems to only work for `strings`.

<img width="490" alt="Screen Shot 2023-04-24 at 10 56 38 PM" src="https://user-images.githubusercontent.com/130017007/234187027-4a5194de-a5af-464b-aa72-fdefd6f04491.png">

>public class ArrayExamples{
> static void reverseInPlace(int[] arr){
>   for (int i = 0; i< arr.length; i += 1) {
>     arr[i] = arr[arr.length; i += 1] {
>   }
>}
>static int[] reversed(int[] arr) {
> int[] newArray = new int[arr.length];
> for (int i = 0; i < arr.length; i += 1)
>   newArray[i] = arr[arr.length - i - 1];
>   }
>   return newArray;
>}

## Part 2
Failure inducing code:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
Input and output:

<img width="764" alt="Screen Shot 2023-04-24 at 11 01 29 PM" src="https://user-images.githubusercontent.com/130017007/234188393-537ef78d-1635-44e8-8509-4a43d58ba772.png">

We can observe that by running 3 tests, one of them failed when we expected 3 but it returned 0 instead. This is because one of the nnumbers was duplicated instead of reversed 
which yields a symptom. An empty array `{ }` and an array with only one input also passed `{1}`, however `{3,0,3}` did not.


>public class ArrayExamples{
>static void main reverseInPlace(int[] arr){
> for(int i=0; i < arr.length; i+=1){
>     arr[i] = arr[arr.length - i - 1];
>   }
>}
>
>static int[] reversed(int[] arr){
> int[] newArray = new int[arr.length];
> for(int i=0; i < arr.length; i+= 1){
> newArray[i] = arr[arr.length - i - 1];
> }
> return newArray;
> }

The problem was that the numbers that were being stored were being stored in the wrong array and the wrong array was being returned. The symptom was that instead of reversing the items in place, the item in the second spot was repeated over the rest of the array. This was because the program was attempting to rewrite an array at the same time that it was referencing it. To fix this problem, it is important to create a new temporary array that we can populate with the contents of the the reference array. If we must return the original array, we can repopulate the original array with the items inside the temporary array.

## Part 3
In the last 2 weeks, I learned how to start using localhost as well as modifying it to run different programs. I installed Github Desktop as well as JUnit, running it for the first time.
I learned how to commit and push programs in GitHub Desktop as well as other simpler things such as forking repositories. I learned the difference between symptoms and bugs as well as a few new commands.
