# Singly Linked List (JavaScript)

## � Overview

A **Linked List** is a linear data structure where elements are stored in nodes. Each node contains:

- **value**: The data stored in the node
- **next**: A pointer/reference to the next node in the list

Unlike arrays, linked lists don't require contiguous memory allocation, making them efficient for dynamic insertion/deletion operations.

### When to Use Linked Lists:

- When you need frequent insertions/deletions in the middle
- When memory is fragmented and you can't allocate large contiguous blocks
- Implementing stacks, queues, graphs
- Memory-constrained environments where you want dynamic size

### Advantages vs Arrays:

- ✅ O(1) insertion/deletion at known position
- ✅ No need to allocate contiguous memory
- ✅ Dynamic size grows as needed
- ❌ No random access (must traverse from head)
- ❌ Extra memory for storing pointers

---

## �📌 Implementation

```js
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class LinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
    this.length = 0;
  }

  push(value) {
    let newNode = new Node(value);

    if (!this.head) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      this.tail.next = newNode;
      this.tail = newNode;
    }

    this.length++;
    return this;
  }
  pop() {
    if (!this.head) return undefined;
    let current = this.head;
    let newTail = current;
    while (current.next) {
      newTail = current;
      current = current.next;
    }
    this.tail = newTail;
    this.tail.next = null;
    this.length--;
    if (this.length === 0) {
      this.head = null;
      this.tail = null;
    }
    return current;
  }
  shift() {
    if (!this.head) return undefined;
    let temp = this.head;
    this.head = temp.next;
    temp.next = null;
    this.length--;
    if (this.length === 1) {
      this.head = null;
      this.tail = null;
    }
  }
  unshift(value) {
    let newNode = new Node(value);
    if (this.length === 0) {
      this.head = newNode;
      this.tail = this.head;
    } else {
      newNode.next = this.head;
      this.head = newNode;
    }
    this.length++;
    return this;
  }
  get(index) {
    if (index < 0 || index > this.length) {
      return null;
    }
    let current = this.head;
    let counter = 0;
    while (counter !== index) {
      current = current.next;
      counter++;
    }
    return current;
  }
  set(index, value) {
    let node = this.get(index);
    if (!node) {
      return false;
    }
    node.value = value;
    return true;
  }
  insert(index, value) {
    if (index < 0 || index > this.length) return false;
    if (index === this.length) return !!this.push(value);
    if (index === 0) return !!this.unshift(value);
    let newNode = new Node(value);
    let prev = this.get(index - 1);
    let temp = prev.next;
    prev.next = newNode;
    newNode.next = temp;
    this.length++;
    return true;
  }
  remove(index) {
    if (index < 0 || index >= this.length) return undefined;
    if (index === 0) return this.shift();
    if (index === this.length - 1) return this.pop();
    let prev = this.get(index - 1);
    let removed = prev.next;
    prev.next = removed.next;
    removed.next = null;
    this.length--;
    return removed;
  }
  reverse() {
    let prev = null;
    let current = this.head;

    // swap head and tail
    this.tail = this.head;

    while (current) {
      let next = current.next; // store next
      current.next = prev;     // reverse link

      prev = current;          // move prev
      current = next;          // move current
    }

    this.head = prev; // new head
    return this;
  }
}
```

---

## ⏱️ Time Complexity Analysis

| Operation | Time Complexity | Space Complexity | Notes |
|-----------|-----------------|------------------|-------|
| **push()** | O(1) | O(1) | Append to end (we track tail) |
| **pop()** | O(n) | O(1) | Must traverse to find second-to-last node |
| **shift()** | O(1) | O(1) | Remove from start (update head) |
| **unshift()** | O(1) | O(1) | Add to start (update head) |
| **get(index)** | O(n) | O(1) | Must traverse from head to index |
| **set(index, value)** | O(n) | O(1) | Uses get() internally |
| **insert(index, value)** | O(n) | O(1) | Worst case: traverse to index |
| **remove(index)** | O(n) | O(1) | Worst case: traverse to index |

