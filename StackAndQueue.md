
# Stack Implementation using Linked List (JavaScript)

## 🧱 Node Class

```js
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}
class Stack{
    constructor(){
        this.first = null;
        this.last = null;     
        this.size = 0;
    }
    push(val){
        var node = new Node(val);

        if (!this.first){
            this.first = node;
            this.last = node;
        } else {
            var tmp = this.first;
            this.first=node;
            this.first.next=tmp;
        }

        return ++this.size;
    }
    pop(){
        if(!this.first) return null;
        let temp = this.first
        if(this.first === this.last){
            this.last = null;
        }
        this.first = this.first.next;
        this.size--;
        return temp.value
    }
    getMin(){
      let min = this.first.value;
      let current = this.first;
      while(current.next){
       if(min > current.value) {
         min = current.value
        }
       current=current.next;
      }
     return min;
    }
        
}

class Node {
    constructor(value){
        this.value = value;
        this.next = null;
    }
}

class Queue {
    constructor(){
        this.first = null;
        this.last = null;
        this.size = 0;
    }
    enqueue(val){
        var newNode = new Node(val);
        if(!this.first){
            this.first = newNode;
            this.last = newNode;
        } else {
            this.last.next = newNode;
            this.last = newNode;
        }
        return ++this.size;
    }

    dequeue(){
        if(!this.first) return undefined;
        let temp = this.first;
        if(this.first === this.last){
            this.last = null;
        }
        this.first = this.first.next;
        this.size--;
        return temp.val
    }
}
