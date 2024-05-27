---
title: 'Article on DSA Topic: Strings'
description: In this article, we delve into Strings in the context of Data Structures and Algorithms (DSA).
date: 2024-05-21
author: Nehal Fathema
tags:
    - Data Structures
    - Algorithms
    - Strings
---
# Strings

## What is a String?
A string is a sequence of characters. In programming, strings are used to store and manipulate text. In C++, strings can be managed using the standard library's `std::string` class, which provides various functions for string manipulation.

## Need for String Data Structures
Strings are fundamental in programming because they allow:
- Representation of textual data.
- Easy manipulation and processing of text.
- Storage and retrieval of user inputs, file contents, and communication messages.

## Types of Strings in C++
1. **C-style Strings**: Arrays of characters terminated by a null character (`'\0'`).
2. **C++ Strings**: Instances of the `std::string` class provided by the C++ Standard Library.

### C-style Strings
C-style strings are arrays of characters terminated by a null character.

#### Declaration and Initialization
```cpp
char str1[] = "Hello";
char str2[6] = {'H', 'e', 'l', 'l', 'o', '\0'};
```
```java
public class Main {
    public static void main(String[] args) {
        String str1 = "Hello"; // Equivalent to char str1[] = "Hello";
        char[] str2 = {'H', 'e', 'l', 'l', 'o', '\0'}; // Equivalent to char str2[6] = {'H', 'e', 'l', 'l', 'o', '\0'};
        
        System.out.println("str1: " + str1);
        System.out.println("str2: " + new String(str2).trim()); // Trim to remove trailing null character
    }
}
```
```python
str1 = "Hello"  # Equivalent to char str1[] = "Hello";
str2 = ['H', 'e', 'l', 'l', 'o', '\0']  # Equivalent to char str2[6] = {'H', 'e', 'l', 'l', 'o', '\0'};

print("str1:", str1)
print("str2:", ''.join(str2).strip('\0'))  # Strip to remove trailing null character
```
### Accessing and Modifying Elements
```cpp
#include <iostream>
using namespace std;

int main() {
    char str[] = "Hello";
    cout << str[1] << endl;  // Output: e
    str[1] = 'a';
    cout << str << endl;     // Output: Hallo
    return 0;
}
```
In Java, strings are immutable, meaning you cannot directly modify their contents. To achieve similar functionality, you can use a char array or StringBuilder. Here, we'll use a char array to directly modify elements:
```java
public class Main {
    public static void main(String[] args) {
        char[] str = {'H', 'e', 'l', 'l', 'o'};
        System.out.println(str[1]);  // Output: e
        str[1] = 'a';
        System.out.println(new String(str));  // Output: Hallo
    }
}
```
In Python, strings are also immutable. You can convert the string to a list of characters to modify it and then convert it back to a string:
```python
str = "Hello"
print(str[1])  # Output: e
str = list(str)
str[1] = 'a'
str = ''.join(str)
print(str)  # Output: Hallo
```
### Declaration and Initialization
```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {
    string str1 = "Hello";
    string str2("World");
    cout << str1 << " " << str2 << endl;  // Output: Hello World
    return 0;
}
```
```java
public class Main {
    public static void main(String[] args) {
        String str1 = "Hello";
        String str2 = "World";
        System.out.println(str1 + " " + str2);  // Output: Hello World
    }
}
```
```python
str1 = "Hello"
str2 = "World"
print(f"{str1} {str2}")  # Output: Hello World
```
## String Operations
Strings support a variety of operations, including:

* Concatenation
* Comparison
* Finding Substrings
* Substring Extraction
* Replacing Substrings
* Length

