## 题目

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.


```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

[原题地址](https://leetcode.com/problems/two-sum/)

## 解题过程

耗时8ms，考虑nums中会有重复的值，但只选择第一个符合target的索引列表，可惜没用到什么好的解题思路
```
func twoSum(nums []int, target int) []int {
	data := make(map[int]([]int), 0)
	for i, value := range nums {
		_, ok := data[value]
		if ok {
			data[value] = append(data[value], i)
		} else if !ok {
			data[value] = []int{i}
		}
	}
	res := make([]int, 0)
	for value, cal := range data { //获取值和索引列表
		rest := target - value
		if rest == value && len(cal) >= 2 { //输入列表可能会有重复的值，取对应值前两个坐标
			if cal[0] < cal[1] {
				res = append(res, cal[0])
				res = append(res, cal[1])
			} else {
				res = append(res, cal[1])
				res = append(res, cal[0])
			}
			break
		} else if val, ok := data[rest]; ok && rest != value { //找到另外一个值
			if cal[0] < val[0] {
				res = append(res, cal[0])
				res = append(res, val[0])
			} else {
				res = append(res, val[0])
				res = append(res, cal[0])
			}
			break
		}
	}
	return res
}
```
