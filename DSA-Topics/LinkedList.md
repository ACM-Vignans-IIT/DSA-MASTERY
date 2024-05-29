---
title: 'Article on DSA Topic: Linked List'
description: In this article, we delve into Linked List in the context of Data Structures and Algorithms (DSA).
date: 2024-05-22
author: Nehal Fathema
tags:
    - Data Structures
    - Algorithms
    - Linked List
---

# Linked List

## What is a Linked List?
A linked list is a linear data structure where each element, called a node, contains two parts:
1. **Data**: The value stored in the node.
2. **Pointer**: A reference to the next node in the sequence.

Unlike arrays, linked lists do not store elements in contiguous memory locations. This allows for efficient insertions and deletions.

## Why Use a Linked List?
Linked lists are useful because:
- They allow for dynamic memory allocation.
- They provide efficient insertions and deletions compared to arrays.
- They can easily grow in size without requiring a large block of memory.

## Types of Linked Lists
1. **Singly Linked List**: Each node points to the next node.
2. **Doubly Linked List**: Each node points to both the next and the previous node.
3. **Circular Linked List**: The last node points to the first node, forming a circle.



## Singly Linked List

### What is a Singly Linked List?
A singly linked list is a type of linked list in which each node contains two parts:
1. **Data**: The value stored in the node.
2. **Pointer**: A reference to the next node in the sequence.

In a singly linked list, each node points to the next node in the list, and the last node points to `nullptr` indicating the end of the list.

### Why Use a Singly Linked List?
Singly linked lists are useful because:
- They allow for dynamic memory allocation.
- They provide efficient insertions and deletions compared to arrays.
- They can easily grow in size without requiring a large block of contiguous memory.

### Basic Operations on Singly Linked Lists
1. **Insertion**: Adding a new node to the list.
2. **Deletion**: Removing a node from the list.
3. **Traversal**: Visiting each node in the list.
4. **Search**: Finding a node with a given value.

### 1. Insertion
Insertion can be performed at the beginning, at the end, or at a given position in the list.
#### C++
```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

// Function to insert a node at the beginning of the list
void insertAtBeginning(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    newNode->next = head;
    head = newNode;
}

// Function to insert a node at the end of the list
void insertAtEnd(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    newNode->next = nullptr;

    if (head == nullptr) {
        head = newNode;
    } else {
        Node* temp = head;
        while (temp->next != nullptr) {
            temp = temp->next;
        }
        temp->next = newNode;
    }
}

// Function to insert a node at a specific position in the list
void insertAtPosition(Node*& head, int position, int newData) {
    if (position < 1) {
        cout << "Position should be >= 1." << endl;
        return;
    }

    if (position == 1) {
        insertAtBeginning(head, newData);
        return;
    }

    Node* newNode = new Node();
    newNode->data = newData;

    Node* temp = head;
    for (int i = 1; i < position - 1 && temp != nullptr; ++i) {
        temp = temp->next;
    }

    if (temp == nullptr) {
        cout << "Position is out of bounds." << endl;
        delete newNode;
    } else {
        newNode->next = temp->next;
        temp->next = newNode;
    }
}

// Function to print the list
void printList(Node* node) {
    while (node != nullptr) {
        cout << node->data << " ";
        node = node->next;
    }
    cout << endl;
}

int main() {
    Node* head = nullptr;

    insertAtBeginning(head, 10);
    insertAtBeginning(head, 20);
    insertAtBeginning(head, 30);
    printList(head);

    insertAtEnd(head, 40);
    printList(head);

    insertAtPosition(head, 2, 25);
    printList(head);

    insertAtPosition(head, 1, 5);
    printList(head);

    insertAtPosition(head, 7, 50); // Inserting at the end
    printList(head);

    insertAtPosition(head, 10, 60); // Position out of bounds
    printList(head);

    return 0;
}
```
#### Java
```java
class Node {
    int data;
    Node next;
    
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class LinkedList {
    Node head;

    // Function to insert a node at the beginning of the list
    void insertAtBeginning(int newData) {
        Node newNode = new Node(newData);
        newNode.next = head;
        head = newNode;
    }

    // Function to insert a node at the end of the list
    void insertAtEnd(int newData) {
        Node newNode = new Node(newData);
        if (head == null) {
            head = newNode;
        } else {
            Node temp = head;
            while (temp.next != null) {
                temp = temp.next;
            }
            temp.next = newNode;
        }
    }

    // Function to insert a node at a specific position in the list
    void insertAtPosition(int position, int newData) {
        if (position < 1) {
            System.out.println("Position should be >= 1.");
            return;
        }
        
        if (position == 1) {
            insertAtBeginning(newData);
            return;
        }

        Node newNode = new Node(newData);
        Node temp = head;
        for (int i = 1; i < position - 1 && temp != null; i++) {
            temp = temp.next;
        }

        if (temp == null) {
            System.out.println("Position is out of bounds.");
        } else {
            newNode.next = temp.next;
            temp.next = newNode;
        }
    }

    // Function to print the list
    void printList() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        LinkedList list = new LinkedList();

        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtBeginning(30);
        list.printList();

        list.insertAtEnd(40);
        list.printList();

        list.insertAtPosition(2, 25);
        list.printList();

        list.insertAtPosition(1, 5);
        list.printList();

        list.insertAtPosition(7, 50); // Inserting at the end
        list.printList();

        list.insertAtPosition(10, 60); // Position out of bounds
        list.printList();
    }
}
```
#### Python
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    # Function to insert a node at the beginning of the list
    def insert_at_beginning(self, new_data):
        new_node = Node(new_data)
        new_node.next = self.head
        self.head = new_node

    # Function to insert a node at the end of the list
    def insert_at_end(self, new_data):
        new_node = Node(new_data)
        if self.head is None:
            self.head = new_node
        else:
            temp = self.head
            while temp.next is not None:
                temp = temp.next
            temp.next = new_node

    # Function to insert a node at a specific position in the list
    def insert_at_position(self, position, new_data):
        if position < 1:
            print("Position should be >= 1.")
            return
        
        if position == 1:
            self.insert_at_beginning(new_data)
            return

        new_node = Node(new_data)
        temp = self.head
        for _ in range(1, position - 1):
            if temp is None:
                break
            temp = temp.next

        if temp is None:
            print("Position is out of bounds.")
        else:
            new_node.next = temp.next
            temp.next = new_node

    # Function to print the list
    def print_list(self):
        temp = self.head
        while temp:
            print(temp.data, end=" ")
            temp = temp.next
        print()

