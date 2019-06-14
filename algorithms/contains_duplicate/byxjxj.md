func containsDuplicate(nums []int) bool {
    
    count := make(map[int]int, len(nums))
    
    for _, v := range nums {
        count[v]++
        if count[v] > 1 {
            return true
        }
    }
    
    return false
}
