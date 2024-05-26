---
title: 'Article on DSA Topic: Queue'
description: In this article, we delve into Queue in the context of Data Structures and Algorithms (DSA).
date: 2024-05-21
author: Nehal Fathema
tags:
    - Data Structures
    - Algorithms
    - Queue
---

# Queue

## What is a Queue?
A queue is a linear data structure that follows the First In, First Out (FIFO) principle. This means that the first element added to the queue will be the first one to be removed. Queues are commonly used in scenarios where order needs to be preserved, such as task scheduling, handling requests in a web server, and breadth-first search in graphs.

## Key Operations
1. **Enqueue**: Add an element to the end of the queue.
2. **Dequeue**: Remove the element from the front of the queue.
3. **Front/Peek**: Get the value of the front element without removing it.
4. **isEmpty**: Check if the queue is empty.
5. **isFull**: Check if the queue is full (only applicable to array-based queues).
6. **Size**: Get the current size of the queue.

## Queue Representation
A queue can be represented using arrays, linked lists, or dynamic data structures in various programming languages. The most common methods involve using arrays or linked lists.

## Array Implementation of Queue
### C++ Code for Array-based Queue
```cpp
#include <iostream>
#include <stdexcept>

using namespace std;

class Queue {
private:
    int* arr;
    int front;
    int rear;
    int capacity;
    int count;

public:
    Queue(int size = 100) {
        arr = new int[size];
        capacity = size;
        front = 0;
        rear = -1;
        count = 0;
    }

    ~Queue() {
        delete[] arr;
    }

    void enqueue(int x) {
        if (isFull()) {
            throw overflow_error("Queue Overflow");
        }
        rear = (rear + 1) % capacity;
        arr[rear] = x;
        count++;
    }

    int dequeue() {
        if (isEmpty()) {
            throw underflow_error("Queue Underflow");
        }
        int x = arr[front];
        front = (front + 1) % capacity;
        count--;
        return x;
    }

    int peek() {
        if (isEmpty()) {
            throw underflow_error("Queue Underflow");
        }
        return arr[front];
    }

    bool isEmpty() {
        return (count == 0);
    }

    bool isFull() {
        return (count == capacity);
    }

    int size() {
        return count;
    }
};

int main() {
    Queue queue(5);

    queue.enqueue(1);
    queue.enqueue(2);
    queue.enqueue(3);

    cout << "Front element is: " << queue.peek() << endl;
    cout << "Queue size is: " << queue.size() << endl;

    queue.dequeue();
    queue.dequeue();
    queue.dequeue();

    if (queue.isEmpty()) {
        cout << "Queue is empty" << endl;
    }

    return 0;
}
```
## Linked List Implementation of Queue
```cpp
#include <iostream>
#include <stdexcept>

using namespace std;

class Node {
public:
    int data;
    Node* next;
};

class Queue {
private:
    Node* front;
    Node* rear;
    int count;

public:
    Queue() {
        front = rear = nullptr;
        count = 0;
    }

    ~Queue() {
        while (!isEmpty()) {
            dequeue();
        }
    }

    void enqueue(int x) {
        Node* temp = new Node();
        temp->data = x;
        temp->next = nullptr;
        if (isEmpty()) {
            front = rear = temp;
        } else {
            rear->next = temp;
            rear = temp;
        }
        count++;
    }

    int dequeue() {
        if (isEmpty()) {
            throw underflow_error("Queue Underflow");
        }
        Node* temp = front;
        front = front->next;
        int popped = temp->data;
        delete temp;
        count--;
        if (front == nullptr) {
            rear = nullptr;
        }
        return popped;
    }

    int peek() {
        if (isEmpty()) {
            throw underflow_error("Queue Underflow");
        }
        return front->data;
    }

    bool isEmpty() {
        return (front == nullptr);
    }

    int size() {
        return count;
    }
};

int main() {
    Queue queue;

    queue.enqueue(1);
    queue.enqueue(2);
    queue.enqueue(3);

    cout << "Front element is: " << queue.peek() << endl;

    queue.dequeue();
    queue.dequeue();
    queue.dequeue();

    if (queue.isEmpty()) {
        cout << "Queue is empty" << endl;
    }

    return 0;
}
```
# Types of Queues

## Overview
Queues are fundamental data structures that follow the First In, First Out (FIFO) principle. Beyond the basic queue, there are several specialized types of queues designed to handle specific scenarios and requirements more efficiently. These include circular queues, priority queues, and double-ended queues (deques).

## Types of Queues

### 1. Simple Queue (Linear Queue)
A simple queue is the basic form of a queue where elements are added at the rear and removed from the front. It follows the FIFO principle strictly.

