### 怎么从图像里提取需要的内容

1.1997 IMB开发了深蓝，已经战胜了象棋人类冠军

2.2016ALphgo 围棋干掉李世石 柯洁  强化学习与深度学习结合 +GPU运算能力+数据

3.用循环神经网络去产生诗歌体，没有灵魂

只是有限搜索

#### 什么是计算机视觉：对摄像头采集的数据的理解

#### 目标：

机器看到数据矩阵，跨越“语义鸿沟”：300×400 灰度0-255 有12万个数据点byte，从中得到结论

物种大繁荣，因为视觉系统的出现

有些简单的细胞对线的方向比较敏感，复杂一点的知道变化，端点，处理信息分层

运动视盲：板子经过，演员替换，对主体关注，对其他东西不太关注   找茬

高效与代价之间的关系

Larry Roberts 研究CV第一人 Apach网 互联网之父

David Marr

两个矩阵100×100相加，在gpu的指令里是一次加法，cpu的指令集是10000次加法

视觉表达的3阶段：边缘、有语义概念的形体2.5D，通过形体去推测3D

图像中包含三维场景的结构信息、语义信息

知道了关键点三维点的运动，也就知道了面部肌肉的运动

城市三维重建 ，就用无人机    扫地机器人

##### 目标检测：

知道在哪个地方，圈出来

##### 分割：

哪些像素属于猫



### 图像分类任务：

难点：视角、光照、尺度、遮挡、形变、背景杂波、类内形变、运动模糊（一个像素同时记录了鸟的多个位置信息）掌握了运算规律，那么就可以把它反向恢复出来、类别繁多

基于规则的分类方法是否可行：通过硬编码方法识别猫是很困难的

数据驱动的图像分类范式：机器学习的方法

##### 	1.数据集构建

##### 	2.分类器设计与学习

##### 图像表示：

像素展示、全局特征表示（风景）、局部特征表示（特征+词带模型，要考虑遮挡）

将图像的所有特征送进系统不好，图像像素太多了，所以特征抽取很重要

而神经网络不在乎特征提取，将特征提取和分类集成在一起

##### 分类模型

##### 损失函数

##### 优化算法

训练过程：数据集划分 数据预处理 数据增强（样本不够，旋转把样本增多，让分类器可以从各个角度去看数据集的内容） 欠拟合与过拟合：减小算法复杂度、使用权重正则项、使用dropout正则化  超参数调整  模型集成

##### 	3.分类器决策

分类平均指标：正确率  Top1指标、Top5指标（imagenet)



# 线性分类器

#### 图像类型：

1.二进制：非黑即白，没有灰，要么是0要么是1，二维矩阵

2.灰度图像，一个像素由一个byte表示，取值范围0-255，二维矩阵，最黑是0

3.彩色图像，每个点3个值rgb,用3个byte，每一个byte也是0-255，500×500×3（深度），有3个深度

#### 图像表示：

大多数分类算法都要求输入向量，直接将矩阵转为向量

是神经网络（大样本）、SVM（小样本）的基础

#### 线性分类器的定义

矩阵表示

权值向量

决策边界

W,b的度量

#### 损失函数：

定义：搭建模型性能（损失值就是模型性能的描述）与模型参数的桥梁

多类支撑向量机损失：



### 全连接神经网络：

多个变化实现输入到输出的映射

f=W2max(0,W1x+b1)+b2

w1行数可以指定

w2行数定，因为最后输出类别的个数



激活函数sigmoid，tanh(x)函数容易造成梯度消失，没法解决  现在都不用了 除非是作为输出层（希望位于0-1、-1-1之间）

ReLU激活函数，有利于梯度流的传输->leaky ReLU函数，基本没有“死区”，尽量选择这两个，训练过程收敛得更快

梯度爆炸，局部点的梯度太大，所有限制步长，大于这个梯度之后只能走这么长，梯度裁剪



# 梯度下降法存在的问题

损失函数特性：一个方向变化迅速但在另一个方向变化缓慢

会在山壁间振荡，往谷低的方向行进较慢。

### 动量法：

真的就是动量的时间累加

鞍点：梯度为0，但是一个上，一个下

不太好的局部最小值点

梯度下降会停在这里，但是动量法仍然会往前走

### 自适应梯度与RMSProp

不同方向学习率不同，不能增大一个总步长

减小振荡方向步长，增大平坦方向步长

区分震荡方向和平坦方向：

梯度幅度的平方较大的方向是震荡方向，否则为平坦方向

#但是当累加时间过长的时候，会非常大，分母，从而失去调节意义

### ADAM

同时使用动量和自适应梯度思想

一般直接用SGD+动量（调优越好，炼丹）、ADAM

一般先是ADAM初始学习，搞不定了再用SGD+动量手动调

# 训练过程

### 权值初始化

调整权值分布使得输入和输出的分布相同

随机初始化 不行

Xavier初始化  N(0,1/N)  sigmoid/tanh

HE初始化

N(0,2/N) ReLu

### 批归一化

直接对神经元的输出进行批归一化

BN在FC和tanh之间

根据对分类的贡献自行决定数据分布的均值和方差











