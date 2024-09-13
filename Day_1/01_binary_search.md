### Binary Search

**Binary Search** is an efficient algorithm for finding an element in a **sorted array** or list. It follows the "divide and conquer" approach, making it faster than linear search, particularly for large datasets.

#### Key Concepts
- **Precondition**: The array must be sorted.
- **Time Complexity**: O(log n), where `n` is the number of elements.
- **Space Complexity**: O(1) for iterative implementation and O(log n) for recursive implementation due to recursion stack.

### Steps in Binary Search
1. **Initialization**: Define two pointers, `low` (start of the array) and `high` (end of the array).
2. **Middle Element**: Calculate the middle index `mid = (low + high) // 2`.
3. **Comparison**:
   - If the middle element equals the target, return its index.
   - If the target is less than the middle element, search the left half by updating `high = mid - 1`.
   - If the target is greater than the middle element, search the right half by updating `low = mid + 1`.
4. **Repeat**: Continue until `low` exceeds `high` (meaning the target is not present).
5. **Termination**: If the target is not found, return -1.

### Example Code: Iterative Approach (Python)
```python
def binary_search(arr, target):
    low, high = 0, len(arr) - 1

    while low <= high:
        mid = (low + high) // 2

        if arr[mid] == target:
            return mid  # Target found at index mid
        elif arr[mid] < target:
            low = mid + 1  # Search in the right half
        else:
            high = mid - 1  # Search in the left half

    return -1  # Target not found
```

### Recursive Approach
```python
def binary_search_recursive(arr, target, low, high):
    if low > high:
        return -1  # Target not found

    mid = (low + high) // 2

    if arr[mid] == target:
        return mid
    elif arr[mid] < target:
        return binary_search_recursive(arr, target, mid + 1, high)
    else:
        return binary_search_recursive(arr, target, low, mid - 1)
```

### Advantages of Binary Search
- **Efficiency**: Binary search is much faster than linear search for large datasets.
- **Low Space Complexity**: The iterative version uses constant space, and the recursive version uses only O(log n) space due to recursion depth.

### Drawbacks
- **Sorted Data Requirement**: Binary search only works on sorted arrays. If the array is unsorted, it must be sorted first, adding O(n log n) time complexity for sorting.
- **Static Nature**: It is not optimal for dynamic datasets (frequently updated), as re-sorting would be needed.

### Variants of Binary Search
1. **Lower Bound Search**: Finds the first occurrence of a target element in the array.
2. **Upper Bound Search**: Finds the last occurrence of a target element.
3. **Search for Insertion Point**: Finds where a target should be inserted in a sorted array to maintain the order.

### Binary Search on Other Data Structures
While binary search is mainly used on arrays, the concept can also be applied to:
- **Binary Search Trees (BST)**: The structure naturally divides elements, and binary search is implicitly used.
- **Rotated Sorted Arrays**: A more complex form of binary search can be applied to handle sorted arrays that have been rotated.

### Time Complexity Analysis
- In each step, binary search divides the dataset in half. This results in O(log n) comparisons in the worst case.
- **Best Case**: O(1) – The middle element is the target.
- **Worst Case**: O(log n) – Target is either at the beginning or end of the array, or not present.

### Conclusion
Binary search is a powerful algorithm for searching sorted data efficiently. It drastically reduces the number of comparisons compared to linear search and is widely used in applications requiring fast search operations.