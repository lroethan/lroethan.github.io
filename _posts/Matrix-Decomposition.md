---
title: '矩阵分解'
date: 2023-03-02
permalink: /posts/Matrix-Decomposition
tags:
  - cool posts
  - category1
  - category2
---

# 矩阵分解

[TOC]

### 10 - LU 分解

【例1】求矩阵 $\boldsymbol{A}=\left[\begin{array}{lll}2 & 1 & 1 \\ 1 & 2 & 1 \\ 1 & 1 & 0\end{array}\right]$ 的 $LU$ 分解。

解：
$$
\left[\begin{array}{lll}
2 & 1 & 1 \\
1 & 2 & 1 \\
1 & 1 & 0
\end{array}\right] \underset{R_{3}-\left(\frac{1}{2}\right) R_{1}}{\stackrel{R_{2}-\left(\frac{1}{2}\right) R_{1}}{\longrightarrow} }\left[\begin{array}{ccc}
2 & 1 & 1 \\
0 & \frac{3}{2} & \frac{1}{2} \\
0 & \frac{1}{2} & -\frac{1}{2}
\end{array}\right] \stackrel{R_{3}-\left(\frac{1}{3}\right) R_{2}}{\longrightarrow}\left[\begin{array}{ccc}
2 & 1 & 1 \\
0 & \frac{3}{2} & \frac{1}{2} \\
0 & 0 & -\frac{2}{3}
\end{array}\right] = \boldsymbol{U}
$$

$$
\boldsymbol{L_1}=\left[\begin{array}{ccc}
1 & 0 & 0 \\
-\frac{1}{2} & 1 & 0 \\
-\frac{1}{2} & 0 & 1
\end{array}\right]
$$

$$
\boldsymbol{L_2}=\left[\begin{array}{ccc}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & -\frac{1}{3} & 1
\end{array}\right]
$$

$$
\boldsymbol{L}=\boldsymbol{L_{1}^{-1} L_{2}^{-1}}=\left[\begin{array}{ccc}
1 & 0 & 0 \\
\frac{1}{2} & 1 & 0 \\
\frac{1}{2} & \frac{1}{3} & 1
\end{array}\right]
$$

综上所述：

$$
\boldsymbol{A}=\left[\begin{array}{lll}
2 & 1 & 1 \\
1 & 2 & 1 \\
1 & 1 & 0
\end{array}\right]=\left[\begin{array}{ccc}
1 & 0 & 0 \\
\frac{1}{2} & 1 & 0 \\
\frac{1}{2} & \frac{1}{3} & 1
\end{array}\right]\left[\begin{array}{ccc}
2 & 1 & 1 \\
0 & \frac{3}{2} & \frac{1}{2} \\
0 & 0 & -\frac{2}{3}
\end{array}\right]=\boldsymbol{L} \boldsymbol{U}
$$







【例2】判定矩阵 $\boldsymbol{C}=\left[\begin{array}{ccc}3 & 2 & -1 \\ -1 & 0 & 0 \\ -1 & 3 & 0\end{array}\right]$ 和 $\boldsymbol{B}=\left[\begin{array}{ccc}0 & 2 & -1 \\ -1 & 4 & -1 \\ 1 & 3 & -5\end{array}\right]$ 能否进行 LU 分解，分解之否则说明理由

解： 

$\boldsymbol{B}$  的一阶顺序主子式为 $0$，所以不能够进行 LU 分解。

$\boldsymbol{C}$  可以进行 LU 分解，分解之：
$$
\left[\begin{array}{ccc}
3 & 2 & -1 \\
-1 & 0 & 0 \\
-1 & 3 & 0
\end{array}\right] \underset{R_{3}+\left(\frac{1}{3}\right)R_{1}}{\stackrel{R_{2}+\left[\frac{1}{3}\right)R_{1}}{\longrightarrow} }\left[\begin{array}{ccc}
3 & 2 & -1 \\
0 & \frac{2}{3} & -\frac{1}{3} \\
0 & \frac{11}{3} & -\frac{1}{3}
\end{array}\right] \stackrel{R_{3}-\left(\frac{11}{2}\right) R_{2}}{\longrightarrow}\left[\begin{array}{ccc}
3 & 2 & -1 \\
0 & \frac{2}{3} & -\frac{1}{3} \\
0 & 0 & \frac{3}{2}
\end{array}\right] = \boldsymbol{U}
$$

