```golang
func permuteUnique(nums []int) [][]int {
    
    if len(nums) == 0 {
        return [][]int{}
    }
    
    sort.Ints(nums)
    
    visited := make([]bool, len(nums))
    res := [][]int{}
    
    backTrack(visited, []int{}, nums, &res)
    
    return res
}

func backTrack(visited []bool, sub, nums []int, res *[][]int) {
    if len(sub) == len(nums) {
        *res = append(*res, append([]int{}, sub...))
        return
    }
    
    for i, num := range nums {
        if visited[i] || (i != 0 && nums[i] == nums[i-1] && !visited[i-1]) {
            continue
        }
        
        visited[i] = true
        sub = append(sub, num)
        backTrack(visited, sub, nums, res)
        visited[i] = false
        sub = sub[:len(sub)-1]
    }
}
```
