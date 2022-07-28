# BN与Dropout的冲突

[大白话《Understanding the Disharmony between Dropout and Batch Normalization by Variance Shift》](https://zhuanlan.zhihu.com/p/33101420)

Dropout 与 BN 之间冲突的关键是网络状态切换过程中存在方差不一致行为。

<aside>
📌 **方差偏移现象**
假设有神经响应 X，当网络从**训练转为测试**时，Dropout 可以通过其随机失活保留率（即 p）来缩放响应，并在学习中改变神经元的方差，而 BN 仍然维持Training时X的统计滑动方差。这种方差不匹配可能导致数值不稳定。

</aside>

![Untitled](BN%E4%B8%8EDropout%E7%9A%84%E5%86%B2%E7%AA%81%20375fc592a8f14536be9108c66b4ede5c/Untitled.png)

<aside>
💡 **解决**

- BN后加Dropout
- [高斯Dropout](Dropout%209155fb8bb1fd4891b55308fcaaeca223.md)，**核心是降低整体的方差偏移**
</aside>