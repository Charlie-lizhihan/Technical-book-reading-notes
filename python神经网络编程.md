如果一个简单的线性分类器不能对数据进行划分，我们就需要使用多个线性分类器来划分数据；使用多个分类器一起工作，这是**神经网络的核心思想**。

神经元不会立刻有输入就产生反应，而是会抑制输出，知道输入增强，强大到可以触发输出，一般我们会用sigmod函数来模拟阶跃函数。



输入到下一层结果矩阵中的信号，可以表示为X = W·I，W表示权值矩阵，I表示输入矩阵。这样一来，第二层的最终输出就称为O = sigmod（X） 

![image-20210315221112381](/Users/lizhihan/Library/Application Support/typora-user-images/image-20210315221112381.png)

![image-20210315221135155](/Users/lizhihan/Library/Application Support/typora-user-images/image-20210315221135155.png)





神经网络通过调整链接权重进行学习，这种方法由误差引导。

内部节点相关联的误差：一种方法是按照链接权重的比例来分割输出层的误差，然后在每个内部节点处重组这些误差。（反向传播误差）

反向传播误差和前向馈送信号都可以使用矩阵实现。

梯度下降法是求解函数最小值的一种很好的办法，函数有很多参数的时候，这种方法仍然可以使用。



两个很常见的问题是饱和和零值权重：大信号（可能由大权重导致）导致了应用在信号上的激活函数的斜率变得非常平缓，这会降低神经网络学习到更好权重的能力；零权值的问题可能导致网络丧失学习更好权重的能力。



输入应该调整到较小值（参考sigmod函数的近0点），但不能为0；输出应该在激活函数能生成的值的范围内。

