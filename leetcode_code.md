# LeetCode代码

## 1. 动态规划

+ [3. 无重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)

	+ 思路：（1）标记重复元素位置的最大index；（2）记录最大长度

	+ 题解：
	```python
	class Solution:
	    def lengthOfLongestSubstring(self, s: str) -> int:
	        if not s:
	            return 0

	        max_length = 0
	        tmp_start = 0
	        tmp_dict = {}

	        for inx, value in enumerate(s):
	            if value in tmp_dict:
	                max_length = max(max_length, inx - tmp_start)
	                tmp_start = max(tmp_start, tmp_dict[value] + 1)

	            tmp_dict[value] = inx

	        return max(max_length, inx + 1 - tmp_start)
	```


## 2. 双指针
+ [15. 三数之和](https://leetcode-cn.com/problems/3sum/solution/3sumpai-xu-shuang-zhi-zhen-yi-dong-by-jyd/)
	+ 思路：排序+双指针

	+ 题解：

	```python
	class Solution:
	    def threeSum(self, nums):

	        if len(nums) < 3:
	            return []

	        result_list = []
	        k = 0

	        nums = sorted(nums)
	        print(nums)

	        for k in range(len(nums) - 2):
	            if nums[k] > 0:
	                break

	            if k >= 1 and nums[k] == nums[k-1]:
	                continue

	            left = k + 1
	            right = len(nums) - 1

	            while left < right:
	                s = nums[k] + nums[left] + nums[right]

	                if s > 0:
	                    right -= 1
	                    while left < right and nums[right] == nums[right+1]:
	                        right -= 1
	                elif s < 0:
	                    left += 1
	                    while left < right and nums[left] == nums[left-1]:
	                        left += 1
	                else:
	                    result_list.append([nums[k], nums[left], nums[right]])
	                    right -= 1
	                    left += 1
	                    while left < right and nums[right] == nums[right+1]:
	                        right -= 1
	                    while left < right and nums[left] == nums[left-1]:
	                        left += 1

	        return result_list
	```