---
title: 'Article on DSA Topic: Stack'
description: In this article, we delve into Stack in the context of Data Structures and Algorithms (DSA).
date: 2024-05-21
author: Nehal Fathema
tags:
    - Data Structures
    - Algorithms
    - Stack
---


# Stack

## What is a Stack?
A stack is a linear data structure that follows the Last In, First Out (LIFO) principle. This means that the last element added to the stack is the first one to be removed.

## Key Operations
1. **Push**: Add an element to the top of the stack.
2. **Pop**: Remove the element from the top of the stack.
3. **Peek/Top**: Get the value of the top element without removing it.
4. **isEmpty**: Check if the stack is empty.

## Stack Representation
A stack can be represented using arrays, linked lists, or dynamic data structures in various programming languages. The most common methods involve using arrays or linked lists.

## Array Implementation of Stack
### C++ Code for Array-based Stack
```cpp
#include <iostream>
#include <stdexcept>

using namespace std;

class Stack {
private:
    int* arr;
    int top;
    int capacity;

public:
    Stack(int size = 100) {
        arr = new int[size];
        capacity = size;
        top = -1;
    }

    ~Stack() {
        delete[] arr;
    }

    void push(int x) {
        if (isFull()) {
            throw overflow_error("Stack Overflow");
        }
        arr[++top] = x;
    }

    int pop() {
        if (isEmpty()) {
            throw underflow_error("Stack Underflow");
        }
        return arr[top--];
    }

    int peek() {
        if (isEmpty()) {
            throw underflow_error("Stack Underflow");
        }
        return arr[top];
    }

    bool isEmpty() {
        return top == -1;
    }

    bool isFull() {
        return top == capacity - 1;
    }

    int size() {
        return top + 1;
    }
};

int main() {
    Stack stack(5);

    stack.push(1);
    stack.push(2);
    stack.push(3);

    cout << "Top element is: " << stack.peek() << endl;
    cout << "Stack size is: " << stack.size() << endl;

    stack.pop();
    stack.pop();
    stack.pop();

    if (stack.isEmpty()) {
        cout << "Stack is empty" << endl;
    }

    return 0;
}
```
### Linked List Implementation of Stack
```cpp
#include <iostream>
#include <stdexcept>

using namespace std;

class Node {
public:
    int data;
    Node* next;
};

class Stack {
private:
    Node* top;

public:
    Stack() {
        top = nullptr;
    }

    ~Stack() {
        while (!isEmpty()) {
            pop();
        }
    }

    void push(int x) {
        Node* temp = new Node();
        temp->data = x;
        temp->next = top;
        top = temp;
    }

    int pop() {
        if (isEmpty()) {
            throw underflow_error("Stack Underflow");
        }
        Node* temp = top;
        top = top->next;
        int popped = temp->data;
        delete temp;
        return popped;
    }

    int peek() {
        if (isEmpty()) {
            throw underflow_error("Stack Underflow");
        }
        return top->data;
    }

    bool isEmpty() {
        return top == nullptr;
    }
};

int main() {
    Stack stack;

    stack.push(1);
    stack.push(2);
    stack.push(3);

    cout << "Top element is: " << stack.peek() << endl;

    stack.pop();
    stack.pop();
    stack.pop();

    if (stack.isEmpty()) {
        cout << "Stack is empty" << endl;
    }

    return 0;
}
```
## Applications of Stack
1. **Expression Evaluation and Conversion**: Used to evaluate expressions (postfix, prefix) and convert expressions (infix to postfix/prefix).
2. **Backtracking**: Helps in backtracking algorithms, such as solving mazes, puzzles, and other recursive problems.
3. **Function Call Management**: Manages function calls and returns in programming languages.
4. **Undo Mechanism**: Used in applications like text editors to implement undo functionality.


