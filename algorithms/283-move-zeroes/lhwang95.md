Runtime: 60 ms, faster than 99.03% of Go online submissions for Move Zeroes.

Memory Usage: 7.9 MB, less than 26.04% of Go online submissions for Move Zeroes.

```
func moveZeroes(nums []int)  {
    setNum, curNum, length := 0, 0, len(nums)
    if length == 0 {
        return
    }
    for curNum < length {
        if nums[curNum] != 0 {
            nums[setNum] = nums[curNum]
            setNum++
        }
        curNum++
    }
    for setNum < length {
        nums[setNum] = 0
        setNum++
    }
}
```