$$
\boldsymbol{L_1}=\left[\begin{array}{ccc}
1 & 0 & 0 \\
\frac{1}{3} & 1 & 0 \\
\frac{1}{3} & 0 & 1
\end{array}\right] 
$$

$$
\boldsymbol{L_2}=\left[\begin{array}{ccc}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & -\frac{11}{2} & 1
\end{array}\right]
$$

$$
\boldsymbol{L}=\boldsymbol{L_{1}^{-1} L_{2}^{-1}}=\left[\begin{array}{ccc}
1 & 0 & 0 \\
-\frac{1}{3} & 1 & 0 \\
-\frac{1}{3} & \frac{11}{2} & 1
\end{array}\right]
$$

即
$$
\boldsymbol{C}=\left[\begin{array}{ccc}
1 & 0 & 0 \\
-\frac{1}{3} & 1 & 0 \\
-\frac{1}{3} & \frac{11}{2} & 1
\end{array}\right]\left[\begin{array}{ccc}
3 & 2 & -1 \\
0 & \frac{2}{3} & -\frac{1}{3} \\
0 & 0 & \frac{3}{2}
\end{array}\right]=\boldsymbol{L} \boldsymbol{U}
$$





### 11 - QR 分解



QR 分解又称正交三角分解，可以通过以下方法实现：

- Gram-Schmidt 正交化
- Householder 变换
-  Givens 变换

QR 分解经常用来解线性最小二乘法问题。QR 分解也是特定特征值算法即 QR 算法的基础。







【例1】利用 QR 分解求解下述线性方程组的解（最终结果可只需写出具体矩阵与向量的乘积形式即可）
$$
\left[\begin{array}{ccc}
1 & 2 & 2 \\
2 & 1 & 2 \\
1 & 2 & 1
\end{array}\right]\left[\begin{array}{c}
x_1 \\
x_2 \\
x_3
\end{array}\right]=\left[\begin{array}{c}
1 \\
2 \\
3
\end{array}\right]
$$
解： 本题使用 Gram-Schmidt 正交化方法解答

1. 提取列向量

$$
\alpha_1 = \left[\begin{array}{c}
1 \\
2 \\
1
\end{array}\right], \quad
\alpha_2 = \left[\begin{array}{c}
2 \\
1 \\
2
\end{array}\right], \quad
\alpha_3 = \left[\begin{array}{c}
2 \\
2 \\
1
\end{array}\right]
$$

2. 施密特正交化

$$
{\beta}_{1}={\alpha}_{1}=\left[\begin{array}{c}
1 \\
2 \\
1
\end{array}\right]
$$

$$
{\beta}_{2}={\alpha}_{2}-\frac{\left\langle{\alpha}_{2}, {\beta}_{1}\right\rangle}{\left\langle{\beta}_{1}, \beta_{1}\right\rangle} {\beta}_{1}=\left[\begin{array}{c}
1 \\
-1 \\
1
\end{array}\right]
$$

$$
{\beta}_{3}={\alpha}_{3}-\frac{\left\langle{\alpha}_{2}, {\beta}_{1}\right\rangle}{\left\langle{\beta}_{1}, {\beta}_{1}\right\rangle} {\beta}_{1}-\frac{\left\langle{\alpha}_{3}, {\beta}_{2}\right\rangle}{\left\langle{\beta}_{2}, {\beta}_{2}\right\rangle} {\beta}_{2}= \left[\begin{array}{c}
\frac{1}{2} \\
0 \\
-\frac{1}{2}
\end{array}\right]
$$

