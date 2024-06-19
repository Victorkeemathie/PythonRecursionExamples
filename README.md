# PythonRecursionExamples
A comprehensive repository of Recursive algorithm examples written in Python, designed for learning and reference


# Challenging Recursion Problems

Hi, and welcome. In this repo, we will explore some challenging recursion problems. Recursion is a fundamental concept in Data Structures and Algorithms. I have written more about it on Hashnode [here](https://hashnode.com/).

## Problem 1: Capitalize Words Recursively  📝

The first problem involves writing a function that takes a list of words (strings) and returns a new list where each word from the original list is converted to uppercase. 
This is achieved recursively, processing one word at a time and building up the resulting list of capitalized words.

### Explanation

The code uses the `def` keyword to define a function named `capitalizeWords`. The function takes one parameter, `arr`, which is expected to be a list of strings.

1. The function checks if the length of `arr` is 0, which means the list is empty.
2. If the list is empty, the function returns the empty `result` list. This acts as the base case for the recursion, stopping further recursive calls when the input list is exhausted.
3. If the list is not empty, the function appends the uppercase version of the first word in the list to `result`.
4. The function then returns the `result` list concatenated with the result of a recursive call to `capitalizeWords` with the remainder of the list (excluding the first word).

### Code

```python
def capitalizeWords(arr):
    result = []
    if len(arr) == 0:
        return result
    result.append(arr[0].upper())
    return result + capitalizeWords(arr[1:])

words = ['i', 'am', 'learning', 'recursion']
print(capitalizeWords(words))  # Output: ['I', 'AM', 'LEARNING', 'RECURSION']
```


# Problem 2: Fibonacci Solution  🌀

The second problem involves writing a function to calculate Fibonacci numbers using recursion.

## Explanation

The `fib` function computes the Fibonacci number for a given `num` using a simple recursive approach.

1. **Base Case**: The function checks if `num` is less than 2. If `num` is less than 2, it returns `num`, which handles the base cases for Fibonacci (F(0) = 0, F(1) = 1).
2. **Changing State and Moving Toward Base Case**: If `num` is 2 or greater, it returns the sum of the previous two Fibonacci numbers (`fib(num - 1) + fib(num - 2)`), which moves the computation closer to the base case in subsequent recursive calls.
3. **Recursive Call**: The function calls itself recursively with `num - 1` and `num - 2`, effectively reducing `num` until it reaches the base case.

### Code:
```python
def fib(num):
    if (num < 2):
        return num
    return fib(num - 1) + fib(num - 2)



print(fib(4)) # 3
print(fib(10)) # 55
print(fib(28)) # 317811
print(fib(35)) # 9227465
```

# Problem 3: stringifyNumbers Solution

This problem involves writing a function that takes an object and recursively converts all the integer values to strings.

### Explanation

1. The function `stringifyNumbers` takes an object `obj` as input.
2. A new object `newObj` is created to store the converted values.
3. The function iterates over each key in `newObj`.
4. If the value of a key is an integer, it converts the value to a string.
5. If the value of a key is another dictionary, the function calls itself recursively to process that dictionary.
6. The function returns the modified `newObj`.

This solution satisfies the three laws of recursion:
- **Base Case**: If the object has no more keys to process, the function stops.
- **State Change**: The function processes each key-value pair and modifies the state by converting integers to strings or calling itself recursively for nested dictionaries.
- **Recursive Call**: The function calls itself recursively to handle nested dictionaries.

### Code:
```python
def stringifyNumbers(obj):
    newObj = obj
    for key in newObj:
        if type(newObj[key]) is int:
            newObj[key] = str(newObj[key])
        if type(newObj[key]) is dict:
            newObj[key] = stringifyNumbers(newObj[key])
    return newObj



obj = {
  "num": 1,
  "test": [],
  "data": {
    "val": 4,
    "info": {
      "isRight": True,
      "random": 66
    }
  }
}

print(stringifyNumbers(obj))

{'num': '1', 
 'test': [], 
 'data': {'val': '4', 
          'info': {'isRight': True, 'random': '66'}
          }
}
```


# Problem 4: Collect Strings Solution 🧩

The fourth problem involves writing a function that collects all the strings from a nested object structure into a single list.

## Explanation

The `collectStrings` function takes an object `obj` as input and returns a list containing all the strings found in `obj`, including those in nested dictionaries.

### Steps

1. **Base Case**: The function checks each key in `obj`.
2. **Changing State and Moving Toward Base Case**: If the value associated with a key is a string (`type(obj[key]) is str`), it appends the string to `resultArr`.
3. **Recursive Call**: If the value associated with a key is a nested dictionary, it recursively calls `collectStrings` on that nested dictionary to collect strings from it as well.

### Code:
```python
def collectStrings(obj):
    resultArr = []
    for key in obj:
        if type(obj[key]) is str:
            resultArr.append(obj[key])
        if type(obj[key]) is dict:
            resultArr = resultArr + collectStrings(obj[key])
    return resultArr



obj = {
  "stuff": 'foo',
  "data": {
    "val": {
      "thing": {
        "info": 'bar',
        "moreInfo": {
          "evenMoreInfo": {
            "weMadeIt": 'baz'
          }
        }
      }
    }
  }
}

print(collectStrings(obj)) # ['foo', 'bar', 'baz'])
```

# Problem 5: Nested Even Sum Solution 🔍

The fifth problem involves writing a function that sums up all even numbers in a nested object structure.

## Explanation

The `nestedEvenSum` function takes an object `obj` as input and returns the sum of all even numbers found in `obj`, including those in nested dictionaries.

### Steps

1. **Base Case**: The function checks each key in `obj`.
2. **Changing State and Moving Toward Base Case**: If the value associated with a key is an integer and even (`type(obj[key]) is int and obj[key] % 2 == 0`), it adds the integer to `sum`.
3. **Recursive Call**: If the value associated with a key is a nested dictionary, it recursively calls `nestedEvenSum` on that nested dictionary to sum even numbers from it as well.

### Code:
```python
def nestedEvenSum(obj, sum=0):
    for key in obj:
        if type(obj[key]) is dict:
            sum += nestedEvenSum(obj[key])
        elif type(obj[key]) is int and obj[key]%2==0:
            sum+=obj[key]
    return sum



obj1 = {
  "outer": 2,
  "obj": {
    "inner": 2,
    "otherObj": {
      "superInner": 2,
      "notANumber": True,
      "alsoNotANumber": "yup"
    }
  }
}

obj2 = {
  "a": 2,
  "b": {"b": 2, "bb": {"b": 3, "bb": {"b": 2}}},
  "c": {"c": {"c": 2}, "cc": 'ball', "ccc": 5},
  "d": 1,
  "e": {"e": {"e": 2}, "ee": 'car'}
}

print(nestedEvenSum(obj1)) # 6
print(nestedEvenSum(obj2)) # 10
```


# Problem 6: Flatten Solution 📏

The sixth problem involves writing a function that flattens a nested array structure into a single array.

## Explanation

The `flatten` function takes a nested list `arr` as input and returns a flattened version of the list where all nested lists are combined into a single list.

### Steps

1. **Base Case**: The function iterates through each item in `arr`.
2. **Changing State and Moving Toward Base Case**: If the item is a list (`type(item) is list`), it extends `resultArr` with the flattened version of the item.
3. **Recursive Call**: If the item is not a list, it appends the item directly to `resultArr`.
### Code:
```python
def flatten(arr):
    resultArr = []
    for custItem in arr:
        if type(custItem) is list:
            resultArr.extend(flatten(custItem))
        else: 
            resultArr.append(custItem)
    return resultArr 



print(flatten([1, 2, 3, [4, 5]])) # [1, 2, 3, 4, 5]
print(flatten([1, [2, [3, 4], [[5]]]])) # [1, 2, 3, 4, 5]
print(flatten([[1], [2], [3]])) # [1, 2, 3]
print(flatten([[[[1], [[[2]]], [[[[[[[3]]]]]]]]]])) # [1, 2, 3]
```

# Problem 7: Recursive Range Solution 🔢

The seventh problem involves writing a function that calculates the sum of all integers from 0 to `num` using recursion.

## Explanation

The `recursiveRange` function takes an integer `num` as input and returns the sum of all integers from 0 to `num`.

### Steps

1. **Base Case**: The function checks if `num` is less than or equal to 0.
2. **Changing State and Moving Toward Base Case**: If `num` is greater than 0, it adds `num` to the result of a recursive call to `recursiveRange` with `num - 1`.
3. **Recursive Call**: The function calls itself recursively with `num - 1` until `num` reaches 0.

### Code:
```python
def recursiveRange(num):
    if num <= 0:
        return 0
    return num + recursiveRange(num - 1)


print(recursiveRange(6))
```


# Problem 8: Product Of Array Solution 🌟

The eighth problem involves writing a function that calculates the product of all elements in an array using recursion.

## Explanation

The `productOfArray` function takes a list `arr` as input and returns the product of all elements in `arr`.

### Steps

1. **Base Case**: The function checks if the length of `arr` is 0.
2. **Changing State and Moving Toward Base Case**: If `arr` is not empty, it returns the product of the first element of `arr` and a recursive call to `productOfArray` with the rest of the elements (`arr[1:]`).
3. **Recursive Call**: The function calls itself recursively with a smaller list until it reaches the base case.

### Code:
```python
def productOfArray(arr):
    if len(arr) == 0:
        return 1
    return arr[0] * productOfArray(arr[1:])

print(productOfArray([1,2,3])) #6
print(productOfArray([1,2,3,10])) #60
```

# Problem 9: Is Palindrome Solution ✨

The ninth problem involves writing a function that checks if a given string is a palindrome using recursion.

## Explanation

The `isPalindrome` function takes a string `strng` as input and returns `True` if `strng` is a palindrome (reads the same forward and backward), otherwise returns `False`.

### Steps

1. **Base Case**: The function checks if the length of `strng` is 0 or 1.
2. **Changing State and Moving Toward Base Case**: If the first and last characters of `strng` are equal, it recursively calls `isPalindrome` with `strng[1:-1]` to check the substring excluding the first and last characters.
3. **Recursive Call**: The function calls itself recursively with a smaller substring until it reaches the base case.

### Code:
```python
def isPalindrome(strng):
    if len(strng) == 0:
        return True
    if strng[0] != strng[len(strng)-1]:
        return False
    return isPalindrome(strng[1:-1])

print(isPalindrome('awesome')) # false
print(isPalindrome('foobar')) # false
print(isPalindrome('tacocat')) # true
print(isPalindrome('amanaplanacanalpanama')) # true
print(isPalindrome('amanaplanacanalpandemonium')) # false
```

# Problem 10: Power Solution ⚡

The tenth problem involves writing a function that calculates the power of a base raised to an exponent using recursion.

## Explanation

The `power` function takes two integers, `base` and `exponent`, as input and returns `base` raised to the power of `exponent`.

### Steps

1. **Base Case**: The function checks if `exponent` is 0.
2. **Changing State and Moving Toward Base Case**: If `exponent` is greater than 0, it returns `base` multiplied by a recursive call to `power` with `base` and `exponent - 1`.
3. **Recursive Call**: The function calls itself recursively with a smaller `exponent` until it reaches the base case.

### Code:
```python
def power(base, exponent):
    if exponent == 0:
        return 1
    return base * power(base, exponent-1)

print(power(2,0)) # 1
print(power(2,2)) # 4
print(power(2,4)) # 16
```

# Problem 11: Capitalize First Solution 🅲

The eleventh problem involves writing a function that capitalizes the first letter of each string in an array using recursion.

## Explanation

The `capitalizeFirst` function takes a list `arr` of strings as input and returns a new list where the first letter of each string is capitalized.

### Steps

1. **Base Case**: The function checks if the length of `arr` is 0.
2. **Changing State and Moving Toward Base Case**: If `arr` is not empty, it appends a string with the first letter capitalized (`arr[0][0].upper() + arr[0][1:]`) to `result`.
3. **Recursive Call**: The function calls itself recursively with the rest of the elements (`arr[1:]`) until `arr` is empty.

### Code:
```python

def capitalizeFirst(arr):
    result = []
    if len(arr) == 0:
        return result
    result.append(arr[0][0].upper() + arr[0][1:])
    return result + capitalizeFirst(arr[1:]) 




print(capitalizeFirst(['car', 'taco', 'banana'])) # ['Car','Taco','Banana']
```

# Problem 12: Some Recursive Solution 🎯

The twelfth problem involves writing a function that checks if any element in an array satisfies a given condition using recursion.

## Explanation

The `someRecursive` function takes a list `arr` and a callback function `cb` as input. It returns `True` if any element in `arr` satisfies the condition specified by `cb`, otherwise returns `False`.

### Steps

1. **Base Case**: The function checks if the length of `arr` is 0.
2. **Changing State and Moving Toward Base Case**: If the first element of `arr` does not satisfy the condition specified by `cb` (`not(cb(arr[0]))`), it recursively calls `someRecursive` with the rest of the elements (`arr[1:]`).
3. **Recursive Call**: The function calls itself recursively with a smaller list until it reaches the base case.

### Code:
```python

def someRecursive(arr, cb):
    if len(arr) == 0:
        return False
    if not(cb(arr[0])):
        return someRecursive(arr[1:], cb)
    return True

def isOdd(num):
    if num%2==0:
        return False
    else:
        return True


print(someRecursive([1,2,3,4], isOdd)) # true
print(someRecursive([4,6,8,9], isOdd)) # true
print(someRecursive([4,6,8], isOdd)) # false
```


# Problem 13: Factorial Solution 🔄

The thirteenth problem involves writing a function that calculates the factorial of a number using recursion.

## Explanation

The `factorial` function takes an integer `num` as input and returns the factorial of `num`.

### Steps

1. **Base Case**: The function checks if `num` is less than or equal to 1.
2. **Changing State and Moving Toward Base Case**: If `num` is greater than 1, it returns `num` multiplied by a recursive call to `factorial` with `num - 1`.
3. **Recursive Call**: The function calls itself recursively with a smaller number until it reaches the base case.

### Code:
```python
def factorial(num):
    if num <= 1:
        return 1
    return num * factorial(num-1)


print(factorial(1)) # 1
print(factorial(2)) # 2
print(factorial(4)) # 24
print(factorial(7)) # 5040
```

# Problem 14: Reverse Solution ↩️

The fourteenth problem involves writing a function that reverses a string using recursion.

## Explanation

The `reverse` function takes a string `strng` as input and returns the reversed version of `strng`.

### Steps

1. **Base Case**: The function checks if the length of `strng` is less than or equal to 1.
2. **Changing State and Moving Toward Base Case**: If `strng` has more than one character, it returns the last character concatenated with a recursive call to `reverse` with the substring excluding the last character (`strng[0:len(strng)-1]`).
3. **Recursive Call**: The function calls itself recursively with a smaller substring until it reaches the base case.
### Code:
```python
def reverse(strng):
    if len(strng) <= 1:
      return strng
    return strng[len(strng)-1] + reverse(strng[0:len(strng)-1])


print(reverse('python')) # 'nohtyp'
print(reverse('appmillers')) # 'srellimppa'
```
