# doubleLinkedList

**Concept Type**:: #DataStructure
**Mastery Level**:: `⚙️ Working`
**Date Started**:: 2025-06-07
**Last Revised**:: 2025-06-09
**Related**:: [[LinkedList|LinkedLis]], [[Array]], [[SinglyLinkedList|singlyLinkedList]]
**Tags**:: #core #fundamentals #LinkedLists #doubleLinkedList

## Core Concept

> _A more complex data structure than a singly LinkedList_

> _because it allows better_

> _ways to insert and delete data by adding pointers to previous_

> _nodes (`prev`) and next nodes (`next`)._

> _This dual-pointer system also allows for more efficient traversal of the_

> _linked list in both forward and backward directions,_

> _which is a key advantage over singly linked lists._

## Why Important?

- Allows more efficient ways to traverse data both forwards and backwards.
- Provides more efficient insertion and deletion of data at arbitrary
  positions compared to singly linked lists
  (as you can easily access the previous node).
- Useful for implementing structures like LRU caches,
  browser history, or undo/redo functionalities.

## How It Works

- Each node in a Doubly Linked List has three important parts:
  - A `prev` pointer: References the preceding node in the sequence.
  - The `data`: Stores the actual value or payload of the node.
  - A `next` pointer: References the subsequent node in the sequence.

## Core Mechanics