**Key Insight**: Operations at the **start** are O(1), but operations in the **middle/end** are O(n) because we lack random access.

---

## 💡 Usage Examples

### 1. **push()** - Add element to end
```js
let list = new LinkedList();
list.push(10);   // List: 10
list.push(20);   // List: 10 → 20
list.push(30);   // List: 10 → 20 → 30
```
- **Time**: O(1) - Direct access to tail
- **Use case**: Building list from data stream

### 2. **pop()** - Remove from end
```js
list.pop();      // Removes 30, returns Node(30)
                 // List: 10 → 20
```
- **Time**: O(n) - Must traverse to find second-to-last node
- **Why slow**: Singly linked lists can't traverse backwards!

### 3. **shift()** - Remove from start
```js
list.shift();    // Removes 10, returns Node(10)
                 // List: 20
```
- **Time**: O(1) - Update head pointer
- **Best operation**: Very efficient for removing first element

### 4. **unshift()** - Add to start
```js
list.unshift(5); // List: 5 → 20
list.unshift(1); // List: 1 → 5 → 20
```
- **Time**: O(1) - Update head pointer
- **Use case**: Prepending elements (like browser history)

### 5. **get(index)** - Access element at index
```js
let node = list.get(1);  // Returns Node(5)
node.value;              // 5
```
- **Time**: O(n) - Must traverse from head
- **Limitation**: No random access like arrays

### 6. **set(index, value)** - Update value at index
```js
list.set(0, 100); // Change first element to 100
                  // List: 100 → 5 → 20
```
- **Time**: O(n) - Uses get() internally

### 7. **insert(index, value)** - Insert at specific position
```js
list.insert(1, 15);  // Insert 15 at index 1
                     // List: 100 → 15 → 5 → 20
```
- **Time**: O(n) - Worst case traverse to index
- **Advantage over arrays**: O(1) once you find the position

### 8. **remove(index)** - Remove element at index
```js
let removed = list.remove(1); // Remove element at index 1 (value 15)
                              // List: 100 → 5 → 20
```
- **Time**: O(n) - Must traverse to find previous node
- **Special cases**: Optimized O(1) for index 0 and last index

---

## 🔍 Detailed Example: Building & Manipulating a List

```js
let myList = new LinkedList();

// Build list: 1 → 2 → 3 → 4 → 5
myList.push(2).push(3).push(4).push(5);
myList.unshift(1);  // Add at start
console.log(myList.length);  // 5

// Access and modify
console.log(myList.get(2).value);  // 3
myList.set(2, 30);                  // Change 3 to 30

// Insert in middle
myList.insert(3, 35);  // List becomes: 1 → 2 → 30 → 35 → 4 → 5

// Remove elements
myList.remove(1);      // Remove 2
myList.pop();          // Remove last (5)
myList.shift();        // Remove first (1)
// Final list: 30 → 35 → 4
```

---

## 🎯 Key Takeaways

1. **Sequential Access**: Must start from head; no direct access to elements
2. **Start Operations are Fast**: unshift, shift are O(1)
3. **End Operations are Slow**: pop is O(n) - need to find predecessor
4. **Middle Operations**: insert/remove/get are O(n) due to traversal
5. **Memory Trade-off**: Extra memory for pointers, but flexible size
6. **Best Use Cases**: 
   - Frequent additions/deletions at start
   - LRU caches, browser history
   - Implementing queues/stacks
   - Graphs (adjacency lists)

---

## 📝 Improvement Suggestion: Doubly Linked List

To make **pop()** O(1), use a **Doubly Linked List** where each node has `prev` and `next` pointers.

```js
class DNode {
  constructor(value) {
    this.value = value;
    this.next = null;
    this.prev = null;  // Previous pointer
  }
}
```

With `prev` pointers, you can traverse backwards from tail → O(1) pop() and efficient removal from end.
```
