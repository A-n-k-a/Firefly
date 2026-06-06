---
title: "Data Structures and Algorithms Revision Notes - Bilingual"
published: 2026-06-06
description: "English-Chinese revision notes for Data Structures and Algorithms."
image: ./145611490_p1.png
tags: []
category: Data Structures and Algorithms
draft: false
pinned: false
lang: en
author: "ChatGPT"
comment: true
---

> 此文章由 GPT-5.5 生成。ChatGPT 也可能会犯错。请核查重要信息。

## Week 1: Big O and Linear Search

Big O describes the upper-bound growth rate of an algorithm as input size `n` increases. If an algorithm always performs the same number of operations, it is `O(1)`. If it halves the search space each step, it is `O(log n)`. If it checks every item once, it is `O(n)`. If it has a loop inside another loop over the same input, it is often `O(n^2)`. When analysing code, keep the fastest-growing term and drop constants: `3n + 10` becomes `O(n)`, and `2n^2 + n` becomes `O(n^2)`.

Big O 描述的是输入规模 `n` 增大时，算法增长速度的上界。如果算法无论输入多大都执行固定数量操作，就是 `O(1)`。如果每一步都把问题规模减半，就是 `O(log n)`。如果逐个检查所有元素，就是 `O(n)`。如果一个循环里面还有一个遍历同一批数据的循环，通常是 `O(n^2)`。分析代码时只保留增长最快的项并去掉常数：`3n + 10` 记为 `O(n)`，`2n^2 + n` 记为 `O(n^2)`。

Linear search starts at the first element of an array and compares each element with the target value. If the current element equals the target, the algorithm returns success or the index. If the end of the array is reached without a match, it returns failure. In the best case, the target is the first item, so the cost is `O(1)`. In the worst case, the target is last or missing, so the cost is `O(n)`.

线性搜索从数组第一个元素开始，把每个元素和目标值比较。如果当前元素等于目标值，就返回成功或返回下标。如果检查完整个数组都没有找到，就返回失败。最好情况是目标值就在第一个位置，复杂度是 `O(1)`。最坏情况是目标值在最后一个位置或根本不存在，需要检查所有元素，复杂度是 `O(n)`。

## Week 2: Binary Search, Sorting, and Linked Lists

Binary search works only on sorted data. It keeps two boundaries, usually `low` and `high`. Each step calculates `mid = (low + high) / 2`. If `array[mid]` is the target, the search stops. If the target is smaller than `array[mid]`, the algorithm moves `high` to `mid - 1`. If the target is larger, it moves `low` to `mid + 1`. The loop stops when `low > high`, meaning the target is not present. Because each step halves the remaining search space, the complexity is `O(log n)`.

二分查找只能用于有序数据。它维护两个边界，通常叫 `low` 和 `high`。每一步计算中间位置 `mid = (low + high) / 2`。如果 `array[mid]` 就是目标值，查找结束。如果目标值小于 `array[mid]`，说明目标只可能在左半边，于是把 `high` 更新为 `mid - 1`。如果目标值大于 `array[mid]`，说明目标只可能在右半边，于是把 `low` 更新为 `mid + 1`。当 `low > high` 时，说明目标不存在。因为每一步都会把搜索范围减半，所以复杂度是 `O(log n)`。

Insertion sort processes the array from left to right. At each position, it takes the current value and inserts it into the correct place inside the already-sorted left part. To do that, it shifts larger elements one position to the right until the correct position is found. It is efficient for nearly sorted or small inputs, but for general input it often needs many shifts, so the average and worst-case complexity are `O(n^2)`.

插入排序从左到右处理数组。每到一个位置，就把当前值插入到左侧已经排好序的部分中。为了插入，它会把比当前值大的元素逐个向右移动，直到找到正确位置。插入排序对小规模数据或接近有序的数据比较好，但普通情况下会产生大量移动，平均和最坏复杂度都是 `O(n^2)`。

Quicksort chooses a pivot value, partitions the array so that smaller values go to one side and larger values go to the other side, then recursively sorts the two partitions. The key operation is partitioning: after partitioning, the pivot is in its final sorted position. If partitions are balanced, quicksort runs in `O(n log n)`. If the pivot repeatedly creates very uneven partitions, such as one side empty and the other side containing almost all elements, it can degrade to `O(n^2)`.

