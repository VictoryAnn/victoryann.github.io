---
title: leetcode刷题-最接近的三数之和
date: 2022-07-22 15:52:55
tag: 排序
banner_image:
category: leetcode刷题
excerpt: 排序+双指针
---
### 16.最接近的三数之和
### 排序+双指针

1. 根据首尾的和跟目标的比较，用来控制首尾指针移动

```go
func threeSumClosest(nums []int, target int) int {
    sort.Ints(nums)
    res := nums[0] + nums[1] + nums[2]
    closed := abs(target, res)
    for i := 0; i< len(nums)-2; i++ {
        left, right := i+1, len(nums)-1
        for left < right {
            subTarget := target - nums[i]
            sum := nums[left] + nums[right]
            if abs(sum, subTarget) < closed {
                closed = abs(sum, subTarget)
                res = sum + nums[i]
            }
            if sum > subTarget {
                right--
            } else {
                left++
            }
        }
    }
    return res
}

func abs(a, b int) int {
    if a - b < 0 {
        return b - a
    }
    return a - b
}
```