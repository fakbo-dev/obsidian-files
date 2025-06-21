# Stacks

**Concept Type**:: #DataStructure #fundamentals
**Mastery Level**:: `🧠 Familiar `
**Date Started**:: 2025-06-21
**Last Revised**::
**Related**:: [[Core|core]], [[LinkedList|linkedLis]],[[Queues|queues]]
**Tags**:: #array #core #stacks #LinkedLists

## Core Concept

> _is a linear data Structure that use the LIFO principle (Last In First Out)_

> _Or FILO (First In Last Out) maintining 3 fundamentals functions_

> _Push: add an element to the collection_

> _Pop: Remove the element from the collection_

> _Peek or Top: return the rear or the front value from the collection_

## Why Important?

- the element is added last is the first to remove
- can be implemented with arrays and linkedList
- undo Mechanisms
- revert previous state
- backtraking

## How It Works

### implement with arr

```javaScript
class Stack {

  constructor() {
    this.items = []
  }

  push(data) {
    this.items.push(data);
  }

  pop() {
    if (this.items) return 'the Stacks in empty'

    return this.items.pop();
  }
  peek() {
    return this.items[this.items.length - 1]
  }
  isEmpty() {
    return this.items.size()  > 0
  }
  size() {
    return this.items.length
  }
}


const myStack = new Stack();
myStack.push(0);
myStack.push(1);
myStack.push(2);
myStack.push(3);
myStack.push(4);
//console.log(myStack);
//console.log(myStack.pop());
//myStack.pop()
//myStack.pop()
//myStack.pop()
//myStack.pop()
//myStack.pop()
console.log(myStack)
//console.log(myStack.peek());
```

### stack with linkedList

```javaScript
class Node {

  constructor(data) {
    this.data = data
    this.next = null
  }
}


class Stack {

  constructor() {
    this.head = null
    this.size = 0
  }

  push(data) {
    const newNode = new Node(data);
    this.size++;
    if (!this.head) {
      this.head = newNode;
      return
    }
    newNode.next = this.head
    this.head = newNode;
    return
  }
  pop() {
    if (!this.head) return null;

    const deleteNode = this.head;

    if (this.head.next === null) {
      this.head = null;
      this.size--;
      return deleteNode.data;
    }
    this.head = this.head.next
    deleteNode.next = null;
    this.size--;
    return deleteNode.data;
  }
  isEmpty() {
    return this.size === 0
  }
}


const myStack = new Stack();
myStack.push(0);
myStack.push(1);
myStack.push(2);
myStack.push(3);
myStack.pop();
console.log(myStack.size);

```

## Resources

1. [Official Documentation]()
2. [Key Tutorial]()
3. [Deep Dive Article]()
4. [Practice Platform]()
