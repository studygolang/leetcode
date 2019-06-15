### 题目
[169. 求众数](https://leetcode-cn.com/problems/majority-element/solution/)

### 思路一
>解法一(不推荐)：创建一个map，出现相同的加一，大于数组一半就返回

## 代码一
```go
// 通过创建map存储的解法
func majorityElement(nums []int) int {
	if len(nums) == 1 {
		return nums[0]
	}

	m := make(map[int]int)
	for _, v := range nums {
		if  m[v] != 0 {
			m[v]++
			if m[v] > len(nums)/2{
				return v
			}
		} else {
			m[v] = 1
		}
	}
	return 0
}
```


## 思路二
>解法二（推荐)：创建一个临时数组arr，再遍历目标的数组
  >>arr里面没有值或遍历的当前值已经在arr中就将该数添加到arr中；
  
  >>如果当前值不等于arr中的值,将arr中的值减去一个，抵消当前值；
  
  >>抵消到最后还存在arr中的就是众数
## 代码二
```go
// 摘抄通过摩尔投票法解法
func majorityElement3(nums []int) int {
	// 创建数组
	arr := make([]int, len(nums))
	// 创建下标
	index := 0

	for i:=0; i<len(nums); i++ {
		// 如果当前数组为空 或者 当前数组已经有这个数
		if index == 0 || arr[index-1] == nums[i] {
			// 将该数再次添加进数组并将index+1
			arr[index] = nums[i]
			index++
		} else {
      // 将下标减1，抵消当前数
			index--
		}
	}
	// 返回该数值中存在的值
	return arr[index-1]
}
