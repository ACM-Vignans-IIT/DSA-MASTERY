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
#### C++
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
#### Java
```java
import java.util.NoSuchElementException;

public class Queue {
    private int[] arr;
    private int front;
    private int rear;
    private int capacity;
    private int count;

    public Queue(int size) {
        arr = new int[size];
        capacity = size;
        front = 0;
        rear = -1;
        count = 0;
    }

    public void enqueue(int x) {
        if (isFull()) {
            throw new IllegalStateException("Queue Overflow");
        }
        rear = (rear + 1) % capacity;
        arr[rear] = x;
        count++;
    }

    public int dequeue() {
        if (isEmpty()) {
            throw new NoSuchElementException("Queue Underflow");
        }
        int x = arr[front];
        front = (front + 1) % capacity;
        count--;
        return x;
    }

    public int peek() {
        if (isEmpty()) {
            throw new NoSuchElementException("Queue Underflow");
        }
        return arr[front];
    }

    public boolean isEmpty() {
        return count == 0;
    }

    public boolean isFull() {
        return count == capacity;
    }

    public int size() {
        return count;
    }

    public static void main(String[] args) {
        Queue queue = new Queue(5);

        queue.enqueue(1);
        queue.enqueue(2);
        queue.enqueue(3);

        System.out.println("Front element is: " + queue.peek());
        System.out.println("Queue size is: " + queue.size());

        queue.dequeue();
        queue.dequeue();
        queue.dequeue();

        if (queue.isEmpty()) {
            System.out.println("Queue is empty");
        }
    }
}
```
#### Python
```python
class Queue:
    def __init__(self, size):
        self.arr = [0] * size
        self.front = 0
        self.rear = -1
        self.capacity = size
        self.count = 0

    def enqueue(self, x):
        if self.isFull():
            raise Exception("Queue Overflow")
        self.rear = (self.rear + 1) % self.capacity
        self.arr[self.rear] = x
        self.count += 1

    def dequeue(self):
        if self.isEmpty():
            raise Exception("Queue Underflow")
        x = self.arr[self.front]
        self.front = (self.front + 1) % self.capacity
        self.count -= 1
        return x

    def peek(self):
        if self.isEmpty():
            raise Exception("Queue Underflow")
        return self.arr[self.front]

    def isEmpty(self):
        return self.count == 0

    def isFull(self):
        return self.count == self.capacity

    def size(self):
        return self.count

if __name__ == "__main__":
    queue = Queue(5)

    queue.enqueue(1)
    queue.enqueue(2)
    queue.enqueue(3)

    print("Front element is:", queue.peek())
    print("Queue size is:", queue.size())

    queue.dequeue()
    queue.dequeue()
    queue.dequeue()

    if queue.isEmpty():
        print("Queue is empty")
```
## Linked List Implementation of Queue
#### C++
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
#### Java
```java
import java.util.NoSuchElementException;

public class Node {
    public int data;
    public Node next;
}

public class Queue {
    private Node front;
    private Node rear;
    private int count;

    public Queue() {
        front = rear = null;
        count = 0;
    }

    public void enqueue(int x) {
        Node temp = new Node();
        temp.data = x;
        temp.next = null;
        if (isEmpty()) {
            front = rear = temp;
        } else {
            rear.next = temp;
            rear = temp;
        }
        count++;
    }

    public int dequeue() {
        if (isEmpty()) {
            throw new NoSuchElementException("Queue Underflow");
        }
        Node temp = front;
        front = front.next;
        int popped = temp.data;
        temp = null;
        count--;
        if (front == null) {
            rear = null;
        }
        return popped;
    }

    public int peek() {
        if (isEmpty()) {
            throw new NoSuchElementException("Queue Underflow");
        }
        return front.data;
    }

    public boolean isEmpty() {
        return front == null;
    }

    public int size() {
        return count;
    }

    public static void main(String[] args) {
        Queue queue = new Queue();

        queue.enqueue(1);
        queue.enqueue(2);
        queue.enqueue(3);

        System.out.println("Front element is: " + queue.peek());

        queue.dequeue();
        queue.dequeue();
        queue.dequeue();

        if (queue.isEmpty()) {
            System.out.println("Queue is empty");
        }
    }
}
```
#### Python
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class Queue:
    def __init__(self):
        self.front = None
        self.rear = None
        self.count = 0

    def enqueue(self, x):
        temp = Node(x)
        if self.isEmpty():
            self.front = self.rear = temp
        else:
            self.rear.next = temp
            self.rear = temp
        self.count += 1

    def dequeue(self):
        if self.isEmpty():
            raise Exception("Queue Underflow")
        temp = self.front
        self.front = self.front.next
        popped = temp.data
        temp = None
        self.count -= 1
        if self.front == None:
            self.rear = None
        return popped

    def peek(self):
        if self.isEmpty():
            raise Exception("Queue Underflow")
        return self.front.data

    def isEmpty(self):
        return self.front == None

    def size(self):
        return self.count

