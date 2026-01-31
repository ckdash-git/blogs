---
title: "Linked List in Swift: A Beginner's Guide"
date: 2026-01-31
draft: false
tags: ["Swift", "Data Structures", "iOS"]
description: "An introduction to Singly Linked Lists and how to implement them in Swift."
authors: ["ckdash"]
---

Hello everyone! In this article, we will discuss the **Linked List** data structure and write a program in Swift to understand how it works.

## Singly Linked List
A Linked List is a container-like structure where each element is a **Node**. A node contains two things:
1. **Value**: The actual data.
2. **Next**: The address (reference) of the next Node.

The starting node is called the **Head**, and the last node (which refers to `nil`) is called the **Tail**.



**Example:**
`Head -> [1] -> [2] -> [3] -> Nil`

---

## 1. Creating the Node Class
We use a generic class so our Linked List can store any data type.

```swift
class Node<T> {
    var value: T
    var next: Node?
    
    init(value: T) {
        self.value = value
        self.next = nil
    }
}

2. Creating the Linked List Class

The LinkedList class keeps track of the head.

class LinkedList<T> {
    var head: Node<T>?
    
    func isEmpty() -> Bool {
        return head == nil
    }
}

3. Inserting Nodes (Append)

To add a node, we traverse to the end of the list and link the new node to the last node's next property.

func append(_ value: T) {
    let newNode = Node(value: value)
    
    if head == nil {
        head = newNode
        return
    }
    
    var current = head
    while current?.next != nil {
        current = current?.next
    }
    current?.next = newNode
}

4. Displaying the List

We iterate through the list and print each value until we hit nil.

func display() {
    var current = head
    while current != nil {
        print(current!.value, terminator: " -> ")
        current = current?.next
    }
    print("nil")
}

Full Implementation & Usage

var list = LinkedList<String>()
list.append("Chandan")
list.append("Kumar")
list.append("Dash")

list.display()
// Output: Chandan -> Kumar -> Dash -> nil

Thank you for reading! If you found this helpful, stay tuned for more Swift content.
