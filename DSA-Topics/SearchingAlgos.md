---
title: 'Article on DSA Topic: Searching Algorithms'
description: In this article, we delve into Searching Algorithms in the context of Data Structures and Algorithms (DSA).
date: 2024-05-21
author: Nehal Fathema
tags:
    - Data Structures
    - Algorithms
    - Searching
---

# Searching Algorithms

## Overview
Searching algorithms are designed to retrieve information stored within some data structure. These algorithms are fundamental to computer science and are used in various applications, from databases to machine learning.

## Types of Searching Algorithms

### 1. Linear Search
Linear search is the simplest search algorithm. It checks each element in the list until it finds the target element or reaches the end of the list.

#### Time Complexity
- Best case: O(1) (element is at the first position)
- Average case: O(n)
- Worst case: O(n) (element is not in the list or at the last position)

#### Space Complexity
- O(1) (iterative)

#### C++
```cpp
#include <iostream>
using namespace std;

int linearSearch(int arr[], int size, int target) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == target) {
            return i;
        }
    }
    return -1;
}

int main() {
    int arr[] = {2, 4, 6, 8, 10};
    int size = sizeof(arr) / sizeof(arr[0]);
    int target = 6;

    int result = linearSearch(arr, size, target);
    if (result != -1) {
        cout << "Element found at index " << result << endl;
    } else {
        cout << "Element not found" << endl;
    }

    return 0;
}
```
#### Java
```java
public class LinearSearch {
    public static int linearSearch(int[] arr, int target) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == target) {
                return i;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8, 10};
        int target = 6;

        int result = linearSearch(arr, target);
        if (result != -1) {
            System.out.println("Element found at index " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```
#### Python
```python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1

arr = [2, 4, 6, 8, 10]
target = 6

result = linear_search(arr, target)
if result != -1:
    print("Element found at index", result)
else:
    print("Element not found")
```
### 2. Binary Search
Binary search is a more efficient search algorithm that works on sorted arrays. It repeatedly divides the search interval in half and compares the target value to the middle element.

### Time Complexity
* Best case: O(1) (element is at the middle)
* Average case: O(log n)
* Worst case: O(log n) (element is not in the list)
### Space Complexity
* O(1) (iterative)
* O(log n) (recursive, due to call stack)
#### C++
```cpp
#include <iostream>
using namespace std;

int binarySearch(int arr[], int size, int target) {
    int left = 0;
    int right = size - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1;
}

int main() {
    int arr[] = {2, 4, 6, 8, 10};
    int size = sizeof(arr) / sizeof(arr[0]);
    int target = 8;

    int result = binarySearch(arr, size, target);
    if (result != -1) {
        cout << "Element found at index " << result << endl;
    } else {
        cout << "Element not found" << endl;
    }

    return 0;
}
```
#### Java
```java
public class BinarySearch {
    public static int binarySearch(int[] arr, int target) {
        int left = 0;
        int right = arr.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] == target) {
                return mid;
            } else if (arr[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8, 10};
        int target = 8;

        int result = binarySearch(arr, target);
        if (result != -1) {
            System.out.println("Element found at index " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```
#### Python
```python
def binary_search(arr, target):
    left = 0
    right = len(arr) - 1

    while left <= right:
        mid = left + (right - left) // 2

        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

arr = [2, 4, 6, 8, 10]
target = 8

result = binary_search(arr, target)
if result != -1:
    print("Element found at index", result)
else:
    print("Element not found")
```
### 3. Ternary Search

Ternary search is a searching algorithm that works on sorted arrays, dividing the search space into three parts instead of two in binary search. It is an improvement over binary search when the search space is large and can be efficiently implemented recursively or iteratively.
### Time Complexity
- Best case: O(1) (target is at the middle)
- Average case: O(log3 n)
- Worst case: O(log3 n) (target is not in the list)

### Space Complexity
- O(1) (iterative)
- O(log3 n) (recursive, due to call stack)