# Example usage
if __name__ == "__main__":
    list = LinkedList()

    list.insert_at_beginning(10)
    list.insert_at_beginning(20)
    list.insert_at_beginning(30)
    list.print_list()

    list.insert_at_end(40)
    list.print_list()

    list.insert_at_position(2, 25)
    list.print_list()

    list.insert_at_position(1, 5)
    list.print_list()

    list.insert_at_position(7, 50) # Inserting at the end
    list.print_list()

    list.insert_at_position(10, 60) # Position out of bounds
    list.print_list()
```

### 2. Deletion
Deletion can be performed at the beginning, at the end, or at a given position in the list.

#### C++
```cpp
#include<iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void insertAtBeginning(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    newNode->next = head;
    head = newNode;
}

void deleteAtBeginning(Node*& head) {
    if (head == nullptr) return;
    Node* temp = head;
    head = head->next;
    delete temp;
}

void deleteAtEnd(Node*& head) {
    if (head == nullptr) return;

    if (head->next == nullptr) {
        delete head;
        head = nullptr;
        return;
    }

    Node* temp = head;
    while (temp->next->next != nullptr) {
        temp = temp->next;
    }

    delete temp->next;
    temp->next = nullptr;
}

void deleteAtPosition(Node*& head, int position) {
    if (position < 1 || head == nullptr) {
        cout << "Position out of bounds." << endl;
        return;
    }

    if (position == 1) {
        deleteAtBeginning(head);
        return;
    }

    Node* temp = head;
    for (int i = 1; i < position - 1 && temp != nullptr; ++i) {
        temp = temp->next;
    }

    if (temp == nullptr || temp->next == nullptr) {
        cout << "Position out of bounds." << endl;
        return;
    }

    Node* nodeToDelete = temp->next;
    temp->next = nodeToDelete->next;
    delete nodeToDelete;
}

void printList(Node* node) {
    while (node != nullptr) {
        cout << node->data << " ";
        node = node->next;
    }
    cout << endl;
}

int main() {
    Node* head = nullptr;

    insertAtBeginning(head, 10);
    insertAtBeginning(head, 20);
    insertAtBeginning(head, 30);
    printList(head);

    deleteAtBeginning(head);
    printList(head);

    insertAtBeginning(head, 40);
    insertAtBeginning(head, 50);
    printList(head);

    deleteAtEnd(head);
    printList(head);

    insertAtBeginning(head, 60);
    insertAtBeginning(head, 70);
    printList(head);

    deleteAtPosition(head, 3);
    printList(head);

    deleteAtPosition(head, 1);
    printList(head);

    deleteAtPosition(head, 10); // Position out of bounds
    printList(head);

    return 0;
}
```
#### Java
```java
class Node {
    int data;
    Node next;
    
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class LinkedList {
    Node head;

    // Function to insert a node at the beginning of the list
    void insertAtBeginning(int newData) {
        Node newNode = new Node(newData);
        newNode.next = head;
        head = newNode;
    }

    // Function to delete a node at the beginning of the list
    void deleteAtBeginning() {
        if (head == null) return;
        Node temp = head;
        head = head.next;
        temp = null; // Java garbage collector will take care of deletion
    }

    // Function to delete a node at the end of the list
    void deleteAtEnd() {
        if (head == null) return;
        
        if (head.next == null) {
            head = null;
            return;
        }

        Node temp = head;
        while (temp.next.next != null) {
            temp = temp.next;
        }

        temp.next = null;
    }

    // Function to delete a node at a specific position in the list
    void deleteAtPosition(int position) {
        if (position < 1 || head == null) {
            System.out.println("Position out of bounds.");
            return;
        }

        if (position == 1) {
            deleteAtBeginning();
            return;
        }

        Node temp = head;
        for (int i = 1; i < position - 1 && temp != null; i++) {
            temp = temp.next;
        }

        if (temp == null || temp.next == null) {
            System.out.println("Position out of bounds.");
            return;
        }

        Node nodeToDelete = temp.next;
        temp.next = temp.next.next;
        nodeToDelete = null; // Java garbage collector will take care of deletion
    }

    // Function to print the list
    void printList() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        LinkedList list = new LinkedList();

        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtBeginning(30);
        list.printList();

        list.deleteAtBeginning();
        list.printList();

        list.insertAtBeginning(40);
        list.insertAtBeginning(50);
        list.printList();

        list.deleteAtEnd();
        list.printList();

        list.insertAtBeginning(60);
        list.insertAtBeginning(70);
        list.printList();

        list.deleteAtPosition(3);
        list.printList();

        list.deleteAtPosition(1);
        list.printList();

        list.deleteAtPosition(10); // Position out of bounds
        list.printList();
    }
}
```
#### Python
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    # Function to insert a node at the beginning of the list
    def insert_at_beginning(self, new_data):
        new_node = Node(new_data)
        new_node.next = self.head
        self.head = new_node

    # Function to delete a node at the beginning of the list
    def delete_at_beginning(self):
        if self.head is None:
            return
        self.head = self.head.next

    # Function to delete a node at the end of the list
    def delete_at_end(self):
        if self.head is None:
            return

        if self.head.next is None:
            self.head = None
            return

        temp = self.head
        while temp.next.next is not None:
            temp = temp.next

        temp.next = None

    # Function to delete a node at a specific position in the list
    def delete_at_position(self, position):
        if position < 1 or self.head is None:
            print("Position out of bounds.")
            return

        if position == 1:
            self.delete_at_beginning()
            return

        temp = self.head
        for _ in range(1, position - 1):
            if temp is None:
                break
            temp = temp.next

        if temp is None or temp.next is None:
            print("Position out of bounds.")
        else:
            temp.next = temp.next.next

    # Function to print the list
    def print_list(self):
        temp = self.head
        while temp:
            print(temp.data, end=" ")
            temp = temp.next
        print()

# Example usage
if __name__ == "__main__":
    list = LinkedList()

    list.insert_at_beginning(10)
    list.insert_at_beginning(20)
    list.insert_at_beginning(30)
    list.print_list()

    list.delete_at_beginning()
    list.print_list()

    list.insert_at_beginning(40)
    list.insert_at_beginning(50)
    list.print_list()

    list.delete_at_end()
    list.print_list()

    list.insert_at_beginning(60)
    list.insert_at_beginning(70)
    list.print_list()

    list.delete_at_position(3)
    list.print_list()

    list.delete_at_position(1)
    list.print_list()

    list.delete_at_position(10) # Position out of bounds
    list.print_list()
```

### 3. Traversal
Traversal involves visiting each node in the list and performing an action on it, such as printing the node's data.