3. 标准化后得到列向量 $q$， 将它们排成矩阵 $Q$（列正交矩阵）

$$
    Q=\left[q_{1}, q_{2}, q_{3}\right]=\left[\begin{array}{ccc}
        \frac{1}{\sqrt{6}} & \frac{1}{\sqrt{3}} & \frac{\sqrt{2}}{2} \\
        \frac{2}{\sqrt{6}} & -\frac{1}{\sqrt{3}} & 0 \\
        \frac{1}{\sqrt{6}} & \frac{1}{\sqrt{3}} & -\frac{\sqrt{2}}{2}
        \end{array}\right] \\
$$

4. 死记矩阵 $R$ （和矩阵 $A$ 行列数相同的上三角矩阵）的填充：

$$
R=\left[\begin{array}{ccc}\left\|\beta_1\right\| & \left\langle\alpha_2, q_1\right\rangle & \left\langle\alpha_3, q_1\right\rangle \\ & \left\|\beta_2\right\| & \left\langle\alpha_3, q_2\right\rangle \\ & & \left\|\beta_3\right\|\end{array}\right]
$$

$$
R=\left[\begin{array}{ccc}
        \sqrt{6} & \sqrt{6} & \frac{7}{\sqrt{6}} \\
        0 & \sqrt{3} & \frac{1}{\sqrt{3}} \\
        0 & 0 & \frac{\sqrt{2}}{2}
        \end{array}\right]
$$

原式变换为 $Rx = Q^{-1}b$ ，即：
$$
\left[\begin{array}{ccc}
    \sqrt{6} & \sqrt{6} & \frac{7\sqrt{6}}{6} \\
    0 & \sqrt{3} & \frac{\sqrt{3}}{3} \\
    0 & 0 & \frac{\sqrt{2}}{2}
    \end{array}\right]\left[\begin{array}{c}
x_{1} \\ x_{2} \\ x_{3} 
\end{array}\right]=\left[\begin{array}{c}
\frac{4\sqrt{6}}{3} \\ \frac{2\sqrt{3}}{3} \\ -\sqrt{2} 
\end{array}\right]
$$





【例2】求矩阵 $A=\left[\begin{array}{ll}3 & 2 \\ 1 & 2 \\ 1 & 0\end{array}\right]$ 的 QR 分解

解：
$$
\alpha_1 = \left[\begin{array}{c}
3 \\
1 \\
1
\end{array}\right], \quad
\alpha_2 = \left[\begin{array}{c}
2 \\
2 \\
0
\end{array}\right]
$$

$$
{\beta}_{1}={\alpha}_{1}=\left[\begin{array}{c}
3 \\
1 \\
1
\end{array}\right]
$$

$$
{\beta}_{2}={\alpha}_{2}-\frac{\left\langle{\alpha}_{2}, {\beta}_{1}\right\rangle}{\left\langle{\beta}_{1}, \beta_{1}\right\rangle} {\beta}_{1}=-\frac{2}{11}\left[\begin{array}{c}
1 \\
-7 \\
4
\end{array}\right]
$$