### 2. Circular Queue
In a circular queue, the last position is connected back to the first position to make a circle. It overcomes the limitation of the simple queue where space is wasted when elements are dequeued.

#### C++ Code for Circular Queue
```cpp
#include <iostream>
#include <stdexcept>

using namespace std;

class CircularQueue {
private:
    int* arr;
    int front;
    int rear;
    int capacity;
    int count;

public:
    CircularQueue(int size = 100) {
        arr = new int[size];
        capacity = size;
        front = 0;
        rear = -1;
        count = 0;
    }

    ~CircularQueue() {
        delete[] arr;
    }

    void enqueue(int x) {
        if (isFull()) {
            throw overflow_error("Queue Overflow");
        }
        rear = (rear + 1) % capacity;
        arr[rear] = x;
        count++;
    }

    int dequeue() {
        if (isEmpty()) {
            throw underflow_error("Queue Underflow");
        }
        int x = arr[front];
        front = (front + 1) % capacity;
        count--;
        return x;
    }

    int peek() {
        if (isEmpty()) {
            throw underflow_error("Queue Underflow");
        }
        return arr[front];
    }

    bool isEmpty() {
        return (count == 0);
    }

    bool isFull() {
        return (count == capacity);
    }

    int size() {
        return count;
    }
};

int main() {
    CircularQueue queue(5);

    queue.enqueue(1);
    queue.enqueue(2);
    queue.enqueue(3);

    cout << "Front element is: " << queue.peek() << endl;
    cout << "Queue size is: " << queue.size() << endl;

    queue.dequeue();
    queue.dequeue();
    queue.dequeue();

    if (queue.isEmpty()) {
        cout << "Queue is empty" << endl;
    }

    return 0;
}
```
## 3. Priority Queue
A priority queue is a special type of queue in which each element is associated with a priority. Elements with higher priority are dequeued before elements with lower priority.
```cpp
#include <iostream>
#include <queue>

using namespace std;

class PriorityQueue {
private:
    priority_queue<int> pq;

public:
    void enqueue(int x) {
        pq.push(x);
    }

    int dequeue() {
        if (pq.empty()) {
            throw underflow_error("Queue Underflow");
        }
        int x = pq.top();
        pq.pop();
        return x;
    }

    int peek() {
        if (pq.empty()) {
            throw underflow_error("Queue Underflow");
        }
        return pq.top();
    }

    bool isEmpty() {
        return pq.empty();
    }

    int size() {
        return pq.size();
    }
};

int main() {
    PriorityQueue queue;

    queue.enqueue(10);
    queue.enqueue(30);
    queue.enqueue(20);

    cout << "Top element is: " << queue.peek() << endl;
    cout << "Queue size is: " << queue.size() << endl;

    queue.dequeue();
    queue.dequeue();
    queue.dequeue();

    if (queue.isEmpty()) {
        cout << "Queue is empty" << endl;
    }

    return 0;
}
```
## 4. Double-ended Queue (Deque)
A deque is a type of queue in which elements can be added or removed from both ends (front and rear). It combines the properties of stacks and queues.
```cpp
#include <iostream>
#include <deque>

using namespace std;

class Deque {
private:
    deque<int> dq;

public:
    void enqueueFront(int x) {
        dq.push_front(x);
    }

    void enqueueRear(int x) {
        dq.push_back(x);
    }

    int dequeueFront() {
        if (dq.empty()) {
            throw underflow_error("Queue Underflow");
        }
        int x = dq.front();
        dq.pop_front();
        return x;
    }

    int dequeueRear() {
        if (dq.empty()) {
            throw underflow_error("Queue Underflow");
        }
        int x = dq.back();
        dq.pop_back();
        return x;
    }

    int peekFront() {
        if (dq.empty()) {
            throw underflow_error("Queue Underflow");
        }
        return dq.front();
    }

    int peekRear() {
        if (dq.empty()) {
            throw underflow_error("Queue Underflow");
        }
        return dq.back();
    }

    bool isEmpty() {
        return dq.empty();
    }

    int size() {
        return dq.size();
    }
};

int main() {
    Deque deque;

    deque.enqueueRear(1);
    deque.enqueueRear(2);
    deque.enqueueFront(3);

    cout << "Front element is: " << deque.peekFront() << endl;
    cout << "Rear element is: " << deque.peekRear() << endl;
    cout << "Deque size is: " << deque.size() << endl;

    deque.dequeueFront();
    deque.dequeueRear();
    deque.dequeueFront();

    if (deque.isEmpty()) {
        cout << "Deque is empty" << endl;
    }

    return 0;
}
```
