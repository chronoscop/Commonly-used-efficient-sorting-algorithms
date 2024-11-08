
# Sorting Algorithms Summary

### 1. Bubble Sort
- **Basic Principle**: Repeatedly traverse the list, compare adjacent elements, and swap them if they are in the wrong order until no more swaps are needed.
- **Time Complexity**: Average and worst case \(O(n^2)\), best case \(O(n)\).
- **Space Complexity**: \(O(1)\).
- **Characteristics**: Simple but inefficient; suitable for small datasets.

### 2. Selection Sort
- **Basic Principle**: Continuously select the smallest (or largest) element from the remaining elements and place it at the end of the sorted sequence.
- **Time Complexity**: Always \(O(n^2)\).
- **Space Complexity**: \(O(1)\).
- **Characteristics**: Unstable, simple, but generally performs slightly better than bubble sort.

### 3. Insertion Sort
- **Basic Principle**: Builds a sorted sequence by inserting each element from the unsorted data into the appropriate position within the sorted part of the sequence.
- **Time Complexity**: Average and worst case \(O(n^2)\), best case \(O(n)\).
- **Space Complexity**: \(O(1)\).
- **Characteristics**: Stable; suitable for small datasets or nearly sorted data.

### 4. Quick Sort
- **Basic Principle**: Selects a pivot element and partitions the data into two parts, one with all elements less than the pivot and the other with elements greater, then recursively applies the same method to each part.
- **Time Complexity**: Average \(O(n \log n)\), worst case \(O(n^2)\); the worst case can be avoided with proper pivot selection.
- **Space Complexity**: \(O(\log n)\) (due to the recursive call stack).
- **Characteristics**: Very efficient, unstable, and suitable for large datasets.

### 5. Merge Sort
- **Basic Principle**: Recursively divides the array into two halves, sorts each half, and then merges the sorted halves back together.
- **Time Complexity**: \(O(n \log n)\) for all cases.
- **Space Complexity**: \(O(n)\).
- **Characteristics**: Stable, performs well on large datasets, but requires extra space.

### 6. Heap Sort
- **Basic Principle**: Builds a max-heap and repeatedly removes the maximum element from the heap, placing it at the end of the sorted array.
- **Time Complexity**: \(O(n \log n)\) for all cases.
- **Space Complexity**: \(O(1)\).
- **Characteristics**: Unstable, in-place sorting, suitable for large datasets.

### 7. Counting Sort
- **Basic Principle**: Counts the occurrences of each element and places them in their final positions based on these counts.
- **Time Complexity**: \(O(n + k)\), where \(k\) is the range of the data.
- **Space Complexity**: \(O(k)\) (for the count array).
- **Characteristics**: Non-comparison sorting, suitable when the data range is small and clear.

### 8. Bucket Sort
- **Basic Principle**: Distributes the data into a finite number of buckets, sorts each bucket individually (often using other algorithms), and then combines them.
- **Time Complexity**: Average \(O(n + k)\), worst \(O(n^2)\).
- **Space Complexity**: \(O(n + k)\).
- **Characteristics**: Effective when data is uniformly distributed.

### 9. Radix Sort
- **Basic Principle**: Sorts data by each digit, starting from the least significant digit to the most significant. Often uses bucket or counting sort as a subroutine.
- **Time Complexity**: \(O(n \cdot k)\), where \(k\) is the number of digits.
- **Space Complexity**: \(O(n + k)\).
- **Characteristics**: Non-comparison sorting, especially efficient for large numbers or strings when \(k\) (digit count or range) is small.

### 10. Shell Sort
- **Basic Principle**: An optimized version of insertion sort, divides the original list into several sub-lists and performs insertion sort on each.
- **Time Complexity**: Depends on the gap sequence; worst case can be \(O(n^2)\), with some sequences achieving \(O(n^{1.5})\) or better.
- **Space Complexity**: \(O(1)\).
- **Characteristics**: Unstable; performs better than simple insertion sort, particularly for medium-sized arrays.
