---
title: 'Article on DSA Topic: Most Popular Divide and Conquer Algorithms'
description: In this article, we delve into Divide and Conquer Algorithms in the context of Data Structures and Algorithms (DSA).
date: 2024-05-22
author: Nehal Fathema
tags:
    - Data Structures
    - Algorithms
    - Divide and Conquer
---
# Divide and Conquer Algorithm

## What is the Divide and Conquer Algorithm?
Divide and conquer is a powerful algorithmic paradigm used to solve complex problems by breaking them down into smaller, more manageable subproblems. Each subproblem is solved independently, and their solutions are combined to solve the original problem.

## Why Use Divide and Conquer?
Divide and conquer is useful for:
- Solving problems that can be broken down into similar subproblems.
- Improving efficiency by reducing the problem size at each step.
- Achieving optimal time complexity in many classical algorithms.

## Steps of Divide and Conquer
1. **Divide**: Break the problem into smaller subproblems of the same type.
2. **Conquer**: Solve each subproblem recursively.
3. **Combine**: Merge the solutions of the subproblems to get the solution to the original problem.

## Examples of Divide and Conquer Algorithms
1. **Merge Sort**
2. **Quick Sort**
3. **Binary Search**
4. **Karatsuba Algorithm for Fast Multiplication**
5. **Closest Pair of Points**

### 1. Merge Sort
Merge Sort is a classic example of a divide and conquer algorithm. It divides the array into two halves, sorts each half, and then merges the sorted halves.

#### Algorithm Explanation
1. **Divide**: Split the array into two halves.
2. **Conquer**: Recursively sort each half.
3. **Combine**: Merge the two sorted halves into a single sorted array.

#### Example
Consider the array: `[38, 27, 43, 3, 9, 82, 10]`

#### Steps
1. Split into `[38, 27, 43]` and `[3, 9, 82, 10]`
2. Recursively sort the halves to get `[27, 38, 43]` and `[3, 9, 10, 82]`
3. Merge the sorted halves to get `[3, 9, 10, 27, 38, 43, 82]`

#### C++ Code
```cpp
#include <iostream>
#include <vector>

using namespace std;

void merge(vector<int>& arr, int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;

    vector<int> L(n1), R(n2);

    for (int i = 0; i < n1; ++i)
        L[i] = arr[left + i];
    for (int j = 0; j < n2; ++j)
        R[j] = arr[mid + 1 + j];

    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            ++i;
        } else {
            arr[k] = R[j];
            ++j;
        }
        ++k;
    }

    while (i < n1) {
        arr[k] = L[i];
        ++i;
        ++k;
    }

    while (j < n2) {
        arr[k] = R[j];
        ++j;
        ++k;
    }
}

void mergeSort(vector<int>& arr, int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;

        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);

        merge(arr, left, mid, right);
    }
}

int main() {
    vector<int> arr = {38, 27, 43, 3, 9, 82, 10};
    mergeSort(arr, 0, arr.size() - 1);

    cout << "Sorted array: ";
    for (int num : arr) {
        cout << num << " ";
    }
    cout << endl;

    return 0;
}
```
#### Note : For "Java" and "Python" code refer to "Sorting Algos" file in the directory "DSA-Topics"
### 2. Quick Sort
Quick Sort is another popular divide and conquer algorithm. It picks a pivot element, partitions the array around the pivot, and recursively sorts the subarrays.

### Algorithm Explanation
1. Divide: Choose a pivot and partition the array such that elements less than the pivot are on the left, and elements greater than the pivot are on the right.
2. Conquer: Recursively sort the left and right subarrays.
3. Combine: The array is already sorted after the partition step, so no further combination is needed.
### Example
* Consider the array: [10, 7, 8, 9, 1, 5]

### Steps
1. Choose pivot as 5 and partition to get [1, 5, 7, 8, 9, 10]
2. Recursively sort the left [1] and right [7, 8, 9, 10] subarrays
#### C++ Code
```cpp
#include <iostream>
#include <vector>

using namespace std;

int partition(vector<int>& arr, int low, int high) {
    int pivot = arr[high];
    int i = low - 1;

    for (int j = low; j < high; ++j) {
        if (arr[j] < pivot) {
            ++i;
            swap(arr[i], arr[j]);
        }
    }
    swap(arr[i + 1], arr[high]);
    return i + 1;
}

void quickSort(vector<int>& arr, int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);

        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

int main() {
    vector<int> arr = {10, 7, 8, 9, 1, 5};
    quickSort(arr, 0, arr.size() - 1);

    cout << "Sorted array: ";
    for (int num : arr) {
        cout << num << " ";
    }
    cout << endl;

    return 0;
}
```
#### Note : For "Java" and "Python" code refer to "Sorting Algos" file in the directory "DSA-Topics"