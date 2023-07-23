# Gradient Descent Method
这个算法很关键

# Task Formation

Minimize  $\quad f(\boldsymbol{x})$ \\
Subject to $\quad \boldsymbol{x} \in \text{dom}(f)$ 

where $\boldsymbol{x} \in \mathbb{R}^n$

# Algorithm and Solution
Firstly, you need to choose $\boldsymbol{x}_0 \in \mathbb{R}^n$ and $\alpha > 0$

The solution given by gradient descent method is:

$\lim \limits_{n \rightarrow \infty}$ GD $(n)$ , where GD $(n)$ is the following acknowlegded function:

<div style="background-color: #f2f2f2; padding: 10px;">

**GD**

**Input:** $n$ 

$x_0 = x_0$
for $k = 1: n$  
$\quad x_k = x_{k-1} - \alpha \cdot \nabla{f}(x_{k-1})$

**Output**: $x_n$   
</div>

# Convergence in 1-dimensional Space
Theorem 1: If (1) there exists $x^*$ such that $f'(x^*) = 0$
(2) $x_0 > x^*$
(3) $f'(x)$ exists on $[x^*,x_0]$
(4) $\exists L >0$ such that $\left|f'(x) - f'(y)\right| \leqslant L|x-y|$ for $\forall x,y \in [x^*,x_0]$
(5) $0 < \alpha < \frac{1}{L}$
(6) $f$ is convex
(7) $\inf \limits_{x \in [x^*,x_0]}|f'(x)| > 0$ 
holds, then $\lim \limits_{n \rightarrow \infty}GD(n) \in A$ where $A$ is the optimal set.


Proof: Since  $f$ is convex, we know that for $\forall x,y \in R$, $f(x) \geqslant f(y) +f'(y)(x-y)$. Put $y = x^*$ into this formula, we know that $f(x) \geqslant f(x^*) + f'(x^*)(x-x^*)$, since $f'(x^*) = 0$, then $f(x) \geqslant f(x^*)$. Therefore, we know that $f(x^*)$ is minimum value.

Then, we assume that if $x_k \in [x^*,x_0]$, we put $x = x^*$ and $y = x_k $ to get $f(x^*) \geqslant f(x_k) + f'(x_k) (x^*-x_k)$. Since $x_k > x^*$, $x^* - x_k <0$, then we can get $\frac{f(x^*)-f(x_k)}{x^*-x_k} \leqslant f'(x_k)$. Since $x^*-x_k < 0$ and $f(x^*) - f(x_k) \leqslant 0$, we know that $\frac{f(x^*)-f(x_k)}{x^*-x_k} \geqslant 0$. Therefore, $f'(x_k) \geqslant \frac{f(x^*)-f(x_k)}{
x^*-x_k} \geqslant 0$ .Then, we would know that $x_k = x_{k-1} - \alpha f'(x_{k-1}) \leqslant x_{k-1}$. 
Let us make a conclusion 1 here: If $x_k \in [x^*,x_0]$, then $x_{k} \leqslant x_{k-1}$.


Since there $\exists L > 0$  such that $\left|f'(x) - f'(y)\right| \leqslant L|x-y|$ for $\forall x,y \in [x^*,x_0]$, we would have $\left|f'(x_{k}) - f'(x_{k-1})\right| \leqslant L|x_{k}-x_{k-1}|$ for $\forall x_{k}, x_{k-1} \in [x^*,x_0]$. 

If $x_{k} \leqslant x_{k-1}$ and $x_{k-1} \in [x^*,x_0]$, we would have $|x_{k} - x_{k-1}| = |x_{k-1} - \alpha f'(x_{k-1})-x_{k-1}| = \alpha |f'(x_{k-1})| = \alpha |f'(x_{k-1}) - 0| = \alpha |f'(x_{k-1})-f'(x^*)|$. Since we assume that $x_{k-1} \in [x^*,x_0]$, then from (4) we have $|f'(x_{k-1}) - f'(x^*)| \leqslant L|x_{k-1}-x^*|$.

$|x_{k} - x_{k-1}| \leqslant \alpha |f'(x_{k-1})-f'(x^*)| \leqslant \alpha L |x_{k-1}-x^*| \leqslant \frac{1}{L} \cdot L|x_{k-1}-x^*| =|x_{k-1}-x^*|$.

Since we have assume that $x_{k-1} \geqslant x^*$ and $x_k \leqslant x_{k-1}$, then we can remove the absolute value of the above inequality:

$x_{k-1} - x_{k} \leqslant x_{k-1} - x^* \rightarrow x_k \geqslant x^*$.

Let us draw a conclusion 2 of the proof above:
If $x_{k} \leqslant x_{k-1}$ and $x_{k-1} \in [x^*,x_0]$, then $x^* \leqslant x_{k} \leqslant x_{k-1}$.

