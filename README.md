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

**Input Data Characteristics**: Asymptotic analysis treats all input data as equal, without considering its unique characterisitcs, which can heavily influence how an algorithm performs in real world applications. For instance, the QuickSort algorithm is generally fast but can slow down if the input array is already sorted in ascending or descending order, due to its choice of pivot. On the other hand, Insertion Sort, despite having a worse asymptotic performance of $O(n^2)$ compared to QuickSort's $O(n log n)$, actually runs faster on small or nearly sorted datasets. This difference happens because Insertion Sort has less overhead (less setup) and takes advantage of the existing order within the data, showing how real-world data characteristics can lead to perofrmance that diverges from what asymptotic analysis typically predicts/expects.

**Practical Considerations (e.g Hardware Specs)**: Several things influence real-world performance, the presence or absence of which won't be evidently shown in the asymptotic analysis. For example, the patterns in memory accesses, the effects of caching, disk I/O, and even compiler optimizations could have a significant effect on the actual running time of the algorithm.<br />

## Binary Search Tree Analysis:<br />
Since searching for an element in a binary search tree with 1,000 requires 5 seconds, you'd expect the search time for a tree with 10 times that amount to increase slightly at the very least (assuming tree is balanced). In a typical balanced binary search tree, the asymptotic complexity of search is O(Log n), where n is the number of elements. If you double the number of elements in a binary search tree, the depth would be increased by 1 thus leading to one additional comparison in the worst case. If we go from 1,000 to 10,000 elements, the depth of the tree is increased by a factor that's logarithmic, so you might expect the time to increase to something slightly more than 5 seconds but not drastically more than that, because log<sub>2</sub>(10000)/log<sub>2</sub>(1000) is not a very large factor.<br /> The approximate increase in time with 10,000 elements would be computed by the following:<br /> log<sub>2</sub>(10000)/log<sub>2</sub>(1000) = 1.33  <br />If searching 1,000 elements takes 5 seconds, then you would expect the search time for 10,000 elements to increase by this factor.<br /> So 5 * 1.33 = 6.65 seconds approximately.<br />

## 10,000 Element Performance:<br />
**Several factors could be used to explain this unexpected performance result**:<br />

**Memory Hierarchy and Cache Misses**: The drastic performance drop can be caused by inefficiencies in memory access patterns, especially for larger datasets. For smaller trees for instance, 1,000 elements, the data structure mostly resides in the faster, upper levels of memory hierarchy, such as the CPU cache, allowing for quick access and search times. However, once the tree size begins to grow to 10,000 elements, the structure's memory usage begins to exceed above the cache capacity, leading to increased cache misses. Hence, requiring more frequent slower main memory accesses, thus drastically impacting search performance. Also, Puzak and Huang (2016) discuss how the structure of BSTs and their memory access patterns can lead to increased cache misses, especially in larger datasets, further impacting performance ("Puzak, T. B., & Huang, C.-H. (2016). An analysis of the effects of spatial locality on the cache performance of binary search trees").

Reference:
https://home.iitk.ac.in/~veena/ICSOFT/Volume%202/Information%20Systems%20and%20Data%20Management/Short%20Papers/C4_200_Puzak.pdf

**Limited System Resources (Insufficient RAM)**: Perhaps the system's resources have now become constrained due to the increasing size of data. For instance the available RAM may no longer be enough for the size of the data, thus casuing the system to search for solutions such as swapping from memory to disk (Virtual memory), which would drastically increase access time, leading to an unexpected performance drop.<br />

**External Factors Affecting Performance (Especially in Larger Datasets)**:
Conducting searches within large datasets, such as our binary search tree with 10,000 elements, can cause significant delays (up to 100 seconds), due to a combination of external factors. These factors include thermal throttling, resource competition from other concurrent processes and energy constraints. Each of these factors have a disproportionately greater impact as our dataset grows larger, impacting efficiency of processing:

- Thermal Throttling Impact: Operations required for large dataset searches generate substantially greater heat than a smaller dataset would, leading to elevated CPU temperatures. Modern-day technology employs thermal throttling to reduce processor speed and prevent overheating, and while this ensures the hardware is protected, it significantly slows down all computational tasks. This effect is more common in large searches where longer, intense computation increases the likelihood for thermal throttling to occur.

- Resource Competition with Other Processes: Large dataset searches require significant system resources, such as CPU cycles and memory bandwidth. In environments where multiple applications/processes are running, these searches begin to compete for limited resources. This competition becomes more severe for larger datasets due to the demand for more resources. Simultaneous resource usage can lead to contention, causing slower search operations as the system struggles to distribute sufficient resources to the search task.

These external factors could explain why searching through a larger dataset, such as 10,000 elements, can cause an increase in slowdowns. It shows that the cause of delays aren't just about how the search is performed but also about the computer's physical limits and what else it's doing at the same time. This emphasizes the importance of managing the computer's resources and setup carefully to avoid any major delays when handling large-scale data searches.




