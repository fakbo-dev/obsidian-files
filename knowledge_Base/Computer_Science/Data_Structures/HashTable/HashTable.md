# HashTable

**Concept Type**:: #fundamentals #DataStructure
**Mastery Level**:: `🧠 Familiar`
**Date Started**:: 2025-06-21
**Last Revised**::
**Related**:: [[Core]]
**Tags**:: #object

## Core Concept

> _is a data structure that allow fast searching data based of a keys_

## Why Important?

- Store data in o(1) and access the data in o(1).
- Key-value Support: Hashing is ideal for implementing key-value data structures.
- Fast data retrieval: Hashing allows for quick access to elementens with constant time complexity
- Efficiency: Insertion, deletion, and searching operations are highly efficient
- Memory usage reduction: Hashin require less memory as it allocates a fixed space for storing
  elementens
- Scalability: Hashing performs well with large data sets maitaining constant access time.
- Security and encryption: Hashing is essential for secure data storage and integrity verification.

## How It Works

```javaScript
class HashTable {

  constructor() {
    this.table = new Array(127);
    this.size = 0;
  }

  _hash(key) {
    let hash = 0;

    for (let i = 0; i < key.length; i++) {
      hash += key.charCodeAt(i);
    }

    return hash % this.table.length;
  }

  set(key,value) {
    const index = this._hash(key);
    if (this.table[index]) {

      for (let i = 0; i < this.table[index].length; i++) {

        if (this.table[index][i][0] === key) {
          this.table[index][i][1] = value;
          return;
        }
      }
      this.table[index].push([key,value]);
    } else {
      this.table[index] = [];
      this.table[index].push([key,value])
    }
    this.size++;
  }
  get(key) {
    const target = this._hash(key);
    if (this.table[target]) {
      for (let i = 0; i < this.table.length; i++) {
        if (this.table[target][i][0] === key) {
          return this.table[target][i][1];
        }
      }
    }
    return undefined;
  }
  remove(key) {
    const index = this._hash(key);

    if (this.table[index] && this.table[index].length) {
      for (let i = 0; i < this.table.length; i++) {
        if (this.table[index][i][0] === key) {
          this.table[index].splice(i, 1);
          this.size--;
          return true;
        }
      }
    } else {
      return false;
    }
  }

}

const collection = new HashTable();
collection.set("Canada", 300);
collection.set("France", 100);
collection.set("Spain", 110);

```

## Core Mechanics

```<language>
// Basic syntax/pattern
function example(param) {
    return transformed(param);
}
```

### Key Parameters

- `param`:
- `return`:

## Practical Examples

### Basic Usage

```<language>
// Minimal implementation
const result = basicUsage(input);
```

### Real-World Scenario

```<language>
// Production-ready pattern
function optimizedSolution(data) {
    // Explain optimizations
}
```

## Common Pitfalls

```<language>
// Anti-pattern example
function badPractice() {
    🚫 // Why this is wrong
}
```

🛑 **Why to Avoid:**

## Mental Models

```mermaid
mindmap
  root((HashTable))
    Core Principles
      Principle 1
      Principle 2
    Application Patterns
      Pattern A
      Pattern B
```

## Practice Exercises

1. **Basic**:
   ```<language>
   // Starter code
   function exercise1(input) {
       // Implement solution
   }
   ```
2. **Intermediate**:
   ```<language>
   // Challenge scaffold
   function exercise2(data) {
       // Optimize this
   }
   ```

## Resources

1. [Official Documentation]()
2. [Key Tutorial]()
3. [Deep Dive Article]()
4. [Practice Platform]()

## Concept Connections

```mermaid
graph TD
    Current{{Current Concept}} --> Prerequisite(Prerequisite Knowledge)
    Current --> Similar(Similar Concepts)
    Current --> Advanced(Advanced Topics)
```

## Recall Triggers

- Mnemonic:
- Visualization:
- Analogy:
