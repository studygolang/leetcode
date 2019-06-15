func rotate(nums []int, k int)  {
        
    res := make([]int, len(nums))
    
    for i, _ := range nums {
        res[(i+k)%len(nums)] = nums[i]
    }
    
    copy(nums, res)
}
