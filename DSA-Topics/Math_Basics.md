---
title: 'Article on DSA Topic: Mathematics Basic'
description: In this article, we delve into the foundational principles of mathematics in the context of Data Structures and Algorithms (DSA).
date: 2024-05-17
author: Nehal Fathema
tags:
    - Data Structures
    - Algorithms
    - Mathematics
---
# Mathematics Basic

# GCD and HCF (Euclidean Algorithm)

## Introduction
GCD (Greatest Common Divisor) or HCF (Highest Common Factor) of two numbers is the largest number that divides both of them. The Euclidean Algorithm is a method for finding the GCD of two numbers.

## Algorithm
The Euclidean Algorithm is based on the principle that the GCD of two numbers does not change if the larger number is replaced by its difference with the smaller number. This process is repeated until the two numbers become equal, which is the GCD of the original two numbers.

### Steps:
1. If a = 0, then GCD(a, b) = b. Similarly, if b = 0, then GCD(a, b) = a.
2. If a > b, replace a with a - b.
3. If b > a, replace b with b - a.
4. Repeat steps 2 and 3 until a = b.
5. The value of a (or b) at this point is the GCD of the original two numbers.

## Example
Let's find the GCD of 48 and 18 using the Euclidean Algorithm:

1. Initial values: a = 48, b = 18
2. Since 48 > 18, replace a with a - b: a = 48 - 18 = 30, b = 18
3. Since 30 > 18, replace a with a - b: a = 30 - 18 = 12, b = 18
4. Since 18 > 12, replace b with b - a: a = 12, b = 18 - 12 = 6
5. Since 12 > 6, replace a with a - b: a = 12 - 6 = 6, b = 6
6. Since a = b, the GCD is 6.

## Code Implementation (Python)
```python
def gcd(a, b):
    while b:
        a, b = b, a % b
    return a

# Example usage:
num1 = 48
num2 = 18
print("GCD of", num1, "and", num2, "is", gcd(num1, num2))
```
## Code Implementation (CPP)
```cpp
#include <iostream>

using namespace std;

int gcd(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int main() {
    int num1 = 48, num2 = 18;
    cout << "GCD of " << num1 << " and " << num2 << " is: " << gcd(num1,num2) << endl;
    return 0;
}

```
## Code Implementation (Java)
```java
public class Main {
    public static int gcd(int a, int b) {
        while (b != 0) {
            int temp = b;
            b = a % b;
            a = temp;
        }
        return a;
    }

    public static void main(String[] args) {
        int num1 = 48, num2 = 18;
        System.out.println("GCD of " + num1 + " and " + num2 + " is: " + gcd(num1, num2));
    }
}
```
# Divisors of a Number

## Introduction
The divisors of a number are the numbers that divide the given number evenly, leaving no remainder. Every number has at least two divisors: 1 and itself. Finding the divisors of a number is a fundamental operation in number theory and has applications in various mathematical and computational problems.

## Algorithm
The algorithm to find the divisors of a number involves iterating through all possible divisors from 1 to the square root of the number and checking if each divisor divides the number evenly. If it does, then it is a divisor. Divisors occur in pairs: if \( d \) is a divisor of \( n \), then \( n/d \) is also a divisor.

### Steps:
1. Iterate from \( i = 1 \) to \( \sqrt{n} \).
2. For each \( i \), check if \( i \) divides \( n \) evenly.
3. If it does, \( i \) is a divisor. Also, if \( i $\neq$ \sqrt{n} \), then \( n/i \) is a divisor.

## Example
Let's find the divisors of 36:

1. Iterate from \( i = 1 \) to \( \sqrt{36} = 6 \).
2. Check for each \( i \) if it divides 36 evenly:
   - \( i = 1 \): \( 36 \% 1 = 0 \) (divides evenly), divisors: 1, 36
   - \( i = 2 \): \( 36 \% 2 = 0 \) (divides evenly), divisors: 2, 18
   - \( i = 3 \): \( 36 \% 3 = 0 \) (divides evenly), divisors: 3, 12
   - \( i = 4 \): \( 36 \% 4 = 0 \) (divides evenly), divisors: 4, 9
   - \( i = 5 \): \( 36 \% 5 \neq 0 \) (does not divide evenly)
   - \( i = 6 \): \( 36 \% 6 = 0 \) (divides evenly), divisors: 6

So, the divisors of 36 are: 1, 2, 3, 4, 6, 9, 12, 18, 36.

## Code Implementation (Python)
```python
import math

def find_divisors(n):
    divisors = []
    for i in range(1, int(math.sqrt(n)) + 1):
        if n % i == 0:
            divisors.append(i)
            if i != n // i:
                divisors.append(n // i)
    return divisors

# Example usage:
number = 36
print("Divisors of", number, "are:", find_divisors(number))
```
## Code Implementation (CPP)
```cpp
#include <iostream>
#include <vector>
#include <cmath>

using namespace std;

vector<int> findDivisors(int n) {
    vector<int> divisors;
    for (int i = 1; i <= sqrt(n); ++i) {
        if (n % i == 0) {
            divisors.push_back(i);
            if (i != n / i) {
                divisors.push_back(n / i);
            }
        }
    }
    return divisors;
}

int main() {
    int number = 36;
    vector<int> divisors = findDivisors(number);
    cout << "Divisors of " << number << " are: ";
    for (int divisor : divisors) {
        cout << divisor << " ";
    }
    cout << endl;
    return 0;
}
```
## Code Implementation (Java)
```java
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static List<Integer> findDivisors(int n) {
        List<Integer> divisors = new ArrayList<>();
        for (int i = 1; i <= Math.sqrt(n); ++i) {
            if (n % i == 0) {
                divisors.add(i);
                if (i != n / i) {
                    divisors.add(n / i);
                }
            }
        }
        return divisors;
    }

    public static void main(String[] args) {
        int number = 36;
        List<Integer> divisors = findDivisors(number);
        System.out.print("Divisors of " + number + " are: ");
        for (int divisor : divisors) {
            System.out.print(divisor + " ");
        }
        System.out.println();
    }
}
```
# Prime Numbers using Sieve of Eratosthenes

## Introduction
The Sieve of Eratosthenes is an ancient algorithm used to find all prime numbers up to a specified integer. It efficiently identifies prime numbers by iteratively marking the multiples of each prime starting from 2. The remaining unmarked numbers are primes.

## Algorithm
The Sieve of Eratosthenes algorithm works as follows:

