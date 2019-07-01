### 581. 最短无序连续子数组


### 代码
 ```
func findUnsortedSubarray(nums []int) int {
    start:=-1
    res:=0
    for i:=1;i<len(nums);i++{
        if nums[i]<nums[i-1]{
            j:=i
            for j>0&&nums[j]<nums[j-1]{
                nums[j], nums[j-1]= nums[j-1],nums[j]
                j--
            }
            if start==-1||start>j{
                start=j
            }
            res=i-start+1
        }
    }
        
    return res
}
 
 ```