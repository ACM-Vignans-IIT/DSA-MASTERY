---
title: Article on DSA Topic: Mathematics Basic
description: In this article, we delve into Arrays in the context of Data Structures and Algorithms (DSA).
date: 2024-05-20
author: Nehal Fathema
tags:
    - Data Structures
    - Algorithms
    - Arrays
---

# Arrays

## What is an Array?
An array is a data structure that can store a fixed-size sequence of elements of the same type. Each element in an array is accessed by its index, which is an integer that indicates the position of the element within the array. Arrays are useful for organizing data that can be processed in a sequence, such as lists of numbers, strings, or other objects.

## Need for Array Data Structures
Arrays are essential for several reasons:
1. **Efficient Data Access**: Arrays provide constant-time access to elements using their index.
2. **Memory Efficiency**: Arrays allocate a contiguous block of memory for elements, which can lead to better cache performance.
3. **Simplicity**: Arrays are simple to implement and use for a wide range of problems.
4. **Data Organization**: Arrays help organize data in a structured manner, making it easier to perform operations like searching, sorting, and iterating.

## Types of Arrays
1. **One-dimensional Array**: A linear sequence of elements.
2. **Multi-dimensional Array**: Arrays with more than one dimension, like 2D arrays (matrices) or 3D arrays.
3. **Dynamic Arrays**: Arrays that can resize themselves during runtime (e.g., `std::vector` in C++).

## Array Operations
1. **Initialization**: Declaring and initializing an array.
2. **Accessing Elements**: Accessing elements using their index.
3. **Modifying Elements**: Changing the value of elements.
4. **Traversing**: Iterating through all elements.
5. **Insertion**: Adding elements at a specific position.
6. **Deletion**: Removing elements from a specific position.
7. **Searching**: Finding elements based on certain criteria.
8. **Sorting**: Rearranging elements in a specific order.

## Basic Operations on Arrays

### Initialization and Access
```cpp
#include <iostream>

using namespace std;

int main() {
    // Declaration and Initialization
    int arr[5] = {1, 2, 3, 4, 5};

    // Accessing Elements
    cout << "Element at index 0: " << arr[0] << endl;
    cout << "Element at index 2: " << arr[2] << endl;

    return 0;
}
```
### Traversing and Modifying Elements
```cpp
#include <iostream>

using namespace std;

int main() {
    int arr[5] = {1, 2, 3, 4, 5};

    // Traversing and Modifying Elements
    cout << "Array before modification: ";
    for (int i = 0; i < 5; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    arr[2] = 10; // Modify element at index 2

    cout << "Array after modification: ";
    for (int i = 0; i < 5; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```
### Insertion and Deletion
```cpp
#include <iostream>
#include <vector>

using namespace std;

int main() {
    vector<int> arr = {1, 2, 3, 4, 5};

    // Insertion
    arr.insert(arr.begin() + 2, 10); // Insert 10 at index 2
    cout << "Array after insertion: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    // Deletion
    arr.erase(arr.begin() + 2); // Remove element at index 2
    cout << "Array after deletion: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```
