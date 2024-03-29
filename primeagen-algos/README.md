# [The Last Algorithms Course You'll Need](https://frontendmasters.com/courses/algorithms/)

---
### Table of Contents
1. [Introduction](#introduction)
2. [Basics](#basics)
    1. [Big O Time Complexity](#big-o-complexity)
        - [What is Big O](#what-is-big-o)
        - [Why do we use it](#why-do-we-use-it)
        - [Big O Complexity](#big-o-complexity)
    2. [Arrays Data Structure](#arrays-data-structure)
        - [Array](#array)
        - [Arrays Q and A](#arrays-q-and-a)
3. [Search](#search)
	1. [Linear Search and Katat Setup](#linear-search-and-kata-setup)
		- [Algorithms](#algorithms)
	2. [Binary Search Algorithm](#binary-search-algorithm)
		- [Is it ordered](#is-it-ordered)
	3. [Psuedo Code Binary Search](#psuedo-code-binary-search)
	4. [Two Crystal Balls Problem](#two-crystal-balls-problem)
	5. [Implementing Two Crystal Balls](#implementing-two-crystal-balls)
4. [Sort](#sort)
	1. [Bubble Sort](#bubble-sort)
	2. [Implementing BUbble Sort](#implementing-bubble-sort)
	3. [Linked List Data Structures](#linked-list-data-structures)
		- [What Sucks about an array](#what-sucks-about-an-array)
		- [Let's talk about linked lists](#lets-talk-about-linked-lists)
		- [Insertion](#insertion)
		- [Deletion](#deletion)
		- [Linked List complexity](#linked-list-complexity)
	4. [Queue](#queue)
		- [Implementing a queue](#implementing-a-queue)
		- [Queue Q and A](#queue-q-and-a)
	5. [Stack](#stack)
		- [Implementing a stack](#implementing-a-stack)
5. [Arrays](#arrays)
	1. [Arrays vs Linked Lists](#arrays-vs-linked-lists)
	2. [ArrayList](#arraylist)
	3. [ArrayBuffer](#arraybuffer)
	4. [Data Structures Q and A](#data-structures-q-and-a)
6. [Recursion](#recursion)
	1. [What is Recursion](#what-is-recursion)
	2. [Path Finding: Base Case](#path-finding-base-case)
		- [Maze Solver](#maze-solver)
		- [Implementing Maze Solver](#implementing-maze-solver)
	3. [Recursion Q and A](#recursion-q-and-a)
7. [Quick Sort](#quick-sort)
	1. [Quick Sort Algorithm](#quick-sort-alogrithm)
	2. [Implementing Quick Sort](#implementing-quick-sort)
8. [Doubly Linked List](#doubly-linked-list)
	1. [Intro](#intro)
	2. [Linked List: prepend, instertAt, and append](#linked-list-prepend-insertat-and-append)
	3. [Linked List: remove, get, and removeAt](#linked-list-remove-get-and-removeat)
	4. [Debugging Linked Lists](#debugging-linked-lists)
9. [Trees](#trees)
	1. [Trees Overview](#trees-overview)
		- [Terminology](#terminology)
	2. [Tree Traversals](#tree-traversals)
	3. [Implement Tree Traversal](#implement-tree-traversal)
10. [Tree Search](#tree-search)
	1. [Breadth-First Search](#breadth--first-search)
	2. [Implement Breadth-First Search](#implement-breadth-first-search)
	3. [Search Practice](#search-practice)
	4. [Implement Binary Tree Comparison](#implement-binary-tree-comparison)
	5. [Depth-First Find](#depth-first-find)
	6. [Depth-First Insert](#depth-first-insert)
	7. [Depth-First Delete](#depth-first-delete)
	8. [Binary Search Q and A](#binary-search-q-and-a)
	9. [Implement Depth-First Search](#implement-depth-first-search)
11. [Heap](#heap)
	1. [Heap](#heap-1)
	2. [Implementing Heap](#implementing-heap)
	3. [Tries](#tries)
12. [Graphs](#graphs)
	1. [Graphs Overview](#graphs-overview)
		- [Terminology of Graphs](#terminology-of-graphs)
	2. [Searching an Adjacency Matrix](#searching-an-adjacency-matrix)
		- [How Are Graphs Represented](#how-are-graphs-represented)
		- [Basic Searches](#basic-searches)
	3. [Implement BFS on Adjacency Matrix](#implementing-bfs-on-adjacency-matrix)
	4. [Implement DFS of Adjacency List](#implement-dfs-on-adjacency-list)
	5. [Dijkstra's Shortest Path](#dijkstras-shortest-path)
	6. [Implement Dijkstra's Shortest Path](#implement-dijkstras-shortest-path)
	7. [Dijkstra's Shortest Path Runtime](#dijkstras-shortest-path-runtime)
13. [Maps and LRU](#maps-and-lru)
	1. [Maps](#maps)
		- [Terms](#terms)
	2. [LRU Cache](#lru-cache)
	3. [LRU Cache Setup](#lru-cache-setup)
	4. [Implementing an LRU Cache](#implementing-an-lru-cache)
---

## Introduction
[A Common-Sense Guide to Data Structures and Algorithms](https://www.amazon.com/Common-Sense-Guide-Structures-Algorithms-Second/dp/1680507222?keywords=introduction+to+algorithms&s=books&sr=1-16&linkId=2000de29907b98b5ac7a98aa6b52c1d9&language=en_US&ref_=as_li_ss_tl)
[Introduction to Algorithms](https://www.amazon.com/Introduction-Algorithms-fourth-Thomas-Cormen/dp/026204630X?keywords=introduction+to+algorithms&s=books&sr=1-1&linkId=83c55b2c018fbe94a1de79ebd447b66a&language=en_US&ref_=as_li_ss_tl)

## Basics
### Big O Time Complexity
#### What is Big O
Big O is a way to categorize your algorithms time or memory requirements based on input. It is not meant to be an exact measurement. It will not tell you how many CPU cycles it takes. Instead, it is meant to generalize the growth of your algorithm.
- Example: When someone says Oh of N, they mean your algorithm will grow linearily based on input

#### Why do we use it
Often it will help us make decisions about what data structures and algorithms to use. Knowing how they will perform can greatly help create the best possible program

**Example**:
```js
function sum_char_codes(n:string): number {
	let sum = 0;
	for (let i=0; i<n.length; ++i) {
		sum += n.charCodeAt(i);
	}
	return sum;
}
```
O(n)?

**Big O, said differently**
As your input grows, how fast does computation grow?

**Important concepts**
	1. growth is with respect to the input

**In the real world**
obviously memory growing is not computationally free, but in the matter of thinking about algorithms, we don't necessarily think about that

In languages like Go or JavaScript, you pay even heavier penalties because the memory can be kept around, grows faster, and causes complete halts in your program for cleanup

**Back to the example**
Simplest trick for complexity is to look for loops

**Another Example**
```js
function sum_char_codes(n:string): number {
	let sum = 0;
	for (let i=0; i<n.length; ++i) {
		sum += n.charCodeAt(i);
	}
	for (let i=0; i<n.length; ++i) {
		sum += n.charCodeAt(i);
	}
	return sum;
}
```
Still O(n)... drop constants

**Important concepts**
1. growth is with respect to inputs
2. Constants are dropped
	- O(2n) -> O(n)... Big O is meant to describe the upper bound of the algorithm (the growth of the algorithm). The constant eventually becomes irrelevant.

Take the following:
N = 1, O(10N) = 10, O(N^2) = 1
N = 5, O(10N) = 50, O(N^2) = 25
N = 100, O(10N) = 1000, O(N^2) = 10,000 // 10x bigger
N = 10000, O(10N) = 100,000, O(N^2) = 100,000,000 //1000x bigger

**There is a practical vs theoretical difference**
Just because N is faster than N^2, doesn't mean practically its always faster for smaller input
We drop constants. Therefore O(100N) is faster than O(N^2). But practically speaking, O(N^2) would probably win for some small set of input.

**Let's do another example**
```js
function sum_char_codes(n:string):number {
	let sum = 0;
	for (let i=0; i<n.length;++i) {
		const charCode = n.charCodeAt(i);
		// Capital E
		if (charCode === 69) {
			return sum;
		}
		sum += charCode;
	}
	return sum;
}
```

**In BigO we often consider the worst case**
Especially in interviews... never asked for best, average, and worst case. Just worst case.
E =69
Therefore any string with E in it will terminate early (unless E is the last item in the list)
IT IS STILL O(N)

**Important concepts**
1. growth is with respect to the input
2. Constants are dropped
3. Worst case is usually the way we measure

#### Big O Complexity
O(1)
O(logn)
O(n)
O(n logn)
O(n^2)
O(2^n)
O(n!)

**Some Examples**
**O(N^2)**
```js
function sum_char_codes(n:string):number {
	let sum=0;
	for (let i=0; i<n.lenth;++i) {
		for (let j=0; j<n.length; ++j) {
			sum += charCode;
		}
	}
	return sum;
}
```
**O(N^3)**
```js
function sum_char_codes(n:string):number {
	let sum=0;
	for (let i=0; i<n.lenth;++i) {
		for (let j=0; j<n.length; ++j) {
			for (let k=0; k<n.length; ++k) {
				sum += charCode;
			}
		}
	}
	return sum;
}
```

**O(n log n)**
Quicksort

**O(log n)**
Binary search trees

There is also O(sqrt(n))

**One more note**
There are different ways to measure the complexity of algorithms, but in general the easiest one to use is the "Upper Band"

### Arrays Data Structure
#### Array
A contiguous memory space, contiguous meaning unbreaking, which contains a certain amount of bytes

```js
const a = new ArrayBuffer(6);

a // ArrayBuffer {[Uint8Contents]: <00 00 00 00 00 00>, byteLength: 6}

const a8 = new Uint8Array(a)

a8[0] = 45 // 45

a // ArrayBuffer {[Uint8Contents]: <2d 00 00 00 00 00>, byteLength: 6}

a8[2] = 45 // 45

a // ArrayBuffer {[Uint8Contents]: <2d 00 2d 00 00 00>, byteLength: 6}

const a16 = new Uint16Array(a)

a // ArrayBuffer {[Uint8Contents]: <2d 00 2d 00 00 00>, byteLength: 6}

a16[2] = 0x4545 // 17733

a // // ArrayBuffer {[Uint8Contents]: <2d 00 2d 00 45 45>, byteLength: 6}
```
The purpose of the above information was to show that arrays and lists are not the same ???

**So Let's Talk About Arrays**
- Getting a specific index
	- Takes the width of type and multiplies it by the offset, puts it at the memory address
	- That may not be the exact process, but it's the simplest way to understand it
- Insertion at a specific index
	- Inserting in to an array doesn't necessarily insert it, it overwrites its
	- Go to memory address and add in width of type
- Deletion at a specific index
	- We don't really "delete" anything
	- It gets a 0 or null value
- Insertion and Deletion have a Big O of O(1)... constant time
	- Constant time doesn't mean you do one thing, it means we do a constant amount of things no matter what the input is, it does not grow with the input

**Arrays**
They are fixed size contiguous memory chunks
- That means you cannot grow it
- There is no "insertAt" or push or pop. But that doesn't mean you can write those methods.

#### Arrays Q and A
Q: Arrays don't have insert, push, pop?
A: Technically not. Not if it is a static array or a traditional array

Q: If an array doesn't grow, does its size and memory allocation need to be specified at initialization of the array.
A: An array has to have its size as part of its allocation... you can't grow it. You can reallocate it... meaning you have to create a new array -> take your old array and write it into the new one

Q: When you're creating an array in JavaScript, are you creating something that has an array underneath the hood?
A: Yes, there is a literal array at some point. There is a memory buffer at some point underneath the hood. But, we don't see it that way in JavaScript. The same occurs in Java. For the most part, it operates as an array.

Q: How big is the array that you instantiate?
A: That is part of optimizing. In Rust, if you create a new vector, it's going to create a memory buffer with a size 5 underneath. As you push and pop, it has 5 units for you to be able to play in.


## Search
### Linear Search and Kata Setup
#### Algorithms
The A in DSA

**When Applicable**
I will pretend that JavaScript actually has arrays
I only have access to the .length property of an array

It is a good practice to visualize the problem, discuss it with boxes and arrows, and then program it. It's definitely a core competency that you will follow for life.

Search is something that you do often.
Possibly the simplest algo, Linear Search.
The ``indexOf`` method is a linear search
**What is the Big O**
O(n)... as the input grows, so does the time (linearly)

**Let's Implement it**
``git clone git@github.com:ThePrimeagen/kata-machine.git``

First example is linear search
```js
export default function linear_search( haystack: number[], needle: number,): boolean {
    for (let i = 0; i < haystack.length; i++) {
        if (haystack[i] === needle) {
            return true;
        }
    }
    return false;
}
```

### Binary Search Algorithm
#### **Is it ordered**
If your data set is ordered, you have new advantages you can take with that data
If we have an array that's ordered, we don't have to start in the first position

**10%**
One approach to take would be not to search from the first but to search maybe 10% of n, and then check to see if what you've searched it larger than what you need.
If it is larger, then you can search that portion to get the solution.

So we do 10 operations of jumping, plus 0.1 N. The worst case is still O(n)

Practically speaking, this is better than linear search.  But theoretically, if our elements go from 100 to 1,000,000 our algorithm will run that much slower. So we didn't "improve" the algorithm, we improved it practically speaking.

**Middle**
Another approach is to jump the middle of the array. If our value isn't in the middle, then we can check only 1 half of the array. We can keep cutting the search in half until we ultimately reach:
(N/2<sup>k</sup>) = 1
N=2<sup>k</sup>
log<sub>2</sub>N = k
logN

**Example**
log4096 = 12
4096
2048
1024
512
256
128
64
32
16
8
4
2
1
We take 12 steps to get to 1

So the worst case is we keep have to half the data, logN, and this is a binary search

##### **Another BigO Trick**
If the input halves at each step, its likely O(logN) or O(NlogN)

### Psuedo Code Binary Search
a function that searches an array with a low and high
``search(arr, lo,hi)n``
We could do a loop until some condition occurs
First we find the midpoint: lo + hi - lo divided by 2
**m = lo + (hi-lo) /2**
Adding low is the "offset", hi-lo /2 is midpoint

Then we assign the value to the midpoint

Condition 1 : value === n... then return true
Condition 2 : value > n... lo = m + 1, m = lo + (hi - lo) /2
Condition 3 : else... hi = m

do all that, while lo is less than high

This works only under the assumption that the array is sorted

```js
export default function bs_list(haystack: number[], needle: number): boolean {
    let lo = 0;
    let hi = haystack.length;

    do {
        const m = Math.floor(lo + (hi - lo) / 2);
        const v = haystack[m];

        if (v === needle) {
            return true;
        } else if (v > needle) {
            hi = m;
        } else {
            lo = m + 1;
        }

    } while (lo < hi);

    return false;
}
```

### Two Crystal Balls Problem
Given two crystal balls that will break from high enough distance, determine the exact spot in which it will break in the most optimized way

We're going to have an array filled with false and true, our goal is to find the first true
We can use a linear search to find the optimal breaking point returning true which would be O(n)
If we used binary search at half the data set, it would still be O(n) considering we have two crystal balls and if the first returns true then a ball breaks???
Using binary search, we cut the space in half, but it would be more efficient to jump a square root amount of times???
Using square roots, we make jumps until it breaks and then move back to the last point of non breaking. This would be O($\sqrt{n}$)

### Implementing Two Crystal Balls
The logic is, that when using binary search, if the ball breaks if we start at the half way point, then we only have one ball left and we would have to start at the last none "good" position which would be the start. Then we would linearly search from there. Even though its half the data set, it's still O(n) after dropping constants.


```js
export default function two_crystal_balls(breaks: boolean[]): number {
    // create the jump using square root
    const jumpAmount = Math.floor(Math.sqrt(breaks.length));

    // use first crystal ball to see where it breaks
    let i = jumpAmount;

    for (; i < breaks.length; i += jumpAmount) {
        if (breaks[i]) {
            break;
        }
    }

    // if it breaks, walk back sqrt(n)
    i -= jumpAmount;

    // as long as j is less than the jump amount and i is less than breaks.length, loop until it breaks
    for (let j = 0; j < jumpAmount && i < breaks.length; ++j, ++i) {
        if (breaks[i]) {
            return i;
        }
    }

    return -1;
}
```
We first walk by $\sqrt{n}$
We check for breaks jumping by $\sqrt{n}$
If it breaks, we jump back $\sqrt{n}$
Then we linearly walk forward at most a $\sqrt{n}$ until we find a break

The reason we choose $\sqrt{n}$ is the only way we can change this from non linear running... if we use binary search, we still run into a linear problem



## Sort
### Bubble Sort
Insertion sort is usually the first sort algorithm that is taught, but bubble sort is easy to visualize. It also has only 3 lines and is simple to write.

**Math definition**: x<sub>i</sub> $\leq$ x<sub>i + 1</sub>
any x<sub>i</sub> is less than or equal to x<sub>i + 1</sub>, true for the entire array
This property doesn't hold true universally for an unsorted array

**How Bubble Sort Works**
It starts in the 0<sup>th</sup> poistion and it goes to the end of the array (O(n)???)
It checks if the next element is larger and swaps positions if so
In a singular iteration, an array has the largest item sorted at the the end
So the next bubble sort will go up to, but not include the last position
This will keep running until there's on position left, which means all elements are sorted

First run : [1,3,7,4,2] -> [1,3,4,2,7] n
Second run : [1,3,7,4,2] -> [1,3,2,4,7] n-1
Third run : [1,3,7,4,2] -> [1,2,3,4,7] n -2
Last run: ... n-n+1

(n+1) x n/2 will tell you the sum of numbers between a range
n(n+1) / 2
drop constants: n<sup>2</sup> + n
drop non significant values: n<sup>2</sup>

Bubble sort = O(n<sup>2</sup>)

### Implementing Bubble Sort
We have an array from 0 to n
we start  at 0 and go up to n, but not including n or n-1... because we take i and compare it to i+1... we don't want to go off the array
for i.. n
for j.. n-1-i
if (arr[i] > arr[j]) then swap i and j

**There are other sorting strategies**
But they involve recursion which is a topic for later

### Linked List Data Structures
Earlier, we declared that in JavaScript ``const a = []`` is not actually an array. It has methods like push, which an actual array wouldn't have. There may be an array underneath the hood, but somehow, we have the ability to add.

It is hard to call an array a data structure because it is so fundamental

##### What sucks about an array?
- Deletion: you can't really delete, you can 0 out something.
- Insertion: you can't really insert, you can write
- It's ungrowable

##### Let's talk about linked lists
Often called a node based data structure... a node is the type of container that will wrap our data
In a linked list, if you have a series of values, you're going to see data organized in a way that visiting a data point will point to the next data point (node)
A linked list does not have an index. You have access to a node which you can use to traverse to the node that you desire
get(i) would involve traversing the entire linked list

A singly linked list, one points to the next... you can't walk backwards
A -> B -> C -> D
```js
node<T>
	val: T
	next: ? Node<T>
```

A doubly linked list comes with an extra property, previous... we can walk back and forth form nodes
A <-> B <-> C <-> D
```js
node<t>
	val: T
	next: ? Node<T>
	prev: Node<T>
```

In linked lists, deletion and insertion can be very fast

##### Insertion
In terms of inserting, if we wanted to insert F in between A and B, we would only have to change next and previous properties... we don't need to know about the rest of the linked list

```
Linked List: A -> B -> C -> D
Insert: F after A
A next -> F
F next -> B
B prev -> F
F prev -> A
```
All of these operations are performed at constant time
Insertion is O(1)
We have to remember, practically speaking constants can matter, but theoretically we drop constants... Yes insertion is O(1), but that is after dropping constants

##### Deletion

```
Linked List: A -> B -> C -> D
Delete C

Goal:
B next -> D
D prev -> B

Order of operations:
C prev = B
B next = C next
D prev = C prev
C prev = C next = null (deleting C)
```

The key here is that we have manage the links of ``next`` and ``prev``
Order of operations is important. If we remove a link, we may not be able to access that node anymore. For example, if we don't have access to ``C.next``, then we don't have access to ``D``
Like insertion, Deletion is O(1)

##### Linked List Complexity
If we were to get a value, we'd have to "walk" the list
Get head/tail can be constant
Deletion from ends (head/tail) is constant
Deletion from the middle requires traversal... two operation cost: traversal + deletion
Prepend/Append are constant time (adding to front and end)
Insertion in the middle requires traversal

```js
interface LinkedList<T> {
	get length(): number;
	insertAt(item: T, index: number): void;
	remove(item: T): T | undefined;
	removeAt(index: number): T | undefined;
	append(item: T): void;
	prepend(item: T): void;
	get(index: number): T | undefined;
}
```

Linked lists are foundational. Every linked list is a graph. Every linked list is a tree.

### Queue
Data structure built on top of a linked list. A queue is a specific implementation of a linked list. It is intentionally constrained to be used in a certain way.

**FIFO**
Queues are first in first out
A -> B -> C -> D
A is the head and D is the tail. When inserting in a queue, it goes to the end. So the tail D, will point to the inserted data

**Insertion**
``this.tail.next = data``
``this.tail = data``

**Pop**
Queues are singly linked lists
If we want to pop head:
h = head
head = head.next
h.next = null
return h.value

A queue constrains what you can do. So you're getting O(1) performance for insertion
The actions associated with queues are generally:
- enqueue (add to start)
- dequeue (remove head)
- peek (view head)

#### Implementing a Queue
```js
type Node<T> = {
    value: T;
    next?: Node<T>;
};

export default class Queue<T> {
    public length: number;
    private head?: Node<T>;
    private tail?: Node<T>;

    constructor() {
        this.head = this.tail = undefined;
        this.length = 0;
    }

    enqueue(item: T): void {
        const node = { value: item } as Node<T>;

        this.length++;

        if (!this.tail) {
            this.tail = this.head = node;
            return;
        }

        this.tail.next = node;
        this.tail = node;
    }

    deque(): T | undefined {
        if (!this.head) {
            return undefined;
        }

        this.length--;

        const head = this.head;

        this.head = this.head.next;

        // this step isn't necessary in js, but required in other languages
        head.next = undefined;

        if (this.length === 0) {
            this.tail = undefined;
        }

        return head.value;
    }

    peek(): T | undefined {
        return this.head?.value;
    }

}
```

#### Queue Q and A
``if (!this.tail)`` is the same check as ``if(this.length === 0)``. TypeScript compiler doesn't like ``this.length`` (object is possibly undefined) so we use ``!this.tail``

``peek`` allows us to see the next value returned without mutating the state of the queue... it just gets the value from the head

Why do we set ``this.tail.next`` to the new ``node``?
If we want to insert an element, we have to do two operations:
We first have to go to the tail and set its next to point to F. After that, our tail will still be pointing at E. So the second operation is to set the ``tail`` to the new ``node``.
The tail should always represent the end of the queue.

The opposite of queue is a stack.

### Stack
A stack is singly linked list in which you only add and remove from the head
A stack is a backwards queue
If were to add to a stack, the new ``node`` would point to ``head``. Then the new ``node`` would become the ``head``
The ``reverse`` operation of a stack is removing it. You would save head, then update head to point to next and return out the node.
Like queues, stacks are constrained by design only allowing pushing and popping from one side.

#### Implementing A Stack
##### My Solution
```js
type Node<T> = {
    value: T;
    prev?: Node<T>;
};

export default class Stack<T> {
    public length: number;
    private head?: Node<T>;

    constructor() {
        this.head = undefined;
        this.length = 0;
    }

    push(item: T): void {
        const node = { value: item } as Node<T>;
        this.length++;

        if (!this.head) {
            this.head = node;
            return;
        }

        node.prev = this.head;
        this.head = node;
    }

    pop(): T | undefined {
        if (!this.head) {
            return undefined;
        }

        this.length--;

        const head = this.head;
        this.head = this.head.prev;

        return head.value;
    }

    peek(): T | undefined {
        return this.head?.value;
    }
}
```

##### Prime Solution
```js
type Node<T> = {
    value: T;
    prev?: Node<T>;
};

export default class Stack<T> {
    public length: number;
    private head?: Node<T>;

    constructor() {
        this.head = undefined;
        this.length = 0;
    }

    push(item: T): void {
        const node = { value: item } as Node<T>;
        this.length++;

        if (!this.head) {
            this.head = node;
            return;
        }

        node.prev = this.head;
        this.head = node;
    }



    pop(): T | undefined {
        this.length = Math.max(0, this.length - 1);

        if (!this.head) {
            return undefined;
        }

        const head = this.head as Node<T>;
        this.head = this.head?.prev;

        return head.value;
    }

    peek(): T | undefined {
        return this.head?.value;
    }
}
```

##### Solution with this.length
```js
type Node<T> = {
    value: T;
    prev?: Node<T>;
};

export default class Stack<T> {
    public length: number;
    private head?: Node<T>;

    constructor() {
        this.head = undefined;
        this.length = 0;
    }

    push(item: T): void {
        const node = { value: item } as Node<T>;

        this.length++;

        if (!this.head) {
            this.head = node;
            return;
        }

        node.prev = this.head;
        this.head = node;
    }

    pop(): T | undefined {

        this.length = Math.max(0, this.length - 1);

        if (this.length === 0) {
            const head = this.head;
            this.head = undefined;
            return head?.value;
        }

        const head = this.head as Node<T>;
        this.head = this.head?.prev;
        return head.value;
    }

    peek(): T | undefined {
        return this.head?.value;
    }

}
```

[Math.max](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/max)returns the largest of the numbers given as the input parameters


## Arrays
### Arrays vs Linked Lists

Arrays give fast access with Indices
There isn't a real "insert" in an array, have to shift and unshift data
With arrays, you have to allocate memory upfront... as opposed to linked lists that start with nothing
WIth a linked list, you always have to traverse the entire list when searching, you can't hop to any specific point
You would want to use something like an array if need to scan or hop into a list through random access
If you just want to push/pop into the head/tail, then linked lists are ideal

### ArrayList
Can we do better. Can we have an array access with the ability to grow
An ArrayList uses an array as the fundamental data type instead of a node based structure
Using push is constant time O(1)
Using pop is constant time O(1)
An ArrayList has a capacity that can be extended to allow growth
Eg, the array start a capacity of 3, if you were to push beyond that, it would copy the original array to a new array with a larger capacity
If we use enqueue with an array list, we have to expand the array if at capacity, and then also move each element over = O(n)
ArrayLists are good with push and pop but bad with queue and dequeue
Also, inserting an element in the middle would require everything beyond the index of the insertion to be shifter

**Which one is better?**
It depends on the situation.
Pushing and popping would be good with both.
Arrays gives use good random access.
Removing from the front is poor in an array

You don't necessarily have to know how to implement things, but you should know about the cost of implementing certain things. Understand the why.

### ArrayBuffer
An ArrayBuffer is similar to an ArrayList, but it doesn't use 0 as the head or length as the tail
With an array buffer, we have an indexed based head and an indexed based tail that exists somewhere within the list. So there are null points in the area outside of the head and the tail
To remove from the head, we +1 to the head and remove the old head O(1)
To add to the tail, we +1 to the tail
Pushing, popping, shifting, unshifting are all O(1)

### Data Structures Q and A
If we have these values:
get O(1), push/pop O(1), unshift/shift O(n)
We are probably working with an arraylist ( technically arrays can't grow)

Slice is a linear operation that copies

```js
const a = new Uint8Array(10)

a[0] = 5
a[1] = 5
a[2] = 69

a // Uint8Array(10) [5,5,69,0,0,0,0,0,0,0]

const b = a.slice(0,5)

b[3] = 5

a // Uint8Array(10) [5,5,69,0,0,0,0,0,0,0]

const buf = Buffer.alloc(5)

buf instanceof Uint8Array // true

buf.writeUint(5,0)

buf // <Buffer 05 00 00 00 00>

const buf2 = buf.slice(0,5)
buf2.writeUint8(5,3)

buf // <Buffer 05 00 00 05 00?
```
``a`` hasn't changed when we change ``b``
``buffers`` and ``nodes`` are "shallow" sliced

## Recursion
### What is Recursion
Something that keeps on calling itself over and over again

The simplest way to think of recursion is a function that calls itself until the problem is solved. This usually involves what is called the base case. The base case is the point at which the problem is solved

**The simplest example**
```js
function foo(n: number): number {
	// Base case
	if (n===1) {
		return 1
	}
	// recurse
	return n + foo(n - 1)
}
```
All ways think clearly about the base case

**Three values that can help us visualize**
Return address - a function needs to know how it got here
Return value - a space if made for the value returned
Arguments - when you call a function, this is roughly some memory put into your system

**The Process**
If we call ``foo(5)``, the return address if whoever called ``foo(5)``. We don't know the value yet, its 5+. And we have an argument of 5.
``foo`` checks if the argument is 1. Since it's 5, we now have ``foo(4)`` : (n-1), which is pointing to ``foo(5)``. The value is 4+ with an argument of 4. This will repeat until we have an argument of 1.
Once we get to the end, we know what the return values will be.

<table>
<thead>
<tr>
<td>rA</td>
<td>rV</td>
<td>A</td>
</tr>
</thead>
<tbody>
<tr>
<td>foo5</td>
<td>5+10</td>
<td>5</td>
</tr>
<tr>
<td>foo4</td>
<td>4+6</td>
<td>4</td>
</tr>
<tr>
<td>foo3</td>
<td>3+3</td>
<td>3</td>
</tr>
<tr>
<td>foo2</td>
<td>2+1</td>
<td>2</td>
</tr>
<tr>
<td>foo1</td>
<td>1</td>
<td>1</td>
</tr>
</tbody>
</table>

If we had ``throw Error`` instead of ``return 1`` for our base case, then we would see a stack trace: the stack of functions that have been called

So we go down the stack, the up the stack.

There are two important steps: 1) base case 2) recurse

When it comes to "pathing" there is an important third step to consider which breaks down recurse into three steps
Recurse:
	1. pre: n+
	2. recurse: calling of the functoin
	3. post: we can do a post operation after recursing

### Path Finding: Base Case
#### **Maze Solver**
A list of strings that contain characters.
"###" are walls that you cannot go through
We can go in 4 directions
But we might go to a spot that we've been to before

So we need to create a strong base cast that we don't check for in our recursion

**Base case**:
1. its a wall... this would be an invalid state
2. off the map... if you're on a spot not on the map, you have to return
3. it's the end... our recursion should be complete
4. if we have seen it... we don't want to visit the same place twice

**Recursive case**
Check every direction

#### Implementing Maze Solver
```js
const dir = [
    [-1, 0],
    [1, 0],
    [0, -1],
    [0, 1],
];

function walk(
    maze: string[],
    wall: string,
    curr: Point,
    end: Point,
    seen: boolean[][],
    path: Point[],
): boolean {

    // 1. Base case
    // off the map
    if (
        curr.x < 0 ||
        curr.x >= maze[0].length ||
        curr.y < 0 ||
        curr.y >= maze.length
    ) {
        return false;
    }

    // on a wall
    if (maze[curr.x][curr.y] === wall) {
        return false;
    }

    // the end
    if (curr.x === end.y && curr.y === end.y) {
        path.push(end);
        return true;
    }

    // already been there
    if (seen[curr.y][curr.x]) {
        return false;
    }

    // 3 recurse
    // pre
    seen[curr.y][curr.x] = true;
    path.push(curr);

    // recurse
    for (let i = 0; i < dir.length; ++i) {
        const [x, y] = dir[i];
        if (
            walk(maze, wall, { x: curr.x + x, y: curr.y + y }, end, seen, path)
        ) {
            return true;
        }
    }

    // post
    path.pop();
    return false;
}

export default function solve(
    maze: string[],
    wall: string,
    start: Point,
    end: Point,
): Point[] {
    const seen: boolean[][] = [];
    const path: Point[] = [];

    for (let i = 0; i < maze.length; ++i) {
        seen.push(new Array(maze[0].length).fill(false));
    }

    walk(maze, wall, start, end, seen, path);

    return path;
}
```

Always think about your base case. Find a clear and defined reason why you should stop recursing
Don't test during the recursive step, do it in the base case.
Move everything you can into the base case.

**When do I use recursion**
It is not able to be done with a for loop

### Recursion Q and A
**We programmed in to stop when we reach an area we've seen?**
`` path.pop();`` allows us to go back to an area we've seen?? Each coordinate is added to

**What is the Big(O)**
At most, we would check every square 4 times. So it would be linear, dropping the constant it should be O(n)


## Quick Sort
### Quick Sort Algorithm
To help understand divide and conquer, we are going to implement quicksort. It is an incredibly simple and impressive algorithm.

There is an algorithm technique known as "divide and conquer". The idea is to split you data into chunks and go over those chunks to solve things faster

There are other techniques/strategies. Linear search is "greedy"

With quick sort, we chose a "pivot" from our data and walk the data set from the pivot point and arrange based on whether the data is smaller or larger than the pivot. At this point, this is a "weak sort". We keep on performing this operation until we get to a specific case

Quicksort eventually sorts all the data without having to hold values in temporary structures.
n/2<sup>k</sup> = 1 = log<sub>n</sub>
BigO = O(n log<sub>n</sub>)
However, this wouldn't be true if we don't have a true middle value.
It can also be O(n<sup>2</sup>)
### Implementing Quick Sort
```js
function qs(arr: number[], lo: number, hi: number): void {
    if (lo >= hi) {
        return;
    }

    const pivotIdx = partition(arr, lo, hi);

    qs(arr, lo, pivotIdx - 1);

    qs(arr, pivotIdx + 1, hi);
}

function partition(arr: number[], lo: number, hi: number): number {
    const pivot = arr[hi];
    let idx = lo - 1;

    for (let i = lo; i < hi; ++i) {
        if (arr[i] <= pivot) {
            idx++;
            const tmp = arr[i];
            arr[i] = arr[idx];
            arr[idx] = tmp;
        }
    }

    idx++;

    arr[hi] = arr[idx];

    arr[idx] = pivot;

    return idx;
}

export default function quick_sort(arr: number[]): void {
    qs(arr, 0, arr.length - 1);
}
```

## Doubly Linked List
### Intro
```js
interface LinkedList<T> {
	get length(): number;
	insertAt(item: T, index: number): void;
	remove(item: T): T | undefined;
	removeAt(index: number): T | undefined;
	append(item: T): void;
	prepend(item: T): void;
	get(index: number): T | undefined;
}
```

```js
type Node<T> = {
    value: T;
    prev?: Node<T>;
    next?: Node<T>;
};

export default class DoublyLinkedList<T> {
    public length: number;
    private head?: Node<T>;
    private tail?: Node<T>;

    constructor() {
        this.length = 0;
        this.head = undefined;
        this.tail = undefined;
    }
...
}
```
### Linked List: prepend, insertAt, and append
```js
    prepend(item: T): void {
        const node = { value: item } as Node<T>;

        this.length++;

        if (!this.head) {
            this.head = this.tail = node;
            return;
        }

        node.next = this.head;
        this.head.prev = node;
        this.head = node;
    }

    insertAt(item: T, idx: number): void {
        if (idx > this.length) {
            throw new Error("can't do");
        }

        if (idx === this.length) {
            this.append(item);
            return;
        } else if (idx === 0) {
            this.prepend(item);
	        return;
        }

        this.length++;
        const curr = this.getAt(idx) as Node<T>;
        const node = { value: item } as Node<T>;

        node.next = curr;
        node.prev = curr.prev;
        curr.next = node;

        if (node.prev) {
            node.prev.next = node;
        }
    }

    append(item: T): void {
        this.length++;
        const node = { value: item } as Node<T>;

        if (!this.tail) {
            this.head = this.tail = node;
            return;
        }

        node.prev = this.tail;
        this.tail.next = node;
        this.tail = node;
    }
```

### Linked List: remove, get, and removeAt
```js
    remove(item: T): T | undefined {
        let curr = this.head;

        for (let i = 0; curr && i < this.length; ++i) {
            if (curr.value === item) {
                break;
            }
            curr = curr.next;
        }

        if (!curr) {
            return undefined;
        }

		return this.removeNode(curr);
    }

    get(idx: number): T | undefined {
        return this.getAt(idx)?.value; //5:15
    }

    removeAt(idx: number): T | undefined {
        const node = this.getAt(idx);

        if (!node) {
            return undefined;
        }

        return this.removeNode(node);
    }
```
### Debugging Linked Lists
```js
private debug() {
        let curr = this.head;
        let out = "";

        for (let i =0; curr && i< this.length; ++i) {
	        out += `${i} => ${curr.value}`;
            curr = curr.next;
        }

        console.log(out);
    }
```

## Trees
### Trees Overview
**Where are trees?**
Your filesystem is a tree
The DOM is a tree
Trees are massively important in compilers. You have probably minimally heard the term Abstract Syntax Tree.

Trees are usually represented by nodes. ``node<T>``
Instead of having a next or previous, there are children, an array of possible connections. Or there is a left/right

#### Terminology
root - the most parent node
height - the longest path from the root to the most child node
binary tree - a tree which has at most two children, at least 0 children
general tree - a tree with 0 or more children
binary search tree - a tree which has a specific ordering to the nodes and at most 2 children
leaves - a node without children
balanced - a tree is perfectly balanced when any node's left and right children have the same height
branching factor - the amount of children  a tree has

### Tree Traversals
There are different ways in which you can visit the nodes of a tree
A traversal is the most basic operation you can perform on a tree
There are three types of tree traversals which depend on where you do the visiting of a node
										7
									23   3
								5     4  18  21

preOrder: first visit root, then recurse ---> 7,23,5,4,3,18,21
inOrder: recurse left, visit root, recurse right ---> 5,23,4,7,18,3,21
postOrder: recurse left, then right, then root  ---> 5,4,23,18,21,3,7
preOrder, the root is first.
inOrder root is in the middle.
postOrder root is at the end

This traversal is linear O(n)

Trees are similar to linked lists. The difference being, the nodes don't point to each other, rather nodes have left/right children or children arrays

### Implement Tree Traversal
For these traversals, the base case would be when we are at a node that doesn't exist

```js
//BTSPreOrder
function walk(curr: BinaryNode<number> | null, path: number[]): number[] {
    if (!curr) {
        return path;
    }

    // recurse
    // pre
    path.push(curr.value);

    // recurse
    walk(curr.left, path);
    walk(curr.right, path);

    return path;
}

export default function pre_order_search(head: BinaryNode<number>): number[] {
    // const path: number[] = []
    return walk(head, []);
    // return path;
}
```

```js
//BTSInOrder
function walk(curr: BinaryNode<number> | null, path: number[]): number[] {
    if (!curr) {
        return path;
    }

    walk(curr.left, path);
    path.push(curr.value);
    walk(curr.right, path);

    return path;
}

export default function in_order_search(head: BinaryNode<number>): number[] {
    return walk(head, []);
}
```

```js
//BTPostOrder.ts
function walk(curr: BinaryNode<number> | null, path: number[]): number[] {
    if (!curr) {
        return path;
    }

    walk(curr.left, path);
    walk(curr.right, path);
    path.push(curr.value);

    return path;
}

export default function post_order_search(head: BinaryNode<number>): number[] {
    return walk(head, []);
}
```

These types of traversals are known as depth first.

When we perform recursion, we keep calling a function with it self. We keep passing in something new until we get to base case.
So for inOrder, we go left until we can no longer go left. We go as deep as possible in the tree on the left hand side, and then visit a node. Then we go right and as left as possible until we can't, then visiting a node. So we're always going depth first.
Explicitly, we are working with a tree. But implicitly, we are working with a stack. We keep searching and adding to the stack, then pop off the stack when we can't search anymore.

Technically, we can do this traversal without recursion. We just have to add children to a stack.

## Tree Search
### Breadth- First Search
The opposite of a depth first search
It visits "tree level" visiting one level of the tree at a time
O(n)... but when using an arraylist O(n<sup>2</sup>)
Make sure to use the right data structure when properly implementing a breadth first search
Use a queue

### Implement Breadth First Search
We don't need to use recursion with a breadth-first search
While ``q.notEmpty()`` ``next = q.deque()``
``enqueue(next.L)````enqueue(next.R)``
```js
export default function bfs(head: BinaryNode<number>, needle: number): boolean {
    const q = [head];

    while (q.length) {
        const curr = q.shift() as BinaryNode<number>;
        // search
        if (curr.value === needle) {
            return true;
        }

        if (curr.left) {
            q.push(curr.left);
        }

        if (curr.right) {
            q.push(curr.right);
        }
    }
    return false;
}
```

### Search Practice
Comparing two binary trees to see if they are equal in shape and structure
Depth first search preserves shape whereas breadth first search does not

		7
	23   3

		7
	23
    3

If we were to use breadth first search, the above data structure would return true not accounting for the strucutre
If we were to use depth first search, it would return false as the first structure would return null where the second would return 3

### Implement Binary Tree Comparison
A good idea to create your own function when using recursion.
However, for this exercise doesn't need to create a new function for recursion
```js
export default function compare(
    a: BinaryNode<number> | null,
    b: BinaryNode<number> | null,
): boolean {
    // structural check
    if (a === null && b === null) {
        return true;
    }

    // structural check
    if (a === null || b === null) {
        return false;
    }

    // value check
    if (a.value !== b.value) {
        return false;
    }

    return compare(a.left, b.left) && compare(a.right, b.right);
}
```

### Depth-First Find
The binary search tree. They are not some new ds that we haven't seen. They are specifically an ordering to the data within the data structure

A completely filled tree is where the left and right is completely filled with the same height

BST only rule is the left side is less than or equal to and the right side is greater than
It looks a lot like quicksort

Similar to a binary search on an array list
In a binary search on an array, we split it in half and look for the value from there. If we don't find the value, then we look at whether the value is larger or smaller.

Find is easier to do on a binary search tree than it is on an ordered array.

``find(node, value): bool``
if !node, return false
if node.value === value, return true
if node.value < value, return find(node.right, value)
return find(node.left, value)

O(h) === O of height. The run time is dependent on the height of the tree

### Depth-First Insert
Insertion is very similar to find in that we have to find our way to a node
First we check the value to see if it is larger than or smaller than or equal to

``insert(node, value)``
if node.value < value, ``insert(node.right, value)``
else if node.value $\geq$ value, ``insert(node.left, value)
In cases for null, we can add parent to the signature of the function, we can go back to the parent when hiding a null point and add in the value
Or we could if a side is null, we can insert the value there

Involve the null
if node.value < value... if !node.right, then insert or traverse

### Depth-First Delete
Case 1: no child... we can simple delete
Case 2: one child... set parent to child

We can find the largest on the small(left side) and set that as the new connection after deletion
OR we can find the smallest on the large(right side) and that that as the new node after deletion
If we keep track of height, we will probably want to reorganize the side with larger height

### Binary Search Q and A
Q: After insertion, will it still be balanced?
A: There is no guarantee after insertion that it will still be balanced.

Q: Do we have to use larger than and less than values to create a tree.
A: No. There are "weak ordered" trees that aren't arranged by value.

### Implement Depth-First Search
```js
function search(curr: BinaryNode<number> | null, needle: number): boolean {
    if (!curr) {
        return false;
    }

    if (curr.value === needle) {
        return true;
    }

    if (curr.value < needle) {
        return search(curr.right, needle);
    }

    return search(curr.left, needle);
}

export default function dfs(head: BinaryNode<number>, needle: number): boolean {
    return search(head, needle);
}
```

## Heap
### Heap
The Heap data structure, often referred to as a priority queue, is a binary tree where every child and grand child is smaller (MaxHeap) or larger (MinHeap) than the current node
Whenever a node is added, we must adjust the tree
Whenever a node is deleted, we must adjust the tree
There is no traversing the tree

So with a MinHeap, the top value must be the smallest
Heaps maintain a weak ordering, meaning that they are ordered, but it's not perfectly ordered
The "heap condition" in a MinHeap would say that every node below it must be larger than or equal to it
Getting the smallest item in a MinHeap would be O(1)

A heap is usually a full or complete tree... it's always adding from left to right and it never has any empty spaces

**Adding a node**
When adding a new node, we go to the final spot in our tree and compare. We "bubble up" and swap until a condition is met. If we're in a MinHeap, then the new node should not be smaller than the nodes it's being compared to. If it is, then it bubbles up

**Deleting a node**
When deleting, we delete a the select node, then move the bottom node to that spot?? Then we "heap down" comparing values until everything is in the right spot

We give each node an index.
So there are no management of links. We can find children based on index.
2i + 1 = left child
2i + 2 = right child
(i-1)/ 2 = parent (JS, we would need the floor operation... other languages won't include decimals)
We can use these calculations to traverse the node
To get the end node, we would use the length

### Implementing Heap
Length is used for insertion and deletion
```js
export default class MinHeap {
    public length: number;
    private data: number[];

    constructor() {
        this.data = [];
        this.length = 0;
    }

    insert(value: number): void {
        this.data[this.length] = value;
        this.heapifyUp(this.length);
        this.length++;
    }

    delete(): number {
        if (this.length === 0) {
            return -1;
        }

        const out = this.data[0];
        this.length--;

        if (this.length === 0) {
            this.data = [];
            return out;
        }

        this.data[0] = this.data[this.length];
        this.heapifyDown(0);
        return out;
    }

    private heapifyDown(idx: number): void {
        const lIdx = this.leftChild(idx);
        const rIdx = this.rightChild(idx);

        if (idx >= this.length || lIdx >= this.length) {
            return;
        }

        const lV = this.data[lIdx];
        const rV = this.data[rIdx];
        const v = this.data[idx];

        if (lV > rV && v > rV) {
            this.data[idx] = rV;
            this.data[rIdx] = v;
            this.heapifyDown(rIdx);
        } else if (rV > lV && v > lV) {
            this.data[idx] = lV;
            this.data[lIdx] = v;
            this.heapifyDown(lIdx);
        }
    }

    private heapifyUp(idx: number): void {
        if (idx === 0) {
            return;
        }

        const p = this.parent(idx);
        const parentV = this.data[p];
        const value = this.data[idx];

        if (parentV > value) {
            this.data[idx] = parentV;
            this.data[p] = value;
            this.heapifyUp(p);
        }
    }

    private parent(idx: number): number {
        return Math.floor((idx - 1) / 2);
    }

    private leftChild(idx: number): number {
        return 2 * idx + 1;
    }

    private rightChild(idx: number): number {
        return 2 * idx + 2;
    }
}
```
Insert: O(log n)
Delete: O(log n)

Be careful about garbage. The previous values in the array remain unless you nil them out.

### Tries
If it's not a priority queue, its a trie.
They are pronounced like tree(it's named after retrieval). So it's a Trie tree (but people keep calling them try trees/ prefix trees/ digital trees)

The easiest way to visualize a trie is to think of auto-complete.

In a trie, we have a root. The root doesn't have any value itself.
In an English language tree, our tree can have 1 of 26 possible symbols as its children (unless we're adding symbols and case)

If we wanted to add the word "cat"... we would add child "c", which would have a child "a", and "a" would have a child "t".

To indicate a word, "t" would have an ``"*"`` child which denotes that the path we are on is a word. Or each child would have an ``"isWord"`` boolean flag.

If we wanted to add ``"cats"`` we would add the ``"s"`` after the ``"t"``
If we wanted to add ``"cattle"`` we would start branching from the ``"t"``

If we wanted to autocomplete when someone type ``"c"``, we would have to do a depth-first search
We can add a ``score`` or ``frequency`` to narrow down the search

**Insertion**
An iterative loop where we go to the current node
``insertion(string)``
	``curr = head``
	``for c in string``
		``if (curr[c])``
			``curr = c``
		``else``
			``node = new Node()``
			``curr[c] = node``
			``current = node``
	``curr.isWord = true``

**Deletion**
The opposite of ``insertion``. It's easier to use recursion for ``deletion`` because we want to get to the point of the node, and then delete our way back up

## Graphs

### Graphs Overview
Everything we've done up until this point is effectively a graph
A graph is a series of nodes with some amount of connections

All trees are graphs. Not all graphs are trees.
#### Terminology of Graphs
This is not an exhaustive list of terms.

**Graph Terms**
cycle: When you starte a Node(x), follow the links, and end back at Node(x)
acyclic: A graph that contains no cycles
connected: When every node has a path to another node
directed: When there is a direction to the connections (Twitter)
undirected: !directed. (Facebook)
weighted: The edges have a weight associated with them (Maps)
dag: directed, acyclic graph

**Implementation terms**
node: a point or vortex on the graph
edge: the connection between two nodes

**Big O**
BigO is commonly stated in terms of V and E where V stands for vertices and E stands for edges
so O(V * E) means that we will check every vertex, and on every vertex check every edge

### Searching an Adjacency Matrix
#### How are graphs represented
There are usually two ways to represent a graph (there is a third way of building a full graph node structure that has references of other graph nodes)
- Adjacency List
- Adjacency Matrix
They both have their uses but in general we will mostly see adjacency lists. The reason is because it takes a lot of setup and memory for an adjacency matrix.

An adjacency list would contain the indexes and connections of a node, a list of edges
An adjacency matrix would have rows representing a node and an array that lists its connection with other nodes

#### Basic Searches
BFS and DFS still exist on a graph, and they are virtually no different than on a tree

In DFS, we have a pre and post condition meaning we can push and pop. This allows us to build our path as we search.

In BFS, we don't have recursion, we don't have something that maintains the shape or the structure of our search. We have to maintain it ourselves.  The best way is to use a ``previous`` array couples with a ``seen``/``visited`` array.

### Implementing BFS on Adjacency Matrix
```js
export default function bfs(
    graph: WeightedAdjacencyMatrix,
    source: number,
    needle: number,
): number[] | null {

    const seen = new Array(graph.length).fill(false);
    const prev = new Array(graph.length).fill(-1);

    seen[source] = true;
    const q: number[] = [source];

    do {
        const curr = q.shift() as number;
        if (curr === needle) {
            break;
        }

        const adjs = graph[curr];

        for (let i = 0; i < graph.length; ++i) {
            if (adjs[i] === 0) {
                continue;
            }

            if (seen[i]) {
                continue;
            }

            seen[i] = true;
            prev[i] = curr;
            q.push(i);
        }
    } while (q.length);

    if (prev[needle] === -1) {
        return null;
    }

    // build it backwards
    let curr = needle;
    const out: number[] = [];

    while (prev[curr] !== -1) {
        out.push(curr);
        curr = prev[curr];
    }

    if (out.length) {
        return [source].concat(out.reverse());
    }

    return [];
}
```

### Implement DFS on Adjacency List
O(V+E)
```js
function walk(
    graph: WeightedAdjacencyList,
    curr: number,
    needle: number,
    seen: boolean[],
    path: number[],
): boolean {

    if (seen[curr]) {
        return false;
    }

    seen[curr] = true;

    // recurse
    // pre
    path.push(curr);
    if (curr === needle) {
        return true;
    }

    // recurse
    const list = graph[curr];
    for (let i = 0; i < list.length; ++i) {
        const edge = list[i];

        if (walk(graph, edge.to, needle, seen, path)) {
            return true;
        }
    }

    // post
    path.pop();

    return false;
}

export default function dfs(
    graph: WeightedAdjacencyList,
    source: number,
    needle: number,
): number[] | null {
    const seen: boolean[] = new Array(graph.length).fill(false);
    const path: number[] = [];

    walk(graph, source, needle, seen, path);

    if (path.length === 0) {
        return null;
    }

    return path;
}
```

### Dijkstra's Shortest Path
Calculating the shortest path from one node to all other nodes in the graph
We can also find the shortest path to individual nodes

A family of greedy algorithms

We need a previous array initially filled with -1
We need a seen array that is initially filled with falses
Then we need a way to calculate the shortest distance... this will be done with a distance array that is filled with infinities except for our source node
The distance of our source node is 0

We want to get the lowest/nearest unseen node
while we have unvisted, we get the lowest unseen... then we mark it as seen
Dijkstras works by working one at a time updating the distances for who has the shortest distance to where

For edge in lo, If edge is in the seen array, then continue. Edge weight is added to distance of lo. If that distance is lower than the last known best distance, we updated the lo.

### Implement Dijkstra's Shortest Path
```js
function hasUnvisited(seen: boolean[], dists: number[]): boolean {
    return seen.some((s, i) => !s && dists[i] < Infinity);
}

function getLowestUnvisited(seen: boolean[], dists: number[]): number {
    let idx = -1;
    let lowestDistance = Infinity;

    for (let i = 0; i < seen.length; ++i) {
        if (seen[i]) {
            continue;
        }

        if (lowestDistance > dists[i]) {
            lowestDistance = dists[i];
            idx = i;
        }
    }

    return idx;
}

export default function dijkstra_list(
    source: number,
    sink: number,
    arr: WeightedAdjacencyList,
): number[] {
    const seen = new Array(arr.length).fill(false);
    const prev = new Array(arr.length).fill(-1);
    const dists = new Array(arr.length).fill(Infinity);
    dists[source] = 0;

    while (hasUnvisited(seen, dists)) {
        const curr = getLowestUnvisited(seen, dists);
        seen[curr] = true;

        const adjs = arr[curr];
        for (let i = 0; i < adjs.length; ++i) {
            const edge = adjs[i];
            if (seen[edge.to]) {
                continue;
            }

            const dist = dists[curr] + edge.weight;
            if (dist < dists[edge.to]) {
                dists[edge.to] = dist;
                prev[edge.to] = curr;
            }
        }
    }

    const out: number[] = [];
    let curr = sink;

    while (prev[curr] !== -1) {
        out.push(curr);
        curr = prev[curr];
    }

    out.push(source);
    return out.reverse();
}
```

### Dijkstra's Shortest Path Runtime
We create arrays that are V long
While loop checking is O(V<sup>2</sup>)
Get low check is also O(V<sup>2</sup>)
This is a situation where just counting loops doesn't give an accurate runtime
The forloop is not exhaustive, it doesn't go over every edge in the graph
So the total run time is O(V<sup>2</sup> + E)
I don't completely follow the logic, but some of the search is actually log V
So the actual run time is O(logV(VxE)) (better than V<sup>2</sup>)


## Maps and LRU
### Maps
**What are maps?**
It is too easy to think of ``{}`` or ``new Map()`` and just assume we know them. The reality is we know how to use them, most of the time we don't actually know how they work
A map is different from ``{}``
#### Terms
load factor: The amount of data points vs the amount of storage (data.len / storage.capacity)
key: a value that is hashable and used to look up data. The hash has to be consistent
value: a value that is associated with a key
collision: when 2 keys map to the same cell

How a map works is that we have a key and it needs to map to a value
They keys mapping to a hash has to be a consistent hash
A hashing function takes in a key and produces a unique number

Under the hood, we're using an ArrayList or a LinkedList

### LRU Cache
**What is a LRU**
Least Recently Used: a caching mechanism that says, we will evict the least recently used item
A doubly linked list is a data structure to use when working with LRUs
We also have the potential to use a hash map
So the hard question is how do we use both at the same time.
So we have a hash map associated with two generics: ``Hashmap<k,v>``
Our value would be a node within the linked list
A hash map lookup is O(1)
So basically, we're combining two data structures to get benefits from both

### LRU Cache Setup
```js
export default class LRU<K, V> {
    private length: number;

    constructor() {}

    update(key: K, value: V): void {
        // does it exist

        // if it doesn't we need to insert
        //  - check capacity and evict if over

        // if it does, we need to update to the front of the list and update value
    }



    get(key: K): V | undefined {
        // check the cache for existance

        // update the value we found and move it to the front

        // return out the value found or undefined if value doesn't exist
    }
}
```

### Implementing an LRU Cache
We're creating a combination of a linked list and a map to cache data
```js
type Node<T> = {
    value: T;
    next?: Node<T>;
    prev?: Node<T>;
};

function createNode<V>(value: V): Node<V> {
    return { value };
}

export default class LRU<K, V> {
    private length: number;
    private head?: Node<V>;
    private tail?: Node<V>;

    private lookup: Map<K, Node<V>>;
    private reverseLookup: Map<Node<V>, K>;

    constructor(private capacity: number = 10) {
        this.length = 0;
        this.head = this.tail = undefined;
        this.lookup = new Map<K, Node<V>>();
        this.reverseLookup = new Map<Node<V>, K>();
    }

    update(key: K, value: V): void {
        let node = this.lookup.get(key);
        if (!node) {
            node = createNode(value);
            this.length++;
            this.prepend(node);
            this.trimCache();

            this.lookup.set(key, node);
            this.reverseLookup.set(node, key);
        } else {
            this.detach(node);
            this.prepend(node);
            node.value = value;
        }
    }

    get(key: K): V | undefined {
        // check the cache for existance
        const node = this.lookup.get(key);
        if (!node) {
            return undefined;
        }

        // update the value we found and move it to the front
        this.detach(node);
        this.prepend(node);

        // return out the value found or undefined if value doesn't exist
        return node.value;
    }

    private detach(node: Node<V>): void {
        if (node.prev) {
            node.prev.next = node.next;
        }

        if (node.next) {
            node.next.prev = node.prev;
        }

        if (this.head === node) {
            this.head = this.head.next;
        }

        if (this.tail === node) {
            this.tail = this.tail.prev;
        }

        node.next = undefined;
        node.prev = undefined;
    }

    private prepend(node: Node<V>) {
        if (!this.head) {
            this.head = this.tail = node;
            return;
        }

        node.next = this.head;
        this.head.prev = node;

        this.head = node;
    }

    private trimCache(): void {
        if (this.length <= this.capacity) {
            return;
        }

        const tail = this.tail as Node<V>;
        this.detach(this.tail as Node<V>);

        const key = this.reverseLookup.get(tail) as K;
        this.lookup.delete(key);
        this.reverseLookup.delete(tail);
        this.length--;
    }
}
```