1. Create a list of consecutive integers from 2 through n: \( (2, 3, 4, ..., n) \).
2. Start with the first prime number, \( p = 2 \).
3. Starting from \( p^2 \), mark all multiples of \( p \) as non-prime.
4. Find the next number in the list that is not marked and set it as the new value of \( p \).
5. Repeat steps 3 and 4 until \( p^2 \) exceeds \( n \).
6. All remaining unmarked numbers in the list are prime.

## Example
Let's find all prime numbers up to 30 using the Sieve of Eratosthenes algorithm:

1. Start with a list of integers from 2 to 30.
2. Start with the first prime number, \( p = 2 \).
3. Mark all multiples of 2 as non-prime: \( (4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26, 28, 30) \).
4. Find the next unmarked number, which is 3. So, 3 is a prime number.
5. Mark all multiples of 3 as non-prime: \( (9, 15, 21, 27) \).
6. Find the next unmarked number, which is 5. So, 5 is a prime number.
7. Mark all multiples of 5 as non-prime: \( (25) \).
8. The remaining unmarked numbers are primes: \( (2, 3, 5, 7, 11, 13, 17, 19, 23, 29) \).

## Code Implementation (Python)
```python
def sieve_of_eratosthenes(n):
    primes = [True] * (n + 1)
    primes[0] = primes[1] = False
    p = 2
    while p * p <= n:
        if primes[p]:
            for i in range(p * p, n + 1, p):
                primes[i] = False
        p += 1
    return [i for i in range(n + 1) if primes[i]]

# Example usage:
limit = 30
print("Prime numbers up to", limit, "are:", sieve_of_eratosthenes(limit))
```
## Code Implementation (CPP)
```cpp
#include <iostream>
#include <vector>

using namespace std;

vector<int> sieveOfEratosthenes(int n) {
    vector<bool> isPrime(n + 1, true);
    vector<int> primes;
    isPrime[0] = isPrime[1] = false;
    for (int p = 2; p * p <= n; ++p) {
        if (isPrime[p]) {
            for (int i = p * p; i <= n; i += p) {
                isPrime[i] = false;
            }
        }
    }
    for (int i = 2; i <= n; ++i) {
        if (isPrime[i]) {
            primes.push_back(i);
        }
    }
    return primes;
}

int main() {
    int limit = 30;
    vector<int> primeNumbers = sieveOfEratosthenes(limit);
    cout << "Prime numbers up to " << limit << " are: ";
    for (int prime : primeNumbers) {
        cout << prime << " ";
    }
    cout << endl;
    return 0;
}
```
## Code Implementation (Java)
```java
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static List<Integer> sieveOfEratosthenes(int n) {
        boolean[] isPrime = new boolean[n + 1];
        for (int i = 2; i <= n; ++i) {
            isPrime[i] = true;
        }
        List<Integer> primes = new ArrayList<>();
        isPrime[0] = isPrime[1] = false;
        for (int p = 2; p * p <= n; ++p) {
            if (isPrime[p]) {
                for (int i = p * p; i <= n; i += p) {
                    isPrime[i] = false;
                }
            }
        }
        for (int i = 2; i <= n; ++i) {
            if (isPrime[i]) {
                primes.add(i);
            }
        }
        return primes;
    }

    public static void main(String[] args) {
        int limit = 30;
        List<Integer> primeNumbers = sieveOfEratosthenes(limit);
        System.out.print("Prime numbers up to " + limit + " are: ");
        for (int prime : primeNumbers) {
            System.out.print(prime + " ");
        }
        System.out.println();
    }
}
```
# Square Root

## Introduction
The square root of a number is a value that, when multiplied by itself, gives the original number. It is denoted by the symbol \( \sqrt{} \). Finding the square root of a number is a common operation in mathematics and has applications in various fields, including geometry, physics, and computer science.

## Methods for Finding Square Root
There are several methods for finding the square root of a number. Some of the common methods include:

