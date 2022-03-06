# rec_blog

新的一年好好学习，准备run run run! 操蛋的经历！！！

## 汇总博客

+ 知乎 Microstrong [推荐系统在工业界的N+1条实战经验](https://zhuanlan.zhihu.com/p/336628289)
+ github deepctr [浅梦学习笔记 公众号文章汇总](https://github.com/shenweichen/AlgoNotes)

## 一. 召回篇

### 1. 理论
#### 1.1 FM
+ 知乎 张俊林 [推荐系统召回四模型之：全能的FM模型](https://zhuanlan.zhihu.com/p/58160982)
+ 知乎 石塔西 [FM：推荐算法中的瑞士军刀](https://zhuanlan.zhihu.com/p/343174108)
#### 1.2 FFM
+ 知乎 张俊林 [推荐系统召回四模型之二：沉重的FFM模型](https://zhuanlan.zhihu.com/p/59528983)
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
+ 知乎 石塔西 [刀功：谈推荐系统特征工程中的几个高级技巧](https://zhuanlan.zhihu.com/p/448680238)
	+ 1. 统计类：用户 -> (对) 物料 -> (在) 时间 -> (进行) 动作 -> (的) 统计对象 -> 统计方法
	+ 2. 排序特征：eg 小资文青喜欢的top10电影之一
	+ 3. 交叉特征：文中提到了匹配度。加减乘除应该都算特征交叉，例如DIN里的相减、相乘，见[DeepCTR](https://github.com/shenweichen/DeepCTR/blob/9f155590cc44c14821dcb691811656eb2ef2f49b/deepctr/layers/core.py#L92)；BERT里的三个向量相加，见[为什么 Bert 的三个 Embedding 可以进行相加？](https://www.zhihu.com/question/374835153/answer/1070264662)
	+ 4. id类特诊是一等公民，分桶（某du用到的特征全部进行分桶处理）
+ 知乎 砍手豪 [探讨特征工程的方法论](https://zhuanlan.zhihu.com/p/466685415)
+ 知乎 问题 [特征工程到底是什么？](https://www.zhihu.com/question/29316149/answer/2346832545)
+ CSDN 京城王多鱼 [商品推荐-画像和统计类特征工程](https://blog.csdn.net/wdh315172/article/details/105439491)
+ 美团技术团队 [7次KDD Cup&Kaggle冠军的经验分享：从多领域优化到AutoML框架](https://tech.meituan.com/2022/01/06/7-kdd-cup-kaggle-automl.html)


### 1. 先验知识
+ 知乎 石塔西 [先入为主：将先验知识注入推荐模型](https://zhuanlan.zhihu.com/p/442845759)

### 2. 蒸馏系列
+ 知乎 张俊林 [知识蒸馏在推荐系统的应用](https://zhuanlan.zhihu.com/p/143155437)
+ 公众号 Microstrong [深度学习中的知识蒸馏技术（上）](https://mp.weixin.qq.com/s/E7-MF18Y-UeKx694kGFHzA)
+ 公众号 Microstrong [深度学习中的知识蒸馏技术(下)-知识蒸馏与推荐系统](https://mp.weixin.qq.com/s/Noac4YLIimr1HM2fln2bjg)
+ 公众号 爱奇艺技术产品团队 [如何提升链路目标一致性？爱奇艺短视频推荐之粗排模型优化历程](https://mp.weixin.qq.com/s/LZlskUK4dmOd5fLTZIATnQ)，另外还包括:
	+ 特征挖掘；
	+ 粗排样本调整：原来是线上真实点展样本。调整为在召回池中随机负采样，精排topk结果作为正样本。

### 3. 对比学习
+ 知乎 石塔西 [少数派报告：谈推荐场景下的对比学习](https://zhuanlan.zhihu.com/p/435903339)
+ 知乎 张俊林 [对比学习（Contrastive Learning）:研究进展精要](https://zhuanlan.zhihu.com/p/367290573)
+ 知乎 张俊林 [对比学习视角:重新审视推荐系统的召回粗排模型](https://zhuanlan.zhihu.com/p/424198603)

### 4. 召回强负样本
+ 知乎 石塔西 [负样本为王：评Facebook的向量化召回算法](https://zhuanlan.zhihu.com/p/165064102)
+ 公众号 蘑菇先生 [KDD'21 | 揭秘Facebook升级版语义搜索技术](https://mp.weixin.qq.com/s/mkC8lSbBXWMUIXUg3KrAjQ)

### 5. 采样策略
+ 公众号 Microstrong [YouTube采样修正的双塔模型论文精读](https://mp.weixin.qq.com/s/us4qGD3LDgLmPy2m-qq-iw)

### 6. 冷启动
+ 知乎 石塔西 [初来乍到：帮助新用户冷启的算法技巧](https://zhuanlan.zhihu.com/p/458843906)

### 7. 多目标
+ 公众号 浅梦学习笔记 [多任务学习在推荐算法中的应用](https://mp.weixin.qq.com/s/4e7gwpP3XHBAMNX9M0nRgw)
+ 知乎 Recommender [推荐系统中的多任务学习与多目标排序工程实践（上）](https://zhuanlan.zhihu.com/p/422925553)
+ CSDN 文文学霸 [[腾讯]RecSys2020最佳长论文-多任务学习模型PLE](https://blog.csdn.net/abcdefg90876/article/details/108898482)
	+ 另外文中有 共享网络、Asymmetry Sharing、Customized Sharing、MMOE等网络结构的介绍
	+ 代码可参考：[deepctr_models_multitask_ple.py](https://github.com/shenweichen/DeepCTR/blob/master/deepctr/models/multitask/ple.py)

### 8. NLP方向
+ CSDN 废柴当自强 [一文读懂BERT(原理篇)](https://blog.csdn.net/jiaowoshouzi/article/details/89073944)
+ CSDN 京城王多鱼 [ERNIE模型系列]()