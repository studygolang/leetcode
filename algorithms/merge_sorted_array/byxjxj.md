```golang
func merge(nums1 []int, m int, nums2 []int, n int) {
    
    nums1 = append(nums1[:m], nums2...)
    sort.Ints(nums1)
}
```
