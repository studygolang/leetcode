```go
func merge(nums1 []int, m int, nums2 []int, n int)  {
    nums1 = append(nums1[0:m], nums2[0:n]...)
	sort.Ints(nums1)
}
```