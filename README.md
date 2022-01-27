# rec_blog

新的一年好好学习，go go go!

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
```
mermaid
graph LR
    start[开始] --> input[输入A,B,C]
    input --> conditionA{A是否大于B}
    conditionA -- YES --> conditionC{A是否大于C}
    conditionA -- NO --> conditionB{B是否大于C}
    conditionC -- YES --> printA[输出A]
    conditionC -- NO --> printC[输出C]
    conditionB -- YES --> printB[输出B]
    conditionB -- NO --> printC[输出C]
    printA --> stop[结束]
    printC --> stop
    printB --> stop

```
### 1. 先验知识
+ 知乎石塔西 [先入为主：将先验知识注入推荐模型](https://zhuanlan.zhihu.com/p/442845759)

### 2. 蒸馏系列
+ 知乎张俊林 [知识蒸馏在推荐系统的应用](https://zhuanlan.zhihu.com/p/143155437)
+ 公众后Microstrong [深度学习中的知识蒸馏技术（上）](https://mp.weixin.qq.com/s/E7-MF18Y-UeKx694kGFHzA)
+ 公众后Microstrong [深度学习中的知识蒸馏技术(下)-知识蒸馏与推荐系统](https://mp.weixin.qq.com/s/Noac4YLIimr1HM2fln2bjg)

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