**注：此时向量只有 2 个，而 $A$ 有 3 行，所以需要补：**
$$
\begin{aligned} & \left\{\begin{array}{l}\beta_1^T \beta_3=0 \\ \beta_2^T \beta_3=0\end{array} \Rightarrow\left[\begin{array}{ccc}3 & 1 & 1 \\ 1 & -7 & 4\end{array}\right] \rightarrow\left[\begin{array}{ccc}1 & -7 & 4 \\ 0 & 22 & -11\end{array}\right] \rightarrow\left[\begin{array}{ccc}1 & -7 & 4 \\ 0 & 2 & -1\end{array}\right] \Rightarrow \beta_3 = \left[\begin{array}{c}
-k \\
k \\
2k
\end{array}\right]\right. \\ \end{aligned}
$$
令 $\beta_3=\left[\begin{array}{c}
 -1\\
1 \\
2\end{array}\right]$ 
$$
\begin{aligned} q_1 & =\frac{\beta_1}{\left\|\beta_1\right\|}=\frac{1}{\sqrt{11}}\left[\begin{array}{c}
3 \\
1 \\
1
\end{array}\right] \\ q_2 & =\frac{\beta_2}{\left\|\beta_2\right\|}=\frac{1}{\sqrt{66}}\left[\begin{array}{c}
1 \\
-7 \\
4
\end{array}\right] \\ q_3 & =\frac{\beta_3}{\left\|\beta_3\right\|}=\frac{1}{\sqrt{6}}\left[\begin{array}{c}
-1 \\
1 \\
2
\end{array}\right] \\ \end{aligned}
$$

$$
Q  =\left[\begin{array}{ccc}\frac{3}{\sqrt{11}} & \frac{1}{\sqrt{66}} & \frac{-1}{\sqrt{6}} \\ \frac{1}{\sqrt{11}} & \frac{-7}{\sqrt{66}} & \frac{1}{\sqrt{6}} \\ \frac{1}{\sqrt{11}} & \frac{4}{\sqrt{66}} & \frac{2}{\sqrt{6}}\end{array}\right]
$$

$$
R=\left[\begin{array}{cc}\sqrt{11} & \frac{8}{\sqrt{11}} \\ 0 & \frac{-2 \sqrt{6}}{\sqrt{11}} \\ 0 & 0\end{array}\right]
$$



【例3】用 Householder 方法求矩阵 $A=\left[\begin{array}{cc}1 & 1 \\ 2 & 0 \\ 2 & 1\end{array}\right]$ 的 QR 分解

解：TODO





【例4】已知矩阵 $\boldsymbol{A}=\left(\begin{array}{ccc}0 & 3 & 1 \\ 0 & 4 & -2 \\ 2 & 1 & 1\end{array}\right)$, 利用 Householder 变换求 $\boldsymbol{A}$ 的 $\boldsymbol{Q R}$ 分解。
解：
因为 $\boldsymbol{\alpha}_1=(0,0,2)^{\mathrm{T}}$, 记 $a_1=\left\|\boldsymbol{\alpha}_1\right\|_2=2$, 令 $\boldsymbol{w}_1=\frac{\boldsymbol{\alpha}_1-a_1 e_1}{\left\|\boldsymbol{\alpha}_1-a_1 e_1\right\|_2}=\frac{1}{\sqrt{2}}(-1,0,1)^{\mathrm{T}}$, 则
$$
\boldsymbol{H}_1=\boldsymbol{I}-2 \boldsymbol{w}_1 \boldsymbol{w}_1^{\mathrm{T}}=\left(\begin{array}{ccc}
0 & 0 & 1 \\
0 & 1 & 0 \\
1 & 0 & 0
\end{array}\right)
$$
从而
$$
\boldsymbol{H}_1 \boldsymbol{A}=\left(\begin{array}{ccc}
2 & 1 & 1 \\
0 & 4 & -2 \\
0 & 3 & 1
\end{array}\right)
$$
记 $\boldsymbol{\beta}_2=(4,3)^{\mathrm{T}}$, 则 $b_2=\left\|\boldsymbol{\beta}_2\right\|_2=5$, 令 $\boldsymbol{w}_2=\frac{\boldsymbol{\beta}_2-b_2 e_2}{\left\|\boldsymbol{\beta}_2-b_2 e_2\right\|_2}=\frac{1}{\sqrt{10}}(-1,3)^{\mathrm{T}}$
$$
\hat{\boldsymbol{H}}_2=\boldsymbol{I}-2 \boldsymbol{w}_2 \boldsymbol{w}_2^{\mathrm{T}}=\left(\begin{array}{cc}
\frac{4}{5} & \frac{3}{5} \\
\frac{3}{5} & -\frac{4}{5}
\end{array}\right)
$$
记
$$
\boldsymbol{H}_2=\left(\begin{array}{cc}
1 & 0^{\mathrm{T}} \\
0 & \hat{\boldsymbol{H}}_2
\end{array}\right)=\left(\begin{array}{ccc}
1 & 0 & 0 \\
0 & \frac{4}{5} & \frac{3}{5} \\
0 & \frac{3}{5} & -\frac{4}{5}
\end{array}\right)
$$
则
$$
\boldsymbol{H}_2\left(\boldsymbol{H}_1 \boldsymbol{A}\right)=\left(\begin{array}{ccc}
2 & 1 & 1 \\
0 & 5 & -1 \\
0 & 0 & -2
\end{array}\right)=\boldsymbol{R}
$$
取
$$
\boldsymbol{Q}=\boldsymbol{H}_1 \boldsymbol{H}_2=\left(\begin{array}{ccc}
0 & \frac{3}{5} & -\frac{4}{5} \\
0 & \frac{4}{5} & \frac{3}{5} \\
1 & 0 & 0
\end{array}\right)
$$
则 $\boldsymbol{A}=\boldsymbol{Q R}$ 。



【例5】已知矩阵 $\boldsymbol{A}=\left(\begin{array}{ccc}0 & 3 & 1 \\ 0 & 4 & -2 \\ 2 & 1 & 1\end{array}\right)$, 利用 Givens 变换求 $\boldsymbol{A}$ 的 $\boldsymbol{Q R}$ 分解。

解：
因为 $a_{11}=0, a_{31}=2$, 取 $c=0, s=1$, 构造
$$
\boldsymbol{T}_{13}=\left(\begin{array}{ccc}
0 & 0 & 1 \\
0 & 1 & 0 \\
-1 & 0 & 0
\end{array}\right)
$$
则有
$$
\boldsymbol{A}^{(1)}=\boldsymbol{T}_{13} \boldsymbol{A}=\left(\begin{array}{ccc}
2 & 1 & 1 \\
0 & 4 & -2 \\
0 & -3 & -1
\end{array}\right)
$$
因为 $a_{22}^{(1)}=4, a_{32}^{(1)}=-3$, 取 $c=\frac{4}{5}, s==-\frac{3}{5}$, 构造
则
$$
\boldsymbol{T}_{23}=\left(\begin{array}{ccc}
1 & & \\
& \frac{4}{5} & -\frac{3}{5} \\
& \frac{3}{5} & \frac{4}{5}
\end{array}\right)
$$
$$
\begin{gathered}
\boldsymbol{A}^{(2)}=\boldsymbol{T}_{23} \boldsymbol{A}^{(1)}=\left(\begin{array}{ccc}
2 & 1 & 1 \\
0 & 5 & -1 \\
0 & 0 & -2
\end{array}\right)=\boldsymbol{R} \\
\end{gathered}
$$
$$
\boldsymbol{Q}=\boldsymbol{T}_{13}^T \boldsymbol{T}_{23}^T=\left(\begin{array}{ccc}
0 & \frac{3}{5} & -\frac{4}{5} \\
0 & \frac{4}{5} & \frac{3}{5} \\
1 & 0 & 0
\end{array}\right)
$$

则 $\boldsymbol{A}=\boldsymbol{Q R}$ 。

### 12 - Cholesky 分解

【例1】求矩阵 $A=\left[\begin{array}{ccc}5 & 2 & -4 \\ 2 & 1 & -2 \\ -4 & -2 & 5\end{array}\right]$ 的 Cholesky 分解

> Cholesky 分解适用于**对称正定矩阵**，$\boldsymbol{A} = \boldsymbol{G}\boldsymbol{G}^T$

解：
$$
\boldsymbol{G}=\left[\begin{array}{ccc}g_{11} & & \\ g_{21} & g_{22} & \\ g_{31} & g_{32} & g_{33}\end{array}\right]
$$
**按列顺序**，列的层面**先算主对角**元素，再按行的顺序补全元素：

第 1 列：
$$
g_{11} = \sqrt{a_{11}} = \sqrt{5}
$$

$$
g_{21}=\frac{a_{21}}{g_{11}}=\frac{2}{\sqrt{5}},\quad g_{31}=\frac{a_{31}}{g_{11}}=\frac{-4}{\sqrt{5}}
$$

第 2 列：
$$
g_{22}=\sqrt{a_{22}-g_{21}^2}= \frac{1}{\sqrt{5}}
$$

$$
g_{32}=\frac{a_{32}-g_{31} g_{21}}{g_{22}}=\frac{-2-\frac{2}{\sqrt{5}} \cdot\left(-\frac{4}{\sqrt{5}}\right)}{\frac{1}{\sqrt{5}}} = \frac{-2}{\sqrt{5}}
$$

第 3 列：
$$
g_{33}=\sqrt{a_{33}-g_{31}^2-g_{32}^2}=\sqrt{5-\left(-\frac{4}{\sqrt{5}}\right)^2-\left(-\frac{2}{\sqrt{5}}\right)^2} = 1
$$
即
$$
\boldsymbol{G} = \left[\begin{array}{ccc}\sqrt{5} & & \\ \frac{2}{\sqrt{5}} & \frac{1}{\sqrt{5}} & \\ -\frac{4}{\sqrt{5}} & -\frac{2}{\sqrt{5}} & 1\end{array}\right]
$$
注：

1. 最后一步 $\boldsymbol{A} = \boldsymbol{G}\boldsymbol{G}^T$ 偷懒不写了
2. 前提是要判定矩阵是对称正定矩阵，即特征值均大于 $0$ 且对称













### 13 - 奇异值分解（SVD）

【例1】求矩阵 $A=\left[\begin{array}{ll}1 & 0 \\ 0 & 1 \\ 1 & 1\end{array}\right]$ 的 SVD 

1. 计算 $A^T A$ 的特征值和对应的特征向量

$$
A^T A=\left[\begin{array}{ll}
2 & 1 \\
1 & 2
\end{array}\right] \\
$$

$$
\begin{gathered}
\left|A^T A-\lambda E\right|=\left|\begin{array}{cc}
2-\lambda & 1 \\
1 & 2-\lambda
\end{array}\right|=\lambda^2-4 \lambda+4-1=(\lambda-3)(\lambda-1)=0
\end{gathered}
$$
得 $\lambda_1=1, \lambda_2=3$
$$
A^T A-E=\left[\begin{array}{ll}
1 & 1 \\
1 & 1
\end{array}\right] \rightarrow\left[\begin{array}{ll}
1 & 1 \\
0 & 0
\end{array}\right] \Rightarrow x=\left[\begin{array}{c}
k \\
-k
\end{array}\right] \rightarrow x_1=\left[\begin{array}{c}
1 \\
-1
\end{array}\right]
$$

$$
A^T A-3 E=\left[\begin{array}{cc}
-1 & 1 \\
1 & -1
\end{array}\right] \rightarrow\left[\begin{array}{cc}
-1 & 1 \\
0 & 0
\end{array}\right] \Rightarrow x=\left[\begin{array}{l}
k \\
k
\end{array}\right] \rightarrow x_2=\left[\begin{array}{l}
1 \\
1
\end{array}\right]
$$

2. 计算 $A A^T$ 的特征值和对应的特征向量

$$
A A^T=\left[\begin{array}{lll}
1 & 0 & 1 \\
0 & 1 & 1 \\
1 & 1 & 2
\end{array}\right]
$$

$$
\begin{aligned}
 \left|A A^T-\eta E\right|&=\left|\begin{array}{ccc}
1-\eta & 0 & 1 \\
0 & 1-\eta & 1 \\
1 & 1 & 2-\eta
\end{array}\right| \rightarrow\left|\begin{array}{ccc}
0 & \eta-1 & 1+(2-\eta)(\eta-1) \\
0 & 1-\eta & 1 \\
1 & 1 & 2-\eta
\end{array}\right| \\
& =\left|\begin{array}{cc}
\eta-1 & -\eta^2+3 \eta-1 \\
1-\eta & 1
\end{array}\right|=(\eta-3)(\eta-1) \eta=0 
\end{aligned}
$$

得 $\eta_1=1, \eta_2=3, \eta_3=0$
$$
A A^T-E=\left[\begin{array}{ccc}
0 & 0 & 1 \\
0 & 0 & 1 \\
1 & 1 & 1
\end{array}\right] \rightarrow\left[\begin{array}{ccc}
1 & 1 & 0 \\
0 & 0 & 1 \\
0 & 0 & 0
\end{array}\right] \Rightarrow x=\left[\begin{array}{c}
k \\
-k \\
0
\end{array}\right] \rightarrow x_1=\left[\begin{array}{c}
1 \\
-1 \\
0
\end{array}\right]
$$

$$
 A A^T-3 E=\left[\begin{array}{ccc}-2 & 0 & 1 \\ 0 & -2 & 1 \\ 1 & 1 & -1\end{array}\right]\rightarrow\left[\begin{array}{ccc}1 & 1 & -1 \\ 0 & -2 & 1 \\ 0 & 0 & 0\end{array}\right] \Rightarrow x=\left[\begin{array}{c}k \\ k \\ 2 k\end{array}\right] \rightarrow x_2=\left[\begin{array}{c}1 \\ 1 \\ 2\end{array}\right]
$$

$$
A A^T=\left[\begin{array}{lll}1 & 0 & 1 \\ 0 & 1 & 1 \\ 1 & 1 & 2\end{array}\right] \rightarrow\left[\begin{array}{lll}1 & 0 & 1 \\ 0 & 1 & 1 \\ 0 & 0 & 0\end{array}\right] \Rightarrow x=\left[\begin{array}{c}-k \\ -k \\ k\end{array}\right] \rightarrow x_3=\left[\begin{array}{c}1 \\ 1 \\ -1\end{array}\right]
$$

3. 记待分解矩阵 $A$ 为 $m \times n$ 矩阵,

（1）依次排列 $A A^T$ **标准化**的特征向量得到矩阵 $\boldsymbol{U}$
（2）依次填入 $A^T A$ 特征值的**根号值**得到对角矩阵 $\boldsymbol{\Sigma}$
（3）依次排列 $A^T A$ **标准化**的特征向量并**转置**得到矩阵 $\boldsymbol{V}^T$
$$
A=\left[\begin{array}{ccc}
\frac{1}{\sqrt{2}} & \frac{1}{\sqrt{6}} & \frac{1}{\sqrt{3}} \\
-\frac{1}{\sqrt{2}} & \frac{1}{\sqrt{6}} & \frac{1}{\sqrt{3}} \\
0 & \frac{2}{\sqrt{6}} & -\frac{1}{\sqrt{3}}
\end{array}\right]\left[\begin{array}{cc}
1 & 0 \\
0 & \sqrt{3} \\
0 & 0
\end{array}\right]\left[\begin{array}{cc}
\frac{1}{\sqrt{2}} & -\frac{1}{\sqrt{2}} \\
\frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}}
\end{array}\right]
$$