Now, we can use the induction. We start from conclusion 1, since $x_0 \in [x^*,x_0]$, then we have $x_1 \leqslant x_0$. Then we use conclusion 2, since $x_1 \leqslant x_0$ and $x_0 \in [x^*, x_0]$, then $x^* \leqslant x_1 \leqslant x_0$. If we repeat this process by using conclusion 1, since $x_1 \in [x^*,x_0]$, we would have $x_2 \leqslant x_1$, and then since $x_2 \leqslant x_1$ and $x_1 \in [x^*, x_0]$, we would have $x^* \leqslant x_2 \leqslant x_1 \leqslant x_0$. If we keep this process we would have the following relationship:$x^* \leqslant x_n \leqslant x_{n-1} \leqslant x_{n-2} \leqslant \cdots \leqslant x_2 \leqslant x_1 \leqslant x_0$.

We need the following Lemma 1:
If $f$ is L-Lipschitz continuous on some interval and $x,y \in$ this interval, then
$f(x) \leqslant f(y) + f'(y) (x - y) + \frac{L}{2} (x - y)^2$

Let us try to prove it:
Proof: Define $g(\tau) = f(y + \tau(x - y))$. By te fundamental theorem of calculus, $f(x) - f(y) = g(1) - g(0) = \int_0^1 g’(\tau) \, d\tau = \int_0^1 f'(y + \tau(x - y)) \cdot (x - y)  d\tau$ .
It follows that $f(x) - f(y) -  f'(y)(x - y) = \int_0^1  f'(y + \tau(x - y)) - f'(y)(x - y) d\tau \\ \leqslant \int_0^1 |f'(y + \tau(x - y)) - \nabla f(y)(x - y)| \, d\tau \\ \leqslant |x - y| \int_0^1 |f'(y + \tau(x - y)) - f'(y)| \, d\tau \\ \leqslant |x - y| \int_0^1 L|\tau(x - y)| \, d\tau \\ = \frac{L}{2} (x - y)^2$

Then we have finish the proof.

Let us continue the proof of convergence: 
By convexity of f, we have:
$f(x_k) \leqslant f(x^*) + f'(x_k)(x_k-x^*)$

As $f$ is L-Lipschitz on $[x_0, x^*]$ and if we assume that $x_k, x_{k-1} \in [x_0,x^*]$, by lemma 1:
$f(x_{k+1}) \leqslant f(x_{k})+ f'(x_k)(x_{k+1})+\frac{L}{2}(x_{k+1}-x_{k})^2 \\ = f(x_k) - \alpha f'(x_{k})^2+\frac{L\alpha^2}{2}f'(x_{k})^2 \\ = f(x_k) - \alpha(1-\frac{L\alpha}{2})f'(x_k)^2 \\ \leqslant f(x_k) - \frac{\alpha}{2}f'(x_k)^2$, the last inequality holds because $0 < \alpha \leqslant \frac{1}{L}$.

It is quite clear that $-\frac{\alpha}{2}f'(x_k)^2 \leqslant 0$. Then we have $f(x_{k+1}) \leqslant f(x_k)$. Now, we know that $x^* \leqslant x_n \leqslant x_{n-1} \leqslant x_{n-2} \leqslant \cdots \leqslant x_2 \leqslant x_1 \leqslant x_0$. By using part of it: $x^* \leqslant  x_1 \leqslant x_0$, we would have $f(x_1) \leqslant f(x_0)$. Then by using another part of it: $x^* \leqslant  x_2 \leqslant x_1$, we would have $f(x_2) \leqslant f(x_1). \cdots$. All in all, we would have $f(x^*) \leqslant f(x_n) \leqslant f(x_{n-1}) \leqslant f(x_{n-2}) \leqslant \cdots \leqslant f(x_2) \leqslant f(x_1) \leqslant f(x_0)$.

By convexity and we continue on $f(x_{k+1}) \leqslant f(x_k) - \frac{\alpha}{2}f'(x_k)^2 \\ \leqslant f(x^*) + f'(x_k)(x_k- x^*)-\frac{\alpha}{2}f'(x_k)^2 \\ = f(x^*) + \frac{1}{\alpha}(x_k -x_{k+1})(x_k -x^*)-\frac{\alpha}{2} \cdot \frac{1}{\alpha^2}(x_k-x_{k+1})^2 \\ = f(x^*) +\frac{1}{2\alpha}(x_i-x^*)^2 - \frac{1}{2\alpha}(x_i-x^*)^2 +\frac{1}{2\alpha} \cdot 2\alpha f'(x_i)(x_i-x^*)-\frac{1}{2\alpha}(x_i-x_{i+1})^2 \\ = f(x^*) +\frac{1}{2\alpha}(x_i-x^*)^2 - \frac{1}{2\alpha}(x_i-x^*)^2 +\frac{1}{2\alpha} \cdot 2(x_k - x_{k+1})(x_i-x^*)-\frac{1}{2\alpha}(x_i-x_{i+1})^2 \\ =f(x^*) + \frac{1}{2\alpha}(x_i-x^*)^2-\frac{1}{2\alpha}(x_n-x^*-x_n+x_{n+1})^2 \\ = f(x^*) + \frac{1}{2\alpha}(x_n-x^*)^2 -\frac{1}{2\alpha}(x_{n+1}-x^*)^2$ . 

