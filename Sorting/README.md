# Sorting

## Bubble Sort

- Time Complexity:
    - Best Case: O(n)
    - Worst Case: O(n²)
- Space Complexity: O(1)

```python
def bubble_sort(nums):
    length = len(nums)

    for _ in nums:
        is_sorted = True

        for i in range(length - 1):
            if nums[i] > nums[i + 1]:
                is_sorted = False
                nums[i], nums[i + 1] = nums[i + 1], nums[i]

        if is_sorted:
            return nums
        
    return nums

print('***** ordenado', bubble_sort([1,2,3,5,4,6,7,8,9,10]))
```