# **TrafficCongestion**

作者：叶芃

关键词：二叉树 递推

# 题目简述

给定一颗高度为H的完全二叉树，要用尽量少的简单路径覆盖每个点恰好一次（路径可以为单个点），求最少的路径数$$mod \ 10^9+7$$。（$$H\le1000000$$）

# 算法一

考虑经过根的路径，设该路径的某端点为x，若x不为叶子节点，设x的某个儿子为y，将经过y的路径从y处断开，并将其中一条与x相连，这样操作不会使路径数增加。于是经过若干次调整，我们可以得到一条从一个叶子节点到另一个叶子节点的路径。

设该完全二叉树高度为H，我们会发现这条路径将整棵二叉树分成了若干棵高度$$\le H-2$$的二叉树，其中高度为$$i(i\in[0,H-2])$$的二叉树均有2棵。我们设高度为$$n$$的完全二叉树的最少路径数为$$f_n$$，可以得到递推式$$f_n=1+2\sum_{i=0}^{n-2}f_i$$，初值为$$f_0=1,f_1=1$$。

直接用该式递推的复杂度是$$O(H^2)$$的，无法通过1000000的数据。考虑优化：我们在上式中用$$n+1$$代替$$n$$，可以得到$$f_{n+1}=1+2\sum_{i=0}^{n-1}f_i$$。再减去上式并移项就可以得到$$f_{n+1}=2f_{n-1}+f_n$$，使用该式递推复杂度为$$O(H)$$，可以通过全部的测试数据。

事实上，对于更大的范围(例如$$10^9$$)，还可以利用上面的递推式构造矩阵，利用矩阵快速幂来求解，将时间复杂度降到$$O(log_2H)$$。