---
title: leetcode刷题-三数之和
date: 2022-07-17 20:12:49
tag: 排序
banner_image:
category: leetcode刷题
excerpt: 排序+双指针
---
### 15.三数之和
### 排序+双指针
1. 在有序数列中跳过重复数字来去重

```go
func threeSum(nums []int) [][]int {
    var res [][]int
    sort.Ints(nums)
    for i := 0;i < len(nums)-2;i++ {
        if i > 0 && nums[i] == nums[i-1] {
            continue
        }
        left, right := i+1, len(nums)-1
        for left < right {
            total := nums[left] + nums[right] + nums[i]
            if  total == 0 {
                res = append(res, []int{nums[i], nums[left], nums[right]})
                left++
                right--
                for left < right && nums[left] == nums[left-1] {
                    left++
                }
                for left <  right && nums[right] == nums[right+1] {
                    right--
                }
                continue
            }
            if total < 0 {
                left++
            } else {
                right--
            }
            
        }
    }
    return res
}
```