### Concatenation
Concatenation is combining two or more strings into one.
```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {
    string str1 = "Hello";
    string str2 = "World";
    string result = str1 + " " + str2;
    cout << result << endl;  // Output: Hello World
    return 0;
}
```
```java
public class Main {
    public static void main(String[] args) {
        String str1 = "Hello";
        String str2 = "World";
        String result = str1 + " " + str2;
        System.out.println(result);  // Output: Hello World
    }
}
```
```python
str1 = "Hello"
str2 = "World"
result = str1 + " " + str2
print(result)  # Output: Hello World
```
### Comparison
Strings can be compared using the comparison operators (`==`, `!=`, `<`, `>`, `<=`, `>=`).
```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {
    string str1 = "Hello";
    string str2 = "World";
    if (str1 == str2) {
        cout << "Strings are equal" << endl;
    } else {
        cout << "Strings are not equal" << endl;
    }
    return 0;
}
```
```java
public class Main {
    public static void main(String[] args) {
        String str1 = "Hello";
        String str2 = "World";
        if (str1.equals(str2)) {
            System.out.println("Strings are equal");
        } else {
            System.out.println("Strings are not equal");
        }
    }
}
```
```python
str1 = "Hello"
str2 = "World"
if str1 == str2:
    print("Strings are equal")
else:
    print("Strings are not equal")
```
### Finding Substrings
Finding the position of a substring within a string can be done using `find()`.
```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {
    string str = "Hello World";
    size_t pos = str.find("World");
    if (pos != string::npos) {
        cout << "Found 'World' at position: " << pos << endl;  // Output: Found 'World' at position: 6
    } else {
        cout << "'World' not found" << endl;
    }
    return 0;
}
```
```java
public class Main {
    public static void main(String[] args) {
        String str = "Hello World";
        int pos = str.indexOf("World");
        if (pos != -1) {
            System.out.println("Found 'World' at position: " + pos);  // Output: Found 'World' at position: 6
        } else {
            System.out.println("'World' not found");
        }
    }
}
```
```python
str = "Hello World"
pos = str.find("World")
if pos != -1:
    print(f"Found 'World' at position: {pos}")  # Output: Found 'World' at position: 6
else:
    print("'World' not found")
```
### Substring Extraction
Extracting a substring from a string can be done using `substr()`.
```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {
    string str = "Hello World";
    string substr = str.substr(6, 5);  // Extract "World"
    cout << substr << endl;  // Output: World
    return 0;
}
```
```java
public class Main {
    public static void main(String[] args) {
        String str = "Hello World";
        String substr = str.substring(6, 11);  // Extract "World"
        System.out.println(substr);  // Output: World
    }
}
```
```python
str = "Hello World"
substr = str[6:11]  # Extract "World"
print(substr)  # Output: World
```
### Replacing Substrings
Replacing part of a string with another string can be done using `replace()`.
```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {
    string str = "Hello World";
    str.replace(6, 5, "Universe");  // Replace "World" with "Universe"
    cout << str << endl;  // Output: Hello Universe
    return 0;
}
```
```java
public class Main {
    public static void main(String[] args) {
        String str = "Hello World";
        String newStr = str.substring(0, 6) + "Universe" + str.substring(11);
        System.out.println(newStr);  // Output: Hello Universe
    }
}
```
```python
str = "Hello World"
new_str = str[:6] + "Universe" + str[11:]
print(new_str)  # Output: Hello Universe
```
### Length
The length of a string can be obtained using `length()` or `size()`.
```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {
    string str = "Hello World";
    cout << "Length of string: " << str.length() << endl;  // Output: Length of string: 11
    return 0;
}
```
```java
public class Main {
    public static void main(String[] args) {
        String str = "Hello World";
        System.out.println("Length of string: " + str.length());  // Output: Length of string: 11
    }
}
```
```python
str = "Hello World"
print("Length of string:", len(str))  # Output: Length of string: 11
```
## Advanced String Operations
### Searching for Characters
```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {
    string str = "Hello World";
    size_t pos = str.find('o');
    if (pos != string::npos) {
        cout << "First occurrence of 'o' at position: " << pos << endl;  // Output: First occurrence of 'o' at position: 4
    } else {
        cout << "'o' not found" << endl;
    }
    return 0;
}
```
```java
public class Main {
    public static void main(String[] args) {
        String str = "Hello World";
        int pos = str.indexOf('o');
        if (pos != -1) {
            System.out.println("First occurrence of 'o' at position: " + pos);  // Output: First occurrence of 'o' at position: 4
        } else {
            System.out.println("'o' not found");
        }
    }
}
```
```python
str = "Hello World"
pos = str.find('o')
if pos != -1:
    print("First occurrence of 'o' at position:", pos)  # Output: First occurrence of 'o' at position: 4
else:
    print("'o' not found")
```
### String to Number Conversion
```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {
    string str = "12345";
    int num = stoi(str);  // Convert string to int
    cout << "Converted number: " << num << endl;  // Output: Converted number: 12345
    return 0;
}
```
```java
public class Main {
    public static void main(String[] args) {
        String str = "12345";
        int num = Integer.parseInt(str);  // Convert string to int
        System.out.println("Converted number: " + num);  // Output: Converted number: 12345
    }
}
```
```python
str = "12345"
num = int(str)  # Convert string to int
print("Converted number:", num)  # Output: Converted number: 12345
```
### Number to String Conversion
```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {
    int num = 12345;
    string str = to_string(num);  // Convert int to string
    cout << "Converted string: " << str << endl;  // Output: Converted string: 12345
    return 0;
}
```
```java
public class Main {
    public static void main(String[] args) {
        int num = 12345;
        String str = String.valueOf(num);  // Convert int to string
        System.out.println("Converted string: " + str);  // Output: Converted string: 12345
    }
}
```
```python
num = 12345
str = str(num)  # Convert int to string
print("Converted string:", str)  # Output: Converted string: 12345
```
## Applications of Strings
1. **Text Processing**: Manipulating and analyzing text data.
2. **User Input**: Storing and processing user inputs in applications.
3. **File I/O**: Reading and writing text data to and from files.
4. **Data Serialization**: Converting data to and from string representations for storage or transmission.