Then we can further conclude tht $f(x_{k+1}) -f(x^*) \leqslant \frac{1}{2\alpha}((x_k-x^*)^2-(x_{k+1}-x^*))^2$. 
Take summation on both sides: $\sum \limits^n \limits_{k = 1} (f(x_k)-f(x^*)) \\ \leqslant \frac{1}{2\alpha} \sum \limits^n \limits_{k = 1}((x_{k-1}-x^*)^2-(x_{k}-x^*))^2 \\ = \frac{1}{2\alpha}((x_0-x^*)^2 -(x_n-x^*)^2) \\ \leqslant \frac{1}{2\alpha}(x_0-x^*)^2$.

Since we have proved that $f(x^*) \leqslant f(x_n) \leqslant f(x_{n-1}) \leqslant f(x_{n-2}) \leqslant \cdots \leqslant f(x_2) \leqslant f(x_1) \leqslant f(x_0)$, then $nf(x_n) \leqslant \sum \limits^n \limits_{k = 1}f(x_k)$.  Then $n(f(x_n)-f(x^*)) \leqslant \sum \limits^n \limits_{k = 1}(f(x_k) - f(x^*))$.

Combine these two facts, we have $n(f(x_n)-f(x^*)) \leqslant \sum \limits^n \limits_{k = 1}(f(x_k) - f(x^*)) \leqslant \frac{1}{2\alpha}(x_0-x^*)^2$. 
Divide two sides by $n$, we derive: $(f(x_n)-f(x^*)) \leqslant \frac{(x_0-x^*)^2}{2n\alpha}$. 

Then $\lim \limits_{n \rightarrow \infty} (f(x_n) -f(x^*)) \leqslant \lim \limits_{n \rightarrow \infty} \frac{(x_0-x^*)^2}{2n\alpha} =0$.

Since $f(x_n) -f(x^*) \geqslant 0$. We have $\lim \limits_{n \rightarrow \infty} (f(x_n) -f(x^*)) = 0$. That is $\lim \limits_{n \rightarrow\infty} f(x_n) = f(x^*) $. If you refer to the algorithm, it is easily observed that $x_n = GD(n)$. Therefore, we have proved that $\lim \limits_{n \rightarrow\infty} f(GD(n)) = f(x^*) $. However, we are not yet finished.


If $f$ is strongly convex on $[x^*,x_0]$, then we know that $f(x) < f(x^*)+f'(x)(x-x^*) $ where we can get $f'(x) > 0$ if $x \in  (x^*,x_0]$, which means that $f$ is monotonically increasing on $[x^*,x_0]$. Then if  $f(x) = f(y)$, we would have $x = y$ if $x,y \in [x^*,x_0]$. 

Suppose the set of points such that $f(x) = f(x^*)$ is $x \in A$. Since $f(x^*) = f(\lim \limits_{n \rightarrow\infty}x_n)$. Then $\lim \limits_{n \rightarrow\infty}x_n \in A$. This is because we have include all points such that $f(x) = f(x^*)$ in $A$ ($A$ is optimal set), if you want $f(\lim \limits_{n \rightarrow\infty}x_n)$ to be equal to $f(x^*)$, then $\lim \limits_{n \rightarrow\infty}x_n $ must be one element in $A$, which means that $\lim \limits_{n \rightarrow\infty}x_n $ must be an optimal solution. Although it may not be exactly $x^*$, it should be another optimal point.

# Example 1
(P) Minimize $x^2$
Subject to $x \in \mathbb{R}$

Find a solution $x$ with 0 relative deviation $(RD(P,x)) = 0$.

Solution: Randomly select $x_0 = 1$, and we know that $f'(x) = 2$ and we select $\alpha = 0.01$. (We know that there exists $L = 100$ such that $\left|f'(x) - f'(y)\right| \leqslant L|x-y| \quad \forall x,y \in [x^*,x_0]$). Therefore, since $0 < \alpha \leqslant \frac{1}{L}$, and by verifying other condition one by one, we can make sure that $\lim \limits_{n \rightarrow\infty}GD(n)$ can converge to an optimal point. Therefore, $RD(P,\lim \limits_{n \rightarrow\infty}GD(n)) = 0$, where $GD(n)$ is the following acknowlegded function:
<div style="background-color: #f2f2f2; padding: 10px;">

**GD**

**Input:** $n$ 

$x_0 = 1$
for $k = 1: n$  
$\quad x_k = x_{k-1} - 2\alpha x_{k-1}$

**Output**: $x_n$   
</div>