快速排序先选择一个 pivot 基准值，然后进行 partition 分区：比 pivot 小的值放到一边，比 pivot 大的值放到另一边。分区完成后，pivot 已经处于最终排序位置。然后算法递归排序左右两个分区。如果每次分区比较均衡，快速排序复杂度是 `O(n log n)`。如果 pivot 选择很差，每次都导致一边为空、另一边几乎包含所有元素，就会退化到 `O(n^2)`。

A linked list stores data as nodes. Each node contains a value and a reference to the next node. To insert at the head, create a new node, set its `next` to the old head, then update `head` to the new node. To insert after a node, set the new node’s `next` to the old next node, then make the previous node point to the new node. To delete the head, move `head` to `head.next`. To delete after a node, change that node’s `next` so it skips the removed node. Searching requires starting at the head and following links one by one, so search is `O(n)`.

链表用节点存储数据。每个节点包含一个值和一个指向下一个节点的引用。头插时，先创建新节点，把新节点的 `next` 指向原来的 head，再把 `head` 更新成新节点。在某个节点后插入时，先让新节点的 `next` 指向原来的后继节点，再让前一个节点指向新节点。删除头节点时，把 `head` 移动到 `head.next`。删除某个节点之后的节点时，让前一个节点的 `next` 跳过被删除节点。链表查找必须从 head 开始沿链接逐个访问，所以查找复杂度是 `O(n)`。

## Week 3: Hash Tables

A hash table stores key-value pairs in an array. The key is passed into a hash function, and the hash function produces an array index. For example, a string key such as `"Alice"` can be converted into an integer hash value, and then reduced into a table index using modulo: `index = hash % tableSize`. In an ideal hash table, insertion, lookup, and deletion are close to `O(1)` because the key tells us where to look.

哈希表用数组存储 key-value 键值对。key 会传入哈希函数，哈希函数生成数组下标。例如字符串 key `"Alice"` 可以先转换成一个整数哈希值，再通过取模得到表中位置：`index = hash % tableSize`。理想情况下，哈希表的插入、查找和删除接近 `O(1)`，因为 key 可以直接告诉我们应该去哪里找。

A collision happens when two different keys produce the same index. Linear probing solves this by checking the next slot, then the next, until an empty slot is found. Its weakness is clustering: groups of occupied cells form, making later searches slower. Quadratic probing checks positions using jumps such as $+1^2$, $+2^2$, $+3^2$, which reduces clustering. Double hashing uses a second hash function to calculate the jump size. Chaining stores a list of entries at each array position, so collided keys are kept together in a linked list or similar structure.

当不同 key 得到同一个数组下标时，就发生哈希冲突。线性探测的做法是检查下一个位置，再下一个位置，直到找到空位。它的问题是容易产生 clustering 聚集，使后续查找变慢。二次探测使用 $+1^2$、$+2^2$、$+3^2$ 这样的跳跃方式，能减少聚集。双重哈希使用第二个哈希函数计算跳跃步长。链地址法则是在数组每个位置存一个列表，发生冲突的 key 都放在同一个链表或类似结构中。

The load factor is usually `numberOfItems / tableSize`. A low load factor means the table has many empty slots, so collisions are less likely. A high load factor means the table is crowded, so collisions become frequent and operations become slower. A hash table may resize itself when the load factor becomes too high.

负载因子通常是 `元素数量 / 表大小`。负载因子低，说明表中空位多，冲突概率低。负载因子高，说明表很满，冲突会变多，操作也会变慢。当负载因子太高时，哈希表通常需要扩容。

## Week 4: Recursion and Call Stack

A recursive method solves a problem by calling itself on a smaller version of the same problem. It must have a base case and a recursive case. For factorial, the base case is `factorial(0) = 1`; the recursive case is `factorial(n) = n * factorial(n - 1)`. Without a base case, or if the recursive call does not move toward the base case, the method causes infinite recursion and eventually stack overflow.

递归方法通过调用自己来解决规模更小的同类问题。递归必须有基本情况和递归情况。以阶乘为例，基本情况是 `factorial(0) = 1`；递归情况是 `factorial(n) = n * factorial(n - 1)`。如果没有基本情况，或者递归调用没有逐步接近基本情况，就会无限递归，最终导致栈溢出。

