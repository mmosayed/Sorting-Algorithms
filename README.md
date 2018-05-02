# Sorting Algorithms
## What is sorting and why is it useful?
Sorting is one of the most commonly used algorithms in the real world. Many tasks just become easier to do if the data is sorted. 

**Challenge #1** 
Given the following array of numbers find the lowest value:
```javascript
let numbers = [ 4 , 1, 7, 9, 0, 55, 2 ];
```
<details>
    <summary>Solution to Challenge #1</summary>

    let numbers = [ 4 , 1, 7, 9, 0, 55, 2 ];

    function lowestVal(arr) {
        let lowest = arr[0];
        for (let i = 1; i < arr.length; i++) {
            if (lowest > arr[i]) {
                lowest = arr[i];
            }
        }
        return lowest;
    }

    lowestVal(numbers); // Returns 0
</details>

<details>
    <summary>Time Complexity?</summary>
    O(n)
</details>

Now what if we had the array already sorted?
```javascript
let numbersSorted = [ 0, 2, 1, 4, 7, 9, 55 ];

let lowest = numbersSorted[0]; // 0
let thirdLowest = numbersSorted[2]; // 1
```
Time complexity: O(1)

## Real world examples of Sorting
- Organizing customers on Amazon based on the most purchases
- Getting the best player in the NBA based on various stats (Points, Assists)

## Sorting Algorithms

There are many ways to sort through a set of data. That is why we call these "algorithms". 
> Algorithm: An algorithm is a set of instructions designed to perform a specific task. 

There are many creative ways computer scientists went onto solving sorting problems. Today we will be discussing two:
- Bubble Sort
- Merge Sort

|Algorithm| Average Time Complexity |
|--|--|
| Selection Sort | O(n^2) |
| Insertion Sort | O(n^2) |
| Bubble Sort | O(n^2) |
| Merge Sort | O(n Log(n)) |
| Quick Sort | O(n Log(n)) |

Sorting algorithms can be very complicated to wrap your head around, but if you can break down the fundemental problems it can be easy. 

It's important to understand very basic algorithms to be able to code more complex ones. 

## Simple Algorithms Practice 1

**Challenge #2**

Loop through an array from end to beginning. Basically in reverse.
<details>
    <summary>Solution to Challenge #2</summary>

```javascript
let numbers = [ 4 , 1, 7, 9, 0, 55, 2 ];

function loopReverse(arr) {
    for (let i = arr.length - 1; i >= 0; i--) {
        console.log(arr[i]);
    }
}

loopReverse(numbers); 
```

</details>

**Challenge #3**

Make a function that swaps two elements in an array.
<details>
    <summary>Solution to Challenge #3</summary>

```javascript
let numbers = [ 4 , 1, 7, 9, 0, 55, 2 ];

function swap(arr, i, j) {
    let temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
}

swap(numbers, 0, 3); 
console.log(numbers);
```

</details>

## Bubble Sort
Bubble Sort is the simplest sorting algorithm that works by repeatedly swapping the adjacent elements if they are in wrong order.

