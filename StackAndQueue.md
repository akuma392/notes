# Stack and Queue Implementation using Linked List (JavaScript)

## 📚 Overview

**Stacks** and **Queues** are fundamental data structures that follow specific ordering principles:

### 🥞 Stack (LIFO - Last In, First Out)

- **Analogy**: Stack of plates - you add/remove from the top
- **Operations**: push (add), pop (remove), peek (view top)
- **Use cases**: Function call stack, undo operations, browser back button

### 🏪 Queue (FIFO - First In, First Out)

- **Analogy**: Line at a store - first person in line is served first
- **Operations**: enqueue (add), dequeue (remove), peek (view front)
- **Use cases**: Print queues, task scheduling, breadth-first search

### Why Linked List Implementation?

- ✅ Dynamic size (no fixed capacity)
- ✅ O(1) operations for push/pop and enqueue/dequeue
- ✅ Memory efficient (no wasted space like arrays)

---

## 🧱 Node Class

```js
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}
```

## 🧱 Stack Class (Linked List Implementation)

```js
class Stack {
  constructor() {
    this.first = null;
    this.last = null;
    this.size = 0;
  }
  push(val) {
    var node = new Node(val);

    if (!this.first) {
      this.first = node;
      this.last = node;
    } else {
      var tmp = this.first;
      this.first = node;
      this.first.next = tmp;
    }

    return ++this.size;
  }
  pop() {
    if (!this.first) return null;
    let temp = this.first;
    if (this.first === this.last) {
      this.last = null;
    }
    this.first = this.first.next;
    this.size--;
    return temp.value;
  }
  getMin() {
    let min = this.first.value;
    let current = this.first;
    while (current.next) {
      if (min > current.value) {
        min = current.value;
      }
      current = current.next;
    }
    return min;
  }
}
```

## 🧱 Stack Class (Array Implementation)

```js
class Stack {
  constructor() {
    this.items = [];
  }

  // Add element to top of stack
  push(value) {
    this.items.push(value);
    return this.items.length; // Return new size
  }

  // Remove and return element from top of stack
  pop() {
    if (this.isEmpty()) return null;
    return this.items.pop();
  }

  // View element at top of stack without removing it
  peek() {
    if (this.isEmpty()) return null;
    return this.items[this.items.length - 1];
  }

  // Check if stack is empty
  isEmpty() {
    return this.items.length === 0;
  }

  // Get size of stack
  size() {
    return this.items.length;
  }

  // Clear all elements from stack
  clear() {
    this.items = [];
  }

  // Get minimum value (O(n) - same as linked list)
  getMin() {
    if (this.isEmpty()) return null;
    let min = this.items[0];
    for (let i = 1; i < this.items.length; i++) {
      if (this.items[i] < min) {
        min = this.items[i];
      }
    }
    return min;
  }
}
```

## 🧱 Queue Class (Array Implementation)

```js
class Queue {
  constructor() {
    this.items = [];
  }

  // Add element to end of queue
  enqueue(value) {
    this.items.push(value);
    return this.items.length; // Return new size
  }

  // Remove and return element from front of queue
  dequeue() {
    if (this.isEmpty()) return null;
    return this.items.shift(); // shift() removes from front
  }

  // View element at front of queue without removing it
  peek() {
    if (this.isEmpty()) return null;
    return this.items[0];
  }

  // Check if queue is empty
  isEmpty() {
    return this.items.length === 0;
  }

  // Get size of queue
  size() {
    return this.items.length;
  }

  // Clear all elements from queue
  clear() {
    this.items = [];
  }

  // Get minimum value (O(n) - same as linked list)
  getMin() {
    if (this.isEmpty()) return null;
    let min = this.items[0];
    for (let i = 1; i < this.items.length; i++) {
      if (this.items[i] < min) {
        min = this.items[i];
      }
    }
    return min;
  }
}
```

---

## ⏱️ Stack Time Complexity Analysis

### Linked List Implementation

| Operation     | Time Complexity | Space Complexity | Notes                            |
| ------------- | --------------- | ---------------- | -------------------------------- |
| **push(val)** | O(1)            | O(1)             | Add to front of linked list      |
| **pop()**     | O(1)            | O(1)             | Remove from front of linked list |
| **peek()**    | O(1)            | O(1)             | Access first node                |
| **isEmpty()** | O(1)            | O(1)             | Check if first is null           |
| **size()**    | O(1)            | O(1)             | Return size property             |
| **getMin()**  | O(n)            | O(1)             | Must traverse entire list        |

