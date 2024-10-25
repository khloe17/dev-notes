---
title: LeetCode Solution for Merge Intervals
date: 2024-10-24 23:28:55
categories: [LeetCode, Algorithm]
tags: [Merge Interval]
---

# Question:

Given an array of intervals intervals where intervals[i] = [starti, endi], return the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping.

Note that intervals which only touch at a point are non-overlapping. For example, [1, 2] and [2, 3] are non-overlapping.

## Explanation

给定一个区间列表 intervals，每个区间是 [start, end] 的形式，代表从 start 到 end 的时间段。可能有多个区间会相互重叠，目标是合并这些重叠的区间，并返回合并后的区间列表。

# Ideas:

1. 排序：首先，我们将区间按照起始时间 start 进行排序，因为排序后的区间更容易处理。
2. 遍历并合并:
   从排序后的第一个区间开始，逐个遍历后面的区间。

   从排序后的第一个区间开始，逐个遍历后面的区间。如果当前区间的开始时间小于等于上一个区间的结束时间，说明它们有重叠。我们将这两个区间合并，合并后的区间的结束时间为两者中较大的结束时间。如果没有重叠，则将当前区间添加到结果列表中，作为一个新的独立区间。

# Code:

```python
def merge(self, intervals: List[List[int]]) -> List[List[int]]:
    if not intervals:
        return []

    intervals.sort(key=lambda x: x[0])
    merged = [intervals[0]]


    for current in intervals[1:]:
        last_merged = merged[-1]

        if current[0] <= last_merged[1]:
            last_merged[1] = max(current[1], last_merged[1])

        else:
            merged.append(current)

    return merged



```
