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

**Input Size Not Large Enough**: We can only apply asymptotic behavior if the input size is large enough. Large enough meaning when the highest order term in a given algorthm's time complexity becomes the dominant factor, thus making constant and lower-order terms relatively insignificant. In other words, when the efficiency becomes primarily determined by the highest order term. For instance in a Big O(n<sup>2</sup> + n) algorithm, "large enough" would be when n begins to reach numbers greater than 100 for example, where the quadratic n<sup>2</sup> begins to overshadow the linear term n. Generally speaking for this example, inputs smaller than 100 are often considered too small for such analysis because, at this scale, both the quadratic and linear components have substantial impacts on the algorithm's perfomance. The contributions from the n term are still significant enough to influence overall efficiency, preventing the demonstration of the quadratic term's dominating effect. Sometimes in practice, the size of input may not be large enough to reach the point to where the asymptotic complexity actually becomes the dominant factor which determines the performance, therefore affecting the results of the analysis.<br />

**Practical Considerations (e.g Hardware Specs)**: Several things influence real-world performance, the presence or absence of which won't be evidently shown in the asymptotic analysis. For example, the patterns in memory accesses, the effects of caching, disk I/O, and even compiler optimizations could have a significant effect on the actual running time of the algorithm.<br />

## Binary Search Tree Analysis:<br />
Since searching for an element in a binary search tree with 1,000 requires 5 seconds, you'd expect the search time for a tree with 10 times that amount to increase slightly at the very least (assuming tree is balanced). In a typical balanced binary search tree, the asymptotic complexity of search is O(Log n), where n is the number of elements. If you double the number of elements in a binary search tree, the depth would be increased by 1 thus leading to one additional comparison in the worst case. If we go from 1,000 to 10,000 elements, the depth of the tree is increased by a factor that's logarithmic, so you might expect the time to increase to something slightly more than 5 seconds but not drastically more than that, because log<sub>2</sub>(10000)/log<sub>2</sub>(1000) is not a very large factor.<br /> The approximate increase in time with 10,000 elements would be computed by the following:<br /> log<sub>2</sub>(10000)/log<sub>2</sub>(1000) = 1.33  <br />If searching 1,000 elements takes 5 seconds, then you would expect the search time for 10,000 elements to increase by this factor.<br /> So 5 * 1.33 = 6.65 seconds approximately.<br />

## 10,000 Element Performance:<br />
**Several factors could be used to explain this unexpected performance result**:<br />
Tree Imbalance: An unbalanced search tree could lead to slightly longer search paths, changing the complexity from O(logn) to O(n). However, this alone would not extend the search time to 100 seconds. The increase from logarithmic to linear complexity doesn't cause such a drastic delay.<br />

**Inefficient Patterns of Data Access**: The method of accessing the binary tree has a significant effect on performance, particularly due to cache efficiency. If the algorithm implemented for search constantly jumps randomly across the tree, the CPU begins to have difficulties in predicting and preloading data which can result in cache misses. Every cache miss then forces the CPU to go and fetch data from even slower forms of main memory, which significantly slows down the search process.

**Limited System Resources**: Perhaps the system's resources have now become constrained due to the increasing size of data. For instance the available RAM may no longer be enough for the size of the data, thus casuing the system to search for solutions such as swapping from memory to disk (Virtual memory), which would drastically increase access time, leading to an unexpected performance drop.<br />

**Algorithm Not Optimized for Scalability and Additional Algorithm Computations**:
When analyzing the performance of a binary search tree with a large dataset, like 10,000 elements, the real challenge arises from the inefficienies that were unaccounted for and the extra steps that become increasingly more problematic as the dataset grows. For example, a recursive search algorithm, while it may work well for small datasets, it might not be the best fit for larger ones (perhaps the algorithm was initially designed for small datasets). This wouldn't mean that the algorithm would fail as soon as it encounters a larger dataset, instead the problem is more subtle with each recursive call adding a small amount of time, and when you add up all these little delays, the total time taken can become surprisingly long. Ontop of the issue of an algorithm not optimized for scalability, there are extra tasks the algorithm might perform that wouldn't necessarily cause errors but significantly increase the search time. For instance, checking the data's validity, logging information, or making sure the data stays consistent during the search. These tasks are minor and easily manageable for small datasets but can significantly slow down the process for large ones. Each of these extra steps take time, and when you're dealing with tens of thousands of elements, the total time added can lead to much longer search times than originally expected. With greater datasets, every single additional processing step must be thoroughly considered due to the potential impact it could have on the total search time. Moreover, ensuring the algorithm is optimized for different size datasets is extremely paramount for performance. <br />




