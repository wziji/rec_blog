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
                    max_length = max(max_length, inx - tmp_start)   # 记录最大值
                    tmp_start = max(tmp_start, tmp_dict[value] + 1) # 记录最大起始位置，与之前的无用的内容割裂开

                tmp_dict[value] = inx

            return max(max_length, inx + 1 - tmp_start)
    ```

+ [32. 最长有效括号](https://leetcode-cn.com/problems/longest-valid-parentheses/)
    + 思路：存储索引，"(" 时增加索引，")" 弹出索引
    + 题解：
    ```python
    class Solution:
        def longestValidParentheses(self, s: str) -> int:
            if not s:
                return 0

            max_length = 0
            tmp_list = [-1] # 存储索引

            for inx, value in enumerate(s):
                if value == "(":
                    tmp_list.append(inx) # 1. 索引进入
                else:
                    tmp_list.pop() # 2. 弹出索引
                    if tmp_list:
                        max_length = max(max_length, inx - tmp_list[-1])

                    if not tmp_list:
                        # 3. 持续为")"时，tmp_list将为空。此时增加inx当做第一个索引号，与之前的无用的内容割裂开
                        tmp_list.append(inx) 

            return max_length
    ```

+ [42. 接雨水](https://leetcode-cn.com/problems/trapping-rain-water/)
    + 思路：双指针，min(max(left), max(right))
        + 1. 维护 左侧最大值，右侧最大值，当做“桶壁”
        + 2. 选择两者的最小值，视为“能盛水的短板”
    + 题解：
    ```python
    class Solution:
        def trap(self, height: List[int]) -> int:
            if len(height) <= 2:
                return 0

            result = 0
            left = 0
            right = len(height) - 1

            left_max = height[0]
            right_max = height[-1]


            while left < right:
                min_value = min(left_max, right_max)
                if height[left] <= height[right]:
                    result += min_value - height[left]
                    left += 1
                    left_max = max(left_max, height[left])
                    
                elif height[left] > height[right]:
                    result += min_value - height[right]
                    right -= 1
                    right_max = max(right_max, height[right])
                    
            return result
    ```

+ [45. 跳跃游戏 II](https://leetcode-cn.com/problems/jump-game-ii/)
    + 思路：贪心法
        + 1. 每一次跳跃时更新能到达的最远距离；
        + 2. 当前索引与边界相等时，才会必须跳跃一次【跳跃点和维护的边界点（记录跳跃次数的点）并不一致，但是两者的总次数是相等的】
    + 题解：
    ```python
    class Solution:
        def jump(self, nums: List[int]) -> int:

            steps = 0
            max_distance = 0
            end_distance = 0

            for i in range(len(nums)-1):
                max_distance = max(max_distance, nums[i]+i)

                if i == end_distance:
                    end_distance = max_distance
                    steps += 1

            return steps
    ```

+ [53. 最大子数组和](https://leetcode-cn.com/problems/maximum-subarray/)
    + 思路：维护（1）当前最大值；（2）全局最大值
    + 题解：
    ```python
    class Solution:
        def maxSubArray(self, nums: List[int]) -> int:
            if not nums:
                return

            cur_max_value = nums[0]
            max_value = nums[0]

            for value in nums[1:]:
                # 当cur_max_value为正，选择cur_max_value+value结果
                # 当cur_max_value为负，断舍离，弃之。选择value结果
                cur_max_value = max(cur_max_value + value, value)
                max_value = max(max_value, cur_max_value)

            return max_value
    ```
+ [55. 跳跃游戏](https://leetcode-cn.com/problems/jump-game/)
    + 思路：判断“跳的最远位置”是否一直掉到“坑”里
    + 题解：
    ```python
    class Solution:
        def canJump(self, nums: List[int]) -> bool:
            if len(nums) == 1:
                return True

            max_length = 0

            for inx in range(len(nums)-1):
                max_length = max(max_length, inx + nums[inx])
                if nums[inx] == 0 and max_length == inx: # 跳的最远位置一直掉到“坑”里
                    return False
            return True
    ```

+ [62. 不同路径](https://leetcode-cn.com/problems/unique-paths/)
    + 思路：（1）第一行和第一列设置为`1`；（2）`dp[i][j]`从`dp[i-1][j]`或`dp[i][j-1]`来的
    + 题解：
    ```python
    class Solution:
        def uniquePaths(self, m: int, n: int) -> int:
            if not m or not n:
                return 0
            if m == 1 or n == 1:
                return 1

            result = [[1]*n] * m

            for i in range(1, m):
                for j in range(1, n):
                    result[i][j] = result[i-1][j] + result[i][j-1]

            return result[-1][-1]
    ```

+ [63. 不同路径 II](https://leetcode-cn.com/problems/unique-paths-ii/)
    + 思路：与62题类似，只是增加了障碍物，把障碍物置为`0`即可，代表此路不通
    + 题解：
    ```python
    import copy
    class Solution:
        def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
            m = len(obstacleGrid)
            n = len(obstacleGrid[0])

            dp = copy.deepcopy(obstacleGrid)
            for index, ch in enumerate(dp[0]):
                if ch == 0:
                    dp[0][index] = 1
                else:
                    for i in range(index, len(dp[0])):
                        dp[0][i] = 0
                    break

            for index, ch in enumerate(obstacleGrid):
                if ch[0] == 0:
                    dp[index][0] = 1
                else:
                    for i in range(index, len(obstacleGrid)):
                        dp[i][0] = 0
                    break

            for i in range(1, m):
                for j in range(1, n):
                    if dp[i][j] == 1:
                        dp[i][j] = 0
                    else:
                        dp[i][j] = dp[i-1][j] + dp[i][j-1]

            return dp[-1][-1]
    ```

+ [64. 最小路径和](https://leetcode-cn.com/problems/minimum-path-sum/)
    + 思路：与`62`和`63`一样，先处理第一行和第一列
    + 题解：
    ```python
    class Solution:
        def minPathSum(self, grid: List[List[int]]) -> int:
            row = len(grid)
            col = len(grid[0])

            # 处理第一行，依次相加
            for i in range(1, col):
                grid[0][i] += grid[0][i-1]

            for j in range(1, row):
                grid[j][0] += grid[j-1][0]

            for i in range(1, row):
                for j in range(1, col):
                    grid[i][j] += min(grid[i-1][j], grid[i][j-1])

            return grid[-1][-1]
    ```

+ [72. 编辑距离](https://leetcode-cn.com/problems/edit-distance/)
    + 思路：与`62`和`63`和`64`一样，[先处理第一行和第一列，再处理内部数据](https://leetcode-cn.com/problems/edit-distance/solution/bian-ji-ju-chi-tu-jie-dp-zui-qing-xi-yi-abfgl/)
    + 题解：
    ```python
    class Solution:
        def minDistance(self, word1: str, word2: str) -> int:

            m = len(word1) # 5
            n = len(word2) # 3
            dp = [[0] * (n+1) for _ in range(m+1)] # 保持这种写法

            # 处理第一行，代表word1为空
            for i in range(1, m+1):
                dp[i][0] = dp[i-1][0] + 1

            # 处理第一列，代表word2为空
            for j in range(1, n+1):
                dp[0][j] = dp[0][j-1] + 1

            for i in range(1, m+1):
                for j in range(1, n+1):
                    if word1[i-1] == word2[j-1]:
                        dp[i][j] = dp[i-1][j-1]
                    else:
                        dp[i][j] = min(
                            dp[i][j-1], 
                            dp[i-1][j],
                            dp[i-1][j-1]
                        ) + 1

            return dp[-1][-1]
    ```


## 2. 左右双指针
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

            for k in range(len(nums) - 2):
                if nums[k] > 0: # 三个元素全部大于0
                    break

                if k >= 1 and nums[k] == nums[k-1]: # 跳过重复数据
                    continue

                left = k + 1
                right = len(nums) - 1

                while left < right:
                    s = nums[k] + nums[left] + nums[right]

                    if s > 0:
                        right -= 1
                        while left < right and nums[right] == nums[right+1]:# 跳过重复数据
                            right -= 1
                    elif s < 0:
                        left += 1
                        while left < right and nums[left] == nums[left-1]:# 跳过重复数据
                            left += 1
                    else:
                        result_list.append([nums[k], nums[left], nums[right]])
                        right -= 1
                        left += 1
                        while left < right and nums[right] == nums[right+1]:# 跳过重复数据
                            right -= 1
                        while left < right and nums[left] == nums[left-1]:# 跳过重复数据
                            left += 1

            return result_list
    ```

