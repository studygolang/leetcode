### 215. 数组中的第K个最大元素

### 代码
```
func findKthLargest(nums []int, k int) int {
    left:=0
    right:=len(nums)-1
    for {
        pos:=sort(nums, left, right)
        if pos==k-1{
            return nums[k-1]
        }else if pos>k-1{
            right=pos-1
        }else{
            left=pos+1
        }  
    }
}


// 快排
func sort(nums []int, top int, tail int)int{
    left:=top
    right:=tail
    mid:=nums[left]
    for left<right{
        for left<right&&nums[right]<=mid{
            right--
        }
        nums[left]=nums[right]
        for left<right&&nums[left]>=mid{
            left++
        }
        nums[right]=nums[left]
        if left==right{
            nums[left]=mid
        }
    }
    return left


```

```
func findKthLargest(nums []int, k int) int {
    sort(&nums, k)
    return nums[k-1]
}
// 选择排序
func sort(nums *[]int, k int){
    var max int
    for i:=0;i<k;i++{
        max=i
        for j:=max+1;j<len(*nums);j++{
            if (*nums)[max]<(*nums)[j]{
                max=j
            }
        }
        if max!=i{
            (*nums)[i], (*nums)[max]=(*nums)[max], (*nums)[i]
        }
    }
}
```