if __name__ == "__main__":
    queue = Queue()

    queue.enqueue(1)
    queue.enqueue(2)
    queue.enqueue(3)

    print("Front element is:", queue.peek())

    queue.dequeue()
    queue.dequeue()
    queue.dequeue()

    if queue.isEmpty():
        print("Queue is empty")
```
# Types of Queues

## Overview
Queues are fundamental data structures that follow the First In, First Out (FIFO) principle. Beyond the basic queue, there are several specialized types of queues designed to handle specific scenarios and requirements more efficiently. These include circular queues, priority queues, and double-ended queues (deques).

## Types of Queues

### 1. Simple Queue (Linear Queue)
A simple queue is the basic form of a queue where elements are added at the rear and removed from the front. It follows the FIFO principle strictly.

### 2. Circular Queue
In a circular queue, the last position is connected back to the first position to make a circle. It overcomes the limitation of the simple queue where space is wasted when elements are dequeued.

#### C++
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
#### Java
```java
import java.util.NoSuchElementException;

public class CircularQueue {
    private int[] arr;
    private int front;
    private int rear;
    private int capacity;
    private int count;

    public CircularQueue(int size) {
        arr = new int[size];
        capacity = size;
        front = 0;
        rear = -1;
        count = 0;
    }

    public void enqueue(int x) {
        if (isFull()) {
            throw new RuntimeException("Queue Overflow");
        }
        rear = (rear + 1) % capacity;
        arr[rear] = x;
        count++;
    }

    public int dequeue() {
        if (isEmpty()) {
            throw new NoSuchElementException("Queue Underflow");
        }
        int x = arr[front];
        front = (front + 1) % capacity;
        count--;
        return x;
    }

    public int peek() {
        if (isEmpty()) {
            throw new NoSuchElementException("Queue Underflow");
        }
        return arr[front];
    }

    public boolean isEmpty() {
        return count == 0;
    }

    public boolean isFull() {
        return count == capacity;
    }

    public int size() {
        return count;
    }

    public static void main(String[] args) {
        CircularQueue queue = new CircularQueue(5);

        queue.enqueue(1);
        queue.enqueue(2);
        queue.enqueue(3);

        System.out.println("Front element is: " + queue.peek());
        System.out.println("Queue size is: " + queue.size());

        queue.dequeue();
        queue.dequeue();
        queue.dequeue();

        if (queue.isEmpty()) {
            System.out.println("Queue is empty");
        }
    }
}
```
#### Python
```python
class CircularQueue:
    def __init__(self, size):
        self.arr = [0] * size
        self.front = 0
        self.rear = -1
        self.capacity = size
        self.count = 0

    def enqueue(self, x):
        if self.isFull():
            raise Exception("Queue Overflow")
        self.rear = (self.rear + 1) % self.capacity
        self.arr[self.rear] = x
        self.count += 1

    def dequeue(self):
        if self.isEmpty():
            raise Exception("Queue Underflow")
        x = self.arr[self.front]
        self.front = (self.front + 1) % self.capacity
        self.count -= 1
        return x

    def peek(self):
        if self.isEmpty():
            raise Exception("Queue Underflow")
        return self.arr[self.front]

    def isEmpty(self):
        return self.count == 0

    def isFull(self):
        return self.count == self.capacity

    def size(self):
        return self.count

if __name__ == "__main__":
    queue = CircularQueue(5)

    queue.enqueue(1)
    queue.enqueue(2)
    queue.enqueue(3)

    print("Front element is:", queue.peek())
    print("Queue size is:", queue.size())

    queue.dequeue()
    queue.dequeue()
    queue.dequeue()

    if queue.isEmpty():
        print("Queue is empty")
```
## 3. Priority Queue
A priority queue is a special type of queue in which each element is associated with a priority. Elements with higher priority are dequeued before elements with lower priority.
#### C++
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
#### Java
```java
import java.util.PriorityQueue;
import java.util.NoSuchElementException;

public class PriorityQueueExample {
    private PriorityQueue<Integer> pq;

    public PriorityQueueExample() {
        pq = new PriorityQueue<>();
    }

    public void enqueue(int x) {
        pq.offer(x);
    }

    public int dequeue() {
        if (isEmpty()) {
            throw new NoSuchElementException("Queue Underflow");
        }
        return pq.poll();
    }

    public int peek() {
        if (isEmpty()) {
            throw new NoSuchElementException("Queue Underflow");
        }
        return pq.peek();
    }

