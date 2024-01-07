---
title: "Code Highlighting Showcase"
date: "2024-01-05T12:00:00+00:00"
comments: true
socialShare: true
toc: true
---

```kotlin
import kotlin.math.ceil

/**
 * 2870. Minimum Number of Operations to Make Array Empty
 * @see <a href="https://leetcode.com/problems/minimum-number-of-operations-to-make-array-empty">Source</a>
 */
fun interface MinOpToMakeArrayEmpty {
    operator fun invoke(nums: IntArray): Int
}

val minOpToMakeArrayEmptyCounting = MinOpToMakeArrayEmpty { nums ->
    val counter = mutableMapOf<Int, Int>()
    for (num in nums) {
        counter[num] = counter.getOrDefault(num, 0) + 1
    }
    var ans = 0
    for ((_, count) in counter) {
        if (count == 1) {
            return@MinOpToMakeArrayEmpty -1
        }
        ans += ceil(count.toDouble() / 3).toInt()
    }
    return@MinOpToMakeArrayEmpty ans
}
```

```dart
int binarySearch(List<int> nums, int target) {
  var low = 0;
  var high = nums.length - 1;
  while (low <= high) {
    var mid = (low + (high - low) / 2).ceil();
    if (nums[mid] == target) {
      return mid;
    } else if (nums[mid] < target) {
      low = mid + 1;
    } else {
      high = mid - 1;
    }
  }

  return -1;
}
```