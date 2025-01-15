@def title = "Interviews for Tailai"
@def date = "04/12/2022"
@def tags = ["meta", "julia"]
@def hasmath = true

# 泰铼面试

## 笔试

1. [剑指Offer：青蛙跳台阶问题（动态规划）](https://leetcode-cn.com/problems/qing-wa-tiao-tai-jie-wen-ti-lcof/)

2. 在自助法的采样过程中，对n个样本进行n次自助抽样，当n趋于无穷大时， 最终有多少数据从未被选择过?

    **答案：** https://blog.csdn.net/GhostintheCode/article/details/104614607 
    
    **拓展：** 从标有1到n的n个小球中有放回地随机抽取，直到所有球都被抽到至少一次，求抽取次数的期望？

3. For uniform $(0,1)$ random independent variables $U_{1}, U_{2}, \ldots$.     Define
    $
    N=\min \left\{n: \sum_{i=1}^{n} U_{i}>1\right\}
    $
        Give an estimate for the value of $\mathbb{E}[N]$. 
          
    **Solution:** Here is a way to compute $\mathbb{E}(N)$. We begin by complicating things, namely, for every $x$ in $(0,1)$, we consider $m_{x}=E\left(N_{x}\right)$ where
    $
    N_{x}=\min \left\{n ; \sum_{k=1}^{n} U_{k}>x\right\} .
    $
    Our goal is to compute $m_{1}$ since $N_{1}=N$. Assume that $U_{1}=u$ for some $u$ in $(0,1)$. If $u>x$, then $N_{x}=1$. If $u < x$, then $N_x=1+N^{\prime}$ where $N^{\prime}$ is distributed like $N_{x-u}$.  Hence
    $
    m_{x}=1+\int_{0}^{x} m_{x-u} \mathrm{~d} u=1+\int_{0}^{x} m_{u} \mathrm{~d} u
    $
    Thus, $x \mapsto m_{x}$ is differentiable with $m_{x}^{\prime}=m_{x}$. Since $m_{0}=1, m_{x}=\mathrm{e}^{x}$ for every $x \leqslant 1$, in particular $\mathbb{E}(N)=m_{1}=\mathrm{e}$.
    
    https://math.stackexchange.com/questions/214399/summing-0-1-uniform-random-variables-up-to-1    
1. 一根绳子切成三段,组成三角形的几率是多少?

    **Solution:** 设绳长为12,分成的三段分别为x,y,12-x-y,且x>y>12-x-y,则x,x应满足以下5条关系：x+y0, y>0, x>y, y>12-x-y,在平面直角坐标系中是以(12,0), (6,6), (4,4)为顶点的三角形区域,易求出面积等于12.
    由于x>y>12-x-y,只需再满足x<6,这三段就能构成三角形.即在上述5条关系后再加上第6条：x<6,组成了以(6,3), (6,6), (4,4)为顶点的三角形区域,易求出面积等于3.
    问题就解决了,构成三角形的概率是3/12=1/4
    最后说一句,这个结果不受x=6的特殊情况影响.因为图形是由无数个点组成的.
2. 1000瓶酒.10只老鼠.有一瓶酒有毒,每只老鼠可以喝无限多的酒,如何测一次就找出哪瓶酒有毒？
   
   **Solution:** https://blog.csdn.net/qq_28979491/article/details/105251995
3. 1000个均匀分布于单位圆的点，以及一个位于(100,100)的点。试着估算$R^2$.
   ```r
    n <- 1000
    r <- runif(n)
    theta <- runif(n)*2*pi
    x <- r*cos(theta)
    y <- r*sin(theta)
    x[n+1] <- 100
    y[n+1] <- 100
    cor(x,y)^2
    # > n <- 1000
    # > r <- runif(n)
    # > theta <- runif(n)*2*pi
    # > x <- r*cos(theta)
    # > y <- r*sin(theta)
    # > x[n+1] <- 100
    # > y[n+1] <- 100
    # > cor(x,y)^2
    # [1] 0.967791
   ```
4. We choose 2n arbitrary points on a circle. How many ways are there of drawing n lines between 2 points, such that there are no intersections between these lines inside the circle?

    **Solution:** Catalan numbers (https://math.stackexchange.com/questions/284512/proof-of-catalan-numbers-on-a-circle).


## 面试问题

1. 掷骰子掷到连续两个6的平均步数。
   * Markov chain
2. 某连续分布$X_i\sim f$, stop if $X_i \leq  X_{i + 1}$ and continue if $X_i > X_{i + 1}$. 问平均步数。
   
   * $\exp(1) - 1$
   * https://stats.stackexchange.com/questions/350923/brain-teaser-what-is-the-expected-length-of-an-iid-sequence-that-is-monotonical
3. 认识关系。n个人至少需要几个认识关系使得任意两个人有同一个人同时认识他们。
4. 52扑克牌，有放回抽取，问抽取到所有花色的A的平均步数。
   * 拓展：无放回， https://math.stackexchange.com/questions/268432/expected-number-of-card-draws-to-get-all-4-suits