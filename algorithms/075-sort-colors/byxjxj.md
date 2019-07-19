```golang
func sortColors(nums []int)  {
    
    l, r, cur := 0, len(nums)-1, 0
    
    for cur <= r {
        switch nums[cur] {
        case 0:
            nums[l], nums[cur] = nums[cur], nums[l]
            l++
            cur++
            
        case 2:
            nums[r], nums[cur] = nums[cur], nums[r]     
            r--
            
        default:
            cur++
        }
        
    }
}
```