### Searching
```cpp
#include <iostream>
#include <vector>

using namespace std;

int linearSearch(vector<int>& arr, int x) {
    for (int i = 0; i < arr.size(); i++) {
        if (arr[i] == x) {
            return i;
        }
    }
    return -1;
}

int main() {
    vector<int> arr = {1, 2, 3, 4, 5};
    int x = 3;

    int index = linearSearch(arr, x);
    if (index != -1) {
        cout << "Element " << x << " found at index " << index << endl;
    } else {
        cout << "Element " << x << " not found in the array" << endl;
    }

    return 0;
}
```
### Sorting
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main() {
    vector<int> arr = {5, 2, 3, 1, 4};

    // Sorting the array
    sort(arr.begin(), arr.end());

    cout << "Array after sorting: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```
### Reversing
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main() {
    vector<int> arr = {1, 2, 3, 4, 5};

    // Reversing the array
    reverse(arr.begin(), arr.end());

    cout << "Array after reversing: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```
### Search, Insert, Delete in a Sorted Array
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

// Binary Search for a sorted array
int binarySearch(vector<int>& arr, int x) {
    int left = 0, right = arr.size() - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == x) return mid;
        if (arr[mid] < x) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}

// Insertion in a sorted array
void sortedInsert(vector<int>& arr, int x) {
    arr.push_back(x);
    sort(arr.begin(), arr.end());
}

// Deletion in a sorted array
void sortedDelete(vector<int>& arr, int x) {
    int index = binarySearch(arr, x);
    if (index != -1) {
        arr.erase(arr.begin() + index);
    }
}

int main() {
    vector<int> arr = {1, 2, 4, 5};
    int x = 3;

    // Insert
    sortedInsert(arr, x);
    cout << "Array after insertion: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    // Delete
    sortedDelete(arr, x);
    cout << "Array after deletion: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```
### Search, Insert, Delete in an Unsorted Array
```cpp
#include <iostream>
#include <vector>

using namespace std;

// Linear Search for an unsorted array
int linearSearch(vector<int>& arr, int x) {
    for (int i = 0; i < arr.size(); i++) {
        if (arr[i] == x) return i;
    }
    return -1;
}

// Insertion in an unsorted array
void unsortedInsert(vector<int>& arr, int x) {
    arr.push_back(x);
}

// Deletion in an unsorted array
void unsortedDelete(vector<int>& arr, int x) {
    int index = linearSearch(arr, x);
    if (index != -1) {
        arr.erase(arr.begin() + index);
    }
}

int main() {
    vector<int> arr = {4, 2, 1, 5};
    int x = 3;

    // Insert
    unsortedInsert(arr, x);
    cout << "Array after insertion: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    // Delete
    unsortedDelete(arr, x);
    cout << "Array after deletion: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```
### Generating all sub arrays
```cpp
#include <iostream>
#include <vector>

using namespace std;

void printSubarrays(vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n; i++) {
        for (int j = i; j < n; j++) {
            cout << "[";
            for (int k = i; k <= j; k++) {
                cout << arr[k];
                if (k < j) cout << ", ";
            }
            cout << "] ";
        }
        cout << endl;
    }
}

int main() {
    vector<int> arr = {1, 2, 3};

    cout << "All subarrays: " << endl;
    printSubarrays(arr);

    return 0;
}
```
# Rotation of Array

## What is Array Rotation?
Array rotation involves shifting the elements of an array either to the left or to the right. Each element is moved by a specified number of positions, and the elements that fall off the end of the array wrap around to the beginning. There are two primary types of rotations:
1. **Left Rotation**: Shifting the elements to the left.
2. **Right Rotation**: Shifting the elements to the right.

## Why Rotate an Array?
Array rotation is useful in various applications including:
- **Data manipulation**: Rearranging data for specific algorithms.
- **Circular buffers**: Implementing circular queues or buffers.
- **Game development**: Rotating game objects or data structures.

## Types of Array Rotation
1. **Left Rotation**
2. **Right Rotation**

## Left Rotation
In left rotation, each element of the array is shifted to its left by a specified number of positions. The elements that fall off the start of the array are wrapped around to the end.

### Example
Consider an array `[1, 2, 3, 4, 5]` and we want to left rotate it by 2 positions. The result will be `[3, 4, 5, 1, 2]`.

### Algorithm for Left Rotation
1. Store the first `d` elements in a temporary array.
2. Shift the remaining elements of the original array to the left.
3. Copy the temporary array elements to the end of the original array.

### C++ Code for Left Rotation
```cpp
#include <iostream>
#include <vector>

using namespace std;

void leftRotate(vector<int>& arr, int d) {
    int n = arr.size();
    vector<int> temp(arr.begin(), arr.begin() + d);

    for (int i = 0; i < n - d; i++) {
        arr[i] = arr[i + d];
    }

    for (int i = 0; i < d; i++) {
        arr[n - d + i] = temp[i];
    }
}

int main() {
    vector<int> arr = {1, 2, 3, 4, 5};
    int d = 2;

    leftRotate(arr, d);

    cout << "Array after left rotation: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```
## Right Rotation
In right rotation, each element of the array is shifted to its right by a specified number of positions. The elements that fall off the end of the array are wrapped around to the beginning.

### Example
Consider an array `[1, 2, 3, 4, 5]` and we want to right rotate it by 2 positions. The result will be `[4, 5, 1, 2, 3]`.

### Algorithm for Left Rotation
1. Store the last `d` elements in a temporary array.
2. Shift the remaining elements of the original array to the right.
3. Copy the temporary array elements to the beginning of the original array.

### C++ Code for Right Rotation
```cpp
#include <iostream>
#include <vector>

using namespace std;

void rightRotate(vector<int>& arr, int d) {
    int n = arr.size();
    vector<int> temp(arr.end() - d, arr.end());

    for (int i = n - 1; i >= d; i--) {
        arr[i] = arr[i - d];
    }

    for (int i = 0; i < d; i++) {
        arr[i] = temp[i];
    }
}

int main() {
    vector<int> arr = {1, 2, 3, 4, 5};
    int d = 2;

    rightRotate(arr, d);

    cout << "Array after right rotation: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```

# Rearranging an Array

## What is Array Rearrangement?
Array rearrangement involves reordering the elements of an array according to certain rules or criteria. This can be done for various purposes such as sorting, creating a specific pattern, or preparing the data for further processing.

## Why Rearrange an Array?
Rearranging arrays is useful in many scenarios:
- **Data Organization**: To organize data in a meaningful way.
- **Pattern Formation**: To arrange elements in a specific sequence or pattern.
- **Algorithm Optimization**: To prepare data for algorithms that require a specific order.

## Common Array Rearrangement Problems
1. **Rearrange Array in Alternating Positive and Negative Items**
2. **Rearrange Array in Zigzag Fashion**
3. **Rearrange Array in Increasing-Decreasing Order**
4. **Move All Zeros to the End**
5. **Segregate Even and Odd Numbers**

## Rearrange Array in Alternating Positive and Negative Items
Rearrange an array such that positive and negative numbers are placed alternately. If either positive or negative numbers are more, they appear at the end of the array.

### Example
Consider an array `[1, 2, -3, -4, 5, -6, 7, -8]`. The rearranged array could be `[1, -3, 2, -4, 5, -6, 7, -8]`.

### Algorithm
1. Separate positive and negative numbers.
2. Merge them by placing one positive and one negative element alternatively.

### C++ Code
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

void rearrange(vector<int>& arr) {
    int n = arr.size();
    vector<int> pos, neg;

    // Separate positive and negative numbers
    for (int i = 0; i < n; i++) {
        if (arr[i] >= 0) pos.push_back(arr[i]);
        else neg.push_back(arr[i]);
    }

    int posIndex = 0, negIndex = 0, index = 0;

    // Place positive and negative numbers alternately
    while (posIndex < pos.size() && negIndex < neg.size()) {
        arr[index++] = pos[posIndex++];
        arr[index++] = neg[negIndex++];
    }

    // Copy remaining positive numbers, if any
    while (posIndex < pos.size()) {
        arr[index++] = pos[posIndex++];
    }

    // Copy remaining negative numbers, if any
    while (negIndex < neg.size()) {
        arr[index++] = neg[negIndex++];
    }
}

int main() {
    vector<int> arr = {1, 2, -3, -4, 5, -6, 7, -8};

    rearrange(arr);

    cout << "Array after rearrangement: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```
## Rearrange Array in Zigzag Fashion
Rearrange an array such that elements are in zigzag order. An array is in zigzag order if `a < b > c < d > e`.

### Example
Consider an array `[4, 3, 7, 8, 6, 2, 1]`. The rearranged array could be `[3, 7, 4, 8, 2, 6, 1]`.

### Algorithm
1. Traverse the array and compare adjacent elements.
2. If the current element is greater than the next element and the current index is even, swap them.
3. If the current element is less than the next element and the current index is odd, swap them.

### C++ Code
```cpp
#include <iostream>
#include <vector>

using namespace std;

void zigzag(vector<int>& arr) {
    bool flag = true; // true indicates < relation expected, false indicates > relation expected

    for (int i = 0; i < arr.size() - 1; i++) {
        if (flag) { // < relation expected
            if (arr[i] > arr[i + 1]) {
                swap(arr[i], arr[i + 1]);
            }
        } else { // > relation expected
            if (arr[i] < arr[i + 1]) {
                swap(arr[i], arr[i + 1]);
            }
        }
        flag = !flag; // flip flag
    }
}

int main() {
    vector<int> arr = {4, 3, 7, 8, 6, 2, 1};

    zigzag(arr);

    cout << "Array after zigzag rearrangement: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```

## Rearrange Array in Increasing-Decreasing Order
Rearrange an array such that the first half is in increasing order and the second half is in decreasing order.

### Example
Consider an array `[5, 2, 9, 1, 5, 6]`. The rearranged array could be `[1, 2, 5, 9, 6, 5]`.

### Algorithm
1. Sort the array.
2. Split the array into two halves.
3. Reverse the second half.

### C++ Code
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

void rearrangeIncDec(vector<int>& arr) {
    sort(arr.begin(), arr.end());
    int n = arr.size();
    int mid = n / 2;

    reverse(arr.begin() + mid, arr.end());
}

int main() {
    vector<int> arr = {5, 2, 9, 1, 5, 6};

    rearrangeIncDec(arr);

    cout << "Array after rearrangement in increasing-decreasing order: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```

## Move All Zeros to the End
Rearrange an array such that all zeros are moved to the end, maintaining the order of non-zero elements.

### Example
Consider an array `[1, 0, 2, 0, 0, 3, 4]`. The rearranged array could be `[1, 2, 3, 4, 0, 0, 0]`.

### Algorithm
1. Traverse the array and count the non-zero elements.
2. Place the non-zero elements in the beginning.
3. Fill the remaining positions with zeros.

## C++ Code 
```cpp
#include <iostream>
#include <vector>

using namespace std;

void moveZerosToEnd(vector<int>& arr) {
    int count = 0; // Count of non-zero elements

    for (int i = 0; i < arr.size(); i++) {
        if (arr[i] != 0) {
            arr[count++] = arr[i]; // Place non-zero element at the current count index
        }
    }

    while (count < arr.size()) {
        arr[count++] = 0; // Fill remaining positions with zeros
    }
}

int main() {
    vector<int> arr = {1, 0, 2, 0, 0, 3, 4};

    moveZerosToEnd(arr);

    cout << "Array after moving zeros to the end: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```
## Segregate Even and Odd Numbers
Rearrange an array such that all even numbers appear before all odd numbers.

### Example
Consider an array `[12, 34, 45, 9, 8, 90, 3]`. The rearranged array could be `[12, 34, 8, 90, 45, 9, 3]`.

### Algorithm
1. Initialize two pointers: one at the start and one at the end of the array.
2. Increment the start pointer until an odd number is found.
3. Decrement the end pointer until an even number is found.
4. Swap the found odd and even numbers.
5. Repeat the process until the start pointer is less than the end pointer.

## C++ Code
```cpp
#include <iostream>
#include <vector>

using namespace std;

void segregateEvenOdd(vector<int>& arr) {
    int left = 0, right = arr.size() - 1;

    while (left < right) {
        while (arr[left] % 2 == 0 && left < right) {
            left++;
        }

        while (arr[right] % 2 == 1 && left < right) {
            right--;
        }

        if (left < right) {
            swap(arr[left], arr[right]);
            left++;
            right--;
        }
    }
}

int main() {
    vector<int> arr = {12, 34, 45, 9, 8, 90, 3};

    segregateEvenOdd(arr);

    cout << "Array after segregating even and odd numbers: ";
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```
## Applications of Arrays
1. **Data Storage**: Arrays are used to store and manage data efficiently in memory.
2. **Matrix Operations**: Multi-dimensional arrays are used for mathematical and scientific computations involving matrices.
3. **Sorting and Searching Algorithms**: Arrays are fundamental in implementing various algorithms like quicksort, mergesort, and binary search.
4. **Graphs and Trees**: Arrays are used to represent adjacency matrices and other data structures in graph and tree algorithms.
5. **Buffers**: Arrays serve as buffers in I/O operations to temporarily hold data.
6. **Dynamic Programming**: Arrays are extensively used in dynamic programming to store intermediate results and optimize algorithms.



# Multidimensional Array

## What is a Multidimensional Array?
A multidimensional array is an array of arrays. It allows the representation of data in a tabular form with multiple dimensions. For example, a two-dimensional array represents data in rows and columns, like a matrix, while higher-dimensional arrays represent more complex data structures.

## Why Use Multidimensional Arrays?
Multidimensional arrays are useful for:
- Representing and manipulating matrices or tables.
- Storing data in multiple dimensions, such as coordinates in a 3D space.
- Simplifying the organization and access of complex data structures.

## Types of Multidimensional Arrays
1. **Two-Dimensional Array (2D Array)**
2. **Three-Dimensional Array (3D Array)**
3. **Higher-Dimensional Arrays**

### 1. Two-Dimensional Array (2D Array)
A 2D array is like a table with rows and columns. It can be visualized as a matrix.

#### Declaration and Initialization
```cpp
int arr[3][4] = {
    {1, 2, 3, 4},
    {5, 6, 7, 8},
    {9, 10, 11, 12}
};
```
### Accessing Elements
Elements in a 2D array are accessed using two indices: `arr[row][column]`.
### Example
Consider a 2D array representing a 3x4 matrix:
```cpp
#include <iostream>

using namespace std;

int main() {
    int arr[3][4] = {
        {1, 2, 3, 4},
        {5, 6, 7, 8},
        {9, 10, 11, 12}
    };

    // Access and print elements
    cout << "Element at arr[1][2]: " << arr[1][2] << endl; // Output: 7

    // Print the 2D array
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 4; j++) {
            cout << arr[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```
### 2. Three-Dimensional Array (3D Array)
A 3D array adds another dimension to the 2D array, representing data in a 3D space.
### Declaration and Initialization
```cpp
int arr[2][3][4] = {
    {
        {1, 2, 3, 4},
        {5, 6, 7, 8},
        {9, 10, 11, 12}
    },
    {
        {13, 14, 15, 16},
        {17, 18, 19, 20},
        {21, 22, 23, 24}
    }
};
```
### Accessing Elements
Elements in a 3D array are accessed using three indices: `arr[depth][row][column]`.
### Example
Consider a 3D array representing a 2x3x4 matrix:
```cpp
#include <iostream>

using namespace std;

int main() {
    int arr[2][3][4] = {
        {
            {1, 2, 3, 4},
            {5, 6, 7, 8},
            {9, 10, 11, 12}
        },
        {
            {13, 14, 15, 16},
            {17, 18, 19, 20},
            {21, 22, 23, 24}
        }
    };

    // Access and print elements
    cout << "Element at arr[1][2][3]: " << arr[1][2][3] << endl; // Output: 24

    // Print the 3D array
    for (int i = 0; i < 2; i++) {
        cout << "Depth " << i << ":" << endl;
        for (int j = 0; j < 3; j++) {
            for (int k = 0; k < 4; k++) {
                cout << arr[i][j][k] << " ";
            }
            cout << endl;
        }
        cout << endl;
    }

    return 0;
}
```
### Higher-Dimensional Arrays
Higher-dimensional arrays extend the concept of 2D and 3D arrays to more dimensions, but they become more complex to visualize and manage. The principles of accessing and manipulating these arrays remain similar, with additional indices for each new dimension.

## Operations on Multidimensional Arrays
### Initializing Multidimensional Arrays
Multidimensional arrays can be initialized in a variety of ways, including nested loops for dynamic initialization.
```cpp
#include <iostream>

using namespace std;

int main() {
    int arr[3][4];
    
    // Initialize the 2D array using nested loops
    int value = 1;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 4; j++) {
            arr[i][j] = value++;
        }
    }

    // Print the 2D array
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 4; j++) {
            cout << arr[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```
### Searching in Multidimensional Arrays
Searching involves iterating through the array to find a specific element.
```cpp
#include <iostream>

using namespace std;

bool searchElement(int arr[3][4], int target) {
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 4; j++) {
            if (arr[i][j] == target) {
                return true;
            }
        }
    }
    return false;
}

int main() {
    int arr[3][4] = {
        {1, 2, 3, 4},
        {5, 6, 7, 8},
        {9, 10, 11, 12}
    };

    int target = 7;
    if (searchElement(arr, target)) {
        cout << "Element " << target << " found in the array." << endl;
    } else {
        cout << "Element " << target << " not found in the array." << endl;
    }

    return 0;
}
```
### Sorting Multidimensional Arrays
Sorting a multidimensional array can be complex and typically involves flattening the array, sorting it, and then restructuring it back into its original dimensions.
```cpp
#include <iostream>
#include <algorithm>

using namespace std;

void sortRows(int arr[3][4]) {
    for (int i = 0; i < 3; i++) {
        sort(arr[i], arr[i] + 4);
    }
}

int main() {
    int arr[3][4] = {
        {4, 2, 3, 1},
        {8, 7, 6, 5},
        {12, 10, 11, 9}
    };

    sortRows(arr);

    // Print the sorted 2D array
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 4; j++) {
            cout << arr[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```
### Transposing a Matrix
Transposing a matrix involves swapping rows and columns.
```cpp
#include <iostream>

using namespace std;

void transpose(int arr[3][3], int transposed[3][3]) {
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            transposed[j][i] = arr[i][j];
        }
    }
}

int main() {
    int arr[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };
    int transposed[3][3];

    transpose(arr, transposed);

    // Print the transposed matrix
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << transposed[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```
## Applications of Multidimensional Arrays
1. **Matrix Operations**: Multiplication, addition, transposition.
2. **Game Development**: Representing game boards (e.g., chess, tic-tac-toe).
3. **Image Processing**: Representing pixel values in images.
4. **Scientific Computations**: Storing and manipulating data in scientific simulations.

# Kadane’s Algorithm

## What is Kadane’s Algorithm?
Kadane’s Algorithm is a dynamic programming algorithm used to find the maximum sum subarray within a one-dimensional array of numbers. The algorithm is known for its efficiency, having a linear time complexity of O(n).

## Why Use Kadane’s Algorithm?
Kadane's Algorithm is useful for:
- Solving the maximum subarray sum problem efficiently.
- Applications in financial analysis to find the best time period for maximum profit.
- Any situation where you need to find contiguous subarrays with the largest sum.

## Algorithm Explanation
Kadane’s Algorithm works by iterating through the array and maintaining two values:
1. **Current Maximum (`current_max`)**: The maximum sum of the subarray that ends at the current position.
2. **Global Maximum (`global_max`)**: The maximum sum of any subarray found so far.

At each step, the algorithm updates `current_max` by considering the current element alone or extending the previous subarray to include the current element. `global_max` is then updated to be the maximum of itself and `current_max`.

## Steps of the Algorithm
1. Initialize `current_max` and `global_max` to the first element of the array.
2. Iterate through the array from the second element to the end.
3. For each element, update `current_max` to be the maximum of the current element and `current_max + current element`.
4. Update `global_max` to be the maximum of `global_max` and `current_max`.
5. After finishing the iteration, `global_max` holds the maximum sum of the subarray.

## Example
Consider the array: `[-2, 1, -3, 4, -1, 2, 1, -5, 4]`

The steps would be:
1. Initialize `current_max = -2`, `global_max = -2`.
2. Iterate and update:
   - `current_max = max(1, -2 + 1) = 1`, `global_max = max(-2, 1) = 1`
   - `current_max = max(-3, 1 - 3) = -2`, `global_max = max(1, -2) = 1`
   - `current_max = max(4, -2 + 4) = 4`, `global_max = max(1, 4) = 4`
   - Continue this process for the rest of the elements.

Final result: The maximum sum subarray is `[4, -1, 2, 1]` with sum `6`.

## C++ Code
```cpp
#include <iostream>
#include <vector>
#include <climits>

using namespace std;

int kadane(const vector<int>& nums) {
    int current_max = nums[0];
    int global_max = nums[0];

    for (size_t i = 1; i < nums.size(); i++) {
        current_max = max(nums[i], current_max + nums[i]);
        if (current_max > global_max) {
            global_max = current_max;
        }
    }

    return global_max;
}

int main() {
    vector<int> nums = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
    int max_sum = kadane(nums);
    cout << "Maximum sum subarray is " << max_sum << endl;
    return 0;
}
```
### Example Explained with Code
Consider the array nums = `[-2, 1, -3, 4, -1, 2, 1, -5, 4]`:

1. Initialize:

* current_max = -2\
* global_max = -2

2. Iterate through the array:

* i = 1: current_max = max(1, -2 + 1) = 1, global_max = max(-2, 1) = 1
* i = 2: current_max = max(-3, 1 - 3) = -2, global_max = 1
* i = 3: current_max = max(4, -2 + 4) = 4, global_max = max(1, 4) = 4
* i = 4: current_max = max(-1, 4 - 1) = 3, global_max = 4
* i = 5: current_max = max(2, 3 + 2) = 5, global_max = max(4, 5) = 5
* i = 6: current_max = max(1, 5 + 1) = 6, global_max = max(5, 6) = 6
* i = 7: current_max = max(-5, 6 - 5) = 1, global_max = 6
* i = 8: current_max = max(4, 1 + 4) = 5, global_max = 6\
The maximum sum subarray found is [4, -1, 2, 1] with sum 6.

# Dutch National Flag Algorithm

## What is the Dutch National Flag Algorithm?
The Dutch National Flag Algorithm is a sorting algorithm that segregates an array into three distinct sections based on a pivot element. The elements in the array are categorized as follows:
- Elements less than the pivot
- Elements equal to the pivot
- Elements greater than the pivot

The algorithm is named after the Dutch national flag, which consists of three colors.

## Why Use the Dutch National Flag Algorithm?
The Dutch National Flag Algorithm is useful for:
- Efficiently sorting arrays with a limited range of values.
- Segregating arrays for problems like the "sort colors" problem.
- Partitioning arrays for quicksort.

## Algorithm Explanation
The algorithm uses three pointers to maintain three sections in the array:
1. **Low (low)**: Marks the end of the section containing elements less than the pivot.
2. **Mid (mid)**: Current element being examined.
3. **High (high)**: Marks the beginning of the section containing elements greater than the pivot.

The algorithm proceeds as follows:
1. Initialize `low` to 0, `mid` to 0, and `high` to the last index.
2. Iterate through the array with `mid` until it exceeds `high`.
   - If `arr[mid]` is less than the pivot, swap it with `arr[low]`, and increment both `low` and `mid`.
   - If `arr[mid]` is equal to the pivot, just increment `mid`.
   - If `arr[mid]` is greater than the pivot, swap it with `arr[high]`, and decrement `high`.
3. The array is partitioned into three sections.

## Steps of the Algorithm
1. Initialize `low = 0`, `mid = 0`, and `high = n - 1`.
2. Traverse the array:
   - If `arr[mid] < pivot`, swap `arr[low]` and `arr[mid]`, increment `low` and `mid`.
   - If `arr[mid] == pivot`, increment `mid`.
   - If `arr[mid] > pivot`, swap `arr[mid]` and `arr[high]`, decrement `high`.
3. Continue until `mid` exceeds `high`.

## Example
Consider the array: `[2, 0, 2, 1, 1, 0]` with pivot `1`.

The steps would be:
1. Initialize `low = 0`, `mid = 0`, `high = 5`.
2. Iterate and update:
   - Swap elements to ensure elements less than pivot are before `low`, elements equal to pivot are between `low` and `high`, and elements greater than pivot are after `high`.

Final result: `[0, 0, 1, 1, 2, 2]`.

## C++ Code
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

void dutchNationalFlag(vector<int>& arr, int pivot) {
    int low = 0;
    int mid = 0;
    int high = arr.size() - 1;

    while (mid <= high) {
        if (arr[mid] < pivot) {
            swap(arr[low], arr[mid]);
            low++;
            mid++;
        } else if (arr[mid] == pivot) {
            mid++;
        } else {
            swap(arr[mid], arr[high]);
            high--;
        }
    }
}

int main() {
    vector<int> arr = {2, 0, 2, 1, 1, 0};
    int pivot = 1;
    dutchNationalFlag(arr, pivot);

    cout << "Sorted array: ";
    for (int num : arr) {
        cout << num << " ";
    }
    cout << endl;

    return 0;
}
```
### Example Explained with Code
Consider the array arr = {2, 0, 2, 1, 1, 0} with pivot 1:

1. Initialize:

low = 0, mid = 0, high = 5\
2. Iterate through the array:

* mid = 0: arr[mid] = 2 > pivot: Swap arr[mid] and arr[high], decrement high.
* mid = 0: arr[mid] = 0 < pivot: Swap arr[low] and arr[mid], increment low and mid.
* Continue this process until mid exceeds high.\
The array is sorted into three sections: [0, 0, 1, 1, 2, 2].


