#### C++
```cpp
#include <iostream>
using namespace std;

int ternarySearch(int arr[], int left, int right, int target) {
    if (left <= right) {
        int leftMid = left + (right - left) / 3;
        int rightMid = right - (right - left) / 3;

        if (arr[leftMid] == target) {
            return leftMid;
        }
        if (arr[rightMid] == target) {
            return rightMid;
        }

        if (target < arr[leftMid]) {
            return ternarySearch(arr, left, leftMid - 1, target);
        } else if (target > arr[rightMid]) {
            return ternarySearch(arr, rightMid + 1, right, target);
        } else {
            return ternarySearch(arr, leftMid + 1, rightMid - 1, target);
        }
    }
    return -1;
}

int main() {
    int arr[] = {2, 4, 6, 8, 10, 12, 14, 16, 18, 20};
    int size = sizeof(arr) / sizeof(arr[0]);
    int target = 10;

    int result = ternarySearch(arr, 0, size - 1, target);
    if (result != -1) {
        cout << "Element found at index " << result << endl;
    } else {
        cout << "Element not found" << endl;
    }

    return 0;
}
```
#### Java
```java
public class TernarySearch {
    public static int ternarySearch(int[] arr, int left, int right, int target) {
        if (left <= right) {
            int leftMid = left + (right - left) / 3;
            int rightMid = right - (right - left) / 3;

            if (arr[leftMid] == target) {
                return leftMid;
            }
            if (arr[rightMid] == target) {
                return rightMid;
            }

            if (target < arr[leftMid]) {
                return ternarySearch(arr, left, leftMid - 1, target);
            } else if (target > arr[rightMid]) {
                return ternarySearch(arr, rightMid + 1, right, target);
            } else {
                return ternarySearch(arr, leftMid + 1, rightMid - 1, target);
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8, 10, 12, 14, 16, 18, 20};
        int target = 10;

        int result = ternarySearch(arr, 0, arr.length - 1, target);
        if (result != -1) {
            System.out.println("Element found at index " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```
#### Python
```python
def ternary_search(arr, left, right, target):
    if left <= right:
        left_mid = left + (right - left) // 3
        right_mid = right - (right - left) // 3

        if arr[left_mid] == target:
            return left_mid
        if arr[right_mid] == target:
            return right_mid

        if target < arr[left_mid]:
            return ternary_search(arr, left, left_mid - 1, target)
        elif target > arr[right_mid]:
            return ternary_search(arr, right_mid + 1, right, target)
        else:
            return ternary_search(arr, left_mid + 1, right_mid - 1, target)
    return -1

arr = [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
target = 10

result = ternary_search(arr, 0, len(arr) - 1, target)
if result != -1:
    print("Element found at index", result)
else:
    print("Element not found")
```
### 4. Jump Search
Jump search is an algorithm for sorted arrays that works by jumping ahead by fixed steps or blocks and then performing a linear search within the block where the target element might be.

### Time Complexity
* Best case: O(1)
* Average case: O(√n)
* Worst case: O(√n)
### Space Complexity
* O(1)
#### C++
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int jumpSearch(int arr[], int size, int target) {
    int step = sqrt(size);
    int prev = 0;

    while (arr[min(step, size) - 1] < target) {
        prev = step;
        step += sqrt(size);
        if (prev >= size) {
            return -1;
        }
    }

    for (int i = prev; i < min(step, size); i++) {
        if (arr[i] == target) {
            return i;
        }
    }
    return -1;
}