The call stack records active method calls. Each call creates a stack frame containing parameters, local variables, and the return point. In recursion, many stack frames can exist for the same method. For example, `factorial(3)` calls `factorial(2)`, which calls `factorial(1)`, which calls `factorial(0)`. After the base case returns, the stack unwinds: `factorial(1)` returns, then `factorial(2)`, then `factorial(3)`.

调用栈记录当前还没有结束的方法调用。每次调用都会创建一个栈帧，里面包含参数、局部变量和返回位置。递归时，同一个方法可能同时有很多个栈帧。例如 `factorial(3)` 调用 `factorial(2)`，后者调用 `factorial(1)`，再调用 `factorial(0)`。基本情况返回后，调用栈开始回退：先返回 `factorial(1)`，再返回 `factorial(2)`，最后返回 `factorial(3)`。

Checked exceptions in Java must be handled or declared. A method can catch an exception using `try/catch`, or it can declare `throws` and let the caller handle it. A `finally` block runs whether an exception happens or not. Try-with-resources is used for resources such as files, because it automatically closes them after use.

Java 的 checked exception 必须被处理或声明。方法可以用 `try/catch` 捕获异常，也可以用 `throws` 声明让调用者处理。`finally` 代码块无论是否发生异常都会执行。try-with-resources 常用于文件等资源，因为它能在使用结束后自动关闭资源。

## Week 5: Trees and Binary Search Trees

A tree consists of nodes connected by edges. The top node is the root. A node’s direct descendants are its children, and its direct ancestor is its parent. A node with no children is a leaf. A subtree is a smaller tree rooted at one node. A binary tree is a tree where each node has at most two children, usually called the left child and right child.

树由节点和边组成。最上面的节点叫 root 根节点。一个节点的直接后代叫 child 子节点，直接上级叫 parent 父节点。没有子节点的节点叫 leaf 叶子节点。以某个节点为根形成的小树叫 subtree 子树。二叉树是每个节点最多有两个子节点的树，通常叫左子节点和右子节点。

Tree traversal means visiting every node in a specific order. Pre-order traversal visits root first, then left subtree, then right subtree. In-order traversal visits left subtree first, then root, then right subtree. Post-order traversal visits left subtree first, then right subtree, then root. For a binary search tree, in-order traversal produces values in sorted order.

树遍历是按特定顺序访问树中所有节点。先序遍历先访问根节点，再访问左子树，再访问右子树。中序遍历先访问左子树，再访问根节点，再访问右子树。后序遍历先访问左子树，再访问右子树，最后访问根节点。对于二叉搜索树，中序遍历会得到从小到大的有序结果。

A binary search tree follows this rule: every value in the left subtree is smaller than the current node, and every value in the right subtree is larger than the current node. To search, compare the target with the current node. If equal, stop. If smaller, move left. If larger, move right. To insert, follow the same comparisons until an empty position is found. If the tree is balanced, search and insertion are `O(log n)`. If the tree becomes a long chain, they become `O(n)`.

二叉搜索树遵守这个规则：左子树中的所有值小于当前节点，右子树中的所有值大于当前节点。查找时，把目标值和当前节点比较；相等就停止；更小就去左边；更大就去右边。插入时也按照同样比较过程移动，直到找到空位置。树平衡时，查找和插入是 `O(log n)`；如果树退化成一条链，就会变成 `O(n)`。

## Week 6: AVL Trees and Huffman Coding

An AVL tree is a self-balancing binary search tree. After insertion, it checks the height difference between the left and right subtrees. This difference is the balance factor. If the balance factor becomes too large or too small, the tree rotates to restore balance. Because it stays balanced, AVL search, insertion, and deletion remain `O(log n)`.

AVL 树是一种自平衡二叉搜索树。插入后，它会检查左右子树高度差，这个差值就是平衡因子。如果平衡因子过大或过小，树会通过旋转恢复平衡。因为 AVL 树保持平衡，所以查找、插入和删除都能保持 `O(log n)`。

There are four common AVL imbalance cases. In the left-left case, the new value is inserted into the left subtree of the left child, so a right rotation is needed. In the right-right case, the new value is inserted into the right subtree of the right child, so a left rotation is needed. In the left-right case, first rotate the left child left, then rotate the root right. In the right-left case, first rotate the right child right, then rotate the root left.

AVL 有四种常见失衡情况。左左情况是新值插入到了左孩子的左子树，需要右旋。右右情况是新值插入到了右孩子的右子树，需要左旋。左右情况要先对左孩子左旋，再对根节点右旋。右左情况要先对右孩子右旋，再对根节点左旋。

