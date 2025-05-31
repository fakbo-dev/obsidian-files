---
id: LinkedList
aliases: [[control structures]]
tags: []
---

Reference: [[Data Structured & Algorithm]]

Important Data Structure that allows to Insert and delete Data in a efficient way, despite arrays, linkedList store memory in the nodes,
Entry point for stacks and qeue.

Structure:

- Node
- Item
- Reference for the next node
- the first value is called Head
- the last value is called tail

# DIfference Between common Arrays

## LinkedLists

- Acces: Secuential
- Data Structure: no-Contiguous
- Inserting and Deleting Data: Exelent
- Memory: located in the nodes

## Arrays

- Acces: Random
- Data Structure: Contiguous
- Inserting and Deleting Data: Defficient
- Memory: Alocated in the whole Array

# Basic Of Linked List

### Single Linked List

is a data structure made for node wich contain a element and a reference to other node, the head is called "head" and is reference is the next node in sequence. for default the nodes referece is null and you need to attach the next node, the last node in the list is called tails and his ference is always null

#### Traversal Singly Linked List

means visit each node and make and operation inside, Like print the result or process the data

The structure is like this:

- make a pointer name `current` who take the
- loop trhough the `current` node and make some operation
- Take the next node has the new `current`
