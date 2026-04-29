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

````js
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

## 🧱 Stack Class
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

---

## ⏱️ Stack Time Complexity Analysis

| Operation | Time Complexity | Space Complexity | Notes |
|-----------|-----------------|------------------|-------|
| **push(val)** | O(1) | O(1) | Add to front of linked list |
| **pop()** | O(1) | O(1) | Remove from front of linked list |
| **getMin()** | O(n) | O(1) | Must traverse entire list |

**Key Insight**: Stack operations are O(1) because we always work with the `first` node.

---

## 💡 Stack Usage Examples

### 1. **push()** - Add elements to stack
```js
let stack = new Stack();
stack.push(10);  // Stack: [10] ← top
stack.push(20);  // Stack: [20, 10] ← top
stack.push(30);  // Stack: [30, 20, 10] ← top
console.log(stack.size); // 3
````

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

## 🧱 Queue Class

class Node {
constructor(value) {
this.value = value;
this.next = null;
}
}

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

````

---

## ⏱️ Queue Time Complexity Analysis

| Operation | Time Complexity | Space Complexity | Notes |
|-----------|-----------------|------------------|-------|
| **enqueue(val)** | O(1) | O(1) | Add to end of linked list |
| **dequeue()** | O(1) | O(1) | Remove from front of linked list |
| **getMin()** | O(n) | O(1) | Must traverse entire list |

**Key Insight**: Queue operations are O(1) because we track both `first` and `last` pointers.

---

## 💡 Queue Usage Examples

### 1. **enqueue()** - Add elements to queue
```js
let queue = new Queue();
queue.enqueue("Alice");    // Queue: Alice ← front
queue.enqueue("Bob");      // Queue: Alice → Bob ← front
queue.enqueue("Charlie");  // Queue: Alice → Bob → Charlie ← front
console.log(queue.size);   // 3
````

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

## 🔄 Stack vs Queue Comparison

| Aspect                 | Stack (LIFO)         | Queue (FIFO)                |
| ---------------------- | -------------------- | --------------------------- |
| **Ordering**           | Last In, First Out   | First In, First Out         |
| **Primary Operations** | push/pop             | enqueue/dequeue             |
| **Real-world Analogy** | Stack of plates      | Line at store               |
| **Use Cases**          | Undo, function calls | Print jobs, task scheduling |
| **Implementation**     | Single pointer (top) | Two pointers (front/back)   |

### Visual Comparison:

```
Stack Operations:
push(1) → [1]
push(2) → [2, 1]
push(3) → [3, 2, 1]
pop()   → [2, 1]     (removes 3)

Queue Operations:
enqueue(1) → [1]
enqueue(2) → [1, 2]
enqueue(3) → [1, 2, 3]
dequeue()  → [2, 3]  (removes 1)
```

---

## 🎯 Key Takeaways

1. **Stack**: Perfect for LIFO scenarios (undo, backtracking, function calls)
2. **Queue**: Ideal for FIFO scenarios (processing in order, task scheduling)
3. **Linked List Advantage**: Dynamic sizing, no capacity limits
4. **getMin() Trade-off**: O(n) traversal vs O(1) operations for main functionality
5. **Memory**: Each element uses extra space for `next` pointer
6. **Thread Safety**: Neither implementation is thread-safe (would need locks)

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
// Test Stack
let stack = new Stack();
stack.push(5);
stack.push(10);
stack.push(15);
console.log(stack.pop()); // 15
console.log(stack.getMin()); // 5
console.log(stack.size); // 2

// Test Queue
let queue = new Queue();
queue.enqueue("A");
queue.enqueue("B");
queue.enqueue("C");
console.log(queue.dequeue()); // "A"
console.log(queue.getMin()); // "B"
console.log(queue.size); // 2
```

This comprehensive guide covers everything you need to understand and implement stacks and queues using linked lists in JavaScript! 🎉

```

```