### Array Implementation

| Operation     | Time Complexity | Space Complexity | Notes                      |
| ------------- | --------------- | ---------------- | -------------------------- |
| **push(val)** | O(1)            | O(1)             | Add to end of array        |
| **pop()**     | O(1)            | O(1)             | Remove from end of array   |
| **peek()**    | O(1)            | O(1)             | Access last element        |
| **isEmpty()** | O(1)            | O(1)             | Check array length         |
| **size()**    | O(1)            | O(1)             | Return array length        |
| **getMin()**  | O(n)            | O(1)             | Must traverse entire array |

**Key Insight**: Array implementation is simpler but may need resizing. Linked list uses more memory per element but is truly dynamic.

---

## 💡 Stack Usage Examples

### Linked List vs Array Implementation

```js
// Linked List Stack (better for large datasets)
let linkedStack = new Stack(); // The linked list version
linkedStack.push(10);
linkedStack.push(20);
console.log(linkedStack.pop()); // 20
console.log(linkedStack.peek()); // 10
console.log(linkedStack.size()); // 1

// Array Stack (simpler, good for small datasets)
class ArrayStack {
  constructor() {
    this.items = [];
  }
  push(value) {
    return this.items.push(value);
  }
  pop() {
    return this.items.length ? this.items.pop() : null;
  }
  peek() {
    return this.items.length ? this.items[this.items.length - 1] : null;
  }
  isEmpty() {
    return this.items.length === 0;
  }
  size() {
    return this.items.length;
  }
}

let arrayStack = new ArrayStack();
arrayStack.push(10);
arrayStack.push(20);
console.log(arrayStack.pop()); // 20
console.log(arrayStack.peek()); // 10
console.log(arrayStack.size()); // 1
```

### 2. **pop()** - Remove from top

```js
let removed = stack.pop(); // Returns 30
console.log(removed); // 30
// Stack now: [20, 10] ← top
console.log(stack.size); // 2
```

### 3. **getMin()** - Find minimum value

```js
stack.push(5); // Stack: [5, 20, 10] ← top
stack.push(50); // Stack: [50, 5, 20, 10] ← top
console.log(stack.getMin()); // 5 (traverses all elements)
```

### 4. **Real-world Example: Browser Back Button**

```js
class BrowserHistory {
  constructor() {
    this.history = new Stack();
    this.current = null;
  }

  visit(page) {
    if (this.current) {
      this.history.push(this.current);
    }
    this.current = page;
    console.log(`Visited: ${page}`);
  }

  back() {
    if (this.history.size > 0) {
      this.current = this.history.pop();
      console.log(`Went back to: ${this.current}`);
      return this.current;
    }
    console.log("No more pages to go back to!");
    return null;
  }
}

let browser = new BrowserHistory();
browser.visit("google.com");
browser.visit("github.com");
browser.visit("stackoverflow.com");
browser.back(); // Goes back to github.com
browser.back(); // Goes back to google.com
```

---

## 🧱 Queue Class (Linked List Implementation)

```js
class Queue {
  constructor() {
    this.first = null;
    this.last = null;
    this.size = 0;
  }
  enqueue(val) {
    var newNode = new Node(val);
    if (!this.first) {
      this.first = newNode;
      this.last = newNode;
    } else {
      this.last.next = newNode;
      this.last = newNode;
    }
    return ++this.size;
  }

  dequeue() {
    if (!this.first) return undefined;
    let temp = this.first;
    if (this.first === this.last) {
      this.last = null;
    }
    this.first = this.first.next;
    this.size--;
    return temp.value;
  }
  getMin() {
    let min = this.first.value;
    let current = this.first;
    while (current.next) {
      if (min > current.value) {
        min = current.value;
      }
      current = current.next;
    }
    return min;
  }
}
```

---

## ⏱️ Queue Time Complexity Analysis

### Linked List Implementation

| Operation        | Time Complexity | Space Complexity | Notes                            |
| ---------------- | --------------- | ---------------- | -------------------------------- |
| **enqueue(val)** | O(1)            | O(1)             | Add to end of linked list        |
| **dequeue()**    | O(1)            | O(1)             | Remove from front of linked list |
| **peek()**       | O(1)            | O(1)             | Access first node                |
| **isEmpty()**    | O(1)            | O(1)             | Check if first is null           |
| **size()**       | O(1)            | O(1)             | Return size property             |
| **getMin()**     | O(n)            | O(1)             | Must traverse entire list        |

### Array Implementation

