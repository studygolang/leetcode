```golang
func permute(nums []int) [][]int {
    
    if len(nums) == 0 {
        return [][]int{}
    }
    
    visited := make([]bool, len(nums))
    res := [][]int{}
    
    backTrack(nums, visited, &res, []int{})
    
    return res
}

func backTrack(nums []int, visited []bool, res *[][]int, sub []int) {
    if len(sub) == len(nums) {
        tmp := make([]int, len(sub))
        copy(tmp, sub)
        *res = append(*res, tmp)
        return
    }
    
    for i, num := range nums {
        if visited[i] {
            continue
        }
        visited[i] = true
        sub = append(sub, num)
        backTrack(nums, visited, res, sub)
        visited[i] = false
        sub = sub[:len(sub)-1]
    }
}
```
