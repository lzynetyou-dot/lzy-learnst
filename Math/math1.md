# 大学数学核心知识点总结（高数、线代、概统）

本文档涵盖了**高等数学**、**线性代数**与**概率论与数理统计**三大核心课程的关键概念、定理与重要公式。

---

# 一、 高等数学 (Higher Mathematics)

## 1. 极限与连续 (Limits & Continuity)
*   **极限性质与运算法则：** 唯一性、局部有界性、保号性。
*   **两个重要极限：**
    1. $\lim_{x \to 0} \frac{\sin x}{x} = 1$
    2. $\lim_{x \to \infty} \left(1 + \frac{1}{x}\right)^x = e$
*   **等价无穷小替换（$x \to 0$）：**
    *   $\sin x \sim x, \quad \tan x \sim x, \quad \arcsin x \sim x, \quad \arctan x \sim x$
    *   $1 - \cos x \sim \frac{1}{2}x^2, \quad e^x - 1 \sim x, \quad \ln(1+x) \sim x, \quad (1+x)^\alpha - 1 \sim \alpha x$
*   **求极限核心方法：** 洛必达法则（L'Hôpital's Rule）、泰勒展开式（Taylor Expansion）、夹逼定理、单调有界准则。
*   **函数的连续性与间断点：**
    *   **第一类间断点：** 可去间断点（极限存在）、跳跃间断点（左右极限均存在但不相等）。
    *   **第二类间断点：** 无穷间断点、振荡间断点。

## 2. 一元函数微分学 (Single-Variable Differential Calculus)
*   **导数定义：** $f'(x_0) = \lim_{\Delta x \to 0} \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x}$
*   **中值定理（核心核心）：**
    *   **罗尔定理 (Rolle)：** 若 $f(x)$ 在 $[a,b]$ 连续、$(a,b)$ 可导，且 $f(a)=f(b)$，则 $\exists \xi \in (a,b)$ 使 $f'(\xi)=0$。
    *   **拉格朗日中值定理 (Lagrange)：** $f(b) - f(a) = f'(\xi)(b - a)$
    *   **柯西中值定理 (Cauchy)：** $\frac{f(b) - f(a)}{g(b) - g(a)} = \frac{f'(\xi)}{g'(\xi)}$
    *   **泰勒中值定理 (Taylor)：** 带拉格朗日余项与佩阿诺余项的展开。
*   **导数应用：** 极值与最值判断（一阶/二阶导数判别法）、凹凸性与拐点（二阶导数符号）、渐近线（水平、铅直、斜渐近线）。

## 3. 一元函数积分学 (Single-Variable Integral Calculus)
*   **不定积分与定积分关系（牛顿-莱布尼茨公式）：**
    $$\int_{a}^{b} f(x)dx = F(b) - F(a)$$
*   **积分技巧：**
    *   第一类/第二类换元法（三角换元、根式换元等）。
    *   分部积分法：$\int u \, dv = uv - \int v \, du$ （口诀：“反对数三指”优先设为 $u$）。
*   **反常积分（瑕积分与无穷限积分）：** 收敛性判别（p-积分检验法）。
*   **几何应用：** 变限积分求导、平面图形面积、旋转体体积（绕 $x$ 轴与 $y$ 轴）。

## 4. 多元函数微积分学 (Multivariable Calculus)
*   **偏导数与全微分：**
    *   全微分存在条件：$\Delta z = A\Delta x + B\Delta y + o(\rho)$，偏导数连续是全微分存在的充分条件。
    *   全微分形式不变性。
*   **多元极值与条件极值：**
    *   无条件极值：驻点处 $\Delta = AC - B^2$（$A=f''_{xx}, B=f''_{xy}, C=f''_{yy}$），若 $\Delta > 0$ 且 $A<0$ 为极大值，$\Delta > 0$ 且 $A>0$ 为极小值。
    *   条件极值：**拉格朗日乘子法**（拉格朗日函数 $L(x,y,\lambda) = f(x,y) + \lambda \varphi(x,y)$）。
*   **二重积分与三重积分：**
    *   直角坐标与极坐标转换（$dxdy = r \, dr d\theta$）。
    *   对称性简化计算（奇零偶倍、轮换对称性）。

