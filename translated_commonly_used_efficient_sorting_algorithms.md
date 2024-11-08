
# Commonly Used Efficient Sorting Algorithms

## 1. Quick Sort

Quick Sort, proposed by Tony Hoare in 1960, is a highly efficient sorting algorithm widely used in various programming environments. Quick Sort uses a Divide and Conquer strategy to split a sequence into two sub-sequences. Here are the steps:

### Steps

1. **Pivot Selection**:  
   Quick Sort begins by selecting an element from the array as the pivot. The pivot choice can vary, such as always choosing the first or last element, selecting it randomly, or choosing the median. The quality of the pivot directly impacts Quick Sort’s efficiency.

2. **Partitioning**:  
   The array is rearranged so that all elements smaller than the pivot move to the left, while elements larger than the pivot move to the right. After this step, the pivot is in its final position. This operation occurs within the array, maintaining low space complexity.

3. **Recursively Sort Sub-arrays**:  
   The left and right sub-arrays are then sorted recursively, stopping when the sequence length is 0 or 1, at which point it is considered sorted.

### Performance

- **Best Case**: When the pivot selection divides the list evenly, the time complexity is \(O(n \log n)\).
- **Worst Case**: When the pivot selection results in one partition with 0 elements and the other with \(n-1\), time complexity is \(O(n^2)\), such as in an already sorted or reverse-sorted array.
- **Average Case**: Even under average conditions, the time complexity remains \(O(n \log n)\).

### Space Complexity

- The space complexity of Quick Sort is \(O(\log n)\), due to stack space needed for recursive calls.

Although Quick Sort is very efficient on average, it can perform worse than other \(O(n \log n)\) algorithms, like Merge Sort, in the worst case. For situations requiring high efficiency, other more stable algorithms might be chosen, or Quick Sort could be optimized in terms of pivot selection and implementation (e.g., using randomized Quick Sort or the median-of-three method).

### Demo

```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    else:
        pivot = arr.pop()
        left = [x for x in arr if x <= pivot]
        right = [x for x in arr if x > pivot]
        return quick_sort(left) + [pivot] + quick_sort(right)
```

## 2. Merge Sort

Merge Sort is a stable, \(O(n \log n)\) sorting algorithm that is suitable for large datasets. It also uses a Divide and Conquer approach, with the specific steps as follows:

### Steps

1. **Divide**:  
   Split the array into two halves until each sub-array contains only one element.
2. **Merge**:  
   Merge each pair of sub-arrays into a single sorted array, progressively merging until a single sorted array remains.

### Performance

- **Best, Worst, and Average Cases**: All cases have a time complexity of \(O(n \log n)\), making Merge Sort very stable.

### Space Complexity

- The space complexity of Merge Sort is \(O(n)\), as it requires extra space for merging.

### Demo

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    return merge(left, right)

def merge(left, right):
    result = []
    while left and right:
        if left[0] <= right[0]:
            result.append(left.pop(0))
        else:
            result.append(right.pop(0))
    result.extend(left or right)
    return result
```

## 3. Heap Sort

Heap Sort is an in-place sorting algorithm with \(O(n \log n)\) complexity. Unlike Merge Sort, it doesn’t require extra space, which can be advantageous.

### Steps

1. **Build a Max-Heap**:  
   Construct a Max-Heap from the array.
2. **Extract Maximum Elements**:  
   Repeatedly extract the maximum element from the heap and place it at the end of the array, reducing the heap size each time.

### Performance

- **Best, Worst, and Average Cases**: All cases have a time complexity of \(O(n \log n)\).

### Space Complexity

- Heap Sort has a space complexity of \(O(1)\) since it is an in-place sorting algorithm.

### Demo

```python
def heapify(arr, n, i):
    largest = i
    left = 2 * i + 1
    right = 2 * i + 2
    if left < n and arr[i] < arr[left]:
        largest = left
    if right < n and arr[largest] < arr[right]:
        largest = right
    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]
        heapify(arr, n, largest)

def heap_sort(arr):
    n = len(arr)
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, n, i)
    for i in range(n - 1, 0, -1):
        arr[i], arr[0] = arr[0], arr[i]
        heapify(arr, i, 0)
```

## 4. Insertion Sort

Insertion Sort is a simple, efficient algorithm for small datasets. For larger datasets, however, its \(O(n^2)\) complexity makes it less efficient.

### Steps

1. **Iterate Over the Array**:  
   Insert each element into its correct position in the sorted part of the array.

### Performance

- **Best Case**: \(O(n)\), when the array is nearly sorted.
- **Worst and Average Cases**: Both have a time complexity of \(O(n^2)\).

### Space Complexity

- Insertion Sort’s space complexity is \(O(1)\) as it’s an in-place algorithm.

### Demo

```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
```

## Summary

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

