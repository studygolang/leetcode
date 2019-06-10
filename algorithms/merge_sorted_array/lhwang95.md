递归解法

Runtime: 4 ms, faster than 19.32% of Go online submissions for Merge Sorted Array.

Memory Usage: 3.7 MB, less than 5.16% of Go online submissions for Merge Sorted Array.

```
func merge(nums1 []int, m int, nums2 []int, n int)  {
    if m > 0 && n > 0 {
        if nums1[m-1] > nums2[n-1] {
            nums1[m+n-1] = nums1[m-1]
            merge(nums1, m-1, nums2, n)
        } else {
            nums1[m+n-1] = nums2[n-1]
            merge(nums1, m, nums2, n-1)
        }
    }
    if m > 0 && n == 0 {
        nums1[m+n-1] = nums1[m-1]
        merge(nums1, m-1, nums2, n)
    } 
    if n > 0 && m == 0 {
        nums1[m+n-1] = nums2[n-1]
        merge(nums1, m, nums2, n-1)
    }
}
```

递归改循环

Runtime: 0 ms, faster than 100.00% of Go online submissions for Merge Sorted Array.

Memory Usage: 3.6 MB, less than 56.45% of Go online submissions for Merge Sorted Array.
```
func merge(nums1 []int, m int, nums2 []int, n int)  {
    for m > 0 || n > 0 {
        if m > 0 && n > 0 {
            if nums1[m-1] > nums2[n-1] {
                nums1[m+n-1] = nums1[m-1]
                m--
            } else {
                nums1[m+n-1] = nums2[n-1]
                n--
            }
        }
        if m > 0 && n == 0 {
            nums1[m+n-1] = nums1[m-1]
            m--
        } 
        if n > 0 && m == 0 {
            nums1[m+n-1] = nums2[n-1]
            n--
        }
    }
}
```
