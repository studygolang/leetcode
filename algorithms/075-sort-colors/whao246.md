### 75. 颜色分类


### 代码

```
func sortColors(nums []int){
    l:=0
    cur:=0
    r:=len(nums)-1
    for cur<=r{
        if nums[cur]==0{
            nums[l], nums[cur]=nums[cur], nums[l]
            cur++
            l++
        }else if nums[cur]==2{
            nums[cur], nums[r]=nums[r], nums[cur]
            r--
        }else{
            cur++
        }
    }
}
```