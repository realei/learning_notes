# Interview Questions

www.CrackingTheCodingInterview.com

## Arrays and Strings

Please note that array questions and string questions are often **interchangeable**. That is, a question that this book states using an array may be asked instead as a string question, and vice versa.

### Hash Tables

A hash table is a **data structure** that maps keys to values for highly efficient lookup. There are a number of ways of implementing this. Here, we will describe a simple but common implementation.

- First, compute the key's hash code

- Then, map the hash code to an index in the array

- At this index, there is a linked list of keys and values

Q1: What if too many *hash code* maps to the same *index*?

### ArrayList & Resizable Arrays

In some languages, arrays (often called lists in this case) are automatically resizable. The array or list will grow as you append items. In other languages, like Java, arrays are fixed length. The size is defined when you create the array.

When you need an array-like data structure that offers **dynamic resizing**, you would usually use an Arraylist. An Arraylist is an array that resizes itself as needed while still providing 0(1) access. A typical implementation is that when the array is full, the array doubles in size. Each doubling takes 0( n) time, but happens so rarely that its amortized insertion time is still O(1).

**This is an essential data structure for interviews.** Be sure you are comfortable with dynamically resizable arrays/lists in whatever language you will be working with. Note that the name of the data structure as well as the "resizing factor" (which is 2 in Java) can vary.

### StringBuilder

- Remember:

  `1 + 2 +3 + ... + n = n*(n+1)/2`
  
  So: O(x + 2x + ... + nx) ~~ O(xn^2)

- StringBuilder simply creates a resizable array of all the strings, copying them back to a string only when necessary.


## Linded Lists

A linked list is a data structure that represents a sequence of nodes. In **a singly linked list**, each node points to the next node in the linked list. **A doubly linked list** gives each node pointers to both the next node and the previous node.

**Unlike an array**, a linked list does not provide constant time access to a particular "index" within the list. This means that if you'd like to find the Kth element in the list, you will need to iterate through K elements.

### Creating a Linked List

**Remember** that when you're discussing a linked list in an interview, you must understand whether it is a singly linked list or a doubly linked list.

### Deleting a Node from a Singly Linked List

Deleting a node from a linked list is fairly straightforward. Given a node `n`, we find the previous node `prev` and set `prev.next` equal to `n.next`. If the list is **doubly linked**, we **must also** update `n.next` to set `n.next`. prev equal to `n.prev`. The important things to remember are:

1. to check for the null pointer 
2. to update the head or tail pointer as necessary.

Additionally, if you implement this code in C, C++ or another language that requires the developer to do **memory management**, you should consider if the removed node should be deallocated.

### The "Runner" Technique

**The "runner" (or second pointer) technique** is used in many linked list problems. The runner technique means that you iterate through the linked list with two pointers simultaneously, with one ahead of the other. The "fast" node might be ahead by a fixed amount, or it might be hopping multiple nodes for each one node that the "slow" node iterates through.

### Recursive Problems

A number of linked list problems rely on recursion. If you're having trouble solving a linked list problem, you should explore if a recursive approach will work. We won't go into depth on recursion here, since a later chapter is devoted to it.

However, you should remember that **recursive algorithms take at least O(n) space**, where n is the depth of the recursive call. **All recursive algorithms can be implemented iteratively**, although they may be much more complex.

## Stacks and Queues

Questions on stacks and queues will be much easier to handle if you are comfortable with the ins and outs of the data structure. The problems can be quite tricky, though. While some problems may be slight modifications on the original data structure, others have much more complex challenges.

### Implementing a Stack 

The stack data structure is precisely what it sounds like: a stack of data. In certain types of problems, it can be favorable to store data in a stack rather than in an array. **A stack uses LIFO (last-in first-out) ordering.** That is, as in a stack of dinner plates, the most recent item added to the stack is the first item to be removed.

It uses the following operations:

	* `pop()`: Remove the top item from the stack.
	* `push(item)`: Add an item to the top of the stack.
	* `peek()`: Return the top of the stack.
	* `isEmpty()`: Return true if and only if the stack is empty.

Unlike an array, a stack does not offer constant-time access to the i^th item. However, it does allow constant­time adds and removes, as it doesn't require shifting elements around.