| Operation        | Time Complexity | Space Complexity | Notes                               |
| ---------------- | --------------- | ---------------- | ----------------------------------- |
| **enqueue(val)** | O(1)            | O(1)             | Add to end of array                 |
| **dequeue()**    | O(n)            | O(1)             | Remove from front (shift operation) |
| **peek()**       | O(1)            | O(1)             | Access first element                |
| **isEmpty()**    | O(1)            | O(1)             | Check array length                  |
| **size()**       | O(1)            | O(1)             | Return array length                 |
| **getMin()**     | O(n)            | O(1)             | Must traverse entire array          |

**Key Insight**: Array dequeue is O(n) due to shifting elements. Linked list is better for frequent dequeue operations.

---

## 💡 Queue Usage Examples

### Linked List vs Array Implementation

```js
// Linked List Queue (better for frequent dequeue operations)
let linkedQueue = new Queue(); // The linked list version
linkedQueue.enqueue("Alice");
linkedQueue.enqueue("Bob");
console.log(linkedQueue.dequeue()); // "Alice"
console.log(linkedQueue.peek()); // "Bob"
console.log(linkedQueue.size()); // 1

// Array Queue (simple, but dequeue is O(n))
class ArrayQueue {
  constructor() {
    this.items = [];
  }
  enqueue(value) {
    return this.items.push(value);
  }
  dequeue() {
    return this.items.length ? this.items.shift() : null;
  }
  peek() {
    return this.items.length ? this.items[0] : null;
  }
  isEmpty() {
    return this.items.length === 0;
  }
  size() {
    return this.items.length;
  }
}

let arrayQueue = new ArrayQueue();
arrayQueue.enqueue("Alice");
arrayQueue.enqueue("Bob");
console.log(arrayQueue.dequeue()); // "Alice"
console.log(arrayQueue.peek()); // "Bob"
console.log(arrayQueue.size()); // 1
```

### 2. **dequeue()** - Remove from front

```js
let served = queue.dequeue(); // Returns "Alice"
console.log(served); // "Alice"
// Queue now: Bob → Charlie ← front
console.log(queue.size); // 2
```

### 3. **getMin()** - Find minimum value

```js
queue.enqueue("1"); // Queue: Bob → Charlie → "1" ← front
queue.enqueue("2"); // Queue: Bob → Charlie → "1" → "2" ← front
console.log(queue.getMin()); // "1" (traverses all elements)
```

### 4. **Real-world Example: Print Queue**

```js
class PrintQueue {
  constructor() {
    this.queue = new Queue();
  }

  addPrintJob(document) {
    this.queue.enqueue(document);
    console.log(`Added to print queue: ${document}`);
  }

  processPrintJob() {
    if (this.queue.size > 0) {
      let document = this.queue.dequeue();
      console.log(`Printing: ${document}`);
      return document;
    }
    console.log("Print queue is empty!");
    return null;
  }
}

let printer = new PrintQueue();
printer.addPrintJob("report.pdf");
printer.addPrintJob("presentation.pptx");
printer.addPrintJob("resume.docx");

printer.processPrintJob(); // Prints report.pdf first
printer.processPrintJob(); // Prints presentation.pptx second
```

---

## 🔄 Implementation Comparison

| Aspect                        | Linked List                         | Array                      |
| ----------------------------- | ----------------------------------- | -------------------------- |
| **Memory Usage**              | Higher (next pointers)              | Lower (just data)          |
| **Dynamic Sizing**            | Truly dynamic                       | May need resizing          |
| **Stack Performance**         | All operations O(1)                 | All operations O(1)        |
| **Queue Performance**         | All operations O(1)                 | dequeue() is O(n)          |
| **Implementation Complexity** | More complex                        | Simpler                    |
| **Best Use Case**             | Large datasets, frequent operations | Small datasets, simple use |

### When to Use Each Implementation:

**Linked List:**

- ✅ Large datasets where memory efficiency matters
- ✅ Frequent enqueue/dequeue operations (for queues)
- ✅ Need true dynamic sizing without reallocation

**Array:**

- ✅ Simpler implementation and understanding
- ✅ Small to medium datasets
- ✅ When you want to avoid pointer overhead
- ✅ Good for stacks (all operations O(1))

---

## 🎯 Key Takeaways