1. **Guess and Check Method**: This method involves guessing a number and checking if its square is close to the original number.
2. **Babylonian Method (or Heron's Method)**: It is an iterative method that continuously improves the guess until it converges to the square root.
3. **Newton's Method**: It is an iterative method that uses the formula \( x_{n+1} = \frac{1}{2} (x_n + \frac{a}{x_n}) \), where \( x_n \) is the current guess and \( a \) is the original number.
4. **Using Exponentiation**: The square root of a number can be found by raising the number to the power of \( \frac{1}{2} \).

## Example
Let's find the square root of 25 using different methods:

1. **Guess and Check Method**: Start with a guess, say 5. \( 5^2 = 25 \), so the guess is correct.
2. **Babylonian Method**: Start with an initial guess \( x_0 = 5 \).
   - Iteration 1: \( x_1 = \frac{1}{2} (5 + \frac{25}{5}) = \frac{1}{2} (5 + 5) = \frac{10}{2} = 5 \)
   - The guess is unchanged, so the square root is 5.
3. **Newton's Method**: Start with an initial guess \( x_0 = 5 \).
   - Iteration 1: \( x_1 = \frac{1}{2} (5 + \frac{25}{5}) = \frac{1}{2} (5 + 5) = \frac{10}{2} = 5 \)
   - The guess is unchanged, so the square root is 5.
4. **Using Exponentiation**: \( \sqrt{25} = 25^{\frac{1}{2}} = 5 \).

## Code Implementation (Python)
```python
def square_root(n):
    return n ** 0.5

# Example usage:
number = 25
print("Square root of", number, "is:", square_root(number))
```
## Code Implementation (CPP)
```cpp
#include <iostream>
#include <cmath>

using namespace std;

double squareRoot(double n) {
    return sqrt(n);
}

int main() {
    double number = 25;
    cout << "Square root of " << number << " is: " << squareRoot(number) << endl;
    return 0;
}
```
## Code Implementation (Java)
```java
public class Main {
    public static double squareRoot(double n) {
        return Math.sqrt(n);
    }

    public static void main(String[] args) {
        double number = 25;
        System.out.println("Square root of " + number + " is: " + squareRoot(number));
    }
}
```
# Modular Arithmetic

## Introduction
Modular arithmetic is a branch of arithmetic that deals with operations on numbers that have a remainder when divided by a fixed modulus. It is used extensively in number theory, cryptography, and computer science. In modular arithmetic, all operations are performed modulo \( m \), where \( m \) is the modulus.

## Operations in Modular Arithmetic
The main operations in modular arithmetic include addition, subtraction, multiplication, and exponentiation. These operations are performed modulo \( m \).

### Addition:
\[ (a + b) \mod m = (a \mod m + b \mod m) \mod m \]

### Subtraction:
\[ (a - b) \mod m = (a \mod m - b \mod m) \mod m \]

### Multiplication:
\[ (a \times b) \mod m = (a \mod m \times b \mod m) \mod m \]

### Exponentiation:
\[ (a^b) \mod m = ((a \mod m)^b) \mod m \]

## Properties of Modular Arithmetic
1. **Closure**: The result of any arithmetic operation in modular arithmetic remains within the set of residues modulo \( m \).
2. **Associativity**: Addition and multiplication are associative in modular arithmetic.
3. **Distributivity**: Addition and multiplication are distributive over each other in modular arithmetic.
4. **Identity Element**: The identity element for addition modulo \( m \) is 0, and for multiplication modulo \( m \) is 1.
5. **Inverse Element**: Every non-zero element in modular arithmetic has a unique multiplicative inverse.

## Example
Let's perform some modular arithmetic operations with \( m = 7 \):

1. Addition: \( (5 + 3) \mod 7 = (5 \mod 7 + 3 \mod 7) \mod 7 = 1 \)
2. Subtraction: \( (5 - 3) \mod 7 = (5 \mod 7 - 3 \mod 7) \mod 7 = 2 \)
3. Multiplication: \( (5 \times 3) \mod 7 = (5 \mod 7 \times 3 \mod 7) \mod 7 = 1 \)
4. Exponentiation: \( (5^3) \mod 7 = ((5 \mod 7)^3) \mod 7 = 6 \)

## Code Implementation (Python)
```python
def mod_addition(a, b, m):
    return (a + b) % m

def mod_subtraction(a, b, m):
    return (a - b) % m

def mod_multiplication(a, b, m):
    return (a * b) % m

def mod_exponentiation(a, b, m):
    return pow(a % m, b, m)

# Example usage:
a = 5
b = 3
m = 7
print("Modular addition:", mod_addition(a, b, m))
print("Modular subtraction:", mod_subtraction(a, b, m))
print("Modular multiplication:", mod_multiplication(a, b, m))
print("Modular exponentiation:", mod_exponentiation(a, b, m))
```
## Code Implementation (CPP)
```cpp
#include <iostream>

using namespace std;

int modAddition(int a, int b, int m) {
    return (a % m + b % m) % m;
}

int modSubtraction(int a, int b, int m) {
    return (a % m - b % m + m) % m;
}

int modMultiplication(int a, int b, int m) {
    return (a % m * b % m) % m;
}

int modExponentiation(int a, int b, int m) {
    int result = 1;
    a = a % m;
    while (b > 0) {
        if (b % 2 == 1)
            result = (result * a) % m;
        b /= 2;
        a = (a * a) % m;
    }
    return result;
}

int main() {
    int a = 5, b = 3, m = 7;
    cout << "Modular addition: " << modAddition(a, b, m) << endl;
    cout << "Modular subtraction: " << modSubtraction(a, b, m) << endl;
    cout << "Modular multiplication: " << modMultiplication(a, b, m) << endl;
    cout << "Modular exponentiation: " << modExponentiation(a, b, m) << endl;
    return 0;
}
```
## Code Implementation (Java)
```java
public class Main {
    public static int modAddition(int a, int b, int m) {
        return (a % m + b % m) % m;
    }

    public static int modSubtraction(int a, int b, int m) {
        return (a % m - b % m + m) % m;
    }

    public static int modMultiplication(int a, int b, int m) {
        return (a % m * b % m) % m;
    }

    public static int modExponentiation(int a, int b, int m) {
        int result = 1;
        a = a % m;
        while (b > 0) {
            if (b % 2 == 1)
                result = (result * a) % m;
            b /= 2;
            a = (a * a) % m;
        }
        return result;
    }

    public static void main(String[] args) {
        int a = 5, b = 3, m = 7;
        System.out.println("Modular addition: " + modAddition(a, b, m));
        System.out.println("Modular subtraction: " + modSubtraction(a, b, m));
        System.out.println("Modular multiplication: " + modMultiplication(a, b, m));
        System.out.println("Modular exponentiation: " + modExponentiation(a, b, m));
    }
}
```

# Fast Power-Exponentiation by Squaring

## Introduction
Fast power-exponentiation by squaring is an algorithm used to efficiently compute the exponentiation of a number to a large power. It reduces the number of multiplications required by utilizing the properties of exponentiation and recursion. This method is particularly useful in situations where the power is large and performance is critical.

## Algorithm
The fast power-exponentiation by squaring algorithm works as follows:

1. If the exponent \( b \) is 0, return 1.
2. If the exponent \( b \) is 1, return the base \( a \).
3. If the exponent \( b \) is even, compute \( (a^{b/2})^2 \).
4. If the exponent \( b \) is odd, compute \( a \times (a^{(b-1)/2})^2 \).
5. Return the result.

## Example
Let's compute \( 3^{13} \) using fast power-exponentiation by squaring:

1. \( 13 \) is odd, so we compute \( 3 \times (3^{(13-1)/2})^2 \).
2. \( (13-1)/2 = 6 \), so we compute \( 3^6 \) recursively.
3. \( 6 \) is even, so we compute \( (3^{6/2})^2 \).
4. \( 3^3 \) is computed recursively, which is odd, so we compute \( 3 \times (3^{(3-1)/2})^2 \).
5. \( (3-1)/2 = 1 \), so we compute \( 3^1 \) recursively, which is the base case.
6. We return \( 3 \) to the power of \( 1 \), which is \( 3 \).
7. Back to step 4, we compute \( 3 \times (3^1)^2 = 3 \times 3^2 = 3 \times 9 = 27 \).
8. Back to step 2, we compute \( 3 \times (27)^2 = 3 \times 729 = 2187 \).

So, \( 3^{13} = 2187 \).

## Code Implementation (Python)
```python
def fast_power(a, b):
    if b == 0:
        return 1
    elif b == 1:
        return a
    elif b % 2 == 0:
        return fast_power(a, b // 2) ** 2
    else:
        return a * fast_power(a, (b - 1) // 2) ** 2

# Example usage:
base = 3
exponent = 13
print(base, "raised to the power of", exponent, "is:", fast_power(base, exponent))
```
## Code Implementation (CPP)
```cpp
#include <iostream>

using namespace std;

int fastPower(int a, int b) {
    if (b == 0)
        return 1;
    else if (b == 1)
        return a;
    else if (b % 2 == 0) {
        int temp = fastPower(a, b / 2);
        return temp * temp;
    } else {
        int temp = fastPower(a, (b - 1) / 2);
        return a * temp * temp;
    }
}

int main() {
    int base = 3, exponent = 13;
    cout << base << " raised to the power of " << exponent << " is: " << fastPower(base, exponent) << endl;
    return 0;
}
```
## Code Implementation (Java)
```java
public class Main {
    public static int fastPower(int a, int b) {
        if (b == 0)
            return 1;
        else if (b == 1)
            return a;
        else if (b % 2 == 0) {
            int temp = fastPower(a, b / 2);
            return temp * temp;
        } else {
            int temp = fastPower(a, (b - 1) / 2);
            return a * temp * temp;
        }
    }

    public static void main(String[] args) {
        int base = 3, exponent = 13;
        System.out.println(base + " raised to the power of " + exponent + " is: " + fastPower(base, exponent));
    }
}
```
# Factorial of a Number

## Introduction
The factorial of a non-negative integer \( n \) is the product of all positive integers less than or equal to \( n \). It is denoted by \( n! \). Factorial is a fundamental operation in combinatorics, probability, and various mathematical calculations.

## Algorithm
The factorial of a number \( n \) can be computed using a recursive or iterative approach:

### Recursive Algorithm:
1. If \( n \) is 0 or 1, return 1.
2. Otherwise, return \( n \times \text{factorial}(n - 1) \).

### Iterative Algorithm:
1. Initialize a variable \( \text{result} \) to 1.
2. Iterate from 1 to \( n \), multiplying \( \text{result} \) by the current number in each iteration.
3. After the loop, \( \text{result} \) will hold the factorial of \( n \).

## Example
Let's calculate the factorial of 5 using both recursive and iterative approaches:

1. **Recursive Algorithm**:
   - \( \text{factorial}(5) = 5 \times \text{factorial}(4) \)
   - \( = 5 \times 4 \times \text{factorial}(3) \)
   - \( = 5 \times 4 \times 3 \times \text{factorial}(2) \)
   - \( = 5 \times 4 \times 3 \times 2 \times \text{factorial}(1) \)
   - \( = 5 \times 4 \times 3 \times 2 \times 1 \)
   - \( = 120 \)

2. **Iterative Algorithm**:
   - Initialize \( \text{result} = 1 \).
   - Iterate from 1 to 5:
     - \( \text{result} = \text{result} \times \text{current number} \).
   - After the loop, \( \text{result} = 120 \).

## Code Implementation (Python)
```python
def factorial_recursive(n):
    if n == 0 or n == 1:
        return 1
    else:
        return n * factorial_recursive(n - 1)

def factorial_iterative(n):
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result

# Example usage:
number = 5
print("Factorial of", number, "using recursive approach:", factorial_recursive(number))
print("Factorial of", number, "using iterative approach:", factorial_iterative(number))
```
## Code Implementation (CPP)
```cpp
#include <iostream>

using namespace std;

// Recursive function to calculate factorial
int factorialRecursive(int n) {
    if (n == 0 || n == 1)
        return 1;
    else
        return n * factorialRecursive(n - 1);
}

// Iterative function to calculate factorial
int factorialIterative(int n) {
    int result = 1;
    for (int i = 1; i <= n; ++i) {
        result *= i;
    }
    return result;
}

int main() {
    int number = 5;
    cout << "Factorial of " << number << " using recursive approach: " << factorialRecursive(number) << endl;
    cout << "Factorial of " << number << " using iterative approach: " << factorialIterative(number) << endl;
    return 0;
}
```
## Code Implementation (Java)
```java
public class Main {
    // Recursive method to calculate factorial
    public static int factorialRecursive(int n) {
        if (n == 0 || n == 1)
            return 1;
        else
            return n * factorialRecursive(n - 1);
    }

    // Iterative method to calculate factorial
    public static int factorialIterative(int n) {
        int result = 1;
        for (int i = 1; i <= n; ++i) {
            result *= i;
        }
        return result;
    }

    public static void main(String[] args) {
        int number = 5;
        System.out.println("Factorial of " + number + " using recursive approach: " + factorialRecursive(number));
        System.out.println("Factorial of " + number + " using iterative approach: " + factorialIterative(number));
    }
}
```
# Fibonacci Number

## Introduction
The Fibonacci sequence is a series of numbers in which each number is the sum of the two preceding ones, usually starting with 0 and 1. The sequence begins: 0, 1, 1, 2, 3, 5, 8, 13, 21, ...

## Algorithm
The Fibonacci sequence can be computed using either a recursive or iterative approach:

### Recursive Algorithm:
1. If \( n \) is 0 or 1, return \( n \).
2. Otherwise, return \( \text{fibonacci}(n-1) + \text{fibonacci}(n-2) \).

### Iterative Algorithm:
1. Initialize variables \( a \) and \( b \) to 0 and 1, respectively.
2. Iterate \( n-1 \) times:
   - Update \( a \) and \( b \) to be \( b \) and \( a + b \), respectively.
3. Return \( b \), which holds the \( n \)-th Fibonacci number.

## Example
Let's calculate the 8th Fibonacci number using both recursive and iterative approaches:

1. **Recursive Algorithm**:
   - \( \text{fibonacci}(8) = \text{fibonacci}(7) + \text{fibonacci}(6) \)
   - \( = (\text{fibonacci}(6) + \text{fibonacci}(5)) + (\text{fibonacci}(5) + \text{fibonacci}(4)) \)
   - \( = ((\text{fibonacci}(5) + \text{fibonacci}(4)) + (\text{fibonacci}(4) + \text{fibonacci}(3))) + ((\text{fibonacci}(4) + \text{fibonacci}(3)) + (\text{fibonacci}(3) + \text{fibonacci}(2))) \)
   - \( = (((\text{fibonacci}(4) + \text{fibonacci}(3)) + (\text{fibonacci}(3) + \text{fibonacci}(2))) + ((\text{fibonacci}(3) + \text{fibonacci}(2)) + (\text{fibonacci}(2) + \text{fibonacci}(1)))) + (((\text{fibonacci}(3) + \text{fibonacci}(2)) + (\text{fibonacci}(2) + \text{fibonacci}(1))) + ((\text{fibonacci}(2) + \text{fibonacci}(1)) + (\text{fibonacci}(1) + \text{fibonacci}(0))))
   - \( = (((3 + 2) + (2 + 1)) + ((2 + 1) + 1)) + (((2 + 1) + 1) + (1 + 1)) \)
   - \( = (5 + 3) + (3 + 2) \)
   - \( = 8 \)

2. **Iterative Algorithm**:
   - Initialize \( a = 0 \) and \( b = 1 \).
   - First iteration: \( a = 1 \) and \( b = 1 \).
   - Second iteration: \( a = 1 \) and \( b = 2 \).
   - Third iteration: \( a = 2 \) and \( b = 3 \).
   - Fourth iteration: \( a = 3 \) and \( b = 5 \).
   - Fifth iteration: \( a = 5 \) and \( b = 8 \).
   - Return \( b = 8 \).

## Code Implementation (Python)
```python
def fibonacci_recursive(n):
    if n == 0 or n == 1:
        return n
    else:
        return fibonacci_recursive(n - 1) + fibonacci_recursive(n - 2)

def fibonacci_iterative(n):
    a, b = 0, 1
    for _ in range(n - 1):
        a, b = b, a + b
    return b

# Example usage:
number = 8
print("8th Fibonacci number using recursive approach:", fibonacci_recursive(number))
print("8th Fibonacci number using iterative approach:", fibonacci_iterative(number))
```
## Code Implementation (CPP)
```cpp
#include <iostream>

using namespace std;

// Recursive function to calculate the Fibonacci number
int fibonacciRecursive(int n) {
    if (n == 0 || n == 1)
        return n;
    else
        return fibonacciRecursive(n - 1) + fibonacciRecursive(n - 2);
}

// Iterative function to calculate the Fibonacci number
int fibonacciIterative(int n) {
    int a = 0, b = 1;
    for (int i = 2; i <= n; ++i) {
        int temp = b;
        b = a + b;
        a = temp;
    }
    return b;
}

int main() {
    int number = 8;
    cout << "8th Fibonacci number using recursive approach: " << fibonacciRecursive(number) << endl;
    cout << "8th Fibonacci number using iterative approach: " << fibonacciIterative(number) << endl;
    return 0;
}
```
## Code Implementation (CPP)
```cpp
#include <iostream>

using namespace std;

// Recursive function to calculate the Fibonacci number
int fibonacciRecursive(int n) {
    if (n == 0 || n == 1)
        return n;
    else
        return fibonacciRecursive(n - 1) + fibonacciRecursive(n - 2);
}

// Iterative function to calculate the Fibonacci number
int fibonacciIterative(int n) {
    int a = 0, b = 1;
    for (int i = 2; i <= n; ++i) {
        int temp = b;
        b = a + b;
        a = temp;
    }
    return b;
}

int main() {
    int number = 8;
    cout << "8th Fibonacci number using recursive approach: " << fibonacciRecursive(number) << endl;
    cout << "8th Fibonacci number using iterative approach: " << fibonacciIterative(number) << endl;
    return 0;
}
```
## Code Implementation (Java)
```java
public class Main {
    // Recursive method to calculate the Fibonacci number
    public static int fibonacciRecursive(int n) {
        if (n == 0 || n == 1)
            return n;
        else
            return fibonacciRecursive(n - 1) + fibonacciRecursive(n - 2);
    }

    // Iterative method to calculate the Fibonacci number
    public static int fibonacciIterative(int n) {
        int a = 0, b = 1;
        for (int i = 2; i <= n; ++i) {
            int temp = b;
            b = a + b;
            a = temp;
        }
        return b;
    }

    public static void main(String[] args) {
        int number = 8;
        System.out.println("8th Fibonacci number using recursive approach: " + fibonacciRecursive(number));
        System.out.println("8th Fibonacci number using iterative approach: " + fibonacciIterative(number));
    }
}
```
# Catalan Numbers

## Introduction
Catalan numbers are a sequence of natural numbers that have various combinatorial interpretations in mathematics. They appear in various counting problems such as counting the number of valid expressions, parenthesizations, and triangulations of convex polygons.

## Formula
The \( n \)-th Catalan number, denoted as \( C_n \), can be calculated using the following formula:
\[ C_n = \frac{{2n!}}{{(n+1)! \cdot n!}} = \frac{{(2n)!}}{{(n+1)! \cdot n!}} \]

## Algorithm
The \( n \)-th Catalan number can also be computed using a recursive algorithm:

### Recursive Algorithm:
1. If \( n \) is 0, return 1.
2. Otherwise, calculate \( C_n \) using the recursive formula:
   \[ C_n = \sum_{i=0}^{n-1} C_i \cdot C_{n-i-1} \]

## Example
Let's calculate the first few Catalan numbers using both the formula and the recursive algorithm:

1. **Using Formula**:
   - \( C_0 = 1 \)
   - \( C_1 = \frac{{2!}}{{(1+1)! \cdot 1!}} = 1 \)
   - \( C_2 = \frac{{4!}}{{(2+1)! \cdot 2!}} = \frac{{24}}{{3 \cdot 2}} = 4 \)
   - \( C_3 = \frac{{6!}}{{(3+1)! \cdot 3!}} = \frac{{720}}{{4 \cdot 6}} = 5 \)
   - \( C_4 = \frac{{8!}}{{(4+1)! \cdot 4!}} = \frac{{40320}}{{5 \cdot 24}} = 14 \)

2. **Using Recursive Algorithm**:
   - \( C_0 = 1 \)
   - \( C_1 = 1 \)
   - \( C_2 = C_0 \cdot C_1 + C_1 \cdot C_0 = 1 \cdot 1 + 1 \cdot 1 = 2 \)
   - \( C_3 = C_0 \cdot C_2 + C_1 \cdot C_1 + C_2 \cdot C_0 = 1 \cdot 2 + 1 \cdot 1 + 2 \cdot 1 = 5 \)
   - \( C_4 = C_0 \cdot C_3 + C_1 \cdot C_2 + C_2 \cdot C_1 + C_3 \cdot C_0 = 1 \cdot 5 + 1 \cdot 2 + 2 \cdot 1 + 5 \cdot 1 = 14 \)

## Code Implementation (Python)
```python
def catalan_number_formula(n):
    if n == 0:
        return 1
    else:
        return (2 * factorial(2 * n)) // (factorial(n + 1) * factorial(n))

def catalan_number_recursive(n):
    if n == 0:
        return 1
    else:
        catalan = 0
        for i in range(n):
            catalan += catalan_number_recursive(i) * catalan_number_recursive(n - i - 1)
        return catalan

# Helper function to calculate factorial
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)

# Example usage:
for i in range(5):
    print("Catalan number for", i, "using formula:", catalan_number_formula(i))
    print("Catalan number for", i, "using recursive algorithm:", catalan_number_recursive(i))
```
## Code Implementation (CPP)
```cpp
#include <iostream>

using namespace std;

// Function to calculate factorial
int factorial(int n) {
    if (n == 0)
        return 1;
    else
        return n * factorial(n - 1);
}

// Function to calculate Catalan number using formula
int catalanNumberFormula(int n) {
    return factorial(2 * n) / (factorial(n + 1) * factorial(n));
}

// Function to calculate Catalan number using recursive algorithm
int catalanNumberRecursive(int n) {
    if (n == 0)
        return 1;
    else {
        int catalan = 0;
        for (int i = 0; i < n; ++i) {
            catalan += catalanNumberRecursive(i) * catalanNumberRecursive(n - i - 1);
        }
        return catalan;
    }
}

int main() {
    for (int i = 0; i < 5; ++i) {
        cout << "Catalan number for " << i << " using formula: " << catalanNumberFormula(i) << endl;
        cout << "Catalan number for " << i << " using recursive algorithm: " << catalanNumberRecursive(i) << endl;
    }
    return 0;
}
```
## Code Implementation (Java)
```java
public class Main {
    // Function to calculate factorial
    public static int factorial(int n) {
        if (n == 0)
            return 1;
        else
            return n * factorial(n - 1);
    }

    // Function to calculate Catalan number using formula
    public static int catalanNumberFormula(int n) {
        return factorial(2 * n) / (factorial(n + 1) * factorial(n));
    }

    // Function to calculate Catalan number using recursive algorithm
    public static int catalanNumberRecursive(int n) {
        if (n == 0)
            return 1;
        else {
            int catalan = 0;
            for (int i = 0; i < n; ++i) {
                catalan += catalanNumberRecursive(i) * catalanNumberRecursive(n - i - 1);
            }
            return catalan;
        }
    }

    public static void main(String[] args) {
        for (int i = 0; i < 5; ++i) {
            System.out.println("Catalan number for " + i + " using formula: " + catalanNumberFormula(i));
            System.out.println("Catalan number for " + i + " using recursive algorithm: " + catalanNumberRecursive(i));
        }
    }
}
```
# Euler Totient Function

## Introduction
The Euler Totient Function, denoted as \( \phi(n) \), counts the number of positive integers less than or equal to \( n \) that are coprime to \( n \). In other words, it calculates the count of numbers less than \( n \) that have no common divisors with \( n \) except for 1.

## Formula
The Euler Totient Function can be calculated using the following formula:
\[ \phi(n) = n \times \left(1 - \frac{1}{p_1}\right) \times \left(1 - \frac{1}{p_2}\right) \times \ldots \times \left(1 - \frac{1}{p_k}\right) \]
where \( p_1, p_2, \ldots, p_k \) are the distinct prime factors of \( n \).

## Algorithm
The Euler Totient Function can also be computed using a simple algorithm:

1. Initialize \( \phi(n) = n \).
2. Iterate through each prime factor \( p \) of \( n \):
   - Reduce \( \phi(n) \) by \( \frac{\phi(n)}{p} \).

## Example
Let's calculate \( \phi(n) \) for \( n = 10 \):

1. **Using Formula**:
   - \( n = 10 = 2 \times 5 \)
   - \( \phi(10) = 10 \times \left(1 - \frac{1}{2}\right) \times \left(1 - \frac{1}{5}\right) = 10 \times \frac{1}{2} \times \frac{4}{5} = 4 \)

2. **Using Algorithm**:
   - \( n = 10 = 2 \times 5 \)
   - \( \phi(10) = 10 - \left(\frac{10}{2} + \frac{10}{5}\right) = 10 - (5 + 2) = 10 - 7 = 3 \)

## Code Implementation (Python)
```python
def euler_totient_function(n):
    result = n
    p = 2
    while p * p <= n:
        if n % p == 0:
            while n % p == 0:
                n //= p
            result -= result // p
        p += 1
    if n > 1:
        result -= result // n
    return result

# Example usage:
number = 10
print("Euler Totient Function for", number, "is:", euler_totient_function(number))
```
## Code Implementation (CPP)
```cpp
#include <iostream>

using namespace std;

// Function to calculate Euler Totient Function
int eulerTotientFunction(int n) {
    int result = n;
    for (int p = 2; p * p <= n; ++p) {
        if (n % p == 0) {
            while (n % p == 0) {
                n /= p;
            }
            result -= result / p;
        }
    }
    if (n > 1) {
        result -= result / n;
    }
    return result;
}

int main() {
    int number = 10;
    cout << "Euler Totient Function for " << number << " is: " << eulerTotientFunction(number) << endl;
    return 0;
}
```
## Code Implementation (Java)
```java
public class Main {
    // Function to calculate Euler Totient Function
    public static int eulerTotientFunction(int n) {
        int result = n;
        for (int p = 2; p * p <= n; ++p) {
            if (n % p == 0) {
                while (n % p == 0) {
                    n /= p;
                }
                result -= result / p;
            }
        }
        if (n > 1) {
            result -= result / n;
        }
        return result;
    }

    public static void main(String[] args) {
        int number = 10;
        System.out.println("Euler Totient Function for " + number + " is: " + eulerTotientFunction(number));
    }
}
```
# Prime Numbers & Primality Tests

## Introduction
Prime numbers are natural numbers greater than 1 that have no positive divisors other than 1 and themselves. Primality tests are algorithms to determine whether a given number is prime or not.

## Primality Tests
There are various primality tests, each with different time complexities and efficiency. Some of the popular primality tests include:

1. **Trial Division**: This is the simplest primality test, which checks divisibility by every number from 2 to the square root of the given number.
2. **Fermat's Little Theorem**: This test states that if \( p \) is prime and \( a \) is any positive integer less than \( p \), then \( a^{p-1} \) is congruent to 1 modulo \( p \).
3. **Miller-Rabin Test**: This probabilistic test determines whether a given number is composite with a probability of error less than 1/4 for each iteration.
4. **AKS Primality Test**: This deterministic test determines whether a given number is prime in polynomial time.

## Algorithm - Trial Division
The Trial Division algorithm checks divisibility of a number \( n \) by every integer from 2 to the square root of \( n \).

1. If \( n \) is 2 or 3, return true (prime).
2. If \( n \) is less than 2 or divisible by 2, return false (not prime).
3. Iterate \( i \) from 3 to the square root of \( n \) with step size 2:
   - If \( n \) is divisible by \( i \), return false.
4. If no divisors are found, return true.

## Example
Let's check whether the number 29 is prime using the Trial Division algorithm:

1. **Trial Division Algorithm**:
   - \( \sqrt{29} \) is approximately 5.385.
   - Iterate from 3 to 5:
     - 29 is not divisible by 3.
     - 29 is not divisible by 5.
   - No divisors found, so 29 is prime.

## Code Implementation (Python)
```python
import math

def is_prime(n):
    if n == 2 or n == 3:
        return True
    if n < 2 or n % 2 == 0:
        return False
    for i in range(3, int(math.sqrt(n)) + 1, 2):
        if n % i == 0:
            return False
    return True

# Example usage:
number = 29
print("Is", number, "prime?", is_prime(number))
```
## Code Implementation (CPP)
```cpp
#include <iostream>
#include <cmath>

using namespace std;

// Function to check if a number is prime using Trial Division
bool isPrime(int n) {
    if (n == 2 || n == 3)
        return true;
    if (n < 2 || n % 2 == 0)
        return false;
    for (int i = 3; i <= sqrt(n); i += 2) {
        if (n % i == 0)
            return false;
    }
    return true;
}

int main() {
    int number = 29;
    cout << "Is " << number << " prime? " << (isPrime(number) ? "Yes" : "No") << endl;
    return 0;
}
```
## Code Implementation (Java)
```java
public class Main {
    // Function to check if a number is prime using Trial Division
    public static boolean isPrime(int n) {
        if (n == 2 || n == 3)
            return true;
        if (n < 2 || n % 2 == 0)
            return false;
        for (int i = 3; i <= Math.sqrt(n); i += 2) {
            if (n % i == 0)
                return false;
        }
        return true;
    }

    public static void main(String[] args) {
        int number = 29;
        System.out.println("Is " + number + " prime? " + (isPrime(number) ? "Yes" : "No"));
    }
}
```
# Prime Factorization & Divisors

## Introduction
Prime factorization is the process of finding the prime numbers that multiply together to give a specific number. Divisors of a number are the integers that can divide the number without leaving a remainder.

## Prime Factorization Algorithm
The prime factorization of a number can be found using the following algorithm:

1. Initialize an empty list to store the prime factors.
2. Iterate from 2 to the square root of the given number:
   - If the number is divisible by the current divisor, divide the number by the divisor repeatedly and add the divisor to the list until the number is no longer divisible.
3. If the number becomes 1, stop the iteration.
4. If the number is greater than 1 after the loop, it is a prime factor itself, so add it to the list.
5. The list contains all the prime factors of the given number.

## Divisors Algorithm
The divisors of a number can be found using its prime factorization:

1. Find the prime factorization of the number.
2. Generate all possible combinations of the prime factors.
3. Multiply each combination to get the divisors.

## Example
Let's find the prime factorization and divisors of the number 60:

1. **Prime Factorization Algorithm**:
   - Start with the number 60.
   - Divide by 2: 60 / 2 = 30 (add 2 to the list).
   - Divide by 2: 30 / 2 = 15 (add 2 to the list).
   - Divide by 3: 15 / 3 = 5 (add 3 to the list).
   - 5 is a prime number (add 5 to the list).
   - Prime factors of 60: [2, 2, 3, 5].

2. **Divisors Algorithm**:
   - Generate combinations of prime factors: [1], [2], [2, 3], [2, 5], [3], [3, 5], [5], [2, 3, 5].
   - Multiply each combination to get divisors: [1, 2, 6, 10, 3, 15, 5, 30].

## Code Implementation (Python)
```python
import math

def prime_factorization(n):
    factors = []
    for i in range(2, int(math.sqrt(n)) + 1):
        while n % i == 0:
            factors.append(i)
            n //= i
    if n > 1:
        factors.append(n)
    return factors

def divisors(n):
    prime_factors = prime_factorization(n)
    divs = [1]
    for i in range(len(prime_factors)):
        for j in range(len(divs)):
            divs.append(divs[j] * prime_factors[i])
    return sorted(divs)

# Example usage:
number = 60
print("Prime factorization of", number, ":", prime_factorization(number))
print("Divisors of", number, ":", divisors(number))
```
## Code Implementation (CPP)
```cpp
#include <iostream>
#include <vector>
#include <cmath>
#include <algorithm>

using namespace std;

// Function to find prime factorization of a number
vector<int> primeFactorization(int n) {
    vector<int> factors;
    for (int i = 2; i * i <= n; ++i) {
        while (n % i == 0) {
            factors.push_back(i);
            n /= i;
        }
    }
    if (n > 1) {
        factors.push_back(n);
    }
    return factors;
}

// Function to find divisors of a number
vector<int> divisors(int n) {
    vector<int> primeFactors = primeFactorization(n);
    vector<int> divs = {1};
    for (int i = 0; i < primeFactors.size(); ++i) {
        int size = divs.size();
        for (int j = 0; j < size; ++j) {
            divs.push_back(divs[j] * primeFactors[i]);
        }
    }
    sort(divs.begin(), divs.end());
    return divs;
}

int main() {
    int number = 60;
    cout << "Prime factorization of " << number << ": ";
    vector<int> factors = primeFactorization(number);
    for (int factor : factors) {
        cout << factor << " ";
    }
    cout << endl;

    cout << "Divisors of " << number << ": ";
    vector<int> divisorsList = divisors(number);
    for (int divisor : divisorsList) {
        cout << divisor << " ";
    }
    cout << endl;

    return 0;
}
```
## Code Implementation (Java)
```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class Main {
    // Function to find prime factorization of a number
    public static List<Integer> primeFactorization(int n) {
        List<Integer> factors = new ArrayList<>();
        for (int i = 2; i * i <= n; ++i) {
            while (n % i == 0) {
                factors.add(i);
                n /= i;
            }
        }
        if (n > 1) {
            factors.add(n);
        }
        return factors;
    }

    // Function to find divisors of a number
    public static List<Integer> divisors(int n) {
        List<Integer> primeFactors = primeFactorization(n);
        List<Integer> divs = new ArrayList<>();
        divs.add(1);
        for (int i = 0; i < primeFactors.size(); ++i) {
            int size = divs.size();
            for (int j = 0; j < size; ++j) {
                divs.add(divs.get(j) * primeFactors.get(i));
            }
        }
        Collections.sort(divs);
        return divs;
    }

    public static void main(String[] args) {
        int number = 60;
        System.out.print("Prime factorization of " + number + ": ");
        List<Integer> factors = primeFactorization(number);
        for (int factor : factors) {
            System.out.print(factor + " ");
        }
        System.out.println();

        System.out.print("Divisors of " + number + ": ");
        List<Integer> divisorsList = divisors(number);
        for (int divisor : divisorsList) {
            System.out.print(divisor + " ");
        }
        System.out.println();
    }
}
```

# Chinese Remainder Theorem

## Introduction
The Chinese Remainder Theorem (CRT) is a theorem in number theory that describes a method to solve a system of congruences with pairwise coprime moduli.

## Statement of the Theorem
Let \( n_1, n_2, \ldots, n_k \) be pairwise coprime positive integers, and let \( a_1, a_2, \ldots, a_k \) be any integers. Then, there exists an integer \( x \) such that:
\[ x \equiv a_1 \pmod{n_1} \]
\[ x \equiv a_2 \pmod{n_2} \]
\[ \vdots \]
\[ x \equiv a_k \pmod{n_k} \]
Moreover, any two solutions \( x \) and \( y \) are congruent modulo \( n_1 \times n_2 \times \ldots \times n_k \).

## Algorithm
The Chinese Remainder Theorem can be implemented using the following algorithm:

1. Compute \( N = n_1 \times n_2 \times \ldots \times n_k \).
2. For each \( i = 1, 2, \ldots, k \), compute \( N_i = \frac{N}{n_i} \).
3. For each \( i = 1, 2, \ldots, k \), compute \( y_i \) such that \( N_i \times y_i \equiv 1 \pmod{n_i} \) (this can be done using the Extended Euclidean Algorithm).
4. Compute the solution \( x \) using \( x = \sum_{i=1}^{k} a_i \times N_i \times y_i \pmod{N} \).

## Example
Let's solve the following system of congruences using the Chinese Remainder Theorem:
\[ x \equiv 2 \pmod{3} \]
\[ x \equiv 3 \pmod{5} \]
\[ x \equiv 2 \pmod{7} \]

1. Compute \( N = 3 \times 5 \times 7 = 105 \).
2. Compute \( N_1 = \frac{105}{3} = 35 \), \( N_2 = \frac{105}{5} = 21 \), and \( N_3 = \frac{105}{7} = 15 \).
3. Compute \( y_1 = 2 \) (since \( 35 \times 2 \equiv 1 \pmod{3} \)), \( y_2 = 1 \) (since \( 21 \times 1 \equiv 1 \pmod{5} \)), and \( y_3 = 1 \) (since \( 15 \times 1 \equiv 1 \pmod{7} \)).
4. Compute the solution \( x = (2 \times 35 \times 2) + (3 \times 21 \times 1) + (2 \times 15 \times 1) \equiv 23 \pmod{105} \).

## Code Implementation (Python)
```python
def extended_gcd(a, b):
    if a == 0:
        return b, 0, 1
    gcd, x1, y1 = extended_gcd(b % a, a)
    x = y1 - (b // a) * x1
    y = x1
    return gcd, x, y

def chinese_remainder_theorem(n, a):
    N = 1
    for num in n:
        N *= num
    result = 0
    for i in range(len(n)):
        Ni = N // n[i]
        _, yi, _ = extended_gcd(Ni, n[i])
        result += a[i] * Ni * yi
    return result % N

# Example usage:
n = [3, 5, 7]
a = [2, 3, 2]
print("Solution using Chinese Remainder Theorem:", chinese_remainder_theorem(n, a))
```
## Code Implementation (CPP)
```cpp
#include <iostream>
#include <vector>

using namespace std;

// Function to calculate the modular inverse using Extended Euclidean Algorithm
int extendedGCD(int a, int b, int &x, int &y) {
    if (a == 0) {
        x = 0;
        y = 1;
        return b;
    }
    int x1, y1;
    int gcd = extendedGCD(b % a, a, x1, y1);
    x = y1 - (b / a) * x1;
    y = x1;
    return gcd;
}

// Function to calculate the solution using Chinese Remainder Theorem
int chineseRemainderTheorem(const vector<int> &n, const vector<int> &a) {
    int N = 1;
    for (int num : n)
        N *= num;

    int result = 0;
    for (int i = 0; i < n.size(); ++i) {
        int Ni = N / n[i];
        int x, y;
        extendedGCD(Ni, n[i], x, y);
        result += a[i] * Ni * y;
    }

    return (result % N + N) % N;
}

int main() {
    vector<int> n = {3, 5, 7};
    vector<int> a = {2, 3, 2};

    cout << "Solution using Chinese Remainder Theorem: " << chineseRemainderTheorem(n, a) << endl;

    return 0;
}
```
## Code Implementation (CPP)
```java
public class Main {
    // Function to calculate the modular inverse using Extended Euclidean Algorithm
    public static int extendedGCD(int a, int b, int[] x, int[] y) {
        if (a == 0) {
            x[0] = 0;
            y[0] = 1;
            return b;
        }
        int[] x1 = new int[1], y1 = new int[1];
        int gcd = extendedGCD(b % a, a, x1, y1);
        x[0] = y1[0] - (b / a) * x1[0];
        y[0] = x1[0];
        return gcd;
    }

    // Function to calculate the solution using Chinese Remainder Theorem
    public static int chineseRemainderTheorem(int[] n, int[] a) {
        int N = 1;
        for (int num : n)
            N *= num;

        int result = 0;
        for (int i = 0; i < n.length; ++i) {
            int Ni = N / n[i];
            int[] x = new int[1], y = new int[1];
            extendedGCD(Ni, n[i], x, y);
            result += a[i] * Ni * y[0];
        }

        return (result % N + N) % N;
    }

    public static void main(String[] args) {
        int[] n = {3, 5, 7};
        int[] a = {2, 3, 2};

        System.out.println("Solution using Chinese Remainder Theorem: " + chineseRemainderTheorem(n, a));
    }
}
```
## Conclusion
In exploring various topics including GCD, prime numbers, modular arithmetic, and the Chinese Remainder Theorem, we've delved into fundamental concepts of number theory and algorithms that hold significant importance in mathematics and computer science. Through detailed explanations, examples, and code implementations in both C++ and Java, we've illustrated how these concepts can be applied to solve problems efficiently. From foundational algorithms like the Euclidean Algorithm to advanced theorems like the Chinese Remainder Theorem, understanding these concepts not only enhances problem-solving skills but also provides valuable tools for cryptography, optimization, and other areas where number theory plays a crucial role.