# Subsequence and Substring

## Subsequence
A subsequence of a string is a new string that is formed from the original string by deleting some (or none) of the characters without changing the relative order of the remaining characters. For example, "abc" is a subsequence of "abcdef", but "acd" is not.

## Substring
A substring of a string is a contiguous sequence of characters within the string. For example, "def" is a substring of "abcdef", but "acd" is not.

## Difference between Subsequence and Substring
- A substring is always contiguous, meaning the characters appear consecutively in the original string.
- A subsequence, on the other hand, may contain characters that are not consecutive in the original string.

## Subsequence and Substring Operations
1. **Finding Subsequences**: Generate all possible subsequences of a string.
2. **Finding Substrings**: Generate all possible substrings of a string.
3. **Checking Subsequence**: Determine if a string is a subsequence of another string.
4. **Checking Substring**: Determine if a string is a substring of another string.

## Example: Subsequence Generation
To generate all possible subsequences of a string, we can use recursion.
```cpp
#include <iostream>
#include <vector>

using namespace std;

void generateSubsequences(string str, int index, string current, vector<string>& subsequences) {
    if (index == str.length()) {
        subsequences.push_back(current);
        return;
    }
    // Include current character
    generateSubsequences(str, index + 1, current + str[index], subsequences);
    // Exclude current character
    generateSubsequences(str, index + 1, current, subsequences);
}

int main() {
    string str = "abc";
    vector<string> subsequences;
    generateSubsequences(str, 0, "", subsequences);
    cout << "Subsequences of 'abc':" << endl;
    for (string subsequence : subsequences) {
        cout << subsequence << endl;
    }
    return 0;
}
```
```java
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void generateSubsequences(String str, int index, String current, List<String> subsequences) {
        if (index == str.length()) {
            subsequences.add(current);
            return;
        }
        // Include current character
        generateSubsequences(str, index + 1, current + str.charAt(index), subsequences);
        // Exclude current character
        generateSubsequences(str, index + 1, current, subsequences);
    }

    public static void main(String[] args) {
        String str = "abc";
        List<String> subsequences = new ArrayList<>();
        generateSubsequences(str, 0, "", subsequences);
        System.out.println("Subsequences of 'abc':");
        for (String subsequence : subsequences) {
            System.out.println(subsequence);
        }
    }
}
```
```python
def generate_subsequences(string, index, current, subsequences):
    if index == len(string):
        subsequences.append(current)
        return
    # Include current character
    generate_subsequences(string, index + 1, current + string[index], subsequences)
    # Exclude current character
    generate_subsequences(string, index + 1, current, subsequences)

def main():
    string = "abc"
    subsequences = []
    generate_subsequences(string, 0, "", subsequences)
    print("Subsequences of 'abc':")
    for subsequence in subsequences:
        print(subsequence)

if __name__ == "__main__":
    main()
```
### Example: Substring Generation
To generate all possible substrings of a string, we can use nested loops.
```cpp
#include <iostream>
#include <vector>

using namespace std;

void generateSubstrings(string str, vector<string>& substrings) {
    for (int i = 0; i < str.length(); i++) {
        for (int j = i; j < str.length(); j++) {
            substrings.push_back(str.substr(i, j - i + 1));
        }
    }
}

int main() {
    string str = "abc";
    vector<string> substrings;
    generateSubstrings(str, substrings);
    cout << "Substrings of 'abc':" << endl;
    for (string substring : substrings) {
        cout << substring << endl;
    }
    return 0;
}
```
```java
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void generateSubstrings(String str, List<String> substrings) {
        for (int i = 0; i < str.length(); i++) {
            for (int j = i; j < str.length(); j++) {
                substrings.add(str.substring(i, j + 1));
            }
        }
    }

    public static void main(String[] args) {
        String str = "abc";
        List<String> substrings = new ArrayList<>();
        generateSubstrings(str, substrings);
        System.out.println("Substrings of 'abc':");
        for (String substring : substrings) {
            System.out.println(substring);
        }
    }
}
```
```python
def generate_substrings(string, substrings):
    for i in range(len(string)):
        for j in range(i, len(string)):
            substrings.append(string[i:j + 1])

def main():
    string = "abc"
    substrings = []
    generate_substrings(string, substrings)
    print("Substrings of 'abc':")
    for substring in substrings:
        print(substring)

if __name__ == "__main__":
    main()
```
### Checking Subsequence
To check if a string is a subsequence of another string, we can use two pointers to iterate through both strings.
```cpp
#include <iostream>

using namespace std;

bool isSubsequence(string s, string t) {
    int i = 0, j = 0;
    while (i < s.length() && j < t.length()) {
        if (s[i] == t[j]) {
            i++;
        }
        j++;
    }
    return i == s.length();
}

int main() {
    string s = "abc", t = "ahbgdc";
    if (isSubsequence(s, t)) {
        cout << s << " is a subsequence of " << t << endl;
    } else {
        cout << s << " is not a subsequence of " << t << endl;
    }
    return 0;
}
```
```java
public class Main {
    public static boolean isSubsequence(String s, String t) {
        int i = 0, j = 0;
        while (i < s.length() && j < t.length()) {
            if (s.charAt(i) == t.charAt(j)) {
                i++;
            }
            j++;
        }
        return i == s.length();
    }

    public static void main(String[] args) {
        String s = "abc", t = "ahbgdc";
        if (isSubsequence(s, t)) {
            System.out.println(s + " is a subsequence of " + t);
        } else {
            System.out.println(s + " is not a subsequence of " + t);
        }
    }
}
```
```python
def is_subsequence(s, t):
    i, j = 0, 0
    while i < len(s) and j < len(t):
        if s[i] == t[j]:
            i += 1
        j += 1
    return i == len(s)

def main():
    s, t = "abc", "ahbgdc"
    if is_subsequence(s, t):
        print(s + " is a subsequence of " + t)
    else:
        print(s + " is not a subsequence of " + t)

if __name__ == "__main__":
    main()
```
Checking Substring
To check if a string is a substring of another string, we can use the `find()` function.
```cpp
#include <iostream>

using namespace std;

bool isSubstring(string s, string t) {
    return t.find(s) != string::npos;
}

int main() {
    string s = "def", t = "abcdef";
    if (isSubstring(s, t)) {
        cout << s << " is a substring of " << t << endl;
    } else {
        cout << s << " is not a substring of " << t << endl;
    }
    return 0;
}
```
```java
public class Main {
    public static boolean isSubstring(String s, String t) {
        return t.contains(s);
    }

    public static void main(String[] args) {
        String s = "def", t = "abcdef";
        if (isSubstring(s, t)) {
            System.out.println(s + " is a substring of " + t);
        } else {
            System.out.println(s + " is not a substring of " + t);
        }
    }
}
```
```python
def is_substring(s, t):
    return s in t

def main():
    s, t = "def", "abcdef"
    if is_substring(s, t):
        print(s + " is a substring of " + t)
    else:
        print(s + " is not a substring of " + t)

if __name__ == "__main__":
    main()
```
# Reverse and Rotation in a String

