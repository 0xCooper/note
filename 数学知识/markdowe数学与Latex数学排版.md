**关系符**

=，>，<，直接输入 

不等号≠ \ne

大于等于号 ≥ \ge

小于等于号 ≤ \le

约等号 ≈ \approx

等价 ≡ \equiv

**算符**

加减乘除 +、−、∗、/ 可直接输入

乘号 × \times

除号 ÷ \div

点乘 · \cdot

加减号 ± \pm / ∓ \mp

三角函数：

\sin 

\cos

\tan

\cot

积分号 ∫(\int)

求和号 ∑ (\sum)
**箭头**：常用的箭头包括→ (\rightarrow 或 \to）、← （\leftarrow 或 \gets）。

LaTeX 提供了多种括号和定界符表示公式块的边界，如小括号 ()、中括号 []、大括号 {} (\{\})、尖括号 ⟨⟩ (\langle \rangle)、上括号(\overbrace)、下括号(\underbrace)等。



![](https://gitee.com/muyinchuan/images/raw/master/img/20200626010241.png)



![](https://gitee.com/muyinchuan/images/raw/master/img/20200626011700.png)





```
$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} 
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
${$tep1}{\style{visibility:hidden}{(x+1)(x+1)}}
$$ 以下是显示结果
```

$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} 
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
${$tep1}{\style{visibility:hidden}{(x+1)(x+1)}}
$$

```
​```mermaid
graph LR
A[方形] -->B(圆角)
    B --> C{条件a}
    C -->|a=1| D[结果1]
    C -->|a=2| E[结果2]
    F[横向流程图]
​```
竖向流程图
​```mermaid
graph TD
A[方形] --> B(圆角)
    B -- C{条件a}
    C --> |a=1| D[结果1]
    C --> |a=2| E[结果2]
    F[竖向流程图]
​```
```

```mermaid
graph LR
A[方形] -->B(圆角)
A -->T[YU]

    B --> C{条件a}
    C -->|a=1| D[结果1]
    C -->|a=2| E[结果2]
    C -->|a=3|G[结果三]
    F[横向流程图]
   
A1[方形] --> B1(圆角)
    B1 --> C1{条件a}
    C1 --> |a=1| D1[结果1]
    C1 --> |a=2| E1[结果2]
    F1[竖向流程图]
```



```
​```mermaid
%% 语法示例
        gantt
        dateFormat  YYYY-MM-DD
        title 软件开发甘特图
        section 设计
        需求                      :done,    des1, 2014-01-06,2014-01-08
        原型                      :active,  des2, 2014-01-09, 3d
        UI设计                     :         des3, after des2, 5d
    未来任务                     :         des4, after des3, 5d
        section 开发
        学习准备理解需求                      :crit, done, 2014-01-06,24h
        设计框架                             :crit, done, after des2, 2d
        开发                                 :crit, active, 3d
        未来任务                              :crit, 5d
        耍                                   :2d
        section 测试
        功能测试                              :active, a1, after des3, 3d
        压力测试                               :after a1  , 20h
        测试报告                               : 48h
​```
```

```mermaid
%% 语法示例
        gantt
        dateFormat  YYYY-MM-DD
        title 软件开发甘特图
        section 设计
        需求                      :done,    des1, 2014-01-06,2014-01-08
        原型                      :active,  des2, 2014-01-09, 3d
        UI设计                     :         des3, after des2, 5d
    未来任务                     :         des4, after des3, 5d
        section 开发
        学习准备理解需求                      :crit, done, 2014-01-06,24h
        设计框架                             :crit, done, after des2, 2d
        开发                                 :crit, active, 3d
        未来任务                              :crit, 5d
        耍                                   :2d
        section 测试
        功能测试                              :active, a1, after des3, 3d
        压力测试                               :after a1  , 20h
        测试报告                               : 48h
```

```
​```flow
st=>start: 开始框
op=>operation: 处理框
cond=>condition: 判断框(是或否?)
sub1=>subroutine: 子流程
io=>inputoutput: 输入输出框
e=>end: 结束框
st(right)->op(right)->cond
cond(yes)->io(bottom)->e
cond(no)->sub1(right)->op
​```
```

```flow
st=>start: 开始框
op=>operation: 处理框
cond=>condition: 判断框(是或否?)
sub1=>subroutine: 子流程
io=>inputoutput: 输入输出框
e=>end: 结束框
st(right)->op(right)->cond
cond(yes)->io(bottom)->e
cond(no)->sub1(right)->op
```