# Linked List Implementation in Go (Golang)

A Linked List implementation in Go (Golang) typically uses **`struct`** and **pointers**. To make it understandable even for someone with no prior data structures knowledge, I will show the two main structures that form the Linked List, followed by a basic insertion (prepend) function.

---

## Go Linked List Implementation

To implement a Linked List in Go, we need two main structures: **Node** and **LinkedList**.

### 1. Structure Definitions

```go
package main

import "fmt"

// 1. NODE Structure
// Holds each piece of data and the address of the next node.
type Node struct {
    Data int     // The data held by this node
    Next *Node   // A pointer to the next node (its address)
}

// 2. LINKED LIST Structure
// Holds only the starting point (Head) of the entire list.
type LinkedList struct {
    Head *Node // Pointer indicating the first node of the list
}
```

### 2. Basic Function: Insertion at the Beginning (Prepend)
Adding a new element to the beginning of the list (Prepend) is one of the simplest and fastest operations in Linked Lists.

```go
// Inserts a new value at the beginning of the list.
func (list *LinkedList) Prepend(data int) {
    // 1. Create the new node.
    newNode := &Node{
        Data: data,
        Next: nil, // Initially, the next node is nil (empty)
    }

    // 2. Point the 'Next' pointer of the new node to the current start (Head) of the list.
    newNode.Next = list.Head

    // 3. Move the list's 'Head' pointer to the new node.
    // The new node is now the new beginning of the list.
    list.Head = newNode
}
```

### 3. Usage Example
Now let's see how to use this structure:

```go
func main() {
    // Create an empty Linked List
    myList := LinkedList{}

    // Prepend elements to the beginning of the list:
    fmt.Println("Adding elements to the list...")
    myList.Prepend(10) // 10 added, list: 10
    myList.Prepend(20) // 20 added, list: 20 -> 10
    myList.Prepend(30) // 30 added, list: 30 -> 20 -> 10

    // Printing the list
    currentNode := myList.Head
    fmt.Print("List Content: ")
    for currentNode != nil {
        fmt.Print(currentNode.Data, " -> ")
        currentNode = currentNode.Next // Move to the next node
    }
    fmt.Println("nil")
}
```

Output:

```
Adding elements to the list...
List Content: 30 -> 20 -> 10 -> nil
```

## Key Points in the Example
* **Pointer:** The *Node structure is a pointer in Go. This pointer allows the list to be flexible; the nodes do not need to be side-by-side in memory, they only need to know each other's address.
* **list.Head:** Knowing only the starting point of the list is enough to manage the list.
* **newNode.Next** = list.Head: This line is the magic of Linked Lists. The new node is linked to the start of the old list, ensuring the rest of the list is not lost.

**Sources:**
Gemini