## Reverse a String

### What is Reversing a String?
Reversing a string means changing the order of the characters so that the last character becomes the first, the second to last becomes the second, and so on until the first character becomes the last.

### Example
Original string: "hello"  
Reversed string: "olleh"

### C++ Code for Reversing a String
We can reverse a string using a loop to swap characters from the beginning and the end, moving towards the center.

```cpp
#include <iostream>
#include <string>

using namespace std;

string reverseString(string str) {
    int n = str.length();
    for (int i = 0; i < n / 2; i++) {
        swap(str[i], str[n - i - 1]);
    }
    return str;
}

int main() {
    string str = "hello";
    cout << "Original string: " << str << endl;
    cout << "Reversed string: " << reverseString(str) << endl;
    return 0;
}
```
```java
public class Main {
    public static String reverseString(String str) {
        return new StringBuilder(str).reverse().toString();
    }

    public static void main(String[] args) {
        String str = "hello";
        System.out.println("Original string: " + str);
        System.out.println("Reversed string: " + reverseString(str));
    }
}
```
```python
def reverse_string(s):
    return s[::-1]

def main():
    s = "hello"
    print("Original string:", s)
    print("Reversed string:", reverse_string(s))

if __name__ == "__main__":
    main()
```
## Rotate a String
### What is Rotating a String?
Rotating a string means shifting the characters of the string to the left or right by a certain number of positions. There are two types of rotations:

1. Left Rotation: Characters are shifted to the left.
2. Right Rotation: Characters are shifted to the right.
### Example
For a string "abcdef":