**One case where stacks are often useful is in certain recursive algorithms.** Sometimes you need to push temporary data onto a stack as you recurse, but then remove them as you backtrack (for example, because the recursive check failed). A stack offers an intuitive way to do this.

**A stack can also be used to implement a recursive algorithm iteratively.** (This is a good exercise! Take a simple recursive algorithm and implement it iteratively.)

### Implementing a Queue

**A queue implements FIFO (first-in first-out) ordering**. As in a line or queue at a ticket stand, items are removed from the data structure in the same order that they are added.

It uses the operations:

    * `add(item)`: Add an item to the end of the list.
	* `remove()`: Remove the first item i the list.
	* `peek()`: Return the top of the queue.
	* `isEmpty()`: Return true if and only if the queue is empty.

A queue can also be implemented with a **linked list**. In fact, they are essentially the same thing, as long as items are added and removed from opposite sides.

It is especially easy to mess up the updating of the first and last nodes in a queue. Be sure to double check this.

**One place where queues are often used is in breadth-first search or in implementing a cache.**

In breadth-first search, for example, we used a queue to store a list of the nodes that we need to process. Each time we process a node, we add its adjacent nodes to the back of the queue. This allows us to process nodes in the order in which they are viewed.

## Trees and Graphs

Many interviewees find **tree and graph problems** to be some of the trickiest. Searching a tree is more complicated than searching in **a linearly organized data structure such as an array or linked list**. Additionally, the worst case and average case time may vary wildly, and we must evaluate both aspects of any algorithm. Fluency in implementing a tree or graph from scratch will prove essential.

### Types of Trees

A nice way to understand a tree is with a recursive explanation. **A tree is a data structure composed of nodes.**

* Each tree has a root node. (Actually, this isn't strictly necessary in graph theory, but it's usually how we use trees in programming, and especially programming interviews.)

* The root node has zero or more child nodes.

* Each child node has zero or more child nodes, and so on.

The tree cannot contain cycles. The nodes may or may not be in a particular order, they could have any data type as values, and they may or may not have links back to their parent nodes.

Tree and graph questions *are rife with 充斥着* ambiguous details and incorrect assumptions. Be sure to watch out for the following issues and seek clarification when necessary.

#### Trees vs. Binary Trees

**A binary tree** is a tree in which each node has up to two children. Not all trees are binary trees. For example, this tree is not a binary tree. You could call it a ternary tree(Check the book).

There are occasions when you might have a tree that is not a binary tree. For example, suppose you were using a tree to represent a bunch of phone numbers. In this case, you might use a 10-ary tree, with each node having up to 10 children (one for each digit).

A node is called a "leaf" node if it has no children.

#### Binary Tree vs. Binary Search Tree

**A binary search tree** is a binary tree in which every node fits a specific ordering property: `all left descendents <= n < all right descendents`. This must be true for each `node n`.

```
The definition of a binary search tree can vary slightly with respect to equality. Under some definitions, the tree cannot have duplicate values. In others, the duplicate values will be on the right or can be on either side. All are valid definitions, but you should clarify this with your interviewer.
```

When given a tree question, many candidates assume the interviewer means *a binary search tree*. Be sure to ask. A binary search tree imposes the condition that, for each node, its left *descendents 后代们* are less than or equal to the current node, which is less than the right descendents.

#### Balanced vs. Unbalanced 

While many trees are balanced, not all are. Ask your interviewer for clarification here. **Note that balancing a tree does not mean the left and right subtrees are exactly the same size** (like you see under "perfect binary trees" in the following diagram).

One way to think about it is that a "balanced" tree really means something more like "not terribly imbalanced:' It's balanced enough to ensure `0(log n)` times for insert and find, but it's not necessarily as balanced as it could be.

Two common types of balanced trees are **red-black trees** (pg 639) and **AVL trees** (pg 637). These are discussed in more detail in the Advanced Topics section.

- **Complete Binary Trees**

  A complete binary tree is a binary tree in which every level of the tree is fully filled, except for perhaps the last level. To the extent that the last level is filled, it is filled left to right.

- **Full Binary Trees**

A full binary tree is a binary tree in which every node has either zero or two children. That is, no nodes have only one child.

- **Perfect Binary Trees**

