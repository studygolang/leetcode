递归+贪心算法
```golang
func canJump(nums []int) bool {
	lenNum := len(nums)
	index := 0
	//***贪心算法优化递归过程，可省去此段优化代码进行测试
	val := nums[0]
	for j := 0; j < lenNum; j++ {
		if nums[j] != 0 {
			if j+1+nums[j] >= lenNum {
				return true
			} else if index+val <= j+nums[j] {
				index = j
				val = nums[j]
			}
		} else {
			break
		}
	}
	//***
	if lenNum <= 1 {
		return true
	}
	if nums[0] == 0 {
		return false
	}
	if nums[0] > lenNum {
		return true
	}
	//递归判断
	temp := nums[index] + index
	for i := index + 1; i <= temp; i++ {
		if temp > lenNum {
			return true
		}
		if canJump(nums[i:lenNum]) {
			return true
		}
	}
	return false
}
```

贪心算法
```golang
func canJump(nums []int) bool {
    l := len(nums)
    if l==0{
        return true
    }
    maxv:=nums[0];
    for k,v := range nums{
        if maxv < k{
            return false
        }else if maxv >= l-1{
            return true
        }else if maxv<k+v{
            maxv = k+v
        }
    }
    if(maxv>=l-1){
        return true
    }else{
        return false
    }
    
}
```