### 15 - 最小二乘问题

【例1】设 $\boldsymbol{A}=\left[\begin{array}{ll}1 & 2 \\ 3 & 4 \\ 5 & 6\end{array}\right], \boldsymbol{b}=\left[\begin{array}{l}1 \\ 1 \\ 1\end{array}\right]$ 

**（1）用正规化方法求对应的 LS 问题的解。**

解：
$$
\boldsymbol{A}^T\boldsymbol{A}=\left[\begin{array}{ccc}1 & 3 & 5 \\ 2& 4 & 6  \end{array}\right] \left[\begin{array}{cc}1 & 2  \\ 3 & 4 \\ 5 & 6  \end{array}\right] = \left[\begin{array}{ccc}35 & 44 \\ 44 & 56  \end{array}\right]
$$

$$
\boldsymbol{A}^T\boldsymbol{b} = \left[\begin{array}{c}9 \\ 12\end{array}\right]
$$


$$
\boldsymbol{A}^T\boldsymbol{A}\boldsymbol{x} = \left[\begin{array}{ccc}35 & 44 \\ 44 & 56  \end{array}\right] \boldsymbol{x} = \left[\begin{array}{c}9 \\ 12\end{array}\right]
$$


$$
\boldsymbol{x} = \left[\begin{array}{c}-1 \\ 1\end{array}\right]
$$