1. **Stack vs Queue**: LIFO vs FIFO ordering principles
2. **Linked List vs Array**: Trade-offs between memory usage and performance
3. **Stack Performance**: Both implementations are O(1) for all operations
4. **Queue Performance**: Linked list is O(1) for all, array dequeue is O(n)
5. **Memory**: Linked list uses more memory per element (pointers)
6. **Use Cases**: Choose based on data size and operation frequency
7. **getMin()**: Always O(n) regardless of implementation
8. **Thread Safety**: None of these implementations are thread-safe

### Quick Decision Guide:

- **Small dataset + simple code** → Array implementation
- **Large dataset + performance** → Linked list implementation
- **Stack operations** → Either implementation works well
- **Heavy queue usage** → Linked list (avoid array shift() performance)

---

## 🚀 Advanced Variations

### 1. **Min Stack** (O(1) getMin)

```js
class MinStack {
  constructor() {
    this.stack = [];
    this.minStack = []; // Tracks minimums
  }

  push(val) {
    this.stack.push(val);
    // Push to minStack if val is smaller than current min
    if (
      this.minStack.length === 0 ||
      val <= this.minStack[this.minStack.length - 1]
    ) {
      this.minStack.push(val);
    }
  }

  pop() {
    if (this.stack.pop() === this.minStack[this.minStack.length - 1]) {
      this.minStack.pop();
    }
  }

  getMin() {
    return this.minStack[this.minStack.length - 1];
  }
}
```

### 2. **Circular Queue** (Fixed Size)

```js
class CircularQueue {
  constructor(capacity) {
    this.capacity = capacity;
    this.queue = new Array(capacity);
    this.front = -1;
    this.rear = -1;
    this.size = 0;
  }

  enqueue(val) {
    if (this.size === this.capacity) return false; // Full
    this.rear = (this.rear + 1) % this.capacity;
    this.queue[this.rear] = val;
    if (this.front === -1) this.front = 0;
    this.size++;
    return true;
  }

  dequeue() {
    if (this.size === 0) return null; // Empty
    let val = this.queue[this.front];
    this.front = (this.front + 1) % this.capacity;
    this.size--;
    if (this.size === 0) {
      this.front = -1;
      this.rear = -1;
    }
    return val;
  }
}
```

---

## 🧪 Testing Your Implementation

```js
// Test Linked List Stack
console.log("=== Linked List Stack ===");
let linkedStack = new Stack();
linkedStack.push(5);
linkedStack.push(10);
linkedStack.push(15);
console.log("Pop:", linkedStack.pop()); // 15
console.log("Peek:", linkedStack.peek()); // 10
console.log("Size:", linkedStack.size()); // 2
console.log("Min:", linkedStack.getMin()); // 5

// Test Array Stack
console.log("\n=== Array Stack ===");
class ArrayStack {
  constructor() {
    this.items = [];
  }
  push(val) {
    return this.items.push(val);
  }
  pop() {
    return this.items.pop() || null;
  }
  peek() {
    return this.items[this.items.length - 1] || null;
  }
  size() {
    return this.items.length;
  }
  getMin() {
    if (!this.items.length) return null;
    return Math.min(...this.items);
  }
}

let arrayStack = new ArrayStack();
arrayStack.push(5);
arrayStack.push(10);
arrayStack.push(15);
console.log("Pop:", arrayStack.pop()); // 15
console.log("Peek:", arrayStack.peek()); // 10
console.log("Size:", arrayStack.size()); // 2
console.log("Min:", arrayStack.getMin()); // 5

// Test Linked List Queue
console.log("\n=== Linked List Queue ===");
let linkedQueue = new Queue();
linkedQueue.enqueue("A");
linkedQueue.enqueue("B");
linkedQueue.enqueue("C");
console.log("Dequeue:", linkedQueue.dequeue()); // "A"
console.log("Peek:", linkedQueue.peek()); // "B"
console.log("Size:", linkedQueue.size()); // 2

// Test Array Queue
console.log("\n=== Array Queue ===");
class ArrayQueue {
  constructor() {
    this.items = [];
  }
  enqueue(val) {
    return this.items.push(val);
  }
  dequeue() {
    return this.items.shift() || null;
  }
  peek() {
    return this.items[0] || null;
  }
  size() {
    return this.items.length;
  }
}

let arrayQueue = new ArrayQueue();
arrayQueue.enqueue("A");
arrayQueue.enqueue("B");
arrayQueue.enqueue("C");
console.log("Dequeue:", arrayQueue.dequeue()); // "A"
console.log("Peek:", arrayQueue.peek()); // "B"
console.log("Size:", arrayQueue.size()); // 2
```

This comprehensive guide covers everything you need to understand and implement stacks and queues using linked lists in JavaScript! 🎉

```

```