```javaScript
class Node {

    constructor(data) {
        this.prev = null;
        this.data = data;
        this.next = null;
    }
}


class DoublyLinkedList {

    constructor() {
        this.head = null; // The first node in the list
    }

    // --- Methods start here ---

    /**
     * Adds a new node with the given data to the end of the Doubly Linked List.
     * @param {*} data - The data to be added to the new node.
     * @returns {Node} The newly created node.
     */
    push(data) {
        const newNode = new Node(data);
        let lastNode = this.head;
        if (this.head === null) {
            this.head = newNode;
            return newNode;
        }
        while (lastNode.next !== null) {
            lastNode = lastNode.next;
        }
        lastNode.next = newNode;
        newNode.prev = lastNode;
        return newNode;
    }

    /**
     * Traverses the Doubly Linked List from head to tail and collects all data.
     * @returns {Array} An array containing all data elements in order.
     */
    traversal() {
        let current = this.head
        const arr = [];
        while (current !== null) {
            arr.push(current.data);
            current = current.next;
        }
        return arr;
    }

    /**
     * Traverses the Doubly Linked List from tail to
     * head (using prev pointers) and collects all data.
     * @returns {Array} An array containing all data elements in reverse order.
     */
    reverseTraversal() {
        if (this.head === null) return [];
        let current = this.head;
        const arr = [];
        // First, find the last node (tail)
        while (current.next !== null) {
            current = current.next;
        }
        // Then, traverse backwards using 'prev' pointers
        while (current !== null) {
            arr.push(current.data);
            current = current.prev;
        }
        return arr;
    }

    /**
     * Calculates the number of nodes in the Doubly Linked List.
     * @returns {number} The total number of nodes in the list.
     */
    length() {
        let length = 0;
        if (this.head === null) return 0;
        let current = this.head;

        while (current !== null) {
            length++;
            current = current.next
        }
        return length;
    }

    /**
     * Adds a new node with the given data to the beginning of
     * the DoublyLinkedList.
     * @param {*} data - The data to be added to the new node.
     * @returns {Node} The newly created node (which is now the new head).
     */
    unshift(data) {
        const newNode = new Node(data);
        if (this.head === null) {
            this.head = newNode;
            return newNode;
        }
        this.head.prev = newNode;
        newNode.next = this.head;
        this.head = newNode;
        return newNode;
    }

    /**
     * Inserts a new node with the given data at a specified index.
     * Handles insertion at the beginning (index 0), end (index === length), and in the middle.
     * @param {number} index - The 0-based index at which to insert the new node.
     * @param {*} data - The data for the new node.
     * @returns {Node|string} The newly inserted node, or an error message if the index is out of bounds.
     */
    insert(index, data) {
        if (index < 0) return 'the index is lower than the first node';
        if (index === 0) { this.unshift(data); return; } // Use unshift for index 0
        if (index === this.length()) { this.push(data); return; } // Use push for end
        if (index > this.length()) return 'the index is greater than the List';

        const newNode = new Node(data);
        let count = 0; // Use 0-based count for traversal
        let current = this.head;

        // Traverse to the node *before* the insertion point
        while (current !== null) {
            if (count + 1 === index) { // `current` is the node before the target index (1-based logic)
                let temp = current.next; // Node currently at the target index
                current.next = newNode;
                newNode.prev = current;
                if (temp !== null) {
                    newNode.next = temp;
                    temp.prev = newNode;
                }
                return newNode;
            }
            count++;
            current = current.next;
        }
        // This line should theoretically not be reached if index validation is perfect
        return newNode;
    }

    /**
     * Removes and returns the first node (head) of the Doubly Linked List.
     * @returns {Node|undefined} The removed node, or undefined if the list was empty.
     */
    shift() {
        if (this.head === null) return undefined;
        if (this.head.next === null) { // Single node list
            const oldHead = this.head;
            this.head = null;
            return oldHead;
        }
        let oldHead = this.head;
        let newHead = this.head.next;
        oldHead.next = null; // Disconnect oldHead from the rest
        newHead.prev = null; // Disconnect newHead from oldHead
        this.head = newHead;
        return oldHead;
    }

    /**
     * Removes and returns the last node (tail) of the Doubly Linked List.
     * @returns {Node|undefined} The removed node, or undefined if the list was empty.
     */
    pop() {
        if (this.head === null) return undefined;
        if (this.head.next === null) { // Single node list
            const removedNode = this.head;
            this.head = null;
            return removedNode;
        }
        let current = this.head;
        // Traverse to the second to last node
        while (current.next.next !== null) {
            current = current.next;
        }
        let removedNode = current.next; // The last node
        current.next = null; // Disconnect second to last from last
        removedNode.prev = null; // Disconnect last from second to last
        return removedNode;
    }

    /**
     * Prints the data of each node in the Doubly Linked List to the console.
     */
    print() {
        let current = this.head;
        while (current !== null) {
            console.log(current.data);
            current = current.next;
        }
    }

    /**
     * Deletes a node at a specified 1-based index from the Doubly Linked List.
     * Handles deletion of head, tail, and middle nodes efficiently.
     * @param {number} index - The 1-based index of the node to delete.
     * @returns {Node|string|undefined} The deleted node, an 'Index Out of Bounds' message, or undefined if the list was empty.
     */
    deleteForIndex(index) {
        // Handle empty list case
        if (this.head === null) {
            return undefined;
        }

        const len = this.length();

        // Handle invalid index ranges (assuming 1-based indexing for 'index')
        if (index < 1 || index > len) {
            return 'Index Out of Bounds';
        }

        // Handle deleting the head (index 1) by reusing the existing shift method
        if (index === 1) {
            return this.shift();
        }

        // Handle deleting the tail (last index) by reusing the existing pop method
        if (index === len) {
            return this.pop();
        }

        // For middle deletions: Traverse to the node *before* the one to be deleted
        let current = this.head;
        let count = 1; // Using 'count' to track the current node's 1-based index

        // Stop when 'current' is the node right before the target 'index'
        // e.g., if deleting index 3, 'current' should be at index 2 (count = 2)
        while (count < index - 1) {
            current = current.next;
            count++;
        }

        // 'current' is now the node *before* the target node.
        let nodeToDelete = current.next; // This is the node at the target 'index'.

        // Re-link 'current' (the node before) to the node *after* 'nodeToDelete'.
        current.next = nodeToDelete.next;

        // Re-link the node *after* 'nodeToDelete' back to 'current'.
        // We know 'nodeToDelete.next' is not null here because 'index === len' (tail case) was handled.
        if (nodeToDelete.next !== null) { // Defensive check
            nodeToDelete.next.prev = current;
        }

        // Disconnect the deleted node's pointers to clean it up
        nodeToDelete.prev = null;
        nodeToDelete.next = null;

        return nodeToDelete; // Return the removed node
    }
}

    adding data at the end of a DoublyLinkedList (push)

    Method to add values at the end of the DoublyLinkedList.

Step by Step

    First, create a newNode to be added to the DoublyLinkedList.
    Check if the DoublyLinkedList is empty. If it is:
        Add the newNode as the head of the list.
    If not empty, create a temporary variable lastNode and initialize it with the head.
    Traverse the list using the next pointers until lastNode.next is null (meaning lastNode is currently the tail).
    Set lastNode.next to point to the newNode, establishing the forward link.
    Set newNode.prev to point to lastNode, establishing the backward link.
    Return the newNode.

Example
JavaScript

    push(data) {
        const newNode = new Node(data);
        let lastNode = this.head;
        if (this.head === null) {
            this.head = newNode;
            return newNode;
        }
        while (lastNode.next !== null) {
            lastNode = lastNode.next;
        }
        lastNode.next = newNode;
        newNode.prev = lastNode;
        return newNode;
    }

traversal the doubleLinkedList (traversal)

    Go through the DoublyLinkedList from head to tail and retrieve the data.

Step by Step

    Create an empty array arr to store the data.
    Create a current variable and initialize it with the head.
    Iterate through the DoublyLinkedList while current is not null.
    In each iteration, add current.data to the arr.
    Move to the next node by setting current = current.next.
    Once the loop finishes, return the arr.

Example
JavaScript

    traversal() {
        let current = this.head
        const arr = [];
        while (current !== null) {
            arr.push(current.data);
            current = current.next;
        }
        return arr;
    }

Reverse traversal the doubleLinkedList (reverseTraversal)

    Go through the DoublyLinkedList from tail to head and retrieve the data using the prev pointers.

Step by Step

    Check if the list is empty. If so, return an empty array.
    Create a current variable and initialize it with the head.
    Traverse forward to reach the last node (tail) by iterating while current.next is not null.
    From the last node, iterate backwards while current is not null.
    In each backward iteration, add current.data to an array.
    Move to the previous node by setting current = current.prev.
    Once the loop finishes, return the array.

Example
JavaScript

    reverseTraversal() {
        if (this.head === null)  return [];
        let current = this.head;
        const arr = [];
        while (current.next !== null) {
            current = current.next;
        }
        while (current !== null) {
            arr.push(current.data);
            current = current.prev;
        }
        return arr;
    }

Get Length of the DoublyLinkedList (length)

    Calculates the number of nodes currently in the Doubly Linked List.

Step by Step

    Initialize a length counter to 0.
    If the head is null, return 0 (empty list).
    Initialize current to this.head.
    Traverse the list from head to tail (while current is not null).
    In each step, increment length and move current to current.next.
    Return the final length.

Example
JavaScript

    length() {
        let length = 0;
        if (this.head === null) return 0;
        let current = this.head;

        while (current !== null) {
        length++;
            current = current.next
        }
        return length;
    }

Add Data at the Beginning of a DoublyLinkedList (unshift)

    Adds a new node with the given data to the very beginning of the Doubly Linked List, making it the new head.

Step by Step

    Create a newNode.
    If the list is empty, set newNode as the head.
    If the list is not empty:
        Set the prev pointer of the current head to the newNode.
        Set the next pointer of the newNode to the current head.
        Update this.head to point to the newNode.
    Return the newNode.

Example
JavaScript

    unshift(data) {
        const newNode = new Node(data);
        if (this.head === null) {
            this.head = newNode;
            return newNode;
        }
        this.head.prev = newNode;
        newNode.next = this.head;
        this.head = newNode;
        return newNode;
    }

Insert Data at a Specific Index (insert)

    Inserts a new node containing the given data at the specified 0-based index. Handles edge cases for inserting at the beginning (index 0) and end (index === length).

Step by Step

    Validate Index: Check if index is negative or greater than the current length. Return an error message if invalid.
    Edge Case - Insert at Head: If index is 0, call the unshift() method.
    Edge Case - Insert at Tail: If index is equal to the length of the list, call the push() method.
    General Case - Insert in Middle:
        Create a newNode.
        Traverse the list using a count variable until count reaches index - 1. current will then be the node before the desired insertion point.
        Store current.next in a temporary variable (temp) to preserve the link to the rest of the list.
        Update current.next to point to newNode.
        Update newNode.prev to point to current.
        If temp is not null (meaning we're not at the very end), update newNode.next to temp and temp.prev to newNode.
        Return the newNode.

Example
JavaScript

    insert(index,data) {
        if (index < 0 ) return 'the index is lower than the first node'
        if (index === 0) {this.unshift(data); return;}
        if (index === this.length()) {this.push(data); return;}
        if (index > this.length()) return 'the index is greater than the List'
        const newNode = new Node(data)
        let length = 0; // Using 0-based length for iteration
        let current = this.head;

        while (current !== null) {
            // If using 1-based index for the parameter:
            if (length + 1 === index) { // `current` is the node *before* the target index
                let temp = current.next;
                current.next = newNode;
                newNode.prev = current;
                if (temp !== null) {
                newNode.next = temp;
                temp.prev = newNode;
                }
                return newNode;
            }

            length++
            current = current.next;
        }
        return newNode;
    }

Remove Data from the Beginning (shift)

    Removes and returns the first node (head) of the Doubly Linked List, updating the head to the next node.

Step by Step

    Handle Empty List: If the list is empty, return undefined.
    Handle Single Node List: If there's only one node, store it, set head to null (making the list empty), and return the stored node.
    Handle Multiple Nodes:
        Store the current head (this will be the oldHead to return).
        Get a reference to the node that will become the newHead (which is oldHead.next).
        Sever the next pointer of oldHead (set oldHead.next = null).
        Sever the prev pointer of newHead (set newHead.prev = null).
        Update this.head to newHead.
        Return oldHead.

Example
JavaScript

    shift() {
        if (this.head === null) return undefined;
        if (this.head.next === null) {
            const oldHead = this.head;
            this.head = null;
            return oldHead;
        }
        let oldHead = this.head;
        let newHead = this.head.next;
        oldHead.next = null;
        newHead.prev = null;
        this.head = newHead;
        return oldHead;
    }

Remove Data from the End (pop)

    Removes and returns the last node (tail) of the Doubly Linked List.

Step by Step

    Handle Empty List: If the list is empty, return undefined.
    Handle Single Node List: If there's only one node, store it, set head to null (making the list empty), and return the stored node.
    Handle Multiple Nodes:
        Traverse the list using current until current.next.next is null. This positions current at the second-to-last node.
        Store a reference to the last node (current.next) in removedNode.
        Sever the next pointer of current (set current.next = null).
        Sever the prev pointer of removedNode (set removedNode.prev = null).
        Return removedNode.

Example
JavaScript

    pop() {
        if (this.head === null)  return undefined;
        if (this.head.next === null) {
            const removedNode = this.head;
            this.head = null;
            return removedNode;
        }
        let current = this.head;

        while (current.next.next !== null) {
            current = current.next;
        }
        let removedNode = current.next;
        current.next = null;
        removedNode.prev = null;
        return removedNode;
    }

Delete Node by Index (deleteForIndex)

    Deletes a node at a specified 1-based index from the Doubly Linked List. Handles deletion of head, tail, and middle nodes efficiently by reusing shift() and pop().

Step by Step

    Handle Empty List: If the list is empty, return undefined.
    Get Length: Get the current length of the list.
    Validate Index: Check if index is less than 1 or greater than the length. Return an "Index Out of Bounds" message if invalid.
    Edge Case - Delete Head: If index is 1, call the shift() method and return its result.
    Edge Case - Delete Tail: If index is equal to length, call the pop() method and return its result.
    General Case - Delete Middle Node:
        Initialize current to this.head and count to 1.
        Traverse the list until count reaches index - 1. current will then be the node before the target deletion point.
        Identify nodeToDelete as current.next.
        Re-link current.next to nodeToDelete.next.
        If nodeToDelete.next is not null (which it won't be if it's a middle node), re-link nodeToDelete.next.prev back to current.
        Finally, disconnect nodeToDelete.prev and nodeToDelete.next to null to isolate the deleted node.
        Return nodeToDelete.

Example
JavaScript

    deleteForIndex(index) {
        if (this.head === null) return undefined; // Consistent return for empty list
        const length = this.length();
        if (index < 1 || index > length) return 'Index Out of Bounds';
        if (index === 1) return this.shift();
        if (index === length) return this.pop();

        let current = this.head;
        let count = 1;

        while (count < index - 1) {
            current = current.next;
            count++;
        }
        let nodeDeleted = current.next
        current.next = nodeDeleted.next; // Link previous node to next node
        if (nodeDeleted.next !== null) { // If there's a node after the deleted one
            nodeDeleted.next.prev = current; // Link that next node back to the previous
        }
        nodeDeleted.prev = null; // Clean up deleted node's prev pointer
        nodeDeleted.next = null; // Clean up deleted node's next pointer

        return nodeDeleted;
    }

Key Parameters & Returns (for all methods)

    push(data):
        param: data (any type) - The data to store in the new node.
        return: Node - The newly added node.
    traversal():
        param: None.
        return: Array - An array of data from the list.
    reverseTraversal():
        param: None.
        return: Array - An array of data from the list in reverse order.
    length():
        param: None.
        return: number - The count of nodes in the list.
    unshift(data):
        param: data (any type) - The data for the new head node.
        return: Node - The newly added node (new head).
    insert(index, data):
        param: index (number) - The 0-based position to insert. data (any type) - The data for the new node.
        return: Node - The newly inserted node, or string error message.
    shift():
        param: None.
        return: Node - The removed head node, or undefined if the list was empty.
    pop():
        param: None.
        return: Node - The removed tail node, or undefined if the list was empty.
    deleteForIndex(index):
        param: index (number) - The 1-based position of the node to delete.
        return: Node - The removed node, string error message, or undefined if the list was empty.

Practical Examples
Basic Usage
JavaScript

const myDoublyLinkedList = new DoublyLinkedList();

// Push elements
myDoublyLinkedList.push(1); // List: 1
myDoublyLinkedList.push(2); // List: 1, 2
myDoublyLinkedList.push(3); // List: 1, 2, 3

console.log("Traversal:", myDoublyLinkedList.traversal()); // [1, 2, 3]
console.log("Reverse Traversal:", myDoublyLinkedList.reverseTraversal()); // [3, 2, 1]
console.log("Length:", myDoublyLinkedList.length()); // 3

// Unshift element
myDoublyLinkedList.unshift(0); // List: 0, 1, 2, 3
console.log("After unshift(0):", myDoublyLinkedList.traversal()); // [0, 1, 2, 3]

// Insert element
myDoublyLinkedList.insert(2, 'middle'); // List: 0, 1, 'middle', 2, 3 (assuming 0-based insert)
console.log("After insert(2, 'middle'):", myDoublyLinkedList.traversal()); // [0, 1, 'middle', 2, 3]

// Shift element
const shifted = myDoublyLinkedList.shift(); // Removes 0
console.log("Shifted:", shifted.data); // 0
console.log("After shift:", myDoublyLinkedList.traversal()); // [1, 'middle', 2, 3]

// Pop element
const popped = myDoublyLinkedList.pop(); // Removes 3
console.log("Popped:", popped.data); // 3
console.log("After pop:", myDoublyLinkedList.traversal()); // [1, 'middle', 2]

// Delete by Index (using 1-based index for this method)
const deleted = myDoublyLinkedList.deleteForIndex(2); // Removes 'middle'
console.log("Deleted at index 2:", deleted.data); // 'middle'
console.log("After deleteForIndex(2):", myDoublyLinkedList.traversal()); // [1, 2]

Real-World Scenario

Doubly Linked Lists are excellent for implementing systems where you need to navigate both forwards and backwards, and frequently add/remove items from any position.
JavaScript

// Production-ready pattern: Browser History
class BrowserHistory {
    constructor() {
        this.history = new DoublyLinkedList();
        this.current = null; // Pointer to the current page node
    }

    // Navigates to a new URL, clearing "forward" history
    visit(url) {
        const newNode = new Node(url);
        if (this.current) {
            // Cut off forward history
            this.current.next = null;
            newNode.prev = this.current;
        } else {
            // First page visited
            this.history.head = newNode;
        }
        this.current = newNode;
        this.history.push(url); // Or more simply, just update current pointer if push is too much
                                // A simpler push equivalent:
                                // if (this.current) {
                                //     this.current.next = newNode;
                                //     newNode.prev = this.current;
                                // } else {
                                //     this.history.head = newNode;
                                // }
                                // this.current = newNode;
    }

    goBack() {
        if (this.current && this.current.prev) {
            this.current = this.current.prev;
            return this.current.data;
        }
        return null; // Cannot go back
    }

    goForward() {
        if (this.current && this.current.next) {
            this.current = this.current.next;
            return this.current.data;
        }
        return null; // Cannot go forward
    }

    printHistory() {
        console.log("History (backward to forward):", this.history.traversal());
        console.log("Current page:", this.current ? this.current.data : 'No page');
    }
}

const browser = new BrowserHistory();
browser.visit("google.com");
browser.visit("youtube.com");
browser.visit("gemini.google.com");
browser.printHistory();
console.log("Going back:", browser.goBack()); // youtube.com
console.log("Going back:", browser.goBack()); // google.com
console.log("Going forward:", browser.goForward()); // youtube.com
browser.visit("stackoverflow.com"); // New page cuts off gemini.google.com from history
console.log("Going forward (after new visit):", browser.goForward()); // null
browser.printHistory();

Common Pitfalls
JavaScript

// Anti-pattern example: Forgetting to update ALL pointers
function badPracticeForgetPointers(list, nodeToRemove) {
    // This is overly simplified and incorrect for a DLL deletion
    if (nodeToRemove.prev) {
        nodeToRemove.prev.next = nodeToRemove.next;
    }
    // 🚫 If nodeToRemove.next exists, its 'prev' pointer is NOT updated
    // 🚫 If nodeToRemove was the head, 'list.head' is NOT updated
    // 🚫 If nodeToRemove was the tail, the previous node's 'next' should be null, which is handled above, but important to remember.
    // 🚫 The deleted node's own pointers are not nulled out (nodeToRemove.prev = null; nodeToRemove.next = null;)
}

🛑 Why to Avoid: Forgetting to update both next and prev pointers (for affected nodes before and after the change, as well as the removed/inserted node itself) will lead to a broken linked list. This can result in:

    Memory leaks (deleted nodes still referenced)
    Incorrect traversal paths (nodes skipped or unreachable)
    Runtime errors (trying to access properties of null or undefined)
    Data inconsistency (list length might not reflect actual nodes)

Mental Models
Fragmento de código

mindmap
  root((Doubly Linked List))
    Core Structure
      Node
        Data
        Prev Pointer (⬅️)
        Next Pointer (➡️)
    Key Operations
      Insertion
        At Head (Unshift)
        At Tail (Push)
        At Middle (Insert at Index)
      Deletion
        From Head (Shift)
        From Tail (Pop)
        From Middle (Delete at Index)
      Traversal
        Forward (using Next)
        Backward (using Prev)
    Advantages
      Bi-directional Traversal
      Efficient Insertion/Deletion (O(1) once position found, O(N) to find)
    Disadvantages
      More Memory per Node (for Prev pointer)
      More Complex Pointer Management

Practice Exercises

    Basic:
    JavaScript

// Starter code
// Implement a method `peekHead()` and `peekTail()`
// that return the data of the head/tail node without removing it.
// Make sure to handle empty list cases.
class DoublyLinkedList {
    // ... (your existing code) ...

    peekHead() {
        // Implement solution
    }

    peekTail() {
        // Implement solution
    }
}

Intermediate:
JavaScript

    // Challenge scaffold
    // Implement a method `reverse()` that reverses the entire Doubly Linked List in-place.
    // This means you should modify the pointers of the existing nodes,
    // not create a new list or just return a reversed array.
    class DoublyLinkedList {
        // ... (your existing code) ...

        reverse() {
            // Optimize this
        }
    }

Resources

    GeeksforGeeks - Doubly Linked List
    MDN Web Docs - Data structures: Linked lists
    FreeCodeCamp - Data Structures: Doubly Linked Lists
    Visualgo - Linked List Visualization (Highly recommended for understanding pointer changes)

Concept Connections

    Arrays: While arrays offer O(1) access by index, insertion and deletion in the middle are O(N). Doubly Linked Lists offer O(1) insertion/deletion once the position is found, but O(N) to find the position.
    Singly Linked Lists: Doubly Linked Lists extend singly linked lists by adding prev pointers, enabling backward traversal and more efficient deletion without needing a reference to the previous node.
    Stacks/Queues: Can be efficiently implemented using Doubly Linked Lists (e.g., unshift/shift for a Queue, push/pop for a Stack).

Recall Triggers

    Mnemonic: "DLL: Double L for Links" - Two links per node (prev & next).
    Visualization: Imagine a train where each car (node) is connected to the car in front (prev) and the car behind (next). You can walk forwards or backwards.
    Analogy: A two-way street or a chain where each link is explicitly connected to both the link before and the link after it.
```
