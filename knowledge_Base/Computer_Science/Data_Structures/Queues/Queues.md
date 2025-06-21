# Queues

**Concept Type**:: #DataStructure #fundamentals
**Mastery Level**:: `🧠 Familiar`
**Date Started**:: 2025-06-15
**Last Revised**::
**Related**:: [[Core|core]], [[Array|array]], [[LinkedList|linkedLis]]
**Tags**::#Queues #array #core

## Core Concept

> _is a data structure that is have a rear (the oldest value) and the front (the newest Value)_

> _is held and access is rectricted to one end_

> _Elements are added in the rear (enqueued) and and removed from the front (dequeued)_

> _This make it a First-in First-Out Data Structure (FIFO)_

## Why Important?

### Useful for

- priting jobs
- handling request in a web server
- scheduling task in system
- can be implemented with array and linkedList

## How It Works

### implementation with Arrays

```javaScript
class Queue {
  constructor() {
    this.items = []
  }

  enqueue(item) {
    this.items.push(item);
  }

  dequeue() {
    if (!this.items) return 'the queue is empty'
  return this.items.pop();
  }

  peek() {
    return this.items[this.items.length - 1];
  }
  isEmpty() {
     return !this.items ? true  :  false;
  }
  size() {
    return this.items.length
  }

  clear() {
    return this.items.splice(0,this.items.this.size());
  }
  print() {

    return this.items.forEach(element => console.log(element));
  }
}


const queue = new Queue
queue.enqueue(0);
queue.enqueue(1);
queue.enqueue(2);
//console.log(queue.dequeue());
//console.log(queue.peek());
//console.log(queue.isEmpty());
//console.log(queue.size());
queue.print();
```

### implementations with linkedList

```javaScript
class Node {

  constructor(data) {
    this.data = data
    this.next = null
  }
}
class Queue {

  constructor() {
    this.rear = null
    this.front = null
    this.size = 0
  }


  enqueue(data) {
    const newNode = new Node(data);
    if (!this.rear) {
      this.rear = newNode;
      this.front = newNode;
    }
    this.rear.next = newNode;
    this.rear = newNode;
    this.size++;
  }
  dequeue() {
    if (!this.front) return null;
    if (!this.front.next) {
      const deletedNode = this.front;
      this.front = null;
      this.rear = null;
      this.size = 0;
      return deletedNode;
    }
    const deletedNode = this.front;
    this.front = this.front.next;
    this.size--;
    return deletedNode;
  }
  peek() {
    if (!this.front) return null;
    return this.front.data;
  }
  isEmpty() {
    return this.size <= 0
  }
  size() {
    return this.size;
  }
}


const myQueue = new Queue();
myQueue.enqueue(0);
myQueue.enqueue(1);
myQueue.enqueue(2);
myQueue.enqueue(3);
//console.log(myQueue);
//myQueue.dequeue();
//console.log(myQueue);
//console.log(myQueue.peek());
console.log(myQueue);
```

## Resources

1. [Official Documentation](https://www.geeksforgeeks.org/dsa/queue-data-structure/)
2. [Key Tutorial]()
3. [Deep Dive Article]()
4. [Practice Platform]()
