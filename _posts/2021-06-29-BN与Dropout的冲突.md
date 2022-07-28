# BN与Dropout的冲突

[大白话《Understanding the Disharmony between Dropout and Batch Normalization by Variance Shift》](https://zhuanlan.zhihu.com/p/33101420)

Dropout 与 BN 之间冲突的关键是网络状态切换过程中存在方差不一致行为。

📌 **方差偏移现象**
假设有神经响应 X，当网络从**训练转为测试**时，Dropout 可以通过其随机失活保留率（即 p）来缩放响应，并在学习中改变神经元的方差，而 BN 仍然维持Training时X的统计滑动方差。这种方差不匹配可能导致数值不稳定。


![Untitled](https://github.com/xucong1018/xucong1018.github.io/blob/master/img/BN与Dropout的冲突/Untitled.png?raw=true)

💡 **解决**

- BN后加Dropout
- 高斯Dropout，**核心是降低整体的方差偏移**