int main() {
    int arr[] = {2, 4, 6, 8, 10, 12, 14, 16, 18, 20};
    int size = sizeof(arr) / sizeof(arr[0]);
    int target = 16;

    int result = jumpSearch(arr, size, target);
    if (result != -1) {
        cout << "Element found at index " << result << endl;
    } else {
        cout << "Element not found" << endl;
    }

    return 0;
}
```
#### Java
```java
public class JumpSearch {
    public static int jumpSearch(int[] arr, int size, int target) {
        int step = (int) Math.sqrt(size);
        int prev = 0;

        while (arr[Math.min(step, size) - 1] < target) {
            prev = step;
            step += (int) Math.sqrt(size);
            if (prev >= size) {
                return -1;
            }
        }

        for (int i = prev; i < Math.min(step, size); i++) {
            if (arr[i] == target) {
                return i;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8, 10, 12, 14, 16, 18, 20};
        int target = 16;

        int result = jumpSearch(arr, arr.length, target);
        if (result != -1) {
            System.out.println("Element found at index " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```
#### Python
```python
import math

def jump_search(arr, size, target):
    step = int(math.sqrt(size))
    prev = 0

    while arr[min(step, size) - 1] < target:
        prev = step
        step += int(math.sqrt(size))
        if prev >= size:
            return -1

    for i in range(prev, min(step, size)):
        if arr[i] == target:
            return i
    return -1

arr = [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
target = 16

result = jump_search(arr, len(arr), target)
if result != -1:
    print("Element found at index", result)
else:
    print("Element not found")
```
### 5. Interpolation Search
Interpolation search is an improved variant of binary search for uniformly distributed data. It estimates the position of the target value based on the values at the ends of the current search interval.

### Time Complexity
* Best case: O(1)
* Average case: O(log log n)
* Worst case: O(n) (non-uniform distribution)
### Space Complexity
* O(1)
#### C++
```cpp
#include <iostream>
using namespace std;

int interpolationSearch(int arr[], int size, int target) {
    int low = 0;
    int high = size - 1;

    while (low <= high && target >= arr[low] && target <= arr[high]) {
        if (low == high) {
            if (arr[low] == target) {
                return low;
            }
            return -1;
        }

        int pos = low + ((double)(high - low) / (arr[high] - arr[low]) * (target - arr[low]));

        if (arr[pos] == target) {
            return pos;
        }

        if (arr[pos] < target) {
            low = pos + 1;
        } else {
            high = pos - 1;
        }
    }
    return -1;
}

int main() {
    int arr[] = {2, 4, 6, 8, 10, 12, 14, 16, 18, 20};
    int size = sizeof(arr) / sizeof(arr[0]);
    int target = 12;

    int result = interpolationSearch(arr, size, target);
    if (result != -1) {
        cout << "Element found at index " << result << endl;
    } else {
        cout << "Element not found" << endl;
    }

    return 0;
}
```
#### Java
```java
public class InterpolationSearch {
    public static int interpolationSearch(int[] arr, int size, int target) {
        int low = 0;
        int high = size - 1;

        while (low <= high && target >= arr[low] && target <= arr[high]) {
            if (low == high) {
                if (arr[low] == target) {
                    return low;
                }
                return -1;
            }

            int pos = low + ((high - low) / (arr[high] - arr[low]) * (target - arr[low]));

            if (arr[pos] == target) {
                return pos;
            }

            if (arr[pos] < target) {
                low = pos + 1;
            } else {
                high = pos - 1;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8, 10, 12, 14, 16, 18, 20};
        int target = 12;

        int result = interpolationSearch(arr, arr.length, target);
        if (result != -1) {
            System.out.println("Element found at index " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```
#### Python
```python
def interpolation_search(arr, size, target):
    low = 0
    high = size - 1

    while low <= high and target >= arr[low] and target <= arr[high]:
        if low == high:
            if arr[low] == target:
                return low
            return -1

        pos = low + ((high - low) // (arr[high] - arr[low]) * (target - arr[low]))

        if arr[pos] == target:
            return pos

        if arr[pos] < target:
            low = pos + 1
        else:
            high = pos - 1
    return -1

arr = [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
target = 12

result = interpolation_search(arr, len(arr), target)
if result != -1:
    print("Element found at index", result)
else:
    print("Element not found")
```
### 6. Exponential Search
Exponential search is particularly useful for unbounded or infinite lists. It works by first finding the range where the target element lies and then performing binary search within that range.

### Time Complexity
* Best case: O(1)
* Average case: O(log n)
* Worst case: O(log n)
### Space Complexity
* O(1)
#### C++
```cpp
#include <iostream>
using namespace std;

int binarySearch(int arr[], int left, int right, int target) {
    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1;
}

int exponentialSearch(int arr[], int size, int target) {
    if (arr[0] == target) {
        return 0;
    }

    int i = 1;
    while (i < size && arr[i] <= target) {
        i *= 2;
    }

    return binarySearch(arr, i / 2, min(i, size - 1), target);
}

int main() {
    int arr[] = {2, 4, 6, 8, 10, 12, 14, 16, 18, 20};
    int size = sizeof(arr) / sizeof(arr[0]);
    int target = 10;

    int result = exponentialSearch(arr, size, target);
    if (result != -1) {
        cout << "Element found at index " << result << endl;
    } else {
        cout << "Element not found" << endl
    }
    return 0;
}
```
#### Java
```java
public class ExponentialSearch {
    public static int binarySearch(int[] arr, int left, int right, int target) {
        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] == target) {
                return mid;
            } else if (arr[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return -1;
    }

    public static int exponentialSearch(int[] arr, int size, int target) {
        if (arr[0] == target) {
            return 0;
        }

        int i = 1;
        while (i < size && arr[i] <= target) {
            i *= 2;
        }

        return binarySearch(arr, i / 2, Math.min(i, size - 1), target);
    }

    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8, 10, 12, 14, 16, 18, 20};
        int target = 10;

        int result = exponentialSearch(arr, arr.length, target);
        if (result != -1) {
            System.out.println("Element found at index " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```
#### Python
```python
def binary_search(arr, left, right, target):
    while left <= right:
        mid = left + (right - left) // 2

        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

def exponential_search(arr, size, target):
    if arr[0] == target:
        return 0

    i = 1
    while i < size and arr[i] <= target:
        i *= 2

    return binary_search(arr, i // 2, min(i, size - 1), target)

arr = [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
target = 10

result = exponential_search(arr, len(arr), target)
if result != -1:
    print("Element found at index", result)
else:
    print("Element not found")
```
