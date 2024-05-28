---
title: 'Article on DSA Topic: Sorting Algorithms'
description: In this article, we delve into Sorting Algorithms in the context of Data Structures and Algorithms (DSA).
date: 2024-05-22
author: Nehal Fathema
tags:
    - Data Structures
    - Algorithms
    - Sorting
---

# Sorting Algorithms

Sorting is a fundamental operation in computer science, used to arrange data in a specific order. Various sorting algorithms are designed to efficiently sort data in different scenarios. This section covers Bubble Sort, Selection Sort, Insertion Sort, Quick Sort, and Merge Sort.

## 1. Bubble Sort

### Algorithm
Bubble Sort repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. This process is repeated until the list is sorted.

### Steps
1. Compare each pair of adjacent elements from the beginning of the list.
2. If a pair is in the wrong order, swap them.
3. Repeat the process for each element, excluding the last one each time, since the largest element will have "bubbled" to the end.

### Pseudocode
```
function bubbleSort(array):
n = length(array)
for i from 0 to n-1:
for j from 0 to n-i-2:
if array[j] > array[j+1]:
swap(array[j], array[j+1])
```

### Time Complexity
- Best case: O(n) (when the array is already sorted)
- Average case: O(n^2)
- Worst case: O(n^2)

### Space Complexity
- O(1)

#### C++
```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n-1; i++) {
        for (int j = 0; j < n-i-1; j++) {
            if (arr[j] > arr[j+1]) {
                swap(arr[j], arr[j+1]);
            }
        }
    }
}

int main() {
    int arr[] = {64, 25, 12, 22, 11};
    int n = sizeof(arr)/sizeof(arr[0]);
    bubbleSort(arr, n);
    cout << "Sorted array: ";
    for (int i=0; i<n; i++)
        cout << arr[i] << " ";
    return 0;
}
```
#### Java
```java
public class BubbleSort {
    public static void bubbleSort(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }

    public static void main(String[] args) {
        int[] arr = {64, 25, 12, 22, 11};
        bubbleSort(arr);
        System.out.print("Sorted array: ");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
```
#### Python
```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n - 1):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]

arr = [64, 25, 12, 22, 11]
bubble_sort(arr)
print("Sorted array:", arr)
```
### Example
* Unsorted array: [64, 25, 12, 22, 11]
* Sorted array: [11, 12, 22, 25, 64]
## 2. Selection Sort
### Algorithm
Selection Sort divides the list into a sorted and an unsorted part. It repeatedly selects the smallest (or largest) element from the unsorted part and moves it to the end of the sorted part.

### Steps
1. Find the minimum element in the unsorted part.
2. Swap it with the first element of the unsorted part.
3. Move the boundary of the sorted part one element forward.
4. Repeat the process until the entire array is sorted.
### Pseudocode
```
function selectionSort(array):
    n = length(array)
    for i from 0 to n-1:
        minIndex = i
        for j from i+1 to n-1:
            if array[j] < array[minIndex]:
                minIndex = j
        swap(array[minIndex], array[i])
```
### Time Complexity
* Best case: O(n^2)
* Average case: O(n^2)
* Worst case: O(n^2)
### Space Complexity
* O(1)
#### C++
```cpp
#include <iostream>
using namespace std;

void selectionSort(int arr[], int n) {
    for (int i = 0; i < n-1; i++) {
        int minIndex = i;
        for (int j = i+1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        swap(arr[minIndex], arr[i]);
    }
}

int main() {
    int arr[] = {64, 25, 12, 22, 11};
    int n = sizeof(arr)/sizeof(arr[0]);
    selectionSort(arr, n);
    cout << "Sorted array: ";
    for (int i=0; i<n; i++)
        cout << arr[i] << " ";
    return 0;
}
```
#### Java
```java
public class SelectionSort {
    public static void selectionSort(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
            int minIndex = i;
            for (int j = i + 1; j < n; j++) {
                if (arr[j] < arr[minIndex]) {
                    minIndex = j;
                }
            }
            int temp = arr[minIndex];
            arr[minIndex] = arr[i];
            arr[i] = temp;
        }
    }

    public static void main(String[] args) {
        int[] arr = {64, 25, 12, 22, 11};
        selectionSort(arr);
        System.out.print("Sorted array: ");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
```
#### Python
```python
def selection_sort(arr):
    n = len(arr)
    for i in range(n - 1):
        min_index = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_index]:
                min_index = j
        arr[i], arr[min_index] = arr[min_index], arr[i]

arr = [64, 25, 12, 22, 11]
selection_sort(arr)
print("Sorted array:", arr)
```
### Example
* Unsorted array: [64, 25, 12, 22, 11]
* Sorted array: [11, 12, 22, 25, 64]

## 3. Insertion Sort
### Algorithm
Insertion Sort builds the sorted array one item at a time. It takes each element from the input and finds its correct position in the sorted part.

