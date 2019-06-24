### 665. 非递减数列

### 代码
```
func checkPossibility(nums []int) bool {
    count:=1
    for i:=0;i<len(nums)-1;i++{
        if nums[i]>nums[i+1]{
            if count==0{
                return false
            }
            if i==0{
                    nums[i]=nums[i+1]
            }else{

                if nums[i-1]<=nums[i+1]{
                    nums[i]=nums[i+1]
                }else{
                    nums[i+1]=nums[i]
                }
            }
            count--
            
        }
    }
    return true
}
  
```