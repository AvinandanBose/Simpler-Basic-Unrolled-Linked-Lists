# 📌 Unrolled Linked List

A comprehensive implementation and mathematical analysis of the **Unrolled Linked List** data structure using **C/C++**, including detailed explanations of capacity-based insertion, compacting deletion, byte-level memory alignment, and structural traversal. This repository is designed for students, educators, and developers who want to deeply understand how Unrolled Linked Lists optimize memory and caching internally.

---

# Repository Link

🔗Repository: [https://github.com/AvinandanBose/Simpler-Basic-Unrolled-Linked-Lists](https://github.com/AvinandanBose/Simpler-Basic-Unrolled-Linked-Lists)

---

## 📘 Introduction

An **Unrolled Linked List** is a hybrid data structure that bridges the gap between traditional linked lists and arrays. By combining the dynamic growth capabilities of a list with the fast, contiguous memory layout of an array, it creates a highly optimized system for managing large amounts of data.

Instead of storing just one piece of data per node, an unrolled linked list stores a fixed-size array of elements (often called a chunk or block) inside each node, alongside a single pointer directing to the next node in the chain. A standard node in this structure consists of:

* **Number of Elements (`numElements`):** An integer tracking how many slots in the current chunk are actively occupied by data.


* **Elements Array (`elements[MAX_ELEMENTS]`):** Multiple data points stored in contiguous, back-to-back memory slots.


* **Next Pointer (`*next`):** The bridge connecting separate chunks, with one pointer per block.



Because of this organization, the Unrolled Linked List is capable of representing sequential data with significantly less overhead than a standard linked list.

---

## 🚀 Key Advantages

* **Cache Locality:** Modern CPUs load data from main memory in blocks (cache lines). Because an unrolled list stores data sequentially in arrays, the CPU can load multiple elements into its high-speed cache at once, making searching and traversing dramatically faster than jumping to random memory addresses.


* **Reduced Pointer Overhead:** In a traditional linked list, a 64-bit system wastes 8 bytes on a pointer for every single integer stored. Unrolled lists slash this overhead by sharing a single pointer across multiple elements (e.g., 1 pointer per 4 elements).


* **Dynamic Growth:** Unlike standard arrays that suffer from expensive, massive memory reallocations when they run out of space, unrolled lists simply attach a new lightweight node to the end of the chain.



## ⚠️ Trade-offs & Disadvantages

* **Shift Penalties:** While finding data is fast, inserting or deleting an item in the middle of an array chunk requires shifting the adjacent elements left or right.


* **Internal Wasted Space (Fragmentation):** If a system heavily deletes items and nodes are left only partially full, the unused array slots within those nodes consume memory that isn't actively storing data.



## 🌍 Real-World Applications

* **High-Performance Computing:** Environments where maximizing CPU cache hits and minimizing cache misses is a top priority.


* **Optimized Sequential Storage:** Managing large amounts of data where standard dynamic arrays would cause severe reallocation lag, but traditional linked lists would waste too much memory on pointers.



## ⚡ Complexity Analysis

### Time Complexity (Main List Operations)

(Note: `N` represents the number of nodes, and `n` represents the total number of elements. Because node capacity `B` is a fixed constant, $N \approx \lceil n/B \rceil$, meaning $O(N)$ is mathematically equivalent to $O(n)$.)

| Operation | Best Case | Worst Case | Average Case |
| --- | --- | --- | --- |
| **Search Element** | $O(1)$<br> | $O(n)$ or $O(N)$<br> | $O(n)$ or $O(N)$<br> |
| **Insert Element** | $O(1)$<br> | $O(n)$ or $O(N)$<br> | $O(n)$ or $O(N)$<br> |
| **Delete Element** | $O(1)$<br> | $O(n)$ or $O(N)$<br> | $O(n)$ or $O(N)$<br> |
| **Display List** | $O(1)$<br> | $O(n)$ or $O(N)$<br> | $O(n)$ or $O(N)$<br> |
| **Destroy List** | $O(1)$<br> | $O(n)$ or $O(N)$<br> | $O(n)$ or $O(N)$<br> |

### Space Complexity

* **Auxiliary Space:** $O(1)$ for basic operations (Insertion, Deletion, Search, Display). The algorithms use a constant number of temporary variables (`temp`, `prev`, `nextNode`) and iterative loops without recursion, meaning the Call Stack does not grow based on list size.


* **Holistic Space:** $O(n)$ or $O(N)$, representing the total memory required by the $N$ nodes to store the $n$ elements in the entire data structure.



## 🛠️ Included Algorithms

This repository implements the following core algorithms:

1. **Capacity-Based Insertion (`insertElement`):** Appends data to the current node's array. The list only requests new memory to create a subsequent node when the current array reaches its absolute maximum capacity (`MAX_ELEMENTS`).


2. **Compacting Deletion (`deleteElement`):** Searches for an element and shifts remaining elements left to fill the gap. If a node's `numElements` reaches 0, the node is surgically removed from the chain and its memory is freed.


3. **Search & Display (`searchElement`, `displayList`):** Utilizes nested loops to traverse horizontally across nodes (`temp = temp->next`) and iterate through the internal element arrays.


4. **List Destruction (`destroyList`):** Iteratively frees every node block by temporarily saving the `nextNode` address, ensuring all dynamically allocated memory is safely returned to the system.



---

## 📚 Learning Outcomes

By studying and implementing the code in this repository, you will gain a deep understanding of advanced data structures and algorithmic analysis. Specifically, you will learn how to:

* **Master Memory Alignment & Padding:** Understand the differences in memory allocation between 32-bit and 64-bit architectures, including how compilers automatically insert 4-byte "padding" blocks to safely align 8-byte pointers.


* **Analyze Time Complexity:** Learn how to mathematically prove that traversing $N$ nodes and $n$ elements simplifies to $O(n)$ by understanding how constants (like maximum node capacity) are absorbed in Big-O notation.


* **Manage Granular Memory Operations:** Discover how to cleanly splice empty nodes out of a chain using `prev` and `temp` pointers, and how to safely deallocate memory using `free()` or `delete`.


* **Implement Structural Variations:** Explore how to adapt the base unrolled list into Doubly Linked, Circular, and Circular-Doubly Unrolled Linked Lists by managing additional `*prev` pointers and cyclic connections.



---

# 👨‍💻 Author

Developed and analyzed by [@AvinandanBose](https://github.com/AvinandanBose)

---

# 📄 License

This project is licensed under the **MIT License**.

---

## ⭐ Support

If you found this helpful:

* ⭐ Star the repository
* 🍴 Fork it
* 📢 Share with others

---
