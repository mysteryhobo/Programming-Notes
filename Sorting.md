# Sorting

Insertion Sort: O(n^2)

- Moves from the left to the right grabbing elements and dragging them to their correct position
- Best for data sets that are already partially sorted

Heap Sort: O(nLog(n))

- Uses a max heap to select the highest remaining unsorted value and places it at the back of the remaining unsorted array
- Doesn't require any extra buffer space

Quick Sort: O(nLog(n))

- Recursive algorithm that uses a pivot, it swaps elements on its left and right until the pivot is in its correct place and then recurses
- Best for unsorted data
- Worst case of O(n^2) which is worse than heap and merge sort

Merge Sort: O(nLog(n))

- Recursively halves the dataset then merges the parts in sorted order
- Requires linear storage space

Tim Sort: O(nLog

- Stable version of Merge Sort (It maintains relative order of elements)