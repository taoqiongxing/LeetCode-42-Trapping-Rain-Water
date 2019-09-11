# LeetCode-42-Trapping-Rain-Water
接雨水——给定 n 个非负整数表示每个宽度为 1 的柱子的高度图，计算按此排列的柱子，下雨之后能接多少雨水。

题目链接：https://leetcode-cn.com/problems/trapping-rain-water/submissions/

·碰到比当前点大的或者相等的，才计算积到的雨水

·正反方向

    class Solution:
      def trap(self, height: List[int]) -> int:
          res=0
          n=len(height)
          begin=0
          end=n-1
          for i in range(1,n):
              if height[i]>=height[begin] and i-begin>1:
                  res+=(i-begin-1)*height[begin]-sum(height[begin+1:i])
                  begin=i
              elif height[i]>=height[begin]:
                  begin=i
          for j in range(n-2,begin-1,-1):
              if height[j]>=height[end] and end-j>1:
                  res+=(end-j-1)*height[end]-sum(height[j+1:end])
                  end=j
              elif height[j]>=height[end]:
                  end=j
          return res

                
                
