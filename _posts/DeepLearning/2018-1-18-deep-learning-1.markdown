---
layout: post
title:  "Deep Learning 1!"
date:   2018-01-18 10:00:00
categories: DeepLearning
comments: true
description: Deep Learning 1!
---


* content
{:toc}

## 前奏

于 2018年1月18日 开始探索深度学习，这一系列将是在《深度学习》探索途中的 ___私密___ 笔记记录

## 定义

层次 化 的 概念 让 计算机 构建 较 简单 的 概念 来 学习 复杂 概念。 如果 绘制 出 表示 这些 概念 如何 建立 在 彼此 之上 的 一幅 图， 我们将 得到 一张‘ 深’（ 层次 很多） 的 图。 由此， 我们 称 这种 方法 为 AI 深度 学习（ deep learning）

AI 系统 需要 具备 自己 获取 知识 的 能力， 即从 原始 数据 中 提取 模式 的 能力。 这种 能力 称为 机器 学习（ machine learning）

深度 学习（ deep learning） 通过 其他 较 简单 的 表示 来 表达 复杂 表示， 解决 了 表示 学习 中的 核心 问题

深度 学习 是 通向 人工智能 的 途径 之一

深度 学习 是一 种 特定 类型 的 机器 学习， 具有 强大 的 能力 和 灵活性， 它将 大千世界 表示 为 嵌套 的 层次 概念 体系（ 由 较 简单 概念 间的 联系 定义 复杂 概念、 从 一般 抽象 概括 到 高级 抽象 表示）

`AI` 包含 `机器学习`

`机器学习` 包含 `表示学习`

`表示学习` 包含 `深度学习`


## 数学符号

| 数和数组 | 描述 |
| :--------- | :--------- |
| _a_ | 标量（整数或实数）|
| ___a___ | 向量 |
| ___A___ | 矩阵 |
| __A__ | 张量 |
| ___I___<sub>n</sub> | n行n列的单位矩阵 |
| ___I___ | 维度蕴含于上下文的矩阵 |
| e<sup>(i)</sup> | 标准基向量 `[0,...,0,1,0,...,0]` ，其中索引 i 处值为 1 |
| diag(a) | 对角方阵，其中对角元素由 a 指定 |
| a | 标量随机变量 |
| __a__ | 向量随机变量 |
| __A__ | 矩阵随机变量 |

| 集合和图 | 描述 |
| :--------- | :--------- |
| $$\Bbb {A}$$ | 集合 |
| $$\Bbb {R}$$ | 实数集 |
| {0,1} | 包含0和1的集合 |
| {0,1,...,n} | 包含0和n以及之间的所有整数的集合 |
| `[a,b]` | 包含 a 和 b 的实数区间 |
| `(a,b]` | 不包含 a 但包含 b 的实数区间 |
| $$\Bbb {A}$$ \ $$\Bbb {B}$$ | 差集，即元素包含于 $$\Bbb {A}$$ 但不包含于 $$\Bbb {B}$$ |
| &sigmaf; | 图 |
| _Pa<sub>&sigmaf;</sub>_(X<sub>i</sub>) | 图 &sigmaf; 中 x<sub>i</sub> 的父节点 |

| 索引 | 描述 |
| :--------- | :--------- |
| a<sub>i</sub> | 向量 ___a___ 的第 i 个元素, 其中索引从 1 开始 |
| a<sub>-i</sub> | 除了第 i 个元素，___a___ 的所有元素 |
| A<sub>i,j</sub> | 矩阵 ___A___ 的 i,j 元素 |
| ___A___<sub>i,:</sub> | 矩阵 ___A___ 的第 i 行 |
| ___A___<sub>:,i</sub> | 矩阵 ___A___ 的第 i 列 |
| __A__<sub>i,j,k</sub> | 三维张量 __A__ 的 (i,j,k) 元素 |
| __A__<sub>:,:,i</sub> | 三维张量的 二维切片 |
| a<sub>i</sub> | 随机向量 __a__ 的第 i 个元素 |

| 线性代数中的操作 | 描述 |
| :--------- | :--------- |
| ___A___<sup>T</sup> | 矩阵 ___A___ 的转置 |
| ___A___<sup>+</sup> | 矩阵 ___A___ 的 Moore-Penose 伪逆 |
| <font size="5">A⊙B</font> | ___A___ 和 ___B___ 的逐元素乘积(Hadamard乘积) |
| det(___A___) | ___A___ 的行列式 |