### Steps
1. Start with the second element, as the first element is considered sorted.
2. Compare the current element with the elements in the sorted part and shift the sorted elements to the right to create the correct position for the current element.
3. Insert the current element in its correct position.
4. Repeat the process for all elements.

### Pseudocode
```
    function insertionSort(array):
    n = length(array)
    for i from 1 to n-1:
        key = array[i]
        j = i-1
        while j >= 0 and array[j] > key:
            array[j+1] = array[j]
            j = j-1
        array[j+1] = key
```
### Time Complexity
* Best case: O(n)
* Average case: O(n^2)
* Worst case: O(n^2)
### Space Complexity
* O(1)

#### C++
```cpp
#include <iostream>
using namespace std;

void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }
        arr[j + 1] = key;
    }
}

int main() {
    int arr[] = {64, 25, 12, 22, 11};
    int n = sizeof(arr)/sizeof(arr[0]);
    insertionSort(arr, n);
    cout << "Sorted array: ";
    for (int i=0; i<n; i++)
        cout << arr[i] << " ";
    return 0;
}
```
#### Java
```java
public class InsertionSort {
    public static void insertionSort(int[] arr) {
        int n = arr.length;
        for (int i = 1; i < n; i++) {
            int key = arr[i];
            int j = i - 1;
            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j = j - 1;
            }
            arr[j + 1] = key;
        }
    }

    public static void main(String[] args) {
        int[] arr = {64, 25, 12, 22, 11};
        insertionSort(arr);
        System.out.print("Sorted array: ");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
```
#### Python
```python
def insertion_sort(arr):
    n = len(arr)
    for i in range(1, n):
        key = arr[i]
        j = i - 1
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key

arr = [64, 25, 12, 22, 11]
insertion_sort(arr)
print("Sorted array:", arr)
```
### Example
* Unsorted array: [64, 25, 12, 22, 11]
* Sorted array: [11, 12, 22, 25, 64]

## 4. Quick Sort
### Algorithm
Quick Sort is a divide-and-conquer algorithm. It works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot.

### Steps
1. Choose a pivot element.
2. Partition the array into two parts: elements less than the pivot and elements greater than the pivot.
3. Recursively apply the above steps to the sub-arrays.
4. Combine the sub-arrays and the pivot into a single sorted array.

### Pseudocode
```
function quickSort(array, low, high):
    if low < high:
        pivotIndex = partition(array, low, high)
        quickSort(array, low, pivotIndex - 1)
        quickSort(array, pivotIndex + 1, high)

function partition(array, low, high):
    pivot = array[high]
    i = low - 1
    for j from low to high - 1:
        if array[j] < pivot:
            i = i + 1
            swap(array[i], array[j])
    swap(array[i + 1], array[high])
    return i + 1
```
### Time Complexity
* Best case: O(n log n)
* Average case: O(n log n)
* Worst case: O(n log n)
### Space Complexity
* O(n)
#### C++
```cpp
#include <iostream>
#include <vector>

void quickSort(std::vector<int>& arr, int low, int high) {
    if (low < high) {
        int pivot = arr[high];
        int i = low - 1;
        for (int j = low; j < high; ++j) {
            if (arr[j] < pivot) {
                ++i;
                std::swap(arr[i], arr[j]);
            }
        }
        std::swap(arr[i + 1], arr[high]);
        int partitionIndex = i + 1;
        
        quickSort(arr, low, partitionIndex - 1);
        quickSort(arr, partitionIndex + 1, high);
    }
}

int main() {
    std::vector<int> arr = {5, 2, 9, 1, 5, 6, 3};
    int n = arr.size();
    
    quickSort(arr, 0, n - 1);
    
    std::cout << "Sorted array: ";
    for (int num : arr) {
        std::cout << num << " ";
    }
    std::cout << std::endl;
    
    return 0;
}
```
#### Java
```java
import java.util.Arrays;

public class QuickSort {
    public static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int pivot = arr[high];
            int i = low - 1;
            for (int j = low; j < high; ++j) {
                if (arr[j] < pivot) {
                    ++i;
                    int temp = arr[i];
                    arr[i] = arr[j];
                    arr[j] = temp;
                }
            }
            int temp = arr[i + 1];
            arr[i + 1] = arr[high];
            arr[high] = temp;
            int partitionIndex = i + 1;
            
            quickSort(arr, low, partitionIndex - 1);
            quickSort(arr, partitionIndex + 1, high);
        }
    }
    
    public static void main(String[] args) {
        int[] arr = {5, 2, 9, 1, 5, 6, 3};
        
        quickSort(arr, 0, arr.length - 1);
        
        System.out.print("Sorted array: ");
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
```
#### Python
```python
def quickSort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quickSort(left) + middle + quickSort(right)

arr = [5, 2, 9, 1, 5, 6, 3]
sorted_arr = quickSort(arr)
print("Sorted array:", sorted_arr)
```
## 5. Merge Sort
### Algorithm
Merge Sort is a divide-and-conquer algorithm. It works by recursively dividing the array into two halves, sorting each half, and then merging them back together.

