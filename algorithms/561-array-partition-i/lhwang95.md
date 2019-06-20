1、本质上是排序之后相邻的组对，然后取最小值的和，但速度不理想

Runtime: 72 ms, faster than 75.00% of Go online submissions for Array Partition I.

Memory Usage: 6.8 MB, less than 31.51% of Go online submissions for Array Partition I.
```
func arrayPairSum(nums []int) int {
    sort.Ints(nums)
    sum := 0
    for i:=0; i<len(nums); i+=2 {
        sum += nums[i]
    }
    return sum
}
```
