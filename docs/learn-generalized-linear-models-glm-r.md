# 使用R学习广义线性模型（GLM）

> 原文：[https://www.kdnuggets.com/2017/10/learn-generalized-linear-models-glm-r.html/2](https://www.kdnuggets.com/2017/10/learn-generalized-linear-models-glm-r.html/2)

**解释对数变换**

对依赖数据和独立数据进行对数变换是一种处理非线性关系的简单方法。这种变换有助于使用线性模型分析非线性关系。我们已经讨论了对数线性回归。还有两个变体 – a) 线性–对数回归 –独立变量进行对数变换，b) 对数–对数回归 –依赖变量和独立变量都进行变换。下表显示了每个模型的方程和解释。

* * *

## 我们的前3个课程推荐

![](../Images/0244c01ba9267c002ef39d4907e0b8fb.png) 1\. [Google 网络安全证书](https://www.kdnuggets.com/google-cybersecurity) - 快速进入网络安全职业生涯

![](../Images/e225c49c3c91745821c8c0368bf04711.png) 2\. [Google 数据分析专业证书](https://www.kdnuggets.com/google-data-analytics) - 提升你的数据分析能力

![](../Images/0244c01ba9267c002ef39d4907e0b8fb.png) 3\. [Google IT 支持专业证书](https://www.kdnuggets.com/google-itsupport) - 支持你的组织的IT需求

* * *

**表2 二项逻辑回归的样本数据**

![Table](../Images/a824f7f69cdc1f6132530940e1f2eb3f.png)

**二项逻辑回归**

当依赖变量是类别型且取值为0和1时，使用二项逻辑回归。与简单线性回归中依赖变量的条件分布为正态分布不同，逻辑回归中的条件分布为伯努利分布。在伯努利分布中，变量只能取两个值 – 0和1，具有一定的概率。

让我们通过一个例子来理解。假设在足球中，将罚球转换为进球的能力取决于射门者的练习小时数。我们可以用1表示成功罚球，用0表示未成功罚球。数据如下：

**表2 二项逻辑回归的样本数据**

![Table](../Images/ff0bddbd88d153781271c2176e3dd98b.png)

二项逻辑回归模型将根据练习小时数输出成功罚球的概率。逻辑回归使用逻辑函数来建模关系。逻辑函数允许将关系建模为概率，因为它的值在0和1之间。其表示如下：

![Eq 4](../Images/2a366fcf4d16d39458ba822795bc1972.png) [4]

β1 的正值（负值）表示当 X 增加时 Y=1 的概率增加（减少）。逻辑回归是广泛使用的类别预测模型之一。多项式逻辑回归将二分类模型扩展到处理涉及多个类别的问题。例如，一个人是否会兑换优惠券 A、优惠券 B 或优惠券 C。现在我们将在 R 中实现逻辑回归模型。样本数据包括两个变量——点球成功/失败表示为 1/0 和练习小时。请点击这里下载。R 代码如下：

```py
## Prepare scatter plot

#Read data from .csv file
data1 = read.csv("Penalty.csv", header = T)
head(data1)

#Scatter Plot
plot(data1, main = "Scatter Plot")
```

**图 4 类别数据的散点图**

![Figure](../Images/6a188c41c7d4dcda490ac3fcea1aac46.png)

我们可以观察到，因变量仅能取两个值——1和0。当练习时间增加时，玩家的效率也提高。现在我们将使用逻辑回归准备一个模型来预测基于练习时间的成功或失败的概率。R 代码如下：

```py
## Fitting Logistic regression model
fit = glm(Outcome ~ Practice, family = binomial(link = "logit"), data = data1)

#Plot probabilities
plot(data1, main ="Scatter Plot")
curve(predict(fit,data.frame(Practice = x), type = "resp"), add = TRUE) 
points(data1$Practice,fitted(fit),pch=20)
```

图 5 显示了从逻辑回归中获得的概率值。我们可以看到模型表现良好。随着练习时间的增加，成功的概率也增加。该模型在方程 [5] 中表示。可以通过插入练习小时数来获得概率值。

![Eq 5](../Images/0a1dd998bc3bd35b7f68b529a54afe99.png) [5]

**图 5 使用逻辑回归的概率图**

![Figure](../Images/f4a7b44e088729746b519fd1f1dcf8b4.png)

**结论**

在这篇文章中，我们学习了广义线性模型（GLM）。简单线性回归是 GLM 的最基本形式。GLM 的高级形式有助于以简单的方式处理非正态分布和非线性关系。我们重点介绍了对数线性回归和二元逻辑回归。当因变量与自变量之间的关系是非线性时，对数线性回归非常有用。当因变量遵循对数正态分布或泊松分布时，它也提供了快速的解决方案。

此外，我们讨论了二元逻辑回归的基本概念。当因变量遵循伯努利分布，即只能取 0 和 1 的值时，二元逻辑回归非常有用。我们还提供了各种对数变换的方程和解释，这些变换与回归模型一起使用。

除了理论解释，我们还分享了 R 代码，以便你可以在 R 中实现该模型。为了更好地理解，我们展示了结果和代码。

我们希望你觉得这篇文章有用。

**[本文中使用的完整代码请点击这里](https://gist.githubusercontent.com/mmmayo13/c8ccb00bf092f654b71a5d6ca7106c1f/raw/2f0a26a1a199f52e7e04cb68a569d8d8f9f9ba3f/glm-r-example.r)**。

**个人简介: [Chaitanya Sagar](https://www.linkedin.com/in/chaitanyasagar/)** 是 [Perceptive Analytics](http://www.perceptive-analytics.com/) 的创始人兼首席执行官。Perceptive Analytics 被《Analytics India Magazine》评选为值得关注的十大分析公司之一。该公司致力于为电子商务、零售和制药公司提供市场分析服务。

**相关内容:**

+   [R 和 dplyr 的下一代数据操作](/2017/08/next-generation-data-manipulation-dplyr.html)

+   [缺失数据的解决方案：使用 R 进行插补](/2017/09/missing-data-imputation-using-r.html)

+   [Python 与 R – 谁在数据科学和机器学习领域真正领先?](/2017/09/python-vs-r-data-science-machine-learning.html)

### 相关主题

+   [广义和可扩展的最优稀疏决策树 (GOSDT)](https://www.kdnuggets.com/2023/02/generalized-scalable-optimal-sparse-decision-treesgosdt.html)

+   [你应该使用线性回归模型而不是…的3个理由](https://www.kdnuggets.com/2021/08/3-reasons-linear-regression-instead-neural-networks.html)

+   [学习机器学习的线性代数的3个免费资源](https://www.kdnuggets.com/2022/03/top-3-free-resources-learn-linear-algebra-machine-learning.html)

+   [了解大型语言模型](https://www.kdnuggets.com/2023/03/learn-large-language-models.html)

+   [比较线性回归与逻辑回归](https://www.kdnuggets.com/2022/11/comparing-linear-logistic-regression.html)

+   [线性回归与逻辑回归：简明解释](https://www.kdnuggets.com/2022/03/linear-logistic-regression-succinct-explanation.html)
��在我们将探讨对数线性模型的解释。*log(a)* 是常数项，*log(b)* 是 Y 随 X 单位变化而增长的增长率。*log(b)* 的负值表明 Y 会因为 X 的单位增加而以一定百分比减少。接下来，我们将使用可口可乐销售数据在 R 中实现该模型。R 代码如下。

```py
## Fitting Log-linear model

# Transform the dependent variable
data$LCola = log(data$Cola, base = exp(1))

#Scatter Plot
plot(LCola ~ Temperature, data  = data , main = "Scatter Plot")

#Fit the best line in log-linear model
model1 = lm(LCola ~ Temperature, data)
abline(model1)

#Calculate RMSE
PredCola1 = predict(model1, data)
RMSE = rmse(PredCola1, data$LCola)
```

**图 3 对数线性回归给出的最佳拟合线**

![图 3](../Images/904c64eb887ca12a309765d48c122b41.png)

图 3 显示了使用对数线性回归的最佳拟合线。我们可以将其视为一个两步过程，即对数据进行变换（对两边取对数），然后对变换后的数据进行简单线性回归。计算出的模型如下：

![方程 3](../Images/941ecb922ca885c4364c6b798ac5daab.png) [3]

可乐销售量可以通过将温度值代入方程[3]来预测。我们观察到与简单线性回归相比，拟合效果有了很大改善。变换后的模型的RMSE仅为0.24。请注意，日志线性回归也解决了可乐销售量出现荒谬负值的问题。对于任何温度值，我们都不会得到负的可乐销售量。简单的对数变换帮助我们处理了这种荒谬情况。在下一部分，我们将讨论其他在各种情况下非常有用的对数变换。

* * *

## 我们的三大课程推荐

![](../Images/0244c01ba9267c002ef39d4907e0b8fb.png) 1\. [谷歌网络安全证书](https://www.kdnuggets.com/google-cybersecurity) - 快速进入网络安全职业生涯。

![](../Images/e225c49c3c91745821c8c0368bf04711.png) 2\. [谷歌数据分析专业证书](https://www.kdnuggets.com/google-data-analytics) - 提升你的数据分析能力。

![](../Images/0244c01ba9267c002ef39d4907e0b8fb.png) 3\. [谷歌IT支持专业证书](https://www.kdnuggets.com/google-itsupport) - 支持你的组织IT需求。

* * *

### 更多相关话题

+   [通用和可扩展的最优稀疏决策树(GOSDT)](https://www.kdnuggets.com/2023/02/generalized-scalable-optimal-sparse-decision-treesgosdt.html)

+   [使用线性回归模型的三大理由而不是…](https://www.kdnuggets.com/2021/08/3-reasons-linear-regression-instead-neural-networks.html)

+   [机器学习中学习线性代数的三大免费资源](https://www.kdnuggets.com/2022/03/top-3-free-resources-learn-linear-algebra-machine-learning.html)

+   [了解大语言模型](https://www.kdnuggets.com/2023/03/learn-large-language-models.html)

+   [比较线性回归与逻辑回归](https://www.kdnuggets.com/2022/11/comparing-linear-logistic-regression.html)

+   [线性回归与逻辑回归：简明解释](https://www.kdnuggets.com/2022/03/linear-logistic-regression-succinct-explanation.html)