+ [16. 最接近的三数之和](https://leetcode-cn.com/problems/3sum-closest/)
    + 思路：（1）排序+双指针；（2）记录 {"3数和与target的差":"3数和"}
    + 题解：
    ```python
    class Solution:
        def threeSumClosest(self, nums, target):

            tmp_dict = {}

            if not nums:
                return 0

            nums = sorted(nums)

            for k in range(len(nums) - 2):
                if k >= 1 and nums[k] == nums[k-1]:
                    continue

                left = k + 1
                right = len(nums) - 1

                while left < right:
                    s = nums[k] + nums[left] + nums[right]
                    tmp_dict[abs(s - target)] = s

                    if s > target:
                        right -= 1
                        while left < right and nums[right] == nums[right+1]:
                            right -= 1
                    elif s < target:
                        left += 1
                        while left < right and nums[left] == nums[left-1]:
                            left += 1
                    else:
                        right -= 1
                        left += 1
                        while left < right and nums[right] == nums[right+1]:
                            right -= 1
                        while left < right and nums[left] == nums[left-1]:
                            left += 1

            return sorted(tmp_dict.items(), key=lambda x: x[0], reverse=False)[0][1]
    ```

+ [11. 盛最多水的容器](https://leetcode-cn.com/problems/container-with-most-water/)
    + 思路：左右双指针 + 动态规划
    + 题解：
    ```python
    class Solution:
        def maxArea(self, height: List[int]) -> int:
            if not height:
                return 0

            left = 0
            right = len(height) - 1
            max_value = 0

            while left <= right:
                tmp_value = (right - left) * min([height[left], height[right]])

                if height[left] <= height[right]:
                    left += 1
                else:
                    right -= 1

                max_value = max(max_value, tmp_value)
            return max_value
    ```


## 3. 递归
+ [22. 括号生成](https://leetcode-cn.com/problems/generate-parentheses/)
    + 思路：如下套路
    ```python
    待补充。。。
    ```
    + 题解：
    ```python
    class Solution:
        def generateParenthesis(self, n):

            res = []

            def df(tmp_str, left, right):
                if left == right == n:
                    res.append(tmp_str)
                    return

                if right > left:
                    return
                if left < n:
                    df(tmp_str+"(", left+1, right)
                if right < n:
                    df(tmp_str+")", left, right+1)

            df("", 0, 0)

            return res
    ```

## 4. 滑动字符串
+ [30. 串联所有单词的子串](https://leetcode-cn.com/problems/substring-with-concatenation-of-all-words/)
    + 思路：滑动input_str，判断连续子串是否在候选集合中
    + 题解：
    ```python
    class Solution:
        def findSubstring(self, s, words):
            import copy
            words_length = len(words[0]) * len(words)
            word_len = len(words[0])

            if words_length > len(s):
                return []

            result = []
            for inx in range(len(s) - words_length + 1):
                tmp_words = copy.deepcopy(words)
                tmp_inx = inx

                while tmp_words:
                    if tmp_inx > len(s):
                        break

                    tmp_str = s[tmp_inx : tmp_inx + word_len]
                    if tmp_str in tmp_words:
                        tmp_inx += word_len
                        tmp_words.remove(tmp_str) # 移除候选集合中的“已经拼上的子串”
                    else:
                        break

                    if not tmp_words: # 当候选集中没有字符串时，代表拼接完成
                        result.append(inx)

            return result
    ```

## 5. 中心扩散法
+ [5. 最长回文子串](https://leetcode-cn.com/problems/longest-palindromic-substring/solution/zhong-xin-kuo-san-dong-tai-gui-hua-by-liweiwei1419/)
    + 思路：以1个节点、2个节点进行中心扩散
    + 题解：
    ```python
    class Solution:
        def longestPalindrome(self, s: str) -> str:

            if not s:
                return 0

            if len(s) == 1:
                return s

            max_str = s[0]
            left_min = 0
            right_max = len(s) - 1

            for inx, value in enumerate(s):
                tmp_max_str = ""

                # 以1个为中心点
                left = inx - 1
                right = inx + 1
                while left >= left_min and right <= right_max and s[left] == s[right]:
                    tmp_max_str = s[left:right+1]
                    left -= 1
                    right += 1

                if len(tmp_max_str) >= len(max_str):
                    max_str = tmp_max_str

                # 这个条件可以节省时间
                if len(max_str) == len(s):
                    return max_str


                # 以2个为中心点
                left = inx - 1
                right = inx + 1            
                if right <= right_max and s[inx] == s[right]:
                    if len(tmp_max_str) <= 2:
                        tmp_max_str = s[inx: right+1]

                    right = right + 1
                    while left >= left_min and right <= right_max and s[left] == s[right]:
                        tmp_max_str = s[left:right+1]
                        left -= 1
                        right += 1

                if len(tmp_max_str) >= len(max_str):
                    max_str = tmp_max_str

                # 这个条件可以节省时间
                if len(max_str) == len(s):
                    return max_str

            return max_str
    ```

## 6. 单调栈
+ [84. 柱状图中最大的矩形](https://leetcode-cn.com/problems/largest-rectangle-in-histogram/)
    + 思路：单调递增栈，`左右哨兵索引差 * 栈顶值`
    + 题解：
    ```python
    class Solution:
        def largestRectangleArea(self, heights: List[int]) -> int:
            if not heights:
                return 0
            if len(heights) == 1:
                return heights[0]

            heights = [-1] + heights + [-1]  # 增加[-1]为了最后弹出所有元素
            inx_list = [0]
            max_value = 0

            for inx in range(1, len(heights)):
                value = heights[inx] # 当前值
                if value < heights[inx_list[-1]]: # `当前值 < 栈顶值`，就弹出栈顶值，维护单调递增栈
                    while inx_list and value < heights[inx_list[-1]]:
                        height = heights[inx_list.pop()] # 弹出`栈顶元素`
                        max_value = max(max_value, height * (inx - inx_list[-1] - 1)) # `栈顶元素` * `左右哨兵的索引差`
                inx_list.append(inx)
        return max_value
    ```