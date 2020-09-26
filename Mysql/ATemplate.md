# 参考文献
https://www.jianshu.com/p/fd761fc43753


- **简介**
  > - 大意
  >> -  内容


- **实例**

```sql
SELECT 
  a.`store_name`,
  b.product_name,
  IFNULL(c.revenue, 0) AS revenue 
FROM
  stores a 
  CROSS JOIN  products b 
  LEFT JOIN 
    (SELECT 
      sto.`id` AS store_id,
      pro.`id` AS product_id,
      sto.`store_name`,
      pro.`product_name`,
      SUM(quantity * price) AS revenue 
    FROM
      sales sal
      INNER JOIN stores sto 
        ON sto.`id` = sal.`store_id` 
      INNER JOIN products pro 
        ON sal.`product_id` = pro.`id` 
    GROUP BY sto.`store_name`,
      pro.`product_name`) c 
  ON a.id = c.store_id 
  AND b.id = c.product_id 
ORDER BY a.store_name ;
```

- [ ] **准备工作**
  -  [x] 完成
  -  [ ] 未完成


## 表格
| hello | world |
| -------- | -----: |
|  11    | 22 |

<table>
    <tr>
        <th rowspan="2">值班人员</th>
        <th>星期一</th>
        <th>星期二</th>
       <th>星期三</th>
    </tr>
    <tr>
        <td>李强</td>
        <td>张明</td>
        <td>王平</td>
    </tr>
</table>

$$\Biggl(\biggl(\Bigl(\bigl((x)\bigr)\Bigr)\biggr)\Biggr) gives (((((x)))))$$

$$ \mathsf{ABCDEFGHIJKLMNOPQRSTUVWXYZ}   $$
$$ \mathcal{ABCDEFGHIJKLMNOPQRSTUVWXYZ}  $$
$$ \mathscr{ABCDEFGHIJKLMNOPQRSTUVWXYZ}  $$
$$ \mathfrak{ABCDEFGHIJKLMNOPQRSTUVWXYZ} $$

$x_i^2$，$x_i^2+x_{i^2}$，$10^{10}$
$\log_2 x$
${x^y}^z+x^{y^z}$
$\sum^{j-1}_{k=0}{\widehat{\gamma}_{kj} z_k}$
$\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$
$f(x_1,x_x,\ldots,x_n) = x_1^2 + x_2^2 + \cdots + x_n^2 $
$\displaystyle \lim_{t \to 0} \int_t^1 f(t)\, dt$
$\lim_{t \to 0} \int_t^1 f(t)\, dt$.

$$(\frac{\sqrt x}{y^3})$$
$$ \left(\frac{\sqrt x}{y^3}\right)$$

$
    \begin{matrix}
    1 & x & x^2 \\
    1 & y & y^2 \\
    1 & z & z^2 \\
    \end{matrix}
$ , $
    \begin{pmatrix} 
    1 & 2 \\
    1 & 2 \\
    \end{pmatrix}
$ , $   
    \begin{bmatrix} 
    1 & 2 \\
    1 & 2 \\
    \end{bmatrix}
$ , $
    \begin{Bmatrix} 
    1 & 2 \\
    1 & 2 \\
    \end{Bmatrix} 
$ , $
    \begin{vmatrix} 
    1 & 2 \\
    1 & 2 \\
    \end{vmatrix} 
$ , $
    \begin{Vmatrix} 
    1 & 2 \\
    1 & 2 \\
    \end{Vmatrix} 
$




$$
    \begin{matrix}
    a_{11} & a_{12} & a_{13} & \cdots & a_{1n} \\
    a_{21} & a_{22} & a_{23} & \cdots & a_{2n} \\
    \vdots & \vdots & \vdots & \ddots & \vdots \\
    a_{n1} & a_{n2} & a_{n3} & \cdots & a_{2n} \\
    \end{matrix}
$$

$$ \left[
\begin{array}{cc|c}
  1&2&3\\
  4&5&6
\end{array}
\right] 
$$


$$
  f(n) =
\begin{cases}
n/2,  & \text{if $n$ is even} \\
3n+1, & \text{if $n$ is odd}
\end{cases}
$$


$$
\left.
\begin{array}{l}
\text{if $n$ is even:}&n/2\\
\text{if $n$ is odd:}&3n+1
\end{array}
\right\}
=f(n)
$$

$$\begin{cases}
a_1x+b_1y+c_1z=d_1 \\[2ex] 
a_2x+b_2y+c_2z=d_2 \\[2ex] 
a_3x+b_3y+c_3z=d_3
\end{cases}
$$

$\color{black}{blackText}$，$\color{gray}{grayText}$
$\color{silver}{silverText}$，$\color{white}{whiteText}$

$\color{maroon}{maroonText}$，$\color{red}{redText}$
$\color{yellow}{yellowText}$，$\color{green}{greenText}$
$\color{teal}{tealText}$，$\color{aqua}{aquaText}$
$\color{blue}{blueText}$，$\color{navy}{navyText}$
$\color{purple}{purpleText}$，$\color{fuchsia}{fuchsiaText}$

$\color{red}{CROSS JOIN}$ 