A perfect binary tree is one that is both full and complete. All leaf nodes will be at the same level, and this level has the maximum number of nodes.

Note that perfect trees are rare in interviews and in real life, as a perfect tree must have exactly 2^k - 1 nodes (where k is the number of levels). In an interview, do not assume a binary tree is perfect.

### Binary Tree Traversal 遍历

[Tree Traversals in GeekforGeeks](https://www.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/)

- **In-Order Traversal** 中序遍历

In order traversal means to "visit"(often, print) the left branch, then the cuirrent node, the right branch.

*Leetcode*:

  * #94 [Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)

- **Pre-Orcder Traversal**

Pre-order traversal visits the current node before its child nodes (hence the name "pre-order").

In a pre-order traversal, the root is always the first node visited.

- **Post-Order Traversal**

Post-order traversal visits the current node after its child nodes (hence the name "post-order").

In a post-order traversal, the root is always the last node visited.

### **Binary Heaps (Min-Heaps and Max-Heaps)**

We'll just discuss min-heaps here. Max-heaps are essentially equivalent, but the elements are in descending order rather than ascending order.

A min-heap is a *complete* binary tree (that is, totally filled other than the rightmost elements on the last level) where each node is smaller than its children. The root, therefore, is the minimum element in the tree.

We have two key operations on a min-heap: `insert` and `extract_min`.

- Insert

When we insert into a min-heap, we always start by inserting the element at the bottom. We insert at the rightmost spot so as to maintain the complete tree property.

:q!Then, we "fix"the tree by swapping the new element with its parent, until we find an appropriate spot for the element. We essentially bubble up the minimum element.

This takes `O(log n)` time, where n is the number of nodes in the heap.

- Extract Minimum Element

Finding the minimum element of a min-heap is easy: it's always at the top. The trickier part is how to remove it. (In fact, this isn't that tricky.)

First, we remove the minimum element and swap it with the last element in the heap (the bottommost, rightmost element). Then, we bubble down this element, swapping it with one of its children until the min­heap property is restored.

Do we swap it with the left child or the right child? That depends on their values. There's no inherent ordering between the left and right element, but you'll need to take the smaller one in order to maintain the min-heap ordering.

This algorithm will also take 0( log n) time.

### Tries (Prefix Trees) --- 单词查找树或键树

A trie (sometimes called a prefix tree) is a funny data structure. It comes up a lot in interview questions, but algorithm textbooks don't spend much time on this data structure.

A trie is a variant of an n-ary tree in which characters are stored at each node. Each path down the tree may represent a word.

The `*` nodes (sometimes called "null nodes") are often used to indicate complete words. For example, the fact that there is a `*` node under MANY indicates that MANY is a complete word. The existence of the MA path indicates there are words that start with MA.

The actual implementation of these `*` nodes might be a special type of child (such as a TerminatingTrieNode, which inherits from TrieNode). Or, we could use just a boolean flag terminates within the "parent" node.

A node in a trie could have anywhere from `1` through `ALPHABET_SIZE + 1` children (or, `0` through `ALPHABET_SIZE` if a boolean flag is used instead of a `*` node).

Very commonly, a trie is used to store the entire (English) language for quick prefix lookups. While a hash table can quickly look up whether a string is a valid word, it cannot tell us if a string is a prefix of any valid words. A trie can do this very quickly.

```
How quickly? A trie can check if a string is a valid prefix in 0(K) time, where K is the length of the string. This is actually the same runtime as a hash table will take. Although we often refer to hash table lookups as being 0(1) time, this isn't entirely true. A hash table must read through all the characters in the input, which takes O(K) time in the case of a word lookup.
```

Many problems involving lists of valid words leverage a trie as an optimization. In situations when we search through the tree on related prefixes repeatedly (e.g., looking up M, then MA, then MAN, then MANY), we might pass around a reference to the current node in the tree. This will allow us to just check if Y is a child of MAN, rather than starting from the root each time.

### Graphs

A tree is actually a type of graph, but not all graphs are trees. Simply put, a tree is a connected graph without cycles.

A graph is simply a collection of nodes with edges between (some of) them.

* Graphs can be either **directed** (like the following graph) or **undirected**. While directed edges are like a one-way street, undirected edges are like a two-way street.