#### Example: Printing All Elements
Traverse from the head to the end of the list, printing each node's data.
#### C++ Code
```cpp
#include <iostream>
using namespace std;
struct Node {
    int data;
    Node* next;
};

void insertAtBeginning(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    newNode->next = head;
    head = newNode;
}

void printList(Node* node) {
    while (node != nullptr) {
        cout << node->data << " ";
        node = node->next;
    }
    cout << endl;
}

int main() {
    Node* head = nullptr;
    insertAtBeginning(head, 10);
    insertAtBeginning(head, 20);
    insertAtBeginning(head, 30);
    printList(head);
    return 0;
}
```
#### Java
```java
class Node {
    int data;
    Node next;

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class LinkedList {

    Node head;

    public void insertAtBeginning(int newData) {
        Node newNode = new Node(newData);
        newNode.next = head;
        head = newNode;
    }

    public void printList() {
        Node node = head;
        while (node != null) {
            System.out.print(node.data + " ");
            node = node.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        LinkedList list = new LinkedList();
        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtBeginning(30);
        list.printList();
    }
}
```
#### Python
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def insert_at_beginning(self, new_data):
        new_node = Node(new_data)
        new_node.next = self.head
        self.head = new_node

    def print_list(self):
        temp = self.head
        while temp:
            print(temp.data, end=" ")
            temp = temp.next
        print()

if __name__ == "__main__":
    list = LinkedList()
    list.insert_at_beginning(10)
    list.insert_at_beginning(20)
    list.insert_at_beginning(30)
    list.print_list()
```

### 4. Search
Search involves finding a node with a given value.

#### Example: Searching for a Value
Traverse from the head to the end of the list, comparing each node's data with the target value.

#### C++
```cpp
#include <iostream>
using namespace std;
struct Node {
    int data;
    Node* next;
};

void insertAtBeginning(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    newNode->next = head;
    head = newNode;
}

bool search(Node* head, int target) {
    Node* current = head;
    while (current != nullptr) {
        if (current->data == target) {
            return true;
        }
        current = current->next;
    }
    return false;
}