Huffman coding builds a binary tree from character frequencies. Characters that appear more often are placed closer to the root and get shorter codes. Characters that appear less often are placed deeper and get longer codes. The final encoding is a prefix code, so no complete code is the prefix of another complete code. This makes decoding unambiguous.

哈夫曼编码根据字符频率构建一棵二叉树。出现频率高的字符更靠近根节点，因此编码更短。出现频率低的字符更深，因此编码更长。最终编码是前缀编码，也就是说没有任何一个完整编码是另一个完整编码的前缀，因此解码不会产生歧义。

## Week 8: Stacks, Queues, Priority Queues, and Graphs

A stack uses last-in-first-out behaviour. `push` adds an item to the top, and `pop` removes the most recently added item. For example, if `A`, `B`, and `C` are pushed in that order, the first pop returns `C`. A stack is useful for undo operations, parsing, recursion simulation, and depth-first traversal.

栈遵守后进先出。`push` 把元素加入栈顶，`pop` 移除最近加入的元素。例如依次压入 `A`、`B`、`C`，第一次 `pop` 会得到 `C`。栈常用于撤销操作、解析、模拟递归和深度优先遍历。

A queue uses first-in-first-out behaviour. `add` or `enqueue` adds an item to the back, and `remove` or `dequeue` removes the item at the front. If `A`, `B`, and `C` enter a queue in that order, the first removal returns `A`. A priority queue removes the item with the highest priority instead of the oldest item. A deque allows adding and removing at both the front and the back.

队列遵守先进先出。`add` 或 `enqueue` 把元素加入队尾，`remove` 或 `dequeue` 从队首移除元素。如果 `A`、`B`、`C` 按顺序进入队列，第一次移除会得到 `A`。优先队列不是移除最早加入的元素，而是移除优先级最高的元素。双端队列允许在队首和队尾两端插入与删除。

A graph contains vertices and edges. In an undirected graph, an edge connects two vertices both ways. In a directed graph, an edge has a direction. In a weighted graph, edges have costs. An adjacency matrix uses a two-dimensional array where `matrix[i][j]` records whether there is an edge from `i` to `j`, or the weight of that edge. An adjacency list stores, for each vertex, a list of its neighbours.

图由顶点和边组成。无向图中的边表示两个顶点可以双向连接。有向图中的边有方向。带权图中的边有代价。邻接矩阵使用二维数组，`matrix[i][j]` 表示从 `i` 到 `j` 是否有边，或这条边的权重。邻接表则为每个顶点保存一个邻居列表。

Depth-first traversal goes as deep as possible before backtracking. It can be implemented with recursion or a stack. Breadth-first traversal visits all immediate neighbours first, then nodes at distance two, then distance three, and so on. It is usually implemented with a queue. Both can be used to check whether all nodes in a graph are reachable.

深度优先遍历会沿一条路径尽可能深入，走不下去再回溯。它可以用递归或栈实现。广度优先遍历会先访问所有直接邻居，再访问距离为 2 的节点，再访问距离为 3 的节点，依此类推。它通常用队列实现。两者都可以用来判断图中所有节点是否可达。

## Week 9: Pathfinding

Dijkstra’s algorithm finds shortest paths in a graph with non-negative edge weights. It starts by setting the start node’s distance to `0` and all other distances to infinity. Each step selects the unvisited node with the smallest known distance. Then it checks that node’s neighbours: if going through the current node gives a shorter distance, the neighbour’s distance is updated. Once a node is marked visited, its shortest distance is fixed.

Dijkstra 算法用于边权非负的图中寻找最短路径。开始时，把起点距离设为 `0`，其他节点距离设为无穷大。每一步选择当前未访问节点中已知距离最小的节点。然后检查它的邻居：如果经过当前节点能得到更短路径，就更新邻居的距离。一旦某个节点被标记为已访问，它的最短距离就确定了。

A* search adds a heuristic to guide the search toward the goal. For each node, it calculates `f(n) = g(n) + h(n)`. `g(n)` is the known cost from the start to the current node. `h(n)` is the estimated cost from the current node to the goal. The algorithm expands the node with the smallest `f(n)`. If the heuristic is good, A* avoids exploring many unnecessary nodes.

