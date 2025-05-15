Source: [[Basic Data Structures]]
Useful Page: https://www.geeksforgeeks.org/array-data-structure-guide/

- It offers mainly the following advantages over other data structures.  
    ****Random Access**** : i-th item can be accessed in O(1) Time as we have the base address and every item or reference is of same size.  
    ****Cache Friendliness**** : Since items / references are stored at contiguous locations, we get the advantage of locality of reference.
- It is not useful in places where we have operations like insert in the middle, delete from middle and search in a unsorted data.
- It is a fundamental and linear data structure using which we build other data structures like Stack Queue, Deque, Graph, Hash Table, etc.

***Array*** is a collection of items of the same variable type that are stored at contiguous memory locations. It is one of the most popular and simple data structures used in programming.
### Basic terminologies of Array

- ***Array Index:*** In an array, elements are identified by their indexes. Array index starts from 0.
- **Array element:** Elements are items stored in an array and can be accessed by their index.
- **Array Length:*** The length of an array is determined by the number of elements it can contain.
### Why do we Need Arrays?

Assume there is a class of five students and if we have to keep records of their marks in examination then, we can do this by declaring five variables individual and keeping track of records but what if the number of students becomes very large, it would be challenging to manipulate and maintain the data.

What it means is that, we can use normal variables (v1, v2, v3, ..) when we have a small number of objects. But if we want to store a large number of instances, it becomes difficult to manage them with normal variables.

