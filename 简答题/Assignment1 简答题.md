# Problem1

(a) 整体模型变得复杂，容易发生过拟合，受个例影响，结果波动较大

(b) 整体的模型变得简单，学习的近似误差会增大，可能导致分类模糊

(c) 因为至少有两个类别的vote相同，导致无法分类

(d)交叉验证

# Problem2

训练O(1)

预测O(N)

# Problem3

(a)NT

(b)B

训练集越大，需要计算的dists矩阵就越大，分类耗费的时间也会越多

# Problem4

可能会该改变损失函数的值。

因为如果当Sj - Syi < -1时，发生微小的改变是不会影响的，反之，则会改变。

# Problem5

最小值：0  当分类正确的概率为1时

最大值正无穷  当正确分类的概率为0时

# Problem6

不一定 

SVM 分类器的决策边界改变与margin有关，与数据量无关

# Problem7

符号可能会改变

在反向传播的时候是利用链式法则，假设上游梯度为a，经过sigmoid激活函数，dσ(x)/dx=(1-σ(x))σ(x)，而σ(x)可能是大于1的，那么dσ(x)/dx<0，故同a相乘，符号发生了改变

# Problem8

![image-20211005171934584](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\image-20211005171934584.png)