int main() {
    Node* head = nullptr;
    insertAtBeginning(head, 10);
    insertAtBeginning(head, 20);
    insertAtBeginning(head, 30);

    int target = 20;
    if (search(head, target)) {
        cout << "Element found." << endl;
    } else {
        cout << "Element not found." << endl;
    }
    return 0;
}
```
#### Java
```java
class Node {
    int data;
    Node next;

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class LinkedList {

    Node head;

    public void insertAtBeginning(int newData) {
        Node newNode = new Node(newData);
        newNode.next = head;
        head = newNode;
    }

    public boolean search(int target) {
        Node current = head;
        while (current != null) {
            if (current.data == target) {
                return true;
            }
            current = current.next;
        }
        return false;
    }

    public static void main(String[] args) {
        LinkedList list = new LinkedList();
        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtBeginning(30);

        int target = 20;
        if (list.search(target)) {
            System.out.println("Element found.");
        } else {
            System.out.println("Element not found.");
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

class LinkedList:
    def __init__(self):
        self.head = None

    def insert_at_beginning(self, new_data):
        new_node = Node(new_data)
        new_node.next = self.head
        self.head = new_node

    def search(self, target):
        current = self.head
        while current:
            if current.data == target:
                return True
            current = current.next
        return False

if __name__ == "__main__":
    list = LinkedList()
    list.insert_at_beginning(10)
    list.insert_at_beginning(20)
    list.insert_at_beginning(30)

    target = 20
    if list.search(target):
        print("Element found.")
    else:
        print("Element not found.")
```
## Doubly Linked List

### What is a Doubly Linked List?
A doubly linked list is a type of linked list in which each node contains three parts:
1. **Data**: The value stored in the node.
2. **Next Pointer**: A reference to the next node in the sequence.
3. **Previous Pointer**: A reference to the previous node in the sequence.

In a doubly linked list, each node points to both its next and previous nodes, allowing traversal in both directions.

### Why Use a Doubly Linked List?
Doubly linked lists are useful because:
- They allow for efficient insertions and deletions compared to arrays.
- They provide bidirectional traversal of the list.
- They can easily grow in size without requiring a large block of contiguous memory.

### Basic Operations on Doubly Linked Lists
1. **Insertion**: Adding a new node to the list.
2. **Deletion**: Removing a node from the list.
3. **Traversal**: Visiting each node in the list.
4. **Search**: Finding a node with a given value.

### 1. Insertion
Insertion can be performed at the beginning, at the end, or at a given position in the list.

#### C++
```cpp
#include <iostream>
using namespace std;
struct Node {
    int data;
    Node* next;
    Node* prev;
};

void insertAtBeginning(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    newNode->next = head;
    newNode->prev = nullptr;
    
    if (head != nullptr) {
        head->prev = newNode;
    }
    
    head = newNode;
}

void insertAtEnd(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    newNode->next = nullptr;
    
    if (head == nullptr) {
        newNode->prev = nullptr;
        head = newNode;
        return;
    }
    
    Node* last = head;
    while (last->next != nullptr) {
        last = last->next;
    }
    
    last->next = newNode;
    newNode->prev = last;
}

void insertAtPosition(Node*& head, int position, int newData) {
    if (position < 1) {
        cout << "Position should be >= 1." << endl;
        return;
    }

    if (position == 1) {
        insertAtBeginning(head, newData);
        return;
    }

    Node* newNode = new Node();
    newNode->data = newData;

    Node* temp = head;
    for (int i = 1; i < position - 1 && temp != nullptr; ++i) {
        temp = temp->next;
    }

    if (temp == nullptr) {
        cout << "Position is out of bounds." << endl;
        delete newNode;
    } else {
        newNode->next = temp->next;
        if (temp->next != nullptr) {
            temp->next->prev = newNode;
        }
        temp->next = newNode;
        newNode->prev = temp;
    }
}

void printList(Node* node) {
    while (node != nullptr) {
        cout << node->data << " ";
        node = node->next;
    }
    cout << endl;
}

int main() {
    Node* head = nullptr;

    insertAtBeginning(head, 10);
    insertAtBeginning(head, 20);
    insertAtBeginning(head, 30);
    printList(head);

    insertAtEnd(head, 40);
    printList(head);

    insertAtPosition(head, 2, 25);
    printList(head);

    insertAtPosition(head, 1, 5);
    printList(head);

    insertAtPosition(head, 7, 50); // Inserting at the end
    printList(head);

    insertAtPosition(head, 10, 60); // Position out of bounds
    printList(head);

    return 0;
}
```
#### Java
```java
class Node {
    int data;
    Node next;
    Node prev;
    
    Node(int data) {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}

public class DoublyLinkedList {
    Node head;

    // Function to insert a node at the beginning of the list
    void insertAtBeginning(int newData) {
        Node newNode = new Node(newData);
        newNode.next = head;
        if (head != null) {
            head.prev = newNode;
        }
        head = newNode;
    }

    // Function to insert a node at the end of the list
    void insertAtEnd(int newData) {
        Node newNode = new Node(newData);
        newNode.next = null;
        
        if (head == null) {
            newNode.prev = null;
            head = newNode;
            return;
        }
        
        Node last = head;
        while (last.next != null) {
            last = last.next;
        }
        
        last.next = newNode;
        newNode.prev = last;
    }

    // Function to insert a node at a specific position in the list
    void insertAtPosition(int position, int newData) {
        if (position < 1) {
            System.out.println("Position should be >= 1.");
            return;
        }

        if (position == 1) {
            insertAtBeginning(newData);
            return;
        }

        Node newNode = new Node(newData);

        Node temp = head;
        for (int i = 1; i < position - 1 && temp != null; ++i) {
            temp = temp.next;
        }

        if (temp == null) {
            System.out.println("Position is out of bounds.");
            return;
        }

        newNode.next = temp.next;
        if (temp.next != null) {
            temp.next.prev = newNode;
        }
        temp.next = newNode;
        newNode.prev = temp;
    }

    // Function to print the list
    void printList() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        DoublyLinkedList list = new DoublyLinkedList();

        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtBeginning(30);
        list.printList();

        list.insertAtEnd(40);
        list.printList();

        list.insertAtPosition(2, 25);
        list.printList();

        list.insertAtPosition(1, 5);
        list.printList();

        list.insertAtPosition(7, 50); // Inserting at the end
        list.printList();

        list.insertAtPosition(10, 60); // Position out of bounds
        list.printList();
    }
}
```
#### Python
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None

class DoublyLinkedList:
    def __init__(self):
        self.head = None

    # Function to insert a node at the beginning of the list
    def insert_at_beginning(self, new_data):
        new_node = Node(new_data)
        new_node.next = self.head
        if self.head:
            self.head.prev = new_node
        self.head = new_node

    # Function to insert a node at the end of the list
    def insert_at_end(self, new_data):
        new_node = Node(new_data)
        if self.head is None:
            new_node.prev = None
            self.head = new_node
            return
        last = self.head
        while last.next:
            last = last.next
        last.next = new_node
        new_node.prev = last

    # Function to insert a node at a specific position in the list
    def insert_at_position(self, position, new_data):
        if position < 1:
            print("Position should be >= 1.")
            return
        if position == 1:
            self.insert_at_beginning(new_data)
            return
        new_node = Node(new_data)
        temp = self.head
        for _ in range(1, position - 1):
            if temp is None:
                return
            temp = temp.next
        if temp is None:
            print("Position is out of bounds.")
            return
        new_node.next = temp.next
        if temp.next:
            temp.next.prev = new_node
        temp.next = new_node
        new_node.prev = temp

    # Function to print the list
    def print_list(self):
        temp = self.head
        while temp:
            print(temp.data, end=" ")
            temp = temp.next
        print()

# Example usage
if __name__ == "__main__":
    list = DoublyLinkedList()

    list.insert_at_beginning(10)
    list.insert_at_beginning(20)
    list.insert_at_beginning(30)
    list.print_list()

    list.insert_at_end(40)
    list.print_list()

    list.insert_at_position(2, 25)
    list.print_list()

    list.insert_at_position(1, 5)
    list.print_list()

    list.insert_at_position(7, 50) # Inserting at the end
    list.print_list()

    list.insert_at_position(10, 60) # Position out of bounds
    list.print_list()
```
### 2. Deletion
Deletion can be performed at the beginning, at the end, or at a given position in the list.

#### C++
```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
    Node* prev;
};

void insertAtBeginning(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    newNode->next = head;
    newNode->prev = nullptr;
    
    if (head != nullptr) {
        head->prev = newNode;
    }
    
    head = newNode;
}

void deleteAtBeginning(Node*& head) {
    if (head == nullptr) return;
    Node* temp = head;
    head = head->next;
    
    if (head != nullptr) {
        head->prev = nullptr;
    }
    
    delete temp;
}

void deleteAtEnd(Node*& head) {
    if (head == nullptr) return;
    if (head->next == nullptr) {
        delete head;
        head = nullptr;
        return;
    }
    
    Node* last = head;
    while (last->next != nullptr) {
        last = last->next;
    }
    
    if (last->prev != nullptr) {
        last->prev->next = nullptr;
    } else {
        head = nullptr;
    }
    
    delete last;
}

void deleteAtPosition(Node*& head, int position) {
    if (position < 1 || head == nullptr) {
        cout << "Position out of bounds." << endl;
        return;
    }

    if (position == 1) {
        deleteAtBeginning(head);
        return;
    }

    Node* temp = head;
    for (int i = 1; i < position && temp != nullptr; ++i) {
        temp = temp->next;
    }

    if (temp == nullptr) {
        cout << "Position out of bounds." << endl;
        return;
    }

    if (temp->next != nullptr) {
        temp->next->prev = temp->prev;
    }
    if (temp->prev != nullptr) {
        temp->prev->next = temp->next;
    }

    delete temp;
}

void printList(Node* node) {
    while (node != nullptr) {
        cout << node->data << " ";
        node = node->next;
    }
    cout << endl;
}

int main() {
    Node* head = nullptr;

    insertAtBeginning(head, 10);
    insertAtBeginning(head, 20);
    insertAtBeginning(head, 30);
    printList(head);

    deleteAtBeginning(head);
    printList(head);

    deleteAtEnd(head);
    printList(head);

    deleteAtPosition(head, 1);
    printList(head);

    deleteAtPosition(head, 1); // Position out of bounds
    printList(head);

    return 0;
}
```
#### Java
```java
class Node {
    int data;
    Node next;
    Node prev;
    
    Node(int data) {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}

public class DoublyLinkedList {
    Node head;

    // Function to insert a node at the beginning of the list
    void insertAtBeginning(int newData) {
        Node newNode = new Node(newData);
        newNode.next = head;
        if (head != null) {
            head.prev = newNode;
        }
        head = newNode;
    }

    // Function to delete a node at the end of the list
    void deleteAtEnd() {
        if (head == null) return;
        
        Node last = head;
        while (last.next != null) {
            last = last.next;
        }

        if (last.prev != null) {
            last.prev.next = null;
        } else {
            head = null;
        }

        last.prev = null;
    }

    // Function to delete a node at a specific position in the list
    void deleteAtPosition(int position) {
        if (position < 1 || head == null) {
            System.out.println("Position out of bounds.");
            return;
        }

        if (position == 1) {
            head = head.next;
            if (head != null) {
                head.prev = null;
            }
            return;
        }

        Node temp = head;
        for (int i = 1; i < position && temp != null; ++i) {
            temp = temp.next;
        }

        if (temp == null || temp.next == null) {
            System.out.println("Position out of bounds.");
            return;
        }

        temp.prev.next = temp.next;
        if (temp.next != null) {
            temp.next.prev = temp.prev;
        }
    }

    // Function to print the list
    void printList() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        DoublyLinkedList list = new DoublyLinkedList();

        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtBeginning(30);
        list.printList();

        list.deleteAtEnd();
        list.printList();

        list.deleteAtPosition(2);
        list.printList();
    }
}
```
#### Python
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None

class DoublyLinkedList:
    def __init__(self):
        self.head = None

    # Function to insert a node at the beginning of the list
    def insert_at_beginning(self, new_data):
        new_node = Node(new_data)
        new_node.next = self.head
        if self.head:
            self.head.prev = new_node
        self.head = new_node

    # Function to delete a node at the end of the list
    def delete_at_end(self):
        if self.head is None:
            return

        last = self.head
        while last.next:
            last = last.next

        if last.prev:
            last.prev.next = None
        else:
            self.head = None

        last.prev = None

    # Function to delete a node at a specific position in the list
    def delete_at_position(self, position):
        if position < 1 or self.head is None:
            print("Position out of bounds.")
            return

        if position == 1:
            self.head = self.head.next
            if self.head:
                self.head.prev = None
            return

        temp = self.head
        for _ in range(1, position - 1):
            if temp is None:
                return
            temp = temp.next

        if temp is None or temp.next is None:
            print("Position out of bounds.")
            return

        if temp.next.next:
            temp.next.next.prev = temp
        temp.next = temp.next.next

    # Function to print the list
    def print_list(self):
        temp = self.head
        while temp:
            print(temp.data, end=" ")
            temp = temp.next
        print()

# Example usage
if __name__ == "__main__":
    list = DoublyLinkedList()

    list.insert_at_beginning(10)
    list.insert_at_beginning(20)
    list.insert_at_beginning(30)
    list.print_list()

    list.delete_at_end()
    list.print_list()

    list.delete_at_position(2)
    list.print_list()
```

### 3. Traversal
Traversal involves visiting each node in the list and performing an action on it, such as printing the node's data.

#### Example: Printing All Elements
Traverse from the head to the end of the list, printing each node's data.

#### C++
```cpp
#include<iostream>
using namespace std;
struct Node {
    int data;
    Node* next;
    Node* prev;
};

void insertAtBeginning(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    newNode->next = head;
    newNode->prev = nullptr;
    
    if (head != nullptr) {
        head->prev = newNode;
    }
    
    head = newNode;
}

void printList(Node* node) {
    Node* last;
    while (node != nullptr) {
        cout << node->data << " ";
        last = node;
        node = node->next;
    }
    cout << endl;
}

int main() {
    Node* head = nullptr;
    insertAtBeginning(head, 10);
    insertAtBeginning(head, 20);
    insertAtBeginning(head, 30);
    printList(head);
    return 0;
}
```
#### Java
```java
class Node {
    int data;
    Node next;
    Node prev;
    
    Node(int data) {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}

public class DoublyLinkedList {
    Node head;

    // Function to insert a node at the beginning of the list
    void insertAtBeginning(int newData) {
        Node newNode = new Node(newData);
        newNode.next = head;
        if (head != null) {
            head.prev = newNode;
        }
        head = newNode;
    }

    // Function to print the list
    void printList() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        DoublyLinkedList list = new DoublyLinkedList();

        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtBeginning(30);
        list.printList();
    }
}
```
#### Python
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None

class DoublyLinkedList:
    def __init__(self):
        self.head = None

    # Function to insert a node at the beginning of the list
    def insert_at_beginning(self, new_data):
        new_node = Node(new_data)
        new_node.next = self.head
        if self.head:
            self.head.prev = new_node
        self.head = new_node

    # Function to print the list
    def print_list(self):
        temp = self.head
        while temp:
            print(temp.data, end=" ")
            temp = temp.next
        print()

# Example usage
if __name__ == "__main__":
    list = DoublyLinkedList()

    list.insert_at_beginning(10)
    list.insert_at_beginning(20)
    list.insert_at_beginning(30)
    list.print_list()
```

### 4. Search
Search involves finding a node with a given value.

#### Example: Searching for a Value
Traverse from the head to the end of the list, comparing each node's data with the target value.
#### C++
```cpp
#include<iostream>
using namespace std;
struct Node {
    int data;
    Node* next;
    Node* prev;
};

void insertAtBeginning(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    newNode->next = head;
    newNode->prev = nullptr;
    
    if (head != nullptr) {
        head->prev = newNode;
    }
    
    head = newNode;
}

bool search(Node* head, int target) {
    Node* current = head;
    while (current != nullptr) {
        if (current->data == target) {
            return true;
        }
        current = current->next;
    }
    return false;
}

int main() {
    Node* head = nullptr;
    insertAtBeginning(head, 10);
    insertAtBeginning(head, 20);
    insertAtBeginning(head, 30);

    int target = 20;
    if (search(head, target)) {
        cout << "Element found." << endl;
    } else {
        cout << "Element not found." << endl;
    }
    return 0;
}
```
#### Java
```java
class Node {
    int data;
    Node next;
    Node prev;
    
    Node(int data) {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}

public class DoublyLinkedList {
    Node head;

    // Function to insert a node at the beginning of the list
    void insertAtBeginning(int newData) {
        Node newNode = new Node(newData);
        newNode.next = head;
        if (head != null) {
            head.prev = newNode;
        }
        head = newNode;
    }

    // Function to search for an element in the list
    boolean search(int target) {
        Node current = head;
        while (current != null) {
            if (current.data == target) {
                return true;
            }
            current = current.next;
        }
        return false;
    }

    public static void main(String[] args) {
        DoublyLinkedList list = new DoublyLinkedList();

        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtBeginning(30);

        int target = 20;
        if (list.search(target)) {
            System.out.println("Element found.");
        } else {
            System.out.println("Element not found.");
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
        self.prev = None

class DoublyLinkedList:
    def __init__(self):
        self.head = None

    # Function to insert a node at the beginning of the list
    def insert_at_beginning(self, new_data):
        new_node = Node(new_data)
        new_node.next = self.head
        if self.head:
            self.head.prev = new_node
        self.head = new_node

    # Function to search for an element in the list
    def search(self, target):
        current = self.head
        while current:
            if current.data == target:
                return True
            current = current.next
        return False

# Example usage
if __name__ == "__main__":
    list = DoublyLinkedList()

    list.insert_at_beginning(10)
    list.insert_at_beginning(20)
    list.insert_at_beginning(30)

    target = 20
    if list.search(target):
        print("Element found.")
    else:
        print("Element not found.")
```
## Circular Linked List

### What is a Circular Linked List?
A circular linked list is a type of linked list where the last node points back to the first node, forming a circle. This means that the list can be traversed starting from any node and eventually returns to the starting node.

### Why Use a Circular Linked List?
Circular linked lists are useful because:
- They allow for continuous traversal of the list.
- They can be useful in applications where the list needs to be cyclically rotated.
- They are beneficial in implementing circular queues and buffers.

### Types of Circular Linked Lists
1. **Singly Circular Linked List**: Each node points to the next node and the last node points to the first node.
2. **Doubly Circular Linked List**: Each node points to both the next and previous nodes, and the last node points back to the first node and vice versa.

### Basic Operations on Circular Linked Lists
1. **Insertion**: Adding a new node to the list.
2. **Deletion**: Removing a node from the list.
3. **Traversal**: Visiting each node in the list.
4. **Search**: Finding a node with a given value.

### 1. Insertion
Insertion can be performed at the beginning, at the end, or at a given position in the list.

#### C++
```cpp
#include<iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

// Function to insert a node at the beginning of the circular linked list
void insertAtBeginning(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    
    if (head == nullptr) {
        newNode->next = newNode;
        head = newNode;
        return;
    }
    
    Node* temp = head;
    while (temp->next != head) {
        temp = temp->next;
    }
    
    newNode->next = head;
    temp->next = newNode;
    head = newNode;
}

// Function to insert a node at the end of the circular linked list
void insertAtEnd(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    newNode->next = nullptr;
    
    if (head == nullptr) {
        newNode->next = newNode;
        head = newNode;
        return;
    }
    
    Node* temp = head;
    while (temp->next != head) {
        temp = temp->next;
    }
    
    temp->next = newNode;
    newNode->next = head;
}

// Function to insert a node at a specific position in the circular linked list
void insertAtPosition(Node*& head, int position, int newData) {
    if (position < 1) {
        cout << "Invalid position." << endl;
        return;
    }

    Node* newNode = new Node();
    newNode->data = newData;

    if (position == 1) {
        if (head == nullptr) {
            newNode->next = newNode;
            head = newNode;
        } else {
            Node* temp = head;
            while (temp->next != head) {
                temp = temp->next;
            }
            newNode->next = head;
            temp->next = newNode;
            head = newNode;
        }
        return;
    }

    Node* temp = head;
    for (int i = 1; i < position - 1 && temp != nullptr; ++i) {
        temp = temp->next;
    }

    if (temp == nullptr) {
        cout << "Invalid position." << endl;
        delete newNode;
        return;
    }

    newNode->next = temp->next;
    temp->next = newNode;
}

// Function to print the circular linked list
void printList(Node* head) {
    if (head == nullptr) return;
    Node* temp = head;
    do {
        cout << temp->data << " ";
        temp = temp->next;
    } while (temp != head);
    cout << endl;
}

int main() {
    Node* head = nullptr;
    insertAtBeginning(head, 10);
    insertAtBeginning(head, 20);
    insertAtEnd(head, 30);
    insertAtPosition(head, 2, 40); // Inserting at position 2
    printList(head);
    return 0;
}
```
#### Java
```java
class Node {
    int data;
    Node next;
    
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class CircularLinkedList {
    Node head;

    // Function to insert a node at the beginning of the circular linked list
    void insertAtBeginning(int newData) {
        Node newNode = new Node(newData);
        
        if (head == null) {
            newNode.next = newNode;
            head = newNode;
            return;
        }
        
        Node temp = head;
        while (temp.next != head) {
            temp = temp.next;
        }
        
        newNode.next = head;
        temp.next = newNode;
        head = newNode;
    }

    // Function to insert a node at the end of the circular linked list
    void insertAtEnd(int newData) {
        Node newNode = new Node(newData);
        
        if (head == null) {
            newNode.next = newNode;
            head = newNode;
            return;
        }
        
        Node temp = head;
        while (temp.next != head) {
            temp = temp.next;
        }
        
        temp.next = newNode;
        newNode.next = head;
    }

    // Function to insert a node at a specific position in the circular linked list
    void insertAtPosition(int position, int newData) {
        if (position < 1) {
            System.out.println("Invalid position.");
            return;
        }

        Node newNode = new Node(newData);

        if (position == 1) {
            if (head == null) {
                newNode.next = newNode;
                head = newNode;
            } else {
                Node temp = head;
                while (temp.next != head) {
                    temp = temp.next;
                }
                newNode.next = head;
                temp.next = newNode;
                head = newNode;
            }
            return;
        }

        Node temp = head;
        for (int i = 1; i < position - 1 && temp != null; ++i) {
            temp = temp.next;
        }

        if (temp == null) {
            System.out.println("Invalid position.");
            return;
        }

        newNode.next = temp.next;
        temp.next = newNode;
    }

    // Function to print the circular linked list
    void printList() {
        if (head == null) return;
        Node temp = head;
        do {
            System.out.print(temp.data + " ");
            temp = temp.next;
        } while (temp != head);
        System.out.println();
    }

    public static void main(String[] args) {
        CircularLinkedList list = new CircularLinkedList();

        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtEnd(30);
        list.insertAtPosition(2, 40); // Inserting at position 2
        list.printList();
    }
}
```
#### Python
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class CircularLinkedList:
    def __init__(self):
        self.head = None

    # Function to insert a node at the beginning of the circular linked list
    def insert_at_beginning(self, new_data):
        new_node = Node(new_data)
        
        if self.head is None:
            new_node.next = new_node
            self.head = new_node
            return
        
        temp = self.head
        while temp.next != self.head:
            temp = temp.next
        
        new_node.next = self.head
        temp.next = new_node
        self.head = new_node

    # Function to insert a node at the end of the circular linked list
    def insert_at_end(self, new_data):
        new_node = Node(new_data)
        
        if self.head is None:
            new_node.next = new_node
            self.head = new_node
            return
        
        temp = self.head
        while temp.next != self.head:
            temp = temp.next
        
        temp.next = new_node
        new_node.next = self.head

    # Function to insert a node at a specific position in the circular linked list
    def insert_at_position(self, position, new_data):
        if position < 1:
            print("Invalid position.")
            return

        new_node = Node(new_data)

        if position == 1:
            if self.head is None:
                new_node.next = new_node
                self.head = new_node
            else:
                temp = self.head
                while temp.next != self.head:
                    temp = temp.next
                new_node.next = self.head
                temp.next = new_node
                self.head = new_node
            return

        temp = self.head
        for i in range(1, position - 1):
            if temp is None:
                print("Invalid position.")
                return
            temp = temp.next

        new_node.next = temp.next
        temp.next = new_node

    # Function to print the circular linked list
    def print_list(self):
        if self.head is None:
            return
        temp = self.head
        while True:
            print(temp.data, end=" ")
            temp = temp.next
            if temp == self.head:
                break
        print()

# Example usage
if __name__ == "__main__":
    list = CircularLinkedList()

    list.insert_at_beginning(10)
    list.insert_at_beginning(20)
    list.insert_at_end(30)
    list.insert_at_position(2, 40) # Inserting at position 2
    list.print_list()
```

### 2. Deletion
Deletion can be performed at the beginning, at the end, or at a given position in the list.
#### C++ 
```cpp
#include<iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

// Function to insert a node at the beginning of the circular linked list
void insertAtBeginning(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    
    if (head == nullptr) {
        newNode->next = newNode;
        head = newNode;
    } else {
        Node* temp = head;
        while (temp->next != head) {
            temp = temp->next;
        }
        newNode->next = head;
        temp->next = newNode;
        head = newNode;
    }
}

// Function to delete a node at the beginning of the circular linked list
void deleteAtBeginning(Node*& head) {
    if (head == nullptr) return;
    
    if (head->next == head) {
        delete head;
        head = nullptr;
    } else {
        Node* temp = head;
        while (temp->next != head) {
            temp = temp->next;
        }
        Node* tempHead = head;
        head = head->next;
        temp->next = head;
        delete tempHead;
    }
}

// Function to delete a node at the end of the circular linked list
void deleteAtEnd(Node*& head) {
    if (head == nullptr) return;
    
    if (head->next == head) {
        delete head;
        head = nullptr;
    } else {
        Node* temp = head;
        Node* prev = nullptr;
        while (temp->next != head) {
            prev = temp;
            temp = temp->next;
        }
        prev->next = head;
        delete temp;
    }
}

// Function to delete a node at a specific position in the circular linked list
void deleteAtPosition(Node*& head, int position) {
    if (head == nullptr || position < 1) return;

    if (position == 1) {
        deleteAtBeginning(head);
        return;
    }

    Node* temp = head;
    Node* prev = nullptr;
    for (int i = 1; i < position && temp->next != head; ++i) {
        prev = temp;
        temp = temp->next;
    }

    if (temp == head) return;

    prev->next = temp->next;
    delete temp;
}

// Function to print the circular linked list
void printList(Node* head) {
    if (head == nullptr) return;
    Node* temp = head;
    do {
        cout << temp->data << " ";
        temp = temp->next;
    } while (temp != head);
    cout << endl;
}

int main() {
    Node* head = nullptr;
    insertAtBeginning(head, 10);
    insertAtBeginning(head, 20);
    insertAtBeginning(head, 30);
    printList(head);
    deleteAtEnd(head);
    printList(head);
    deleteAtBeginning(head);
    printList(head);
    deleteAtPosition(head, 1); // Deleting node at position 1
    printList(head);
    return 0;
}
```
#### Java
```java
class Node {
    int data;
    Node next;
    
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class CircularLinkedList {
    Node head;

    // Function to insert a node at the beginning of the circular linked list
    void insertAtBeginning(int newData) {
        Node newNode = new Node(newData);
        
        if (head == null) {
            newNode.next = newNode;
            head = newNode;
            return;
        }
        
        Node temp = head;
        while (temp.next != head) {
            temp = temp.next;
        }
        
        newNode.next = head;
        temp.next = newNode;
        head = newNode;
    }

    // Function to delete a node at the beginning of the circular linked list
    void deleteAtBeginning() {
        if (head == null) return;
        
        if (head.next == head) {
            head = null;
            return;
        }
        
        Node temp = head;
        while (temp.next != head) {
            temp = temp.next;
        }
        
        Node tempHead = head;
        head = head.next;
        temp.next = head;
        tempHead = null;
    }

    // Function to delete a node at the end of the circular linked list
    void deleteAtEnd() {
        if (head == null) return;
        
        if (head.next == head) {
            head = null;
            return;
        }
        
        Node temp = head;
        Node prev = null;
        while (temp.next != head) {
            prev = temp;
            temp = temp.next;
        }
        prev.next = head;
        temp = null;
    }

    // Function to delete a node at a specific position in the circular linked list
    void deleteAtPosition(int position) {
        if (head == null || position < 1) return;

        if (position == 1) {
            deleteAtBeginning();
            return;
        }

        Node temp = head;
        Node prev = null;
        for (int i = 1; i < position && temp.next != head; ++i) {
            prev = temp;
            temp = temp.next;
        }

        if (temp == head) return;

        prev.next = temp.next;
        temp = null;
    }

    // Function to print the circular linked list
    void printList() {
        if (head == null) return;
        Node temp = head;
        do {
            System.out.print(temp.data + " ");
            temp = temp.next;
        } while (temp != head);
        System.out.println();
    }

    public static void main(String[] args) {
        CircularLinkedList list = new CircularLinkedList();

        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtBeginning(30);
        list.printList();

        list.deleteAtEnd();
        list.printList();

        list.deleteAtBeginning();
        list.printList();

        list.deleteAtPosition(1); // Deleting node at position 1
        list.printList();
    }
}
```
#### Python
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class CircularLinkedList:
    def __init__(self):
        self.head = None

    # Function to insert a node at the beginning of the circular linked list
    def insert_at_beginning(self, new_data):
        new_node = Node(new_data)
        
        if self.head is None:
            new_node.next = new_node
            self.head = new_node
            return
        
        temp = self.head
        while temp.next != self.head:
            temp = temp.next
        
        new_node.next = self.head
        temp.next = new_node
        self.head = new_node

    # Function to delete a node at the beginning of the circular linked list
    def delete_at_beginning(self):
        if self.head is None:
            return
        
        if self.head.next == self.head:
            self.head = None
            return
        
        temp = self.head
        while temp.next != self.head:
            temp = temp.next
        
        temp_head = self.head
        self.head = self.head.next
        temp.next = self.head
        temp_head = None

    # Function to delete a node at the end of the circular linked list
    def delete_at_end(self):
        if self.head is None:
            return
        
        if self.head.next == self.head:
            self.head = None
            return
        
        temp = self.head
        prev = None
        while temp.next != self.head:
            prev = temp
            temp = temp.next
        prev.next = self.head
        temp = None

    # Function to delete a node at a specific position in the circular linked list
    def delete_at_position(self, position):
        if self.head is None or position < 1:
            return

        if position == 1:
            self.delete_at_beginning()
            return

        temp = self.head
        prev = None
        for i in range(1, position):
            prev = temp
            temp = temp.next

        if temp == self.head:
            return

        prev.next = temp.next
        temp = None

    # Function to print the circular linked list
    def print_list(self):
        if self.head is None:
            return
        temp = self.head
        while True:
            print(temp.data, end=" ")
            temp = temp.next
            if temp == self.head:
                break
        print()

# Example usage
if __name__ == "__main__":
    list = CircularLinkedList()

    list.insert_at_beginning(10)
    list.insert_at_beginning(20)
    list.insert_at_beginning(30)
    list.print_list()

    list.delete_at_end()
    list.print_list()

    list.delete_at_beginning()
    list.print_list()

    list.delete_at_position(1) # Deleting node at position 1
    list.print_list()
```

### 3. Traversal
Traversal involves visiting each node in the list and performing an action on it, such as printing the node's data.

#### Example: Printing All Elements
Traverse from the head to the end of the list, printing each node's data.

#### C++
```cpp
#include <iostream>
using namespace std;
struct Node {
    int data;
    Node* next;
};

void insertAtBeginning(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    
    if (head == nullptr) {
        newNode->next = newNode;
        head = newNode;
    } else {
        Node* temp = head;
        while (temp->next != head) {
            temp = temp->next;
        }
        newNode->next = head;
        temp->next = newNode;
        head = newNode;
    }
}

void printList(Node* head) {
    if (head == nullptr) return;
    Node* temp = head;
    do {
        cout << temp->data << " ";
        temp = temp->next;
    } while (temp != head);
    cout << endl;
}

int main() {
    Node* head = nullptr;
    insertAtBeginning(head, 10);
    insertAtBeginning(head, 20);
    insertAtBeginning(head, 30);
    printList(head);
    return 0;
}
```
```java
class Node {
    int data;
    Node next;

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class CircularLinkedList {
    Node head;

    // Function to insert a node at the beginning of the circular linked list
    void insertAtBeginning(int newData) {
        Node newNode = new Node(newData);

        if (head == null) {
            newNode.next = newNode;
            head = newNode;
            return;
        }

        Node temp = head;
        while (temp.next != head) {
            temp = temp.next;
        }

        newNode.next = head;
        temp.next = newNode;
        head = newNode;
    }

    // Function to print the circular linked list
    void printList() {
        if (head == null) return;
        Node temp = head;
        do {
            System.out.print(temp.data + " ");
            temp = temp.next;
        } while (temp != head);
        System.out.println();
    }

    public static void main(String[] args) {
        CircularLinkedList list = new CircularLinkedList();

        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtBeginning(30);
        list.printList();
    }
}
```
#### Python
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class CircularLinkedList:
    def __init__(self):
        self.head = None

    # Function to insert a node at the beginning of the circular linked list
    def insert_at_beginning(self, new_data):
        new_node = Node(new_data)

        if self.head is None:
            new_node.next = new_node
            self.head = new_node
            return

        temp = self.head
        while temp.next != self.head:
            temp = temp.next

        new_node.next = self.head
        temp.next = new_node
        self.head = new_node

    # Function to print the circular linked list
    def print_list(self):
        if self.head is None:
            return
        temp = self.head
        while True:
            print(temp.data, end=" ")
            temp = temp.next
            if temp == self.head:
                break
        print()

# Example usage
if __name__ == "__main__":
    list = CircularLinkedList()

    list.insert_at_beginning(10)
    list.insert_at_beginning(20)
    list.insert_at_beginning(30)
    list.print_list()
```
### 4. Search
Search involves finding a node with a given value.

### Example: Searching for a Value
Traverse from the head to the end of the list, comparing each node's data with the target value.

#### C++ Code
```cpp
#include <iostream>
using namespace std;
struct Node {
    int data;
    Node* next;
};

void insertAtBeginning(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    
    if (head == nullptr) {
        newNode->next = newNode;
        head = newNode;
    } else {
        Node* temp = head;
        while (temp->next != head) {
            temp = temp->next;
        }
        newNode->next = head;
        temp->next = newNode;
        head = newNode;
    }
}

bool search(Node* head, int target) {
    if (head == nullptr) return false;
    Node* current = head;
    do {
        if (current->data == target) {
            return true;
        }
        current = current->next;
    } while (current != head);
    return false;
}

int main() {
    Node* head = nullptr;
    insertAtBeginning(head, 10);
    insertAtBeginning(head, 20);
    insertAtBeginning(head, 30);

    int target = 20;
    if (search(head, target)) {
        cout << "Element found." << endl;
    } else {
        cout << "Element not found." << endl;
    }
    return 0;
}
```
#### Java
```java
class Node {
    int data;
    Node next;

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class CircularLinkedList {
    Node head;

    // Function to insert a node at the beginning of the circular linked list
    void insertAtBeginning(int newData) {
        Node newNode = new Node(newData);

        if (head == null) {
            newNode.next = newNode;
            head = newNode;
            return;
        }

        Node temp = head;
        while (temp.next != head) {
            temp = temp.next;
        }

        newNode.next = head;
        temp.next = newNode;
        head = newNode;
    }

    // Function to search for a target value in the circular linked list
    boolean search(int target) {
        if (head == null) return false;
        Node current = head;
        do {
            if (current.data == target) {
                return true;
            }
            current = current.next;
        } while (current != head);
        return false;
    }

    public static void main(String[] args) {
        CircularLinkedList list = new CircularLinkedList();

        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtBeginning(30);

        int target = 20;
        if (list.search(target)) {
            System.out.println("Element found.");
        } else {
            System.out.println("Element not found.");
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

class CircularLinkedList:
    def __init__(self):
        self.head = None

    # Function to insert a node at the beginning of the circular linked list
    def insert_at_beginning(self, new_data):
        new_node = Node(new_data)

        if self.head is None:
            new_node.next = new_node
            self.head = new_node
            return

        temp = self.head
        while temp.next != self.head:
            temp = temp.next

        new_node.next = self.head
        temp.next = new_node
        self.head = new_node

    # Function to search for a target value in the circular linked list
    def search(self, target):
        if self.head is None:
            return False
        current = self.head
        while True:
            if current.data == target:
                return True
            current = current.next
            if current == self.head:
                break
        return False

# Example usage
if __name__ == "__main__":
    list = CircularLinkedList()

    list.insert_at_beginning(10)
    list.insert_at_beginning(20)
    list.insert_at_beginning(30)

    target = 20
    if list.search(target):
        print("Element found.")
    else:
        print("Element not found.")
```

## Applications of Linked Lists
1. **Implementation of Stacks and Queues:** Linked lists are used to implement stack and queue data structures.
2. **Dynamic Memory Allocation:** They are used in memory management to allocate and deallocate memory dynamically.
3. **Graph Representation:** Adjacency lists in graph theory are implemented using linked lists.
4. **Symbol Table Management:** In compilers, linked lists are used to manage symbol tables.