| 微积分 | 描述 |
| :--------- | :--------- |
| $$\frac{dy}{dx}$$ | y 关于 x 的导数 |
| $$\frac{∂y}{∂x}$$ | y 关于 x 的偏导 |
| &nabla;<sub>_x_</sub>y | y 关于 _x_ 的梯度 |
| &nabla;<sub>___X___</sub>y | y 关于 ___X___ 的矩阵导数 |
| &nabla;<sub>__X__</sub>y | y 关于 __X__ 求导后的张量 |
| $$\frac{∂ƒ}{∂x}$$ | &fnof;: $$\Bbb {R}$$<sup>n</sup> &rarr; $$\Bbb {R}$$<sup>m</sup> 的Jacobian矩阵 ___J___ &isin; $$\Bbb {R}$$<sup>m x n</sup> |
| &part;<sub>x</sub><sup>2</sup>&fnof;(__x__) or H(&fnof;)(__x__) | f 在 __x__ 处的 Hessian 矩阵 |
| &int;f(__x__) dx | __x__ 整个域上的定积分 |
| &int;<sub>$$\Bbb {S}$$</sub>f(__x__) dx | 集合 $$\Bbb {S}$$ 上关于 x 的定积分 |

| 概率和信息论 | 描述 |
| :--------- | :--------- |
| a&perp;b | a和b相互独立的随机变量 |
| a&perp;b&#124;c | 给定 c 后条件独立 |
| P(a) | 离散变量上的概率分布 |
| p(a) | 连续变量上(或变量类型未指定时)的概率分布 |
| a~P | 具有分布 P 的随机变量a |
| $$\Bbb {E}$$<sub>x~P</sub>\[&fnof;(x)\] or $$\Bbb {E}$$&fnof;(x) | f(___x___) 关于 P(x)的期望 |
| Var(f(___x___)) | f(___x___) 在分布 P(x) 下的方差 |
| Cov(f(___x___), g(x)) | f(___x___) 和 g(x) 在分布 P(x) 的协方差 |
| H(x) | 随机变量的x的香浓熵 |
| D<sub>KL</sub>(P&#124;&#124;Q) | P 和 Q 的 KL 散度 |
| ___$$\mathcal {N}$$(x; &mu;, &sum; )___ | 均值为 &mu;, 协方差为 &sum;, x 上的高斯分布 |

| 函数 | 描述 |
| :--------- | :--------- |
| &fnof; : $$\Bbb {A} $$ &rarr; $$\Bbb {B} $$ | 定义域为 $$\Bbb {A} $$，值域为 $$\Bbb {B} $$ 的函数 f |
| f&ordm;g | f 和 g 的组合 |
| f(___x;&theta;___) | 由 &theta; 参数变化，关于 x 的函数（有时为了简化而忽略了 &theta; 记为 f(___x___)） |
| log x | x 的自然对数　|
| &sigma;(x) | Logistic sigmoid, $$\frac{1}{1 + exp(-x)}$$ |
| &zeta;(x) | Softplus, log(1+exp(x)) |
| &#124;&#124;___x___&#124;&#124;<sub>p</sub> | ___x___ 的 L<sup>p</sup> 范数 |
| &#124;&#124;___x___&#124;&#124; | ___x___ 的 L<sup>2</sup> 范数 |
| x<sup>+</sup> | x 的正数部分,即 max(0, x) |
| __1__<sub>condition</sub> | 如果条件为真则为1，否则为0 |


| 数据集和分布 | 描述 |
| :--------- | :--------- |
| ___Pdata___ | 数据生成分布 |
| $$\widehat {P}$$<sub>train</sub> | 由训练集定义的分布 |
| $$\Bbb {X} $$ | 训练样本的集合 |
| __x__<sup>(i)</sup> | 数据集的第 i 个样本（输入） |
| y<sup>(i)</sup> 或 __y__<sup>(i)</sup> | 监督学习中与 __x__<sup>(i)</sup> 关联的目标 |
| ___X___ | m x n 矩阵， 其中 ___X___<sub>i,:</sub> 为输入样本 ___x___<sup>(i)</sup> |




