    public boolean isEmpty() {
        return pq.isEmpty();
    }

    public int size() {
        return pq.size();
    }

    public static void main(String[] args) {
        PriorityQueueExample queue = new PriorityQueueExample();

        queue.enqueue(10);
        queue.enqueue(30);
        queue.enqueue(20);

        System.out.println("Top element is: " + queue.peek());
        System.out.println("Queue size is: " + queue.size());

        queue.dequeue();
        queue.dequeue();
        queue.dequeue();

        if (queue.isEmpty()) {
            System.out.println("Queue is empty");
        }
    }
}
```
#### Python
```python
import queue

class PriorityQueue:
    def __init__(self):
        self.pq = queue.PriorityQueue()

    def enqueue(self, x):
        self.pq.put(x)

    def dequeue(self):
        if self.isEmpty():
            raise Exception("Queue Underflow")
        return self.pq.get()

    def peek(self):
        if self.isEmpty():
            raise Exception("Queue Underflow")
        return self.pq.queue[0]

    def isEmpty(self):
        return self.pq.empty()

    def size(self):
        return self.pq.qsize()

if __name__ == "__main__":
    queue = PriorityQueue()

    queue.enqueue(10)
    queue.enqueue(30)
    queue.enqueue(20)

    print("Top element is:", queue.peek())
    print("Queue size is:", queue.size())

    queue.dequeue()
    queue.dequeue()
    queue.dequeue()

    if queue.isEmpty():
        print("Queue is empty")
```
## 4. Double-ended Queue (Deque)
A deque is a type of queue in which elements can be added or removed from both ends (front and rear). It combines the properties of stacks and queues.
#### C++
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
```
#### Java
```java
import java.util.Deque;
import java.util.LinkedList;
import java.util.NoSuchElementException;

public class DequeExample {
    private Deque<Integer> dq;

    public DequeExample() {
        dq = new LinkedList<>();
    }

    public void enqueueFront(int x) {
        dq.offerFirst(x);
    }

    public void enqueueRear(int x) {
        dq.offerLast(x);
    }

    public int dequeueFront() {
        if (isEmpty()) {
            throw new NoSuchElementException("Queue Underflow");
        }
        return dq.pollFirst();
    }

    public int dequeueRear() {
        if (isEmpty()) {
            throw new NoSuchElementException("Queue Underflow");
        }
        return dq.pollLast();
    }

    public int peekFront() {
        if (isEmpty()) {
            throw new NoSuchElementException("Queue Underflow");
        }
        return dq.peekFirst();
    }

    public int peekRear() {
        if (isEmpty()) {
            throw new NoSuchElementException("Queue Underflow");
        }
        return dq.peekLast();
    }

    public boolean isEmpty() {
        return dq.isEmpty();
    }

    public int size() {
        return dq.size();
    }

    public static void main(String[] args) {
        DequeExample deque = new DequeExample();

        deque.enqueueRear(1);
        deque.enqueueRear(2);
        deque.enqueueFront(3);

        System.out.println("Front element is: " + deque.peekFront());
        System.out.println("Rear element is: " + deque.peekRear());
        System.out.println("Deque size is: " + deque.size());

        deque.dequeueFront();
        deque.dequeueRear();
        deque.dequeueFront();

        if (deque.isEmpty()) {
            System.out.println("Deque is empty");
        }
    }
}
```
#### Python
```python
from collections import deque

class Deque:
    def __init__(self):
        self.dq = deque()

    def enqueueFront(self, x):
        self.dq.appendleft(x)

    def enqueueRear(self, x):
        self.dq.append(x)

    def dequeueFront(self):
        if self.isEmpty():
            raise Exception("Queue Underflow")
        return self.dq.popleft()

    def dequeueRear(self):
        if self.isEmpty():
            raise Exception("Queue Underflow")
        return self.dq.pop()

    def peekFront(self):
        if self.isEmpty():
            raise Exception("Queue Underflow")
        return self.dq[0]

    def peekRear(self):
        if self.isEmpty():
            raise Exception("Queue Underflow")
        return self.dq[-1]

    def isEmpty(self):
        return len(self.dq) == 0

    def size(self):
        return len(self.dq)

if __name__ == "__main__":
    deque = Deque()

    deque.enqueueRear(1)
    deque.enqueueRear(2)
    deque.enqueueFront(3)

    print("Front element is:", deque.peekFront())
    print("Rear element is:", deque.peekRear())
    print("Deque size is:", deque.size())

    deque.dequeueFront()
    deque.dequeueRear()
    deque.dequeueFront()

    if deque.isEmpty():
        print("Deque is empty")
}
```
