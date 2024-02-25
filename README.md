[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/FgMJElkj)
# Theory vs. Practice

- List 3 reasons why asymptotic analysis may be misleading with respect to
  actual performance in practice.

- Suppose finding a particular element in a binary search tree with 1,000
  elements takes 5 seconds. Given what you know about the asymptotic complexity
  of search in a binary search tree, how long would you guess finding the same
  element in a search tree with 10,000 elements takes? Explain your reasoning.

- You measure the time with 10,000 elements and it takes 100 seconds! List 3
  reasons why this could be the case, given that reasoning with the asymptotic
  complexity suggests a different time.

Add your answers to this markdown file.

## Reasons Why Asymptotic Analysis May Be Misleading:<br />
**Constant factors and Any Lower Order Terms**: Generally, these are neglected in asymptotic analysis, even though in practical scenarios, constant factors and lower order terms can be significant. An algorithm with worse asymptotic complexity might actually perform better for a small number of items/inputs due to small constants or some lower order terms which are advantageous.<br />

**Different Dataset Sizes**: Asymptotic analysis gives us insight on how an algorithm's running time changes when the dataset size increases. This analysis is most accurate for large datasets. For example, considering an algorithm with time complexity $O(n^2 + n)$. To clearly see and visualize the impact of the n<sup>2</sup> part, we need a large number of items. For instance, the number 100 is used for simplicity to illustrate the point, but in reality the exact number where $n$<sup>$2$</sup> starts to dominate could be more or less than 100. The essential idea is that the bigger the dataset, the more the highest order-term ($n$<sup>$2$</sup>) influences performance, especially when it becomes much larger than the lower-order terms and constants. This means that for smaller datasets, the effect of $n$<sup>$2$</sup> might not be as noticeable since both $n$<sup>$2$</sup> and n affect the algorithm's speed. Therefore, relying solely on asymptotic analysis can be misleading for smaller datasets due to its inability to accurately reflect the algorithm's efficiency. It is not always the case that the more significant terms overshadow the others.

**Practical Considerations (e.g Hardware Specs)**: Several things influence real-world performance, the presence or absence of which won't be evidently shown in the asymptotic analysis. For example, the patterns in memory accesses, the effects of caching, disk I/O, and even compiler optimizations could have a significant effect on the actual running time of the algorithm.<br />

## Binary Search Tree Analysis:<br />
Since searching for an element in a binary search tree with 1,000 requires 5 seconds, you'd expect the search time for a tree with 10 times that amount to increase slightly at the very least (assuming tree is balanced). In a typical balanced binary search tree, the asymptotic complexity of search is O(Log n), where n is the number of elements. If you double the number of elements in a binary search tree, the depth would be increased by 1 thus leading to one additional comparison in the worst case. If we go from 1,000 to 10,000 elements, the depth of the tree is increased by a factor that's logarithmic, so you might expect the time to increase to something slightly more than 5 seconds but not drastically more than that, because log<sub>2</sub>(10000)/log<sub>2</sub>(1000) is not a very large factor.<br /> The approximate increase in time with 10,000 elements would be computed by the following:<br /> log<sub>2</sub>(10000)/log<sub>2</sub>(1000) = 1.33  <br />If searching 1,000 elements takes 5 seconds, then you would expect the search time for 10,000 elements to increase by this factor.<br /> So 5 * 1.33 = 6.65 seconds approximately.<br />

## 10,000 Element Performance:<br />
**Several factors could be used to explain this unexpected performance result**:<br />

**Memory Hierarchy and Cache Misses**: The drastic performance drop can be caused by inefficiencies in memory access patterns, especially for larger datasets. For smaller trees for instance, 1,000 elements, the data structure mostly resides in the faster, upper levels of memory hierarchy, such as the CPU cache, allowing for quick access and search times. However, once the tree size begins to grow to 10,000 elements, the structure's memory usage begins to exceed above the cache capacity, leading to increased cache misses. Hence, requiring more frequent slower main memory accesses, thus drastically impacting search performance. Also, Puzak and Huang (2016) discuss how the structure of BSTs and their memory access patterns can lead to increased cache misses, especially in larger datasets, further impacting performance ("Puzak, T. B., & Huang, C.-H. (2016). An analysis of the effects of spatial locality on the cache performance of binary search trees").

Reference:
https://home.iitk.ac.in/~veena/ICSOFT/Volume%202/Information%20Systems%20and%20Data%20Management/Short%20Papers/C4_200_Puzak.pdf

**Limited System Resources (Insufficient RAM)**: Perhaps the system's resources have now become constrained due to the increasing size of data. For instance the available RAM may no longer be enough for the size of the data, thus casuing the system to search for solutions such as swapping from memory to disk (Virtual memory), which would drastically increase access time, leading to an unexpected performance drop.<br />

**Impact of Update Operations on Large Binary Search Trees**: Large binary search trees face significant slowdowns when they undergo frequent updates, such as insertions and deletions. These operations disrupt and disturb the tree's balance, drastically affecting the search time. This problem grows as the tree expands, where maintaining an efficient structure begins to become a complex challenge. Smaller trees might manage the changes with minimal impact on their performance, but for large trees, the impact is much more significant. The continuous need to rebalance after each update leads to longer paths for searches, increasing time to locate elements. According to Culberson, J. (1985), "the effect of updates on binary search trees, can drastically degrade search performance, emphasizing the scalability challenges for BSTs in managing dynamic data environments." This illustrates the difficulties for binary search trees in keeping up when they have to keep changing.

Reference:
https://dl.acm.org/doi/pdf/10.1145/22145.22168




