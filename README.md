# Quick Sort

## Overview
<p><b>Quick Sort</b> is a widely-used divide-and-conquer sorting algorithm.
It works by selecting a pivot element from the array, partitioning the array into elements less than and greater than the pivot, and recursively sorting the partitions.</b>

It is known for being
-   ✅ Fast on average with O(n log n) time complexity

-   ✅ In-place (requires minimal extra memory)

-   ❌ Not stable (may reorder equal elements)

-   ⚠️ Worst-case performance O(n²) if pivot selection is poor

## ⚙️ How Quick Sort Works

#### Step 1 - Choose Pivot
Select a pivot element. Common strategies
-   First element
-   Last element
-   Random element
-   Median of three

Example array:

```[38,27,43,3,9,82,10]```

Pivot chosen: ```38```


#### Step 2 - Partition
Reorder the array so that
-   Elements < pivot go left
-   Elements > pivot go right

Example:

Left: ```[27,3,9,10]```

Pivot: ```38```

Right: ```[43,82]```


#### Step 3 - Recursively Sort
Apply quick sort recursively on the left and right subarrays:

Left sorted: ```[3,9,10,27]```
Right sorted: ```[43,82]```
Comine: ```[3,9,10,27,38,43,82]```

### ⏱️ Time & Space Complexity
| ⏱️ Case       | Time Complexity |
|---------------|----------------|
| Best Case     | O(n log n)     |
| Average Case  | O(n log n)     |
| Worst Case    | O(n log n)     |

**Space Complexity:** O(log n) due to recursion stack(in-place sorting)



## 📁 Python Implementation
```python
# %% [markdown]
# # Quick Sort

# %%
import random

# %%
def quick_sort(arr):
    # The main Qucik Sort function
    # Qucik Sort is a Divide and Conquer Algorithm. It picks an element as "pivot"
    # and partitions the given array around the picked pivot

    # Base case: If the list has 0 or 1 elements, It's already sorted
    if len(arr) <= 1:
        return arr

    # Choosing the pivot
    # We use the middle element here to avoid worst-case O(n^2) on already sorted lists.
    pivot = arr[len(arr) // 2]

    # Illustration of the Partitioning Strategy:
    # ---------------------------------------------------------
    # Initial: [Left Elements < Pivot]  [Pivot]  [Right Elements > Pivot]
    # Example: [3, 6, 8, 10, 1, 2, 1]  Pivot: 10 (incorrect example, let's use 6)
    # If Pivot = 6:
    # Left:  [3, 1, 2, 1]   (All elements < 6)
    # Mid:   [6]            (The pivot itself)
    # Right: [8, 10]        (All elements > 6)
    # ---------------------------------------------------------

    # Create three sub-lists using list comprehension

    # 1. Elements smaller than the pivot
    left = [x for x in arr if x < pivot]

    # 2. Elements equal to the pivot (handles duplicates values efficiently)
    middle = [x for x in arr if x == pivot]

    # 3. Elements greater than the pivot
    right = [x for x in arr if x > pivot]

    # Recursively sort the left and right parts, then combine them with the middle
    return quick_sort(left) + middle + quick_sort(right)

# %%
def visualize_step(label,list_state):
    # Helper function to print the current state of a list
    print(f"{label:15}: {list_state}")

# %%
def run_demonstration():
    # Runs various examples to showcase the Quick Sort algprithm

    print("----- QUICK SORT PROJECT -----")

    # Example 1. Standard Unsorted Integers
    numbers = [34,7,23,32,5,62,32,12,5]
    print("Example 1: Random Integers")
    visualize_step("Original", numbers)
    sorted_numbers = quick_sort(numbers)
    visualize_step("Sorted", sorted_numbers)

    # Example 2. Strings (Lexicographical sorting)
    fruits = ["apple","orange","bannana","kiwi","pear","cherry"]
    print("Example 2: Alphabetical Strings")
    visualize_step("Original", fruits)
    sorted_fruits = quick_sort(fruits)
    visualize_step("Sorted", sorted_fruits)

    # Example 3: Already Sorted (Efficiency Test)
    sorted_list = [1,2,3,4,5,6,7,8,9]
    print("Example3: Already Sorted List")
    visualize_step("Original", sorted_list)
    result = quick_sort(sorted_list)
    visualize_step("Sorted", result)

    # Example 4: Large Random List
    large_list = [random.randint(0,100) for _ in range(15)]
    print("Example 4: 15 Random Numbers")
    visualize_step("Original", large_list)
    sorted_large = quick_sort(large_list)
    visualize_step("Sorted", sorted_large)

# %%
if __name__ == "__main__":
    # Start the program
    run_demonstration()

# %%
# --- THE LOGIC EXPLAINED ---
# 1. Pivot Selection: We pick a 'pivot' value from the array.
# 2. Partitioning: We reorder the array so that all elements with values 
#    less than the pivot come before it, and all elements with values 
#    greater than the pivot come after it.
# 3. Recursion: We apply the same steps to the 'left' and 'right' 
#    sub-arrays until the entire array is sorted.
# 
# Time Complexity:
# - Best/Average Case: O(n log n)
# - Worst Case: O(n^2) (usually avoided with good pivot selection)
# Space Complexity: O(n) for this recursive implementation using list slices.



```






## 👍 Advantages
-   Fast average-case performance

-   In-place sorting (minimal extra memory)

-   Simple to implement recursively

-   Works well for large datasets

## 👎 Disadvantages

-   Worst-case O(n²) if pivot selection is poor

-   Not stable (equal elements may change order)

-   Recursive calls may hit stack limits for huge arrays



## 📌 When to Use Quick Sort

Use Quick Sort when:

-   Sorting large datasets efficiently

-   Extra memory is limited

-   Stability is not required

-   You can implement good pivot selection (random or median-of-three)


## 🏁 Summary

Quick Sort is a fast, in-place sorting algorithm with excellent average performance.
While it is not stable and has a worst-case scenario, good pivot selection strategies make it very practical for most applications.