**（2）用 QR 分解方法求对应的 LS 问题的解**

解：

1. 对矩阵 $\boldsymbol{A}$ 的列向量做施密特正交化

$$
\alpha_1 = \left[\begin{array}{c}1  \\ 3  \\ 5   \end{array}\right],\quad \alpha_2 = \left[\begin{array}{c}2  \\ 4  \\ 6   \end{array}\right]
$$

$$
\beta_1=\alpha_1=\left[\begin{array}{l}
1 \\
3 \\
5
\end{array}\right], \quad \beta_2=\alpha_2-\frac{\left\langle\alpha_2, \beta_1\right\rangle}{\left\langle\beta_1, \beta_1\right\rangle} \beta_1=\frac{2}{35}\left[\begin{array}{c}
13 \\
4 \\
-5
\end{array}\right]
$$



2. 对正交向量标准化得到正交矩阵 $\mathbf{Q}$

$$
\mathbf{Q}=\left[\begin{array}{cc}
\frac{1}{\sqrt{35}} & \frac{13}{\sqrt{210}} \\
\frac{3}{\sqrt{35}} & \frac{4}{\sqrt{210}} \\
\frac{5}{\sqrt{35}} & \frac{-5}{\sqrt{210}}
\end{array}\right]
$$
3. 计算上三角矩阵 $\mathbf{R}$ 。