## 5. 常微分方程 (Differential Equations)
*   **一阶微分方程：**
    *   可分离变量型、齐次型。
    *   一阶线性微分方程 $y' + p(x)y = q(x)$ 通解公式：
        $$y = e^{-\int p(x)dx} \left( \int q(x) e^{\int p(x)dx} dx + C \right)$$
*   **二阶常系数齐次/非齐次线性微分方程：**
    *   特征方程法求齐次解：$r^2 + pr + q = 0$（根据 $\Delta$ 情况分类讨论）。
    *   待定系数法求特解。

---

# 二、 线性代数 (Linear Algebra)

## 1. 行列式与矩阵 (Determinants & Matrices)
*   **行列式展开：** 按行（列）展开定理，余因式与代数余子式 $A_{ij} = (-1)^{i+j}M_{ij}$。
*   **矩阵基本运算：** 加法、数乘、乘法（不满足交换律！$AB \neq BA$）。
*   **逆矩阵 (Inverse Matrix)：**
    *   $A$ 可逆 $\iff |A| \neq 0$（非奇异矩阵）。
    *   公式：$A^{-1} = \frac{1}{|A|} A^*$ （$A^*$ 为伴随矩阵）。
    *   性质：$(AB)^{-1} = B^{-1}A^{-1}$, $(A^T)^{-1} = (A^{-1})^T$。
*   **初等变换与矩阵的秩 (Rank)：**
    *   初等行变换不改变矩阵的秩与行向量组的线性相关性。
    *   $r(A)$ 的重要性质：$r(A+B) \le r(A) + r(B)$， $r(AB) \le \min(r(A), r(B))$。

## 2. 向量组与线性方程组 (Vectors & Linear Systems)
*   **线性相关与线性无关：**
    *   向量组 $\alpha_1, \alpha_2, \dots, \alpha_m$ 线性相关 $\iff \exists$ 不全为 0 的 $k_i$ 使 $\sum k_i \alpha_i = 0$。
*   **极大线性无关组与向量组的秩：**
    *   向量组的秩等于其构成的矩阵的秩。
*   **线性方程组 $Ax = b$ 的解：**
    *   齐次方程组 $Ax = 0$：
        *   有非零解 $\iff r(A) < n$。基础解系中包含 $n - r(A)$ 个线性无关解向量。
    *   非齐次方程组 $Ax = b$：
        *   无解 $\iff r(A) \neq r(A|b)$。
        *   有唯一解 $\iff r(A) = r(A|b) = n$。
        *   有无穷多解 $\iff r(A) = r(A|b) < n$。通解结构：$x = x^* + \sum c_i \xi_i$ （特解 + 齐次通解）。

## 3. 特征值与特征向量 (Eigenvalues & Eigenvectors)
*   **基本定义：** $A\alpha = \lambda\alpha \quad (\alpha \neq 0)$，特征方程：$|\lambda I - A| = 0$。
*   **重要性质：**
    *   $\sum \lambda_i = \text{tr}(A)$ （矩阵的迹/对角线元素之和）。
    *   $\prod \lambda_i = |A|$。
*   **相似矩阵与对角化 (Diagonalization)：**
    *   $A \sim B \iff P^{-1}AP = B$。
    *   $A$ 可对角化 $\iff A$ 有 $n$ 个线性无关的特征向量（重特征值的几何重数等于代数重数）。
    *   **实对称矩阵：** 必定可以正交对角化（不同特征值对应的特征向量相互正交）。

## 4. 二次型 (Quadratic Forms)
*   **标准形与规范形：** 通过正交变换或配方法将 $f(x) = x^T A x$ 化为 $\sum d_i y_i^2$。
*   **惯性定理：** 正系数与负系数的个数（正/负惯性指数）由二次型唯一决定。
*   **正定矩阵 (Positive Definite Matrix)：**
    *   $x^T A x > 0$（对任意 $x \neq 0$）。
    *   判定方法：顺序主子式全大于 0；特征值全大于 0；正惯性指数等于 $n$。

---

# 三、 概率论与数理统计 (Probability & Mathematical Statistics)