![Bubble Sort](https://upload.wikimedia.org/wikipedia/commons/c/c8/Bubble-sort-example-300px.gif)

**Steps to solve this problem:**
1. Understand how many cycles the algorithm will need to go through.
    - You will most likely have an outer loop starting at the end of the array.
    - This will help you keep track of where to stop during each cycle. 
2. Understand how to loop through the array for each iteration.
    - You will most likely have an inner loop starting at the beginning of the array.
    - This will go through the array and compare two consecutive indexes
    - This will stop before hitting where the last cycle left off
3. Understand that every iteration you will be comparing the current and next indexes. 
    - If the left index is greater than the right index then swap. 
    - Else don't do any swapping 

**Bubble Sort Step 1**
```javascript
function bubbleSort(arr) {
    // Understand how many cycles the algorithm will need to go through.
    for (var i = arr.length - 1; i >= 0; i--) {

    }
}
```

**Bubble Sort Step 2**
```javascript
function bubbleSort(arr) {
    // Understand how many cycles the algorithm will need to go through.
    for (var i = arr.length - 1; i >= 0; i--) {
        // Understand how to loop through the array for each iteration.
        for(var j = 1; j <= i; j++) {

        }
    }
}
```

**Bubble Sort Step 3**
```javascript
function bubbleSort(arr) {
    // Understand how many cycles the algorithm will need to go through.
    for (var i = arr.length - 1; i >= 0; i--) {
        // Understand how to loop through the array for each iteration.
        for(var j = 1; j <= i; j++) {
            // Understand that every iteration you will be comparing the current and next indexes.
            if(arr[j-1] > arr[j]) {
                // SWAP
                var temp = arr[j-1];
                arr[j-1] = arr[j];
                arr[j] = temp;
            }
        }
    }
    return arr;
}
```

Bubble sort is a simple algorithm to program but it's very slow with a O(n^2) time complexity. 

<hr/>

## Simple Algorithms Practice 2

**Challenge #4**

Write a basic Factorial recursive function. 

For example: 5! = 1 * 2 * 3 * 4 * 5 = 120
<details>
    <summary>Solution to Challenge #4</summary>

```javascript
function factorial(num) {
    // BASE CASE:
    if (num == 0) {
        return 1;
    }
    // RECURSIVE CASE:
    else {
        return num * factorialize(num - 1);
    }
}
factorial(5); 
```

</details>

**Challenge #5**

Given the following array, how do you break it into two halves?
```javascript
let arr = [ 4 , 1, 7, 9, 0, 55, 2 ];

// Left Half [ 4, 1, 7 ]
// Right Half [ 9, 0, 55, 2 ]

```
<details>
    <summary>Solution to Challenge #5</summary>

```javascript
let arr = [ 4 , 1, 7, 9, 0, 55, 2 ];

// Get the middle index of array
let mid = Math.floor(arr.length/2);

// Use slice to get the left and right half 
// The slice() method selects the elements starting at the given start argument, and ends at, but does not include, the given end argument.
// If slice() is only given one arguement, it starts their and ends at the end of the array
let left = arr.slice(0, mid);
let right = arr.slice(mid);

```

</details>

## Merge Sort

Merge Sort is a Divide and Conquer algorithm. It divides input array in two halves, calls itself for the two halves and then merges the two sorted halves.

![Mergesort](https://upload.wikimedia.org/wikipedia/commons/c/cc/Merge-sort-example-300px.gif)

A typical Divide and Conquer algorithm solves a problem using following three steps.

1. Divide: Break the given problem into subproblems of same type.
2. Conquer: Recursively solve these subproblems
3. Combine: Correctly combine the answers

This image describes the steps a merge sort algorithm takes to solve the problem:

![Mergesort](https://www.geeksforgeeks.org/wp-content/uploads/Merge-Sort-Tutorial.png)



## Solving Merge Sort

**Steps to solve this problem:**
1. Understand that there are going to be TWO functions
    - One will be called mergeSort()
        - This is the recursive main function where you pass in the array you wish to sort
    - One will be called merge()
        - This is a regular function that takes in two arrays and sorts it

```javascript
function mergeSort(arr) {
    // Base case

    // Recursive case
    // Will call merge() in here
}

function merge(left, right) {
    // Will loop through the arrays and sort
}
```


2. mergeSort()
    - Satisfy the base case, when can you not break an array in half anymore?
    - Find the midpoint of the array
    - Call merge sort on the LEFT and RIGHT halves
    - Return the MERGED value 

```javascript
function mergeSort(arr) {

    // Satisfy the base case, when can you not break an array in half anymore?
    if (arr.length < 2) {
        return arr;
    }

    // Mid point of the array and halves
    let mid = Math.floor(arr.length/2);
    let left = arr.slice(0, mid);
    let right = arr.slice(mid);

    // Return the MERGED VALUE && Recursive case
    return merge(mergeSort(left), mergeSort(right));
}
```

3. merge()
    1. Understand that you will need two pointers to compare each array
        - Example: let l and let r
    2. We need to store the values from least to greatest in an array and return it
        - Example: let result = []; return result;
    3. We need to loop through both left and right at the same time 
        - Example: while(l < left.length && r < right.length)
    4. Compare both pointers and push the smaller value to the result array
        - Example: if (left[l] < right[r])
    5. Add any leftovers to the result array
        - Example: result.concat( left.slice(l) )

**Merge Step 1**
```javascript
function merge(left, right) {
    // Understand that you will need two pointers to compare each array
    let l = 0; 
    let r = 0;

}
```

**Merge Step 2**
```javascript
function merge(left, right) {
    // Understand that you will need two pointers to compare each array
    let l = 0; 
    let r = 0;
    // We need to store the values from least to greatest in an array and return it
    let result = [];


    return result;
}
```

**Merge Step 3**
```javascript
function merge(left, right) {
    // Understand that you will need two pointers to compare each array
    let l = 0; 
    let r = 0;
    // We need to store the values from least to greatest in an array and return it
    let result = [];
    // We need to loop through both left and right at the same time 
    while(l < left.length &&  r < right.length) {

    }
    
    return result;
}
```

**Merge Step 4**
```javascript
function merge(left, right) {
    // Understand that you will need two pointers to compare each array
    let l = 0; 
    let r = 0;
    // We need to store the values from least to greatest in an array and return it
    let result = [];
    // We need to loop through both left and right at the same time 
    while(l < left.length &&  r < right.length) {
        // Compare both pointers and push the smaller value to the result array
        if (left[l] < right[r]) {
            result.push(left[l]);
            l++;
        }
        else {
            result.push(right[r]);
            r++;
        }
    }
    
    return result;
}
```

**Merge Step 5**
```javascript
function merge(left, right) {
    // Understand that you will need two pointers to compare each array
    let l = 0; 
    let r = 0;
    // We need to store the values from least to greatest in an array and return it
    let result = [];
    // We need to loop through both left and right at the same time 
    while(l < left.length &&  r < right.length) {
        // Compare both pointers and push the smaller value to the result array
        if (left[l] < right[r]) {
            result.push(left[l]);
            l++;
        }
        else {
            result.push(right[r]);
            r++;
        }
    }

    // Add any leftovers to the result array    
    return result.concat(left.slice(l)).concat(right.slice(r));
}
```

