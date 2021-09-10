1. Arrays
Elements are accesed by index (usually zero indexed) and it's a continuous block of memory. They are usually
the same datatype (numpy arrays, arrays in C++ and arrays in Javascripts, etc). Insert and access with index is
O(1) while search and remove is O(n).
2. Linked Lists
They are linear data structures whose elements aro not stored in contiguous location. It's composed of *nodes* which
have the current value and a pointer to the next element.(There are double linked list and circular linked list too).
An application can be previous and next page of web browser or user search. **Perfect for memory management because
dynamic memory**. Insert and remove is O(1) while access and search is O(n).
3. Stacks
It has restricted access (follow rule of LIFO: last element added is first element added). They can be implemented with
arrays or linked list. An example is when need to obtain reverse order of given elements (like a balanced parentheses problem).
Access an element is O(n) while other problems are made in O(1).
4. Queues (+ Deque + Priority Queue)
It has restricted access collection (FIFO: first inserted element is the first removed) and can be implemented with
an array, circular array or linked list. Deque has IN/OUT in both sites while priority queues are like a queue but elements are
ordered like FIFO. This ADT (abstract data type) is essential in many Graph Algorithms (Dijkstra's Algorithm, BFS, Prim's 
Algorithm, Huffman Coding - more about them below). It is implemented using a heap.
5. Maps & Hash Tables
Also known as dictionaries which contains key-value pairs (each key has a value associated)(Most of operations are O(logn)).
On the other side, hash table (type of map) uses a hash function to generate a hash code: key is hashed while hash indicates 
where is stored (all operations are O(1)). Hash functions are popular because pre-image resistance and second pre-image resistance
6. Graphs
It's a nonlinear DS which represent 2 sets: G={V,E}, where V are vertices/nodes and E are the edges (rows). This edges represent
dependency between 2 nodes (sometimes associated to a cost/distance). They can be directed or undirected (edge available in both directions).
This structure is the foundation of Networks. Some properties: degree of undirected node is the number of edges, for directed graph we have
internal/external degree of node. A chain is a succesion of adjacent edges. A graph can be traversed and processed using Breadth First
Search (BFS) or Depth First Search (DFS)
12. Trees
13. Binary Trees & Binary Search Trees
14. Self-balancing Trees (AVL Trees, Red-Black Trees, Splay Trees)
15. Heaps
16. Tries
17. Segment Trees
18. Fenwick Trees
19. Disjoint Set Union
20. Minimum Spanning Trees