A* 搜索加入启发函数来引导算法朝目标方向搜索。对于每个节点，它计算 `f(n) = g(n) + h(n)`。`g(n)` 是从起点到当前节点的已知代价。`h(n)` 是从当前节点到目标节点的估计代价。算法每次扩展 `f(n)` 最小的节点。如果启发函数设计得好，A* 可以避免搜索很多无关节点。

## Week 10: Choosing Data Structures

A list keeps elements in a sequence. An `ArrayList` is good when indexed access is frequent, because getting `list[i]` is fast. However, inserting or deleting near the front or middle can require shifting many elements. A `LinkedList` is better when insertion or deletion near a known node is frequent, but finding an element by index is slower because it must follow links from node to node.

List 保存一组有顺序的元素。`ArrayList` 适合频繁按下标访问，因为读取 `list[i]` 很快。但是在开头或中间插入、删除时，可能需要移动大量元素。`LinkedList` 适合在已知节点附近频繁插入或删除，但按下标查找较慢，因为它必须沿节点链接逐个移动。

A set stores unique values. A `HashSet` is usually fast for add, remove, and contains operations, close to `O(1)`, but it does not keep elements sorted. A `TreeSet` keeps elements ordered, but operations are usually `O(log n)` because it is based on a tree. Choose `HashSet` for fast membership testing, and `TreeSet` when sorted order matters.

Set 存储不重复的值。`HashSet` 的添加、删除和包含检查通常很快，接近 `O(1)`，但它不保持排序。`TreeSet` 会保持元素有序，但操作通常是 `O(log n)`，因为它基于树结构。如果只需要快速判断元素是否存在，选 `HashSet`；如果需要有序结果，选 `TreeSet`。

A map stores key-value pairs. `HashMap` is usually the best choice for fast lookup when order does not matter. `TreeMap` keeps keys sorted, so it is useful when keys must be processed in order. The tradeoff is that `TreeMap` operations are usually `O(log n)`, while `HashMap` operations are usually close to `O(1)` if hashing works well.

Map 存储 key-value 键值对。如果不关心顺序，只需要快速查找，`HashMap` 通常是最佳选择。`TreeMap` 会保持 key 有序，适合需要按 key 顺序处理数据的场景。代价是 `TreeMap` 操作通常是 `O(log n)`，而 `HashMap` 在哈希效果良好时通常接近 `O(1)`。

A graph should be used when the important information is relationships between objects. If the graph is dense and many pairs of nodes are connected, an adjacency matrix can be appropriate because edge lookup is fast. If the graph is sparse, an adjacency list is usually better because it stores only existing edges and uses less memory.

当问题的核心是对象之间的关系时，应使用图。如果图很密集，很多节点之间都有边，邻接矩阵比较合适，因为查询两点之间是否有边很快。如果图很稀疏，邻接表通常更好，因为它只存实际存在的边，更节省内存。

## Week 11: Final Exam Focus

The exam content centres on basic concepts, data structures, and algorithms. For basic concepts, you should be able to calculate or estimate Big O from code. For data structures, you should understand arrays, lists, stacks, queues, priority queues, hash tables, trees, and graphs. For algorithms, you should be able to execute sorting, linear search, binary search, hashing, recursion, tree traversal, and pathfinding by hand.

考试内容主要围绕基础概念、数据结构和算法。基础概念方面，你需要能从代码中计算或估计 Big O。数据结构方面，你需要理解数组、列表、栈、队列、优先队列、哈希表、树和图。算法方面，你需要能手动执行排序、线性搜索、二分查找、哈希、递归、树遍历和路径搜索。

A good way to prepare is to practise tracing. Given stack operations, write down the value returned by each `pop`. Given queue operations, write down the value removed each time. Given a hash table, calculate the hash index and resolve collisions. Given a tree, write its pre-order, in-order, and post-order traversals. Given an AVL insertion, identify the imbalance case and rotation. Given a graph, run DFS, BFS, Dijkstra, or A* step by step.

比较有效的复习方式是练习追踪过程。给出栈操作时，写出每次 `pop` 返回的值。给出队列操作时，写出每次移除的值。给出哈希表时，计算哈希下标并解决冲突。给出一棵树时，写出先序、中序、后序遍历结果。给出 AVL 插入时，判断失衡类型并执行旋转。给出一张图时，逐步执行 DFS、BFS、Dijkstra 或 A*。
