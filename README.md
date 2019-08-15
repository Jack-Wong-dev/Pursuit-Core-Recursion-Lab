# Recursion Exercises

- ### Sum of all from 1 to n

Write a function that takes in a number as input and recursively finds the sum of all numbers up to and including that number.

```js
input: 6
output: 21

//21 = 6 + 5 + 4 + 3 + 2 + 1
```
```swift
  func sumOfAllFromOneToN(_ n: Int)->Int{
      //base case
      if n <= 1{
          return n
      }
      //recursive case
      return n + sumOfAllFromOneToN(n-1)

  }
```

- ### Multiply array

Write a function called `multArr` that takes in an array of numbers as an argument and recursively multiplies together all of the values in the array.

```js
multArr([2, 3, 5]); // returns 30
multArr([5, 5, 1, 2]); //returns 50
```
```swift
  func multArr(_ arr: [Int])-> Int{
      var array = arr
      //base case: if the array has only one element
      if arr.count == 1{
          return arr[0]
      }else{
          return array.popLast()! * multArr(array)
      }
  }
  print(multArr([2,3,5]))
```

- ### Concatenate array

Write a function called `concatArr` that takes in an array of strings as an argument and recursively concatenates the strings together into a single string, with spaces between each original string.

```js
concatArr(['is', 'it', 'tomorrow']); // returns 'is it tomorrow'
concatArr(['or', 'just', 'the', 'end', 'of', 'time']); //returns 'or just the end of time'
```

```swift
  func concatArr(_ arr: [String]) -> String {
      //base case
      if arr.count == 1 { return arr[0] }
      //recursive call
      let firstElement = arr[0]
      let remainingElements = Array(arr[1...])
      return firstElement + " " + concatArr(remainingElements)
  }

  print(concatArr(["is", "it", "tomorrow"]))
```

- ### Sum evens

Write a function called `sumEvens` that takes in an array of numbers as an argument and recursively sums only the even numbers in the array.

```swift

func sumEvens(_ arr: [Int])->Int{
  //base case
  //If there's only one element in the array and the value is even
  if arr.count == 1 && arr[0] % 2 == 0{
      return arr[0]
  }
  //If there's only one element in the array and the value is odd
  else if arr.count == 1 && arr[0] % 2 == 1{
      return 0
  }
  //recursive call
  let firstElement = arr[0]
  let remainingElements = Array(arr[1...])

  //If first element is even
  if firstElement % 2 == 0{
      return firstElement + sumEvens(remainingElements)
  }else{
      return 0 + sumEvens(remainingElements)
  }
}

```

```js
sumEvens([2, 3, 5, 6]); // returns 8
sumEvens([10, 5, 1, 2, 12]); //returns 24
```

- ### Recursive range

Write a function called `range` which takes in two numbers (num1, num2) as arguments. The function should return an array of numbers between num1 and num2.

```js
range(2,10); // returns [2, 3, 4, 5, 6,7, 8, 9, 10]
range(17,20); // returns [17, 18, 19, 20]
```
```swift
  func range(_ num1: Int,_ num2: Int)->[Int]{
      //base case
      if num1 == num2{
          return [num1]
      }
      //recursive call
      return [num1] + range(num1+1, num2)
  }

  print(range(2,10)); // returns [2, 3, 4, 5, 6,7, 8, 9, 10]
  print(range(17,20)); // returns [17, 18, 19, 20]
```


- ### Triple Step

A child is running up a staircase with n steps and can hop either 1 step 2 steps or 3 steps at a time. Write a function called 'tripleStep', that takes in an argument `n` that represents the number of steps in the staircase, and returns a count of how many possible ways the child can run up the stairs.

```js
tripleStep(3); //returns 4
tripleStep(4); //returns 7
tripleStep(5); //returns 13
tripleStep(10); //returns 274
```
```swift
  func tripleStep(_ n: Int)->Int{
    //base case.  n == 0 is required in order to avoid calling tripleStep(0-1)
      if n == 1 || n == 0 {
          return 1
      } else if n == 2 {
          return 2
      } else {
          return tripleStep(n-3) + tripleStep(n-2) + tripleStep(n-1)
      }
  }
```

Source: Cracking the Coding Interview

- ### Coin Combos

Given an infinite number of quarters, dimes, nickels, and pennies, write code to calculate the number of possible ways of giving exact change for `n` cents.

In other words, write a function called `coinCombos` that takes in one argument: `n`, which represents the total amount of money (in cents) that you need to make change for. Your function should return the amount of possible combinations you can make to return that exact amount of change.

For example:
```js
coinCombos(5); //returns 2
coinCombos(10); //returns 4
coinCombos(25); //returns 13
coinCombos(60); //returns 73
```

```swift
func coinCombos(_ arr:[Int],_ size: Int,_ n: Int)->Int{
    //base case:  There's no change.
    if n == 0{
        return 1
    }
    //no solution exists.  can use a guard statement instead
    if n < 0{
        return 0
    }
    // No coins and n > 0, no solution exists
    if (size <= 0 && n >= 1){
        return 0
    }
    //recursive call
    return coinCombos( arr, size - 1, n ) + coinCombos( arr, size, n - arr[size - 1] )
}

var coins = [1,5,10,25]
print(coinCombos(coins, coins.count,10))
```

Source: CTCI

# Resources
- [JavaScript Recursion Exercises](http://www.w3resource.com/javascript-exercises/javascript-recursion-functions-exercises.php)
- [Swift Recursion Exercises](https://www.weheartswift.com/recursion/)