* Left rotation by 2 positions: "cdefab"
* Right rotation by 2 positions: "efabcd"
### Left Rotation in C++
Left rotation can be achieved by concatenating the substring from the rotation point to the end of the string with the substring from the beginning of the string to the rotation point.
```cpp
#include <iostream>
#include <string>

using namespace std;

string leftRotateString(string str, int d) {
    int n = str.length();
    d = d % n; // Handle cases where d > n
    return str.substr(d) + str.substr(0, d);
}

int main() {
    string str = "abcdef";
    int d = 2;
    cout << "Original string: " << str << endl;
    cout << "Left rotated string by " << d << " positions: " << leftRotateString(str, d) << endl;
    return 0;
}
```
```java
public class Main {
    public static String leftRotateString(String str, int d) {
        int n = str.length();
        d = d % n; // Handle cases where d > n
        return str.substring(d) + str.substring(0, d);
    }

    public static void main(String[] args) {
        String str = "abcdef";
        int d = 2;
        System.out.println("Original string: " + str);
        System.out.println("Left rotated string by " + d + " positions: " + leftRotateString(str, d));
    }
}
```
```python
def left_rotate_string(s, d):
    d = d % len(s)  # Handle cases where d > len(s)
    return s[d:] + s[:d]

def main():
    s = "abcdef"
    d = 2
    print("Original string:", s)
    print("Left rotated string by", d, "positions:", left_rotate_string(s, d))

if __name__ == "__main__":
    main()
```
### Right Rotation in C++
Right rotation can be achieved by concatenating the substring from the end of the string to the rotation point with the substring from the beginning of the string to the end of the string minus the rotation point.
```cpp
#include <iostream>
#include <string>

using namespace std;

string rightRotateString(string str, int d) {
    int n = str.length();
    d = d % n; // Handle cases where d > n
    return str.substr(n - d) + str.substr(0, n - d);
}

int main() {
    string str = "abcdef";
    int d = 2;
    cout << "Original string: " << str << endl;
    cout << "Right rotated string by " << d << " positions: " << rightRotateString(str, d) << endl;
    return 0;
}
```
### Applications of String Reversal and Rotation
1. **Palindrome Check**: Reversing a string can be used to check if the string is a palindrome.
2. **Data Encryption**: String rotations can be used in simple encryption algorithms.
3. **Text Processing**: Useful in various text processing applications where string manipulation is required.

# Binary String

## What is a Binary String?
A binary string is a sequence of characters that consists only of '0's and '1's. These strings are used extensively in computer science, particularly in contexts involving binary arithmetic, bit manipulation, and data representation.

## Need for Binary Strings
Binary strings are fundamental in computer science because they:
- Represent binary data and bit patterns.
- Are used in binary arithmetic and bitwise operations.
- Serve as a basis for encoding and data compression algorithms.

## Common Operations on Binary Strings
1. **Counting Ones and Zeros**
2. **Bitwise Operations**
3. **Binary to Decimal Conversion**
4. **Decimal to Binary Conversion**
5. **Finding Substrings**

### Counting Ones and Zeros
Counting the number of '1's and '0's in a binary string is a common operation.

