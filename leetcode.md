# LeetCode，刷题跑路

## 1. 动态规划
+ [3. 无重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)
    + 思路：（1）标记重复元素位置的最大index；（2）记录最大长度
+ [32. 最长有效括号](https://leetcode-cn.com/problems/longest-valid-parentheses/)
    + 思路：存储索引，"(" 时增加索引，")" 弹出索引
+ [42. 接雨水](https://leetcode-cn.com/problems/trapping-rain-water/)
    + 思路：双指针，min(max(left), max(right))
        + 1. 维护 左侧最大值，右侧最大值，当做“桶壁”
        + 2. 选择两者的最小值，视为“能盛水的短板”
+ [45. 跳跃游戏 II](https://leetcode-cn.com/problems/jump-game-ii/)
    + 思路：贪心法
        + 1. 每一次跳跃时更新能到达的最远距离；
        + 2. 当前索引与边界相等时，才会必须跳跃一次【跳跃点和维护的边界点（记录跳跃次数的点）并不一致，但是两者的总次数是相等的】
+ [53. 最大子数组和](https://leetcode-cn.com/problems/maximum-subarray/)
    + 思路：维护（1）当前最大值；（2）全局最大值
+ [55. 跳跃游戏](https://leetcode-cn.com/problems/jump-game/)
    + 思路：判断“跳的最远位置”是否一直掉到“坑”里
+ [62. 不同路径](https://leetcode-cn.com/problems/unique-paths/)
    + 思路：（1）第一行和第一列设置为`1`；（2）`dp[i][j]`从`dp[i-1][j]`或`dp[i][j-1]`来的
+ [63. 不同路径 II](https://leetcode-cn.com/problems/unique-paths-ii/)
    + 思路：与62题类似，只是增加了障碍物，把障碍物置为`0`即可，代表此路不通
+ [64. 最小路径和](https://leetcode-cn.com/problems/minimum-path-sum/)
    + 思路：与`62`和`63`一样，先处理第一行和第一列
+ [72. 编辑距离](https://leetcode-cn.com/problems/edit-distance/)
    + 思路：与`62`和`63`和`64`一样，[先处理第一行和第一列，再处理内部数据](https://leetcode-cn.com/problems/edit-distance/solution/bian-ji-ju-chi-tu-jie-dp-zui-qing-xi-yi-abfgl/)
+ [85. 最大矩形](https://leetcode-cn.com/problems/maximal-rectangle/)
    + 思路：逐行处理，利用单调栈，参考 [84. 柱状图中最大的矩形](https://leetcode-cn.com/problems/largest-rectangle-in-histogram/)
    + 题解：[Python3 前缀和+单调栈计算最大矩形](https://leetcode-cn.com/problems/maximal-rectangle/solution/python3-qian-zhui-he-dan-diao-zhan-ji-su-vkpp/)

## 2. 双指针
+ [15. 三数之和](https://leetcode-cn.com/problems/3sum/solution/3sumpai-xu-shuang-zhi-zhen-yi-dong-by-jyd/)
    + 思路：排序+双指针
+ [16. 最接近的三数之和](https://leetcode-cn.com/problems/3sum-closest/)
    + 思路：（1）排序+双指针；（2）记录 {"3数和与target的差":"3数和"}
+ [11. 盛最多水的容器](https://leetcode-cn.com/problems/container-with-most-water/)
    + 思路：左右双指针 + 动态规划

## 3. 递归
+ [22. 括号生成](https://leetcode-cn.com/problems/generate-parentheses/)

## 4. 滑动字符串
+ [30. 串联所有单词的子串](https://leetcode-cn.com/problems/substring-with-concatenation-of-all-words/)
    + 思路：滑动input_str，判断连续子串是否在候选集合中

## 5. 中心扩散法
+ [5. 最长回文子串](https://leetcode-cn.com/problems/longest-palindromic-substring/solution/zhong-xin-kuo-san-dong-tai-gui-hua-by-liweiwei1419/
)
    + 思路：以1个节点、2个节点进行中心扩散

## 6. 单调栈
+ [84. 柱状图中最大的矩形](https://leetcode-cn.com/problems/largest-rectangle-in-histogram/)
    + 思路：单调递增栈，`左右哨兵索引差 * 栈顶值`