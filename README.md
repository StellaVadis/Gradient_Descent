# Gradient Descent Method
这个算法很关键

#Task Formation

$$ \\

\begin{align}
\text{Minimize} & \quad f(\boldsymbol{x})  \\
\text{Subject to} &\quad 
    \boldsymbol{x} \in \text{dom}(f) 
\end{align}

$$ \\

where $\boldsymbol{x} \in \mathbb{R}^n$

# Algorithm and Solution
The solution given by gradient descent method is:
$\lim \limits_{n \rightarrow \infty}$ GD $(n)$, where GD $(n)$ is the following acknowlegded function:

<div style="background-color: #f2f2f2; padding: 10px;">

**GD**

**Input:** $n$ 

$x_0 = 0$
for $k = 1: n$  
$\quad x_k = x_{k-1} - \alpha \cdot \nabla{f}(x_{k-1})$

**Output**: $x_n$   
</div>

#Convergence in 1-dimensional Space
