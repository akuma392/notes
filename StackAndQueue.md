
# Stack Implementation using Linked List (JavaScript)

## 🧱 Node Class

```js
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}
class Stack {
  constructor() {
    this.first = null; // top of stack
    this.last = null;  // bottom of stack
    this.size = 0;
  }

  // 🔼 Push (Add to top)
  push(val) {
    let newNode = new Node(val);

    if (!this.first) {
      this.first = this.last = newNode;
    } else {
      newNode.next = this.first;
      this.first = newNode;
    }

    return ++this.size;
  }

  // 🔽 Pop (Remove from top)
  pop() {
    if (!this.first) return null;

    let temp = this.first;

    if (this.first === this.last) {
      this.last = null;
    }

    this.first = this.first.next;
    temp.next = null; // cleanup reference

    this.size--;
    return temp.value;
  }
}
