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

**Input Size Not Large Enough**: We can only apply asymptotic behavior if the input size is large enough. Large enough meaning when the highest order term in a given algorthm's time complexity becomes the dominant factor, thus making constant and lower-order terms relatively insignificant. In other words, when the efficiency becomes primarily determined by the highest order term. For instance in a Big O(n<sup>2</sup> + n) algorithm, "large enough" would be when n begins to reach numbers greater than 100 for example, where n<sup>2</sup> begins to overshadow the n term. Sometimes in practice, the size of input may not be large enough to reach the point to where the asymptotic complexity actually becomes the dominant factor which determines the performance, therefore effecting the results of the analysis.<br />

**Practical Considerations (e.g Hardware Specs)**: Several things influence real-world performance, the presence or absence of which won't be evidently shown in the asymptotic analysis. For example, the patterns in memory accesses, the effects of caching, disk I/O, and even compiler optimizations could have a significant effect on the actual running time of the algorithm.<br />

## Binary Search Tree Analysis:<br />
Since searching for an element in a binary search tree with 1,000 requires 5 seconds, you'd expect the search time for a tree with 10 times that amount to increase slightly at the very least (assuming tree is balanced). In a typical balanced binary search tree, the asymptotic complexity of search is O(Log n), where n is the number of elements. If you double the number of elements in a binary search tree, the depth would be increased by 1 thus leading to one additional comparison in the worst case. If we go from 1,000 to 10,000 elements, the depth of the tree is increased by a factor that's logarithmic, so you might expect the time to increase to something slightly more than 5 seconds but not drastically more than that, because log<sub>2</sub>(10000)/log<sub>2</sub>(1000) is not a very large factor.<br /> The approximate increase in time with 10,000 elements would be computed by the following:<br /> log<sub>2</sub>(10000)/log<sub>2</sub>(1000) = 1.33  <br />If searching 1,000 elements takes 5 seconds, then you would expect the search time for 10,000 elements to increase by this factor.<br /> So 5 * 1.33 = 6.65 seconds approximately.<br />

## 10,000 Element Performance:<br />
**Several factors could be used to explain this unexpected performance result**:<br />
Tree Imbalance: An unbalanced search tree could lead to slightly longer search paths, changing the complexity from O(logn) to O(n). However, this alone would not extend the search time to 100 seconds. The increase from logarithmic to linear complexity doesn't cause such a drastic delay.<br />

**Inefficient Patterns of Data Access**: The method of accessing the binary tree has a significant effect on performance, particularly due to cache efficiency. If the algorithm implemented for search constantly jumps randomly across the tree, the CPU begins to have difficulties in predicting and preloading data which can result in cache misses. Every cache miss then forces the CPU to go and fetch data from even slower forms of main memory, which significantly slows down the search process.

**Limited System Resources**: Perhaps the system's resources have now become constrained due to the increasing size of data. For instance the available RAM may no longer be enough for the size of the data, thus casuing the system to search for solutions such as swapping from memory to disk (Virtual memory), which would drastically increase access time, leading to an unexpected performance drop.<br />

**Improper Algorithm Implementation**: It could be the case that the search algorithm used may become largely inefficient with ever-growing size of data. For instance, recursive implementations could be causing stack overflow thus wasting CPU time and memory.<br />

**Errors related to Programming**: If programming errors occur while updating the binary search tree, such as during additions, deletions, data handling and comparisons; the tree's structure can easily get disrupted as a cause. As a result this disruption would slow down the search process significantly, making it difficult to find items quickly.



