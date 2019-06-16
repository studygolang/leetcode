## 题目
[189. 旋转数组](https://leetcode-cn.com/problems/rotate-array/submissions/)

## 思路
如果直接用apend将nums[i:], nums[:i]相加后重新赋值给nums打印出来是正确的，但是被赋值的nums是一个新的地址，原来的nums并没有改变
使用copy直接将正确翻转后的值直接赋给nums即可

## 代码
```go
func rotate(nums []int, k int) {
	i := len(nums) -  k % len(nums)
	copy(nums, append(nums[i:], nums[:i]...))
}