### Steps
1. Divide the array into two halves.
2. Recursively sort each half.
3. Merge the sorted halves back together.
### Pseudocode
```
function mergeSort(array):
    if length of array <= 1:
        return array
    mid = length of array / 2
    leftHalf = mergeSort(first half of array)
    rightHalf = mergeSort(second half of array)
    return merge(leftHalf, rightHalf)

function merge(leftHalf, rightHalf):
    result = empty array
    while leftHalf is not empty and rightHalf is not empty:
        if first element of leftHalf <= first element of rightHalf:
            append first element of leftHalf to result
            remove first element from leftHalf
        else:
            append first element of rightHalf to result
            remove first element from rightHalf
    append remaining elements of leftHalf to result
    append remaining elements of rightHalf to result
    return result
```
### Time Complexity
* Best case: O(n log n)
* Average case: O(n log n)
* Worst case: O(n log n)
### Space Complexity
* O(n)

#### C++
```cpp
#include <iostream>
using namespace std;

void merge(int arr[], int l, int m, int r) {
    int n1 = m - l + 1;
    int n2 = r - m;

    int L[n1], R[n2];

    for (int i = 0; i < n1; i++)
        L[i] = arr[l + i];
    for (int j = 0; j < n2; j++)
        R[j] = arr[m + 1 + j];

    int i = 0;
    int j = 0;
    int k = l;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        } else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }

    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }

    while (j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }
}

void mergeSort(int arr[], int l, int r) {
    if (l < r) {
        int m = l + (r - l) / 2;

        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);

        merge(arr, l, m, r);
    }
}

int main() {
    int arr[] = {64, 25, 12, 22, 11};
    int n = sizeof(arr)/sizeof(arr[0]);
    mergeSort(arr, 0, n - 1);
    cout << "Sorted array: ";
    for (int i=0; i<n; i++)
        cout << arr[i] << " ";
    return 0;
}
```
#### Java
```java
public class MergeSort {
    public static void merge(int[] arr, int l, int m, int r) {
        int n1 = m - l + 1;
        int n2 = r - m;

        int[] L = new int[n1];
        int[] R = new int[n2];

        for (int i = 0; i < n1; ++i)
            L[i] = arr[l + i];
        for (int j = 0; j < n2; ++j)
            R[j] = arr[m + 1 + j];

        int i = 0, j = 0;

        int k = l;
        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                arr[k] = L[i];
                i++;
            } else {
                arr[k] = R[j];
                j++;
            }
            k++;
        }

        while (i < n1) {
            arr[k] = L[i];
            i++;
            k++;
        }

        while (j < n2) {
            arr[k] = R[j];
            j++;
            k++;
        }
    }

    public static void mergeSort(int[] arr, int l, int r) {
        if (l < r) {
            int m = (l + r) / 2;

            mergeSort(arr, l, m);
            mergeSort(arr, m + 1, r);

            merge(arr, l, m, r);
        }
    }

    public static void main(String[] args) {
        int[] arr = {64, 25, 12, 22, 11};
        int n = arr.length;
        mergeSort(arr, 0, n - 1);
        System.out.print("Sorted array: ");
        for (int i = 0; i < n; ++i)
            System.out.print(arr[i] + " ");
    }
}
```
#### Python
```python
def merge(arr, l, m, r):
    n1 = m - l + 1
    n2 = r - m

    L = [0] * n1
    R = [0] * n2

    for i in range(n1):
        L[i] = arr[l + i]
    for j in range(n2):
        R[j] = arr[m + 1 + j]

    i = 0
    j = 0
    k = l
    while i < n1 and j < n2:
        if L[i] <= R[j]:
            arr[k] = L[i]
            i += 1
        else:
            arr[k] = R[j]
            j += 1
        k += 1

    while i < n1:
        arr[k] = L[i]
        i += 1
        k += 1

    while j < n2:
        arr[k] = R[j]
        j += 1
        k += 1

def mergeSort(arr, l, r):
    if l < r:
        m = (l + (r - 1)) // 2

        mergeSort(arr, l, m)
        mergeSort(arr, m + 1, r)
        merge(arr, l, m, r)

arr = [64, 25, 12, 22, 11]
n = len(arr)
mergeSort(arr, 0, n - 1)
print("Sorted array:", end=" ")
for i in range(n):
    print(arr[i], end=" ")
```
### Example
* Unsorted array: [64, 25, 12, 22, 11]
* Sorted array: [11, 12, 22, 25, 64]