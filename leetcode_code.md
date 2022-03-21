# LeetCode代码

## 动态规划

+ [3. 无重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)

	+ 思路：（1）标记重复元素位置的最大index；（2）记录最大长度

	+ 题解：
	```
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