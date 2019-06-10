Runtime: 4 ms, faster than 19.32% of Go online submissions for Merge Sorted Array.

Memory Usage: 3.7 MB, less than 5.16% of Go online submissions for Merge Sorted Array.

应该有更好的解法
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
