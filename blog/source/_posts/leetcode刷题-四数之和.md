---
title: leetcode刷题-四数之和
date: 2022-07-22 20:23:19
tag: 排序
banner_image:
category: leetcode刷题
excerpt: 排序+双指针
---
### 18.四数之和
### 排序+双指针
做法跟三数之和一样
```go
func fourSum(nums []int, target int) [][]int {
    sort.Ints(nums)
    res := make([][]int, 0)
    for i:=0;i<len(nums)-3;i++ {
        if i-1>=0 && nums[i] == nums[i-1] {continue}
        a := nums[i]
        for j:=i+1;j<len(nums)-2;j++ {
            if j-1>i && nums[j] == nums[j-1] {continue}
            b := nums[j]
            left, right := j+1, len(nums)-1
            for left < right {
                c,d := nums[left], nums[right]
                if a+b+c+d == target {
                    res = append(res, []int{a,b,c,d})
                    left++
                    right--
                    for left < len(nums) && nums[left] == nums[left-1] {left++}
                    for right > -1 && nums[right] == nums[right+1] {right--}
                } else if a+b+c+d < target {
                    left++
                } else {
                    right--
                }
            }
        }
    }
    return res
}
```