* The graph might consist of multiple isolated subgraphs. If there is a path between every pair of *vertices 顶点(多个)*, it is called a **"connected graph:"**

* The graph can also have cycles (or not). An **"acyclic graph 无环的" is one without cycles**.

- **Adjacency List**

This is the most common way to represent a graph. Every *vertex 顶点* (or node) stores a list of adjacent *vertices 顶点(多个)*. In an undirected graph, an edge like (a, b) would be stored twice: once in a's adjacent vertices and once in b's adjacent vertices.

A simple class definition for a graph node could look essentially the same as a tree node.

```
class Graph {
  public Node[] nodes;
}

class Node {
  public String name;
  public Node[] children;
}
```

The Graph class is used because, unlike in a tree, you can't necessarily reach all the nodes from a single node.

- **Adjacency Matrices**

An adjacency matrix is an NxN boolean matrix (where N is the number of nodes), where a true value at `matrix[i][j]` indicates an edge from node i to node j. (You can also use an integer matrix with Os and 1s.)

In an undirected graph, an adjacency matrix will be *symmetric 对称的*. In a directed graph, it will not(necessarily) be.

The same graph algorithms that are used on adjacency lists (breadth-first search, etc.) can be performed with adjacency matrices, but they may be somewhat less efficient. In the adjacency list representation, you can easily iterate through the neighbors of a node. In the adjacency matrix representation, you will need to iterate through all the nodes to identify a node's neighbors.

### Graph Search

The two most common ways to search a graph are **depth-first search** and **breadth-first search**.

In **depth-first search (DFS)**, we start at the root (or another arbitrarily selected node) and explore each branch completely before moving on to the next branch. That is, we go deep first (hence the name depth­first search) before we go wide.

In **breadth-first search (BFS)**, we start at the root (or another arbitrarily selected node) and explore each neighbor before going on to any of their children. That is, we go wide (hence breadth-first search) before we go deep.

Breadth-first search and depth-first search tend to be used in different scenarios. **DFS is often preferred if we want to visit every node in the graph.** Both will work just fine, but depth-first search is a bit simpler.

However, **if we want to find the shortest path (or just any path) between two nodes, BFS is generally better.** Consider representing all the friendships in the entire world in a graph and trying to find a path of friendships between Ash and Vanessa.

**In depth-first search**, we could take a path like `Ash -> Brian -> Car let on -> Davis -> Eric -> Farah -> Gayle -> Harry -> Isabella -> John·-> Kari ...` and then find ourselves very far away. We could go through most of the world without realizing that, in fact, Vanessa is Ash's friend. We will still eventually find the path, but it may take a long time. It also won't find us the shortest path.

**In breadth-first search**, we would stay close to Ash for as long as possible. We might iterate through many of Ash's friends, but we wouldn't go to his more distant connections until absolutely necessary. If Vanessa is Ash's friend, or his friend-of-a-friend, we'll find this out relatively quickly.

- **Depth-First Search(DFS)**

In DFS, we visit a node `a` and then iterate through each of `a`'s neighbors. When visiting a node `b` that is a neighbor of `a`, we visit all of `b`'s neighbors before going on to `a`'s other neighbors. That is, a exhaustively searches `b`'s branch before any of its other neighbors.

**Note** that pre-order and other forms of tree traversal are a form of DFS. The **key difference** is that when implementing this algorithm for a graph, we must check if the node has been visited. If we don't, we risk getting stuck in an infinite loop.

- **Breadth-First Search(BFS)**

BFS is a bit less intuitive, and many interviewees struggle with the implementation unless they are already familiar with it. **The main *tripping point 引爆点* is the (false) assumption that BFS is recursive. It's not. Instead, it uses a queue.**

In BFS, node `a` visits each of `a`'s neighbors before visiting any of their neighbors. You can think of this as searching level by level out from `a`. An iterative solution involving a queue usually works best.

If you are asked to implement BFS, the **key thing** to remember is the use of the queue. The rest of the algorithm flows from this fact.

- **Bidirectional Search**

Bidirectional search is used to find the shortest path between a source and destination node. It operates by essentially running two simultaneous breadth-first searches, one from each node. When their searches *collide 碰撞*, we have found a path.