#### C++ Code Example
```cpp
#include <iostream>
#include <string>

using namespace std;

pair<int, int> countOnesAndZeros(const string& binaryString) {
    int countOnes = 0, countZeros = 0;
    for (char ch : binaryString) {
        if (ch == '1') {
            countOnes++;
        } else if (ch == '0') {
            countZeros++;
        }
    }
    return make_pair(countOnes, countZeros);
}

int main() {
    string binaryString = "1101001";
    pair<int, int> counts = countOnesAndZeros(binaryString);
    cout << "Number of 1's: " << counts.first << endl;
    cout << "Number of 0's: " << counts.second << endl;
    return 0;
}
```
### Bitwise Operations
Bitwise operations are performed directly on the bits of binary strings.
### AND Operation
```cpp
#include <iostream>
#include <string>

using namespace std;

string bitwiseAND(const string& str1, const string& str2) {
    string result;
    int len = min(str1.length(), str2.length());
    for (int i = 0; i < len; i++) {
        result += (str1[i] == '1' && str2[i] == '1') ? '1' : '0';
    }
    return result;
}

int main() {
    string str1 = "1101";
    string str2 = "1011";
    cout << "Bitwise AND: " << bitwiseAND(str1, str2) << endl;  // Output: 1001
    return 0;
}
```
### OR Operation
```cpp
#include <iostream>
#include <string>

using namespace std;

string bitwiseOR(const string& str1, const string& str2) {
    string result;
    int len = min(str1.length(), str2.length());
    for (int i = 0; i < len; i++) {
        result += (str1[i] == '1' || str2[i] == '1') ? '1' : '0';
    }
    return result;
}

int main() {
    string str1 = "1101";
    string str2 = "1011";
    cout << "Bitwise OR: " << bitwiseOR(str1, str2) << endl;  // Output: 1111
    return 0;
}
```
### XOR Operation
```cpp 
#include <iostream>
#include <string>

using namespace std;

string bitwiseXOR(const string& str1, const string& str2) {
    string result;
    int len = min(str1.length(), str2.length());
    for (int i = 0; i < len; i++) {
        result += (str1[i] != str2[i]) ? '1' : '0';
    }
    return result;
}

int main() {
    string str1 = "1101";
    string str2 = "1011";
    cout << "Bitwise XOR: " << bitwiseXOR(str1, str2) << endl;  // Output: 0110
    return 0;
}
```
### Binary to Decimal Conversion
Converting a binary string to a decimal integer.
```cpp
#include <iostream>
#include <string>
#include <cmath>

using namespace std;

int binaryToDecimal(const string& binaryString) {
    int decimalValue = 0;
    int length = binaryString.length();
    for (int i = 0; i < length; i++) {
        if (binaryString[length - i - 1] == '1') {
            decimalValue += pow(2, i);
        }
    }
    return decimalValue;
}

int main() {
    string binaryString = "1101";
    cout << "Decimal value: " << binaryToDecimal(binaryString) << endl;  // Output: 13
    return 0;
}
```
### Decimal to Binary Conversion
Converting a decimal integer to a binary string.
```cpp
#include <iostream>
#include <string>

using namespace std;

string decimalToBinary(int decimalValue) {
    if (decimalValue == 0) return "0";
    string binaryString;
    while (decimalValue > 0) {
        binaryString = (decimalValue % 2 == 0 ? "0" : "1") + binaryString;
        decimalValue /= 2;
    }
    return binaryString;
}

int main() {
    int decimalValue = 13;
    cout << "Binary string: " << decimalToBinary(decimalValue) << endl;  // Output: 1101
    return 0;
}
```
### Finding Substrings in a Binary String
Finding all occurrences of a substring in a binary string.
```cpp
#include <iostream>
#include <string>
#include <vector>

using namespace std;

vector<int> findAllSubstrings(const string& str, const string& substr) {
    vector<int> positions;
    size_t pos = str.find(substr, 0);
    while (pos != string::npos) {
        positions.push_back(pos);
        pos = str.find(substr, pos + 1);
    }
    return positions;
}

int main() {
    string str = "110110011";
    string substr = "110";
    vector<int> positions = findAllSubstrings(str, substr);
    cout << "Positions of '" << substr << "': ";
    for (int pos : positions) {
        cout << pos << " ";
    }
    cout << endl;  // Output: Positions of '110': 0 3 
    return 0;
}
```
# Palindrome

## What is a Palindrome?
A palindrome is a sequence of characters that reads the same forward and backward. In other words, a palindrome remains unchanged when its characters are reversed.

### Examples
- "madam"
- "racecar"
- "level"
- "radar"

### Non-Examples
- "hello"
- "world"

## Types of Palindromes
1. **String Palindromes**: The entire string reads the same forward and backward.
2. **Number Palindromes**: The number reads the same forward and backward.
3. **Phrase Palindromes**: Phrases or sentences that read the same forward and backward, ignoring spaces, punctuation, and capitalization (e.g., "A man, a plan, a canal, Panama!").

## Checking if a String is a Palindrome
To determine if a string is a palindrome, we can compare characters from the beginning and end of the string moving towards the center. If all corresponding characters match, the string is a palindrome.

### C++ Code for Checking Palindrome
Here is a simple implementation to check if a string is a palindrome:

```cpp
#include <iostream>
#include <string>

using namespace std;

bool isPalindrome(const string& str) {
    int left = 0;
    int right = str.length() - 1;
    while (left < right) {
        if (str[left] != str[right]) {
            return false;
        }
        left++;
        right--;
    }
    return true;
}

int main() {
    string str = "racecar";
    if (isPalindrome(str)) {
        cout << str << " is a palindrome." << endl;
    } else {
        cout << str << " is not a palindrome." << endl;
    }
    return 0;
}
```
### C++ Code for Checking Number Palindrome
Here is an implementation to check if a number is a palindrome:
```cpp
#include <iostream>
#include <string>

using namespace std;

bool isPalindrome(int number) {
    string str = to_string(number);
    int left = 0;
    int right = str.length() - 1;
    while (left < right) {
        if (str[left] != str[right]) {
            return false;
        }
        left++;
        right--;
    }
    return true;
}

int main() {
    int number = 12321;
    if (isPalindrome(number)) {
        cout << number << " is a palindrome." << endl;
    } else {
        cout << number << " is not a palindrome." << endl;
    }
    return 0;
}
```
### Checking if a Phrase is a Palindrome
To check if a phrase is a palindrome, we need to ignore spaces, punctuation, and capitalization.
```cpp
#include <iostream>
#include <string>
#include <algorithm>

using namespace std;

bool isPalindromePhrase(const string& str) {
    string filteredStr;
    for (char ch : str) {
        if (isalnum(ch)) {
            filteredStr += tolower(ch);
        }
    }
    int left = 0;
    int right = filteredStr.length() - 1;
    while (left < right) {
        if (filteredStr[left] != filteredStr[right]) {
            return false;
        }
        left++;
        right--;
    }
    return true;
}

int main() {
    string phrase = "A man, a plan, a canal, Panama!";
    if (isPalindromePhrase(phrase)) {
        cout << "\"" << phrase << "\" is a palindrome." << endl;
    } else {
        cout << "\"" << phrase << "\" is not a palindrome." << endl;
    }
    return 0;
}
```
# Lexicographic Pattern

## What is Lexicographic Order?
Lexicographic order, also known as lexical order or dictionary order, is a generalization of the way words are alphabetically ordered in dictionaries. In lexicographic order, sequences are ordered in the same way as they would be if they were listed in a dictionary.

## Lexicographic Order Rules
1. **Character-by-Character Comparison**: Compare strings character by character from left to right.
2. **Shorter Prefix**: If one string is a prefix of another, the shorter string is considered smaller.
3. **ASCII Values**: Comparisons are based on the ASCII values of characters.

### Examples
- "apple" < "banana"
- "cat" < "catalog"
- "dog" < "dogs"
- "abc" < "abd"

## Generating Lexicographic Patterns
Generating permutations or combinations in lexicographic order can be useful in various applications, including algorithm design and combinatorial problems.

### Algorithm for Generating Next Lexicographic Permutation
To generate the next lexicographic permutation of a string or array:
1. Find the largest index `k` such that `str[k] < str[k + 1]`. If no such index exists, the permutation is the last permutation.
2. Find the largest index `l` greater than `k` such that `str[k] < str[l]`.
3. Swap the value of `str[k]` with that of `str[l]`.
4. Reverse the sequence from `str[k + 1]` to the end.

### C++ Code for Generating Next Lexicographic Permutation
Here is an implementation to find the next lexicographic permutation of a string:

```cpp
#include <iostream>
#include <algorithm>

using namespace std;

bool nextPermutation(string& str) {
    int n = str.length();
    int k = n - 2;
    while (k >= 0 && str[k] >= str[k + 1]) {
        k--;
    }
    if (k < 0) {
        return false;
    }
    int l = n - 1;
    while (str[k] >= str[l]) {
        l--;
    }
    swap(str[k], str[l]);
    reverse(str.begin() + k + 1, str.end());
    return true;
}

int main() {
    string str = "abc";
    cout << "Original string: " << str << endl;
    while (nextPermutation(str)) {
        cout << "Next permutation: " << str << endl;
    }
    return 0;
}
```
### Lexicographic Sorting
Sorting a collection of strings in lexicographic order.
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main() {
    vector<string> words = {"apple", "banana", "cat", "catalog", "dog", "dogs"};
    sort(words.begin(), words.end());
    cout << "Lexicographically sorted strings:" << endl;
    for (const string& word : words) {
        cout << word << endl;
    }
    return 0;
}
```
# Pattern Searching

## What is Pattern Searching?
Pattern searching is the process of finding a specific sequence of characters, known as a pattern, within a larger text. This is a common problem in computer science and is used in various applications such as text editing, search engines, DNA sequencing, and data mining.

## Common Pattern Searching Algorithms
1. **Naive Pattern Searching Algorithm**
2. **Knuth-Morris-Pratt (KMP) Algorithm**
3. **Rabin-Karp Algorithm**
4. **Boyer-Moore Algorithm**

### 1. Naive Pattern Searching Algorithm
The naive pattern searching algorithm checks for the pattern at every possible position in the text.

#### C++ Code for Naive Pattern Searching
```cpp
#include <iostream>
#include <string>

using namespace std;

void naivePatternSearch(const string& text, const string& pattern) {
    int textLen = text.length();
    int patternLen = pattern.length();

    for (int i = 0; i <= textLen - patternLen; i++) {
        int j;
        for (j = 0; j < patternLen; j++) {
            if (text[i + j] != pattern[j]) {
                break;
            }
        }
        if (j == patternLen) {
            cout << "Pattern found at index " << i << endl;
        }
    }
}