$$
\begin{gathered}
r_{11}=\left\|\beta_1\right\|=\sqrt{35}, \quad r_{22}=\left\|\beta_2\right\|=\frac{\sqrt{24}}{\sqrt{35}}, \quad r_{12}=\left\langle\mathbf{q}_1, \alpha_2\right\rangle=\frac{44}{\sqrt{35}} \\
\end{gathered}
$$
$$
\mathbf{R}=\left[\begin{array}{cc}
\sqrt{35} & \frac{44}{\sqrt{35}} \\
0 & \frac{\sqrt{24}}{\sqrt{35}}
\end{array}\right]
$$

4. 将 $\mathbf{A}=\mathbf{Q R}$ 代入方程组 $\mathbf{A x}=\mathbf{b}$ 。

$$
\mathbf{Q R \mathbf { x }}=\mathbf{b}
$$

$$
\mathbf{x}=\mathbf{R}^{-1} \mathbf{Q}^T \mathbf{b}=\left[\begin{array}{c}
-1 \\
1
\end{array}\right]
$$

对于 $\mathbf{R x}=\mathbf{Q}^T \mathbf{b}=\left[\begin{array}{c}
\frac{9}{\sqrt{35}} \\
\frac{\sqrt{24}}{\sqrt{35}}
\end{array}\right]$  ，亦可利用初等行变换解方程，即
$$
\left[\begin{array}{cc:c}
\sqrt{35} & \frac{44}{\sqrt{35}}& \frac{9}{\sqrt{35}} \\
0 & \frac{\sqrt{24}}{\sqrt{35}} & \frac{\sqrt{24}}{\sqrt{35}}
\end{array}\right]
$$

$$
\left[\begin{array}{cc:c}
35 & 44& 9 \\
0 & 12 & 12
\end{array}\right]
$$

$$
\mathbf{x}=\left[\begin{array}{c}
-1 \\
1
\end{array}\right]
$$
