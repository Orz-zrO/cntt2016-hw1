#ArcadeManao
作者：NiroBC

关联词：并查集 最小生成树
#题目简述
很久很久以前，有一个$$N*M$$的网格，其中有一些格子上是可以停留的，有一些是悬空的。

这是一个有重力存在的世界。

有一个可爱的小朋友，他现在在网格的底部（保证底部的每一个格子都是可以停留的），需要到达一个特定的可停留的格子。

现在有两种移动方式：左右移动和上下移动。

左右移动：左右紧挨的两个格子，如果都可以停留，就可以在这两个格子之间自由移动。

上下移动：同一条竖直线上的两个可停留的格子（可以不紧挨）可以互相移动，不过你需要拥有一
把长度至少为两个格子纵坐标之差的绝对值的梯子。

梯子可以重复使用，问从网格底部到达目标点，需要的梯子的最短长度。

$$1<=N,M<=50$$
#算法
任意两个可左右移动的点之间加入一条权值为$$0$$的边，任意两个可上下移动的点之间加入一条权值为最小梯子长度的边，将所有边从小到大加入，直到网格的底部上的某点和目标点连通，并查集维护。