To see why this is faster, consider a graph where every node has at most `k` adjacent nodes and the shortest path from node `s` to node `t` has length `d`. 

* In traditional breadth-first search, we would search up to k nodes in the first "level" of the search. In the second level, we would search up to k nodes for each of those first k nodes, so k^2 nodes total (thus far). We would do this d times, so that's O(k^d) nodes.

* In bidirectional search, we have two searches that collide after approximately d/2 levels (the midpoint of the path). The search from `s` visits approximately k^(d/2) , as does the search from `t`. That's approximately 2k^(d/2), or 0(k^(d/2)), nodes total.

This might seem like a minor difference, but it's not. It's huge. Recall that `(k^(d/2)) * (k^(d/2)) = k^d`. The bidirectional search is actually faster by a factor of k^(d/2).

Put another way: if our system could only support searching "friend of friend" paths in breadth-first search, it could now likely support "friend of friend of friend of friend" paths. We can support paths that are twice as long.

**Additional Reading**: Topological Sort (pg 632), Dijkstra's Algorithm (pg 633), AVL Trees (pg 637), Red-Black Trees(pg 639).

## Recursion and Dynamic Programming

While there are a large number of recursive problems, many follow similar patterns. **A good hint that a problem is recursive is that it can be built off of subproblems.**

When you hear a problem beginning with the following statements, it's often (though not always) a good candidate for recursion: "Design an algorithm to compute the nth .. :; "Write code to list the first n .. :; "Implement a method to compute all..:; and so on.

### How to Approach

**Recursive solutions, by definition, are built off of solutions to subproblems.** Many times, this will mean simply to compute `f(n)` by adding something, removing something, or otherwise changing the solution for `f(n-1)`. In other cases, you might solve the problem for the first half of the data set, then the second half, and then merge those results.

There are many ways you might divide a problem into subproblems. **Three of the most common approaches** to develop an algorithm are **bottom-up, top-down, and half-and-half**.

- **Bottom-Up Approach**

The bottom-up approach is often the most intuitive. We start with knowing how to solve the problem for a simple case, like a list with only one element. Then we figure out how to solve the problem for two elements, then for three elements, and so on. **The key here** is to think about how you can *build* the solution for one case off of the previous case (or multiple previous cases).

- **Top-Down Approach**

The top-down approach can be more complex since it's less *concrete 具体的*. But sometimes, it's the best way to think about the problem.

In these problems, we think about how we can divide the problem for case N into subproblems.

Be careful of overlap between the cases.

- **Half-and-Half Approach**

In addition to top-down and bottom-up approaches, it's often effective to divide the data set in half.

For example, binary search works with a "half-and-half" approach. When we look for an element in a sorted array, we first figure out which half of the array contains the value. Then we recurse and search for it in that half.

Merge sort is also a "half-and-half" approach. We sort each half of the array and then merge together the sorted halves.

### Recursive vs. Iterative Solutions 递归与迭代

**Recursive algorithms can be very space inefficient.** Each recursive call adds a new layer to the stack, which means that if your algorithm recurses to a depth of `n`, it uses at least `O(n)` memory.

For this reason, **it's often better to implement a recursive algorithm iteratively**. All recursive algorithms can be implemented iteratively, although sometimes the code to do so is much more complex. Before diving into recursive code, ask yourself how hard it would be to implement it iteratively, and discuss the tradeoffs with your interviewer.

### Dynamic Programming & Memoization

Although people make a big deal about how scary dynamic programming problems are, there's really no need to be afraid of them. In fact, once you *get the hang of 掌握窍门* them, these can actually be very easy problems.

**Dynamic programming** is mostly just a matter of taking a recursive algorithm and finding the overlapping subproblems (that is, the repeated calls). You then cache those results for future recursive calls.

Alternatively, you can study the pattern of the recursive calls and implement something iterative. You still "cache" previous work.

*A note on terminology*: Some people call top-down dynamic programming "memoization" and only use "dynamic programming" to refer to bottom-up work. We do not make such a distinction here. We call both dynamic programming.

One of the simplest examples of dynamic programming is computing the nth Fibonacci number. A good way to approach such a problem is often to implement it as a normal recursive solution, and then add the caching part.