int main() {
    string text = "AABAACAADAABAAABAA";
    string pattern = "AABA";
    naivePatternSearch(text, pattern);
    return 0;
}
```
2. ### Knuth-Morris-Pratt (KMP) Algorithm
The KMP algorithm improves the naive algorithm by avoiding redundant comparisons. It preprocesses the pattern to create a longest prefix suffix (LPS) array to skip characters.
```cpp
#include <iostream>
#include <vector>
#include <string>

using namespace std;

void computeLPSArray(const string& pattern, vector<int>& lps) {
    int length = 0;
    lps[0] = 0;
    int i = 1;
    while (i < pattern.length()) {
        if (pattern[i] == pattern[length]) {
            length++;
            lps[i] = length;
            i++;
        } else {
            if (length != 0) {
                length = lps[length - 1];
            } else {
                lps[i] = 0;
                i++;
            }
        }
    }
}

void KMPSearch(const string& text, const string& pattern) {
    int textLen = text.length();
    int patternLen = pattern.length();
    vector<int> lps(patternLen);

    computeLPSArray(pattern, lps);

    int i = 0;
    int j = 0;
    while (i < textLen) {
        if (pattern[j] == text[i]) {
            i++;
            j++;
        }
        if (j == patternLen) {
            cout << "Pattern found at index " << (i - j) << endl;
            j = lps[j - 1];
        } else if (i < textLen && pattern[j] != text[i]) {
            if (j != 0) {
                j = lps[j - 1];
            } else {
                i++;
            }
        }
    }
}

int main() {
    string text = "AABAACAADAABAAABAA";
    string pattern = "AABA";
    KMPSearch(text, pattern);
    return 0;
}
```
3. ### Rabin-Karp Algorithm
The Rabin-Karp algorithm uses hashing to find any one of a set of pattern strings in a text. It compares the hash value of the pattern with the hash values of substrings of the text.
```cpp
#include <iostream>
#include <string>

using namespace std;

#define d 256
#define q 101

void RabinKarpSearch(const string& text, const string& pattern) {
    int textLen = text.length();
    int patternLen = pattern.length();
    int i, j;
    int patternHash = 0;
    int textHash = 0;
    int h = 1;

    for (i = 0; i < patternLen - 1; i++) {
        h = (h * d) % q;
    }

    for (i = 0; i < patternLen; i++) {
        patternHash = (d * patternHash + pattern[i]) % q;
        textHash = (d * textHash + text[i]) % q;
    }

    for (i = 0; i <= textLen - patternLen; i++) {
        if (patternHash == textHash) {
            for (j = 0; j < patternLen; j++) {
                if (text[i + j] != pattern[j]) {
                    break;
                }
            }
            if (j == patternLen) {
                cout << "Pattern found at index " << i << endl;
            }
        }
        if (i < textLen - patternLen) {
            textHash = (d * (textHash - text[i] * h) + text[i + patternLen]) % q;
            if (textHash < 0) {
                textHash = (textHash + q);
            }
        }
    }
}

int main() {
    string text = "AABAACAADAABAAABAA";
    string pattern = "AABA";
    RabinKarpSearch(text, pattern);
    return 0;
}
```
4. ### Boyer-Moore Algorithm
The Boyer-Moore algorithm preprocesses the pattern and uses two heuristic methods - the bad character heuristic and the good suffix heuristic - to skip sections of the text.
```cpp
#include <iostream>
#include <string>
#include <vector>

using namespace std;

#define NO_OF_CHARS 256

void badCharHeuristic(const string& str, int size, vector<int>& badChar) {
    for (int i = 0; i < NO_OF_CHARS; i++) {
        badChar[i] = -1;
    }
    for (int i = 0; i < size; i++) {
        badChar[(int)str[i]] = i;
    }
}

void BoyerMooreSearch(const string& text, const string& pattern) {
    int textLen = text.length();
    int patternLen = pattern.length();
    vector<int> badChar(NO_OF_CHARS);

    badCharHeuristic(pattern, patternLen, badChar);

    int shift = 0;
    while (shift <= (textLen - patternLen)) {
        int j = patternLen - 1;

        while (j >= 0 && pattern[j] == text[shift + j]) {
            j--;
        }
        if (j < 0) {
            cout << "Pattern found at index " << shift << endl;
            shift += (shift + patternLen < textLen) ? patternLen - badChar[text[shift + patternLen]] : 1;
        } else {
            shift += max(1, j - badChar[text[shift + j]]);
        }
    }
}

int main() {
    string text = "AABAACAADAABAAABAA";
    string pattern = "AABA";
    BoyerMooreSearch(text, pattern);
    return 0;
}
```