## 1. 随机事件与概率 (Random Events & Probability)
*   **基本条件与公式：**
    *   **条件概率：** $P(A|B) = \frac{P(AB)}{P(B)}$
    *   **乘法公式：** $P(AB) = P(A)P(B|A)$
    *   **全概率公式：** $P(B) = \sum_{i=1}^{n} P(A_i)P(B|A_i)$ （划分/完备事件组）
    *   **贝叶斯公式 (Bayes)：** $P(A_k|B) = \frac{P(A_k)P(B|A_k)}{\sum P(A_i)P(B|A_i)}$ （由果溯因）
*   **事件独立性：** $A$ 与 $B$ 独立 $\iff P(AB) = P(A)P(B)$。

## 2. 一维与二维随机变量 (Random Variables)
*   **分布函数：** $F(x) = P(X \le x)$。
*   **常见离散型分布：**
    *   0-1分布 (Bernoulli)、二项分布 $B(n, p)$、泊松分布 $P(\lambda)$。
*   **常见连续型分布：**
    *   均匀分布 $U(a, b)$、指数分布 $E(\lambda)$（具有无后效性）、正态分布 $N(\mu, \sigma^2)$。
*   **边缘分布与条件分布（二维）：**
    *   $F_X(x) = F(x, +\infty)$，连续型 $f_X(x) = \int_{-\infty}^{+\infty} f(x,y)dy$。
    *   独立性判别：$f(x,y) = f_X(x)f_Y(y)$ 或 $F(x,y) = F_X(x)F_Y(y)$。

## 3. 随机变量的数字特征 (Numerical Characteristics)
*   **期望 $E(X)$ 与 方差 $D(X)$：**
    *   方差公式：$D(X) = E(X^2) - [E(X)]^2$。
    *   性质：$E(aX+b) = aE(X)+b$；若 $X,Y$ 独立，$D(X\pm Y) = D(X) + D(Y)$。
*   **常见分布的期望与方差：**
    *   $B(n,p)$：$E=np, D=np(1-p)$
    *   $P(\lambda)$：$E=\lambda, D=\lambda$
    *   $U(a,b)$：$E=\frac{a+b}{2}, D=\frac{(b-a)^2}{12}$
    *   $E(\lambda)$：$E=\frac{1}{\lambda}, D=\frac{1}{\lambda^2}$
    *   $N(\mu, \sigma^2)$：$E=\mu, D=\sigma^2$
*   **协方差与相关系数：**
    *   协方差：$\text{Cov}(X,Y) = E(XY) - E(X)E(Y)$。
    *   相关系数：$\rho_{XY} = \frac{\text{Cov}(X,Y)}{\sqrt{D(X)D(Y)}}$。
    *   $\rho_{XY} = 0 \iff X,Y$ 不相关（正态分布下，不相关等价于独立）。

## 4. 大数定律与中心极限定理 (Limit Theorems)
*   **切比雪夫不等式：** $P(|X - \mu| \ge \epsilon) \le \frac{\sigma^2}{\epsilon^2}$。
*   **辛钦大数定律：** 独立同分布样本的算术平均依概率收敛于均值 $\mu$。
*   **中心极限定理 (CLT)：** 大量独立同分布随机变量之和近似服从正态分布：
    $$\frac{\sum_{i=1}^n X_i - n\mu}{\sqrt{n}\sigma} \xrightarrow{d} N(0, 1)$$

## 5. 数理统计初步 (Mathematical Statistics)
*   **三大抽样分布：**
    *   $\chi^2$ 分布（卡方）：独立标准正态变量平方和。
    *   $t$ 分布：$t = \frac{X}{\sqrt{Y/n}}$ （$X \sim N(0,1), Y \sim \chi^2(n)$）。
    *   $F$ 分布：两个独立卡方变量除以自由度之比。
*   **正态总体抽样定理：**
    *   $\bar{X} \sim N\left(\mu, \frac{\sigma^2}{n}\right)$
    *   $\frac{(n-1)S^2}{\sigma^2} \sim \chi^2(n-1)$，且 $\bar{X}$ 与 $S^2$ 相互独立。
*   **参数估计：**
    *   矩估计法（用样本矩替代总体矩）。
    *   最大似然估计法（MLE）：构造似然函数 $L(\theta) = \prod f(x_i; \theta)$，取对数后求导令其为 0。