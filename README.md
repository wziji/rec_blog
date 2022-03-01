# rec_blog

新的一年好好学习，准备run run run! 操蛋的经历！！！

## 汇总博客

+ 知乎Microstrong [推荐系统在工业界的N+1条实战经验](https://zhuanlan.zhihu.com/p/336628289)
+ github_deepctr [浅梦学习笔记 公众号文章汇总](https://github.com/shenweichen/AlgoNotes)

## 一. 召回篇

### 1. 理论
#### 1.1 FM
+ 知乎张俊林 [推荐系统召回四模型之：全能的FM模型](https://zhuanlan.zhihu.com/p/58160982)
+ 知乎石塔西 [FM：推荐算法中的瑞士军刀](https://zhuanlan.zhihu.com/p/343174108)
#### 1.2 FFM
+ 知乎张俊林 [推荐系统召回四模型之二：沉重的FFM模型](https://zhuanlan.zhihu.com/p/59528983)
+ 美团技术团队 [深入FFM原理与实践](https://tech.meituan.com/2016/03/03/deep-understanding-of-ffm-principles-and-practices.html)

#### 1.3 双塔模型


### 2. 实践

## 二. 粗排篇

### 1. 理论
### 2. 实践

## 三. 排序篇

### 1. 理论
### 2. 实践

## 四. 基础知识篇

### 0. 特征工程
+ 知乎石塔西 [刀功：谈推荐系统特征工程中的几个高级技巧](https://zhuanlan.zhihu.com/p/448680238)
```python
1. 统计论：用户 ->(对) `物料` ->(在) 时间 ->(进行) 动作 ->(的) 统计对象 -> `统计方法`
2. 排序特征：eg 小资文青喜欢的top10电影之一
3. 交叉特征
4. id类特诊是一等公民，分桶（baidu用到的特征全分桶）
```

+ CSDN京城王多鱼 [商品推荐-画像和统计类特征工程](https://blog.csdn.net/wdh315172/article/details/105439491)


### 1. 先验知识
+ 知乎石塔西 [先入为主：将先验知识注入推荐模型](https://zhuanlan.zhihu.com/p/442845759)

### 2. 蒸馏系列
+ 知乎张俊林 [知识蒸馏在推荐系统的应用](https://zhuanlan.zhihu.com/p/143155437)
+ 公众号Microstrong [深度学习中的知识蒸馏技术（上）](https://mp.weixin.qq.com/s/E7-MF18Y-UeKx694kGFHzA)
+ 公众号Microstrong [深度学习中的知识蒸馏技术(下)-知识蒸馏与推荐系统](https://mp.weixin.qq.com/s/Noac4YLIimr1HM2fln2bjg)
+ 公众号爱奇艺技术产品团队 [如何提升链路目标一致性？爱奇艺短视频推荐之粗排模型优化历程](https://mp.weixin.qq.com/s/LZlskUK4dmOd5fLTZIATnQ)，另外还包括特征挖掘、粗排样本调整：原来是线上真实点展，调整为召回随机负采样，精排topk正样本

### 3. 对比学习
+ 知乎石塔西 [少数派报告：谈推荐场景下的对比学习](https://zhuanlan.zhihu.com/p/435903339)
+ 知乎张俊林 [对比学习（Contrastive Learning）:研究进展精要](https://zhuanlan.zhihu.com/p/367290573)
+ 知乎张俊林 [对比学习视角:重新审视推荐系统的召回粗排模型](https://zhuanlan.zhihu.com/p/424198603)

### 4. 召回强负样本
+ 知乎石塔西 [负样本为王：评Facebook的向量化召回算法](https://zhuanlan.zhihu.com/p/165064102)
+ 公众号蘑菇先生 [KDD'21 | 揭秘Facebook升级版语义搜索技术](https://mp.weixin.qq.com/s/mkC8lSbBXWMUIXUg3KrAjQ)

### 5. 采样策略
+ 公众后Microstrong [YouTube采样修正的双塔模型论文精读](https://mp.weixin.qq.com/s/us4qGD3LDgLmPy2m-qq-iw)

### 6. 冷启动
+ 知乎石塔西 [初来乍到：帮助新用户冷启的算法技巧](https://zhuanlan.zhihu.com/p/458843906)
