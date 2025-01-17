# 为什么使用 k 折交叉验证？

> 原文：[`www.kdnuggets.com/2022/07/kfold-cross-validation.html`](https://www.kdnuggets.com/2022/07/kfold-cross-validation.html)

![为什么使用 k 折交叉验证？](img/aacfb45cb2f16b61d7002d768975c272.png)

编辑提供的图片

泛化是一个在机器学习讨论中经常出现的术语。它指的是模型适应新数据的能力以及如何有效地使用各种输入。可以理解的是，如果将新的未见数据输入模型中，只要这些未见数据与训练数据具有类似的特征，模型会表现良好。

* * *

## 我们的前三个课程推荐

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 1\. [谷歌网络安全证书](https://www.kdnuggets.com/google-cybersecurity) - 快速进入网络安全职业生涯。

![](img/e225c49c3c91745821c8c0368bf04711.png) 2\. [谷歌数据分析专业证书](https://www.kdnuggets.com/google-data-analytics) - 提升你的数据分析能力

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 3\. [谷歌 IT 支持专业证书](https://www.kdnuggets.com/google-itsupport) - 支持你的组织 IT 部门

* * *

对我们人类来说，泛化是容易的，但对机器学习模型来说可能具有挑战性。这就是交叉验证发挥作用的地方。

# 交叉验证

你可能会看到交叉验证也被称为轮换估计和/或样本外测试。交叉验证的总体目标是将其作为工具来评估机器学习模型，通过在不同的输入数据子集上训练多个模型。

交叉验证可以用来检测模型的过拟合，这意味着模型在新输入数据中无法有效地泛化模式和相似性。

## 一个典型的交叉验证工作流程

为了执行交叉验证，通常采取以下步骤：

1.  将数据集拆分为训练数据和测试数据

1.  参数将经过交叉验证测试，以确定哪些参数是最佳选择。

1.  这些参数将被应用到模型中以进行重新训练

1.  最终评估将会发生，这将取决于是否需要再次进行周期，这取决于模型的准确性和泛化水平。

有不同类型的交叉验证技术

+   保留法

+   K 折

+   留一法

+   留出法

然而，我们将特别关注 K 折。

# K 折交叉验证

K 折交叉验证是指将数据集拆分为 K 个折，并用来评估模型在面对新数据时的能力。K 表示数据样本被拆分成的组数。例如，如果看到 k 值为 5，我们可以称之为 5 折交叉验证。在过程中，每个折在某一时刻被用作测试集。

## K 折交叉验证过程：

1.  选择你的 k 值

1.  将数据集拆分为 k 折。

1.  从使用你的 k-1 折作为测试数据集和其余折作为训练数据集开始

1.  在训练数据集上训练模型，并在测试数据集上验证模型

1.  保存验证分数

1.  重复步骤 3 到 5，但改变你的 k 测试数据集的值。比如我们在第一轮选择 k-1 作为测试数据集，接着在下一轮选择 k-2 作为测试数据集。

1.  到最后，你将会在每一个折上验证模型。

1.  对第 5 步中产生的结果进行平均，以总结模型的技能。

你可以使用 sklearn.model_selection.KFold 轻松实现这一点

```py
import numpy as np
from sklearn.model_selection import KFold

X = np.array([[1, 2], [3, 4], [1, 2], [3, 4]])
y = np.array([1, 2, 3, 4])
kf = KFold(n_splits=2)

for train_index, test_index in kf.split(X):
  print("TRAIN:", train_index, "TEST:", test_index)
  X_train, X_test = X[train_index], X[test_index]
  y_train, y_test = y[train_index], y[test_index]
```

# 为什么我应该使用 K 折交叉验证？

我将分解为什么你应该使用 K 折交叉验证的原因

## 利用你的数据

我们有很多现成的数据，可以解释很多事情并帮助我们识别隐藏的模式。然而，如果我们只有一个小数据集，将其分成 80:20 的训练和测试数据集似乎对我们帮助不大。

然而，当使用 K 折交叉验证时，数据的所有部分都可以作为测试数据的一部分使用。这样，我们小数据集中的所有数据都可以用于训练和测试，从而更好地评估模型的性能。

## 更多可用的指标来帮助评估

让我们回到将数据集拆分为 80:20 比例的训练和测试的例子——这只提供一个结果用于评估模型。我们不能确定这个结果的准确性，是由于偶然、偏差程度，还是它确实表现良好。

然而，当使用 k 折交叉验证时，我们有更多的模型会产生更多的结果。例如，如果我们选择 k 值为 10，我们将有 10 个结果用于评估模型的性能。

如果我们使用准确率作为衡量标准；拥有 10 个不同的准确率结果，其中所有数据都用于测试阶段，总是比使用一个由训练-测试拆分产生的准确率结果更好，更可靠——因为不是所有数据都在测试阶段使用过。

如果准确率输出为 94.0、92.8、93.0、97.0 和 94.5 在 5 折交叉验证中，那么相比于训练-测试拆分中 93.0 的准确率，你会对模型的性能有更多的信任和信心。这向我们证明了我们的算法在泛化和积极学习，并提供了一致可靠的输出。

## 使用相关数据获得更好的性能

在随机训练-测试划分中，我们假设数据输入是独立的。让我们进一步扩展这个问题。假设我们在一个语音识别数据集中使用随机训练-测试划分，这些讲者都是来自伦敦的英国英语讲者。共有 5 位讲者，每位讲者有 250 个录音。模型进行随机训练-测试划分后，训练集和测试集都会来自同一位讲者，并且这些录音会说相同的对话。

是的，这确实提高了准确性并增强了算法的性能，但是，当引入新讲者时，模型的表现如何？那时模型的表现怎么样？

使用 K 折交叉验证将允许你训练 5 个不同的模型，每个模型使用一个讲者作为测试数据集，其余的作为训练数据集。通过这种方式，我们不仅可以评估模型的性能，还可以使模型在新讲者上的表现更好，并且可以部署到生产中，为其他任务提供类似的性能。

# 为什么 10 是一个如此理想的 k 值？

选择合适的 k 值很重要，因为它会影响你的准确性、方差、偏差，并可能导致对模型整体性能的误解。

选择 k 值的最简单方法是将其等同于你的‘n’值，也称为留一法交叉验证。n 代表数据集的大小，这样每个测试样本都有机会作为测试数据或保留数据使用。

然而，通过数据科学家、机器学习工程师和研究人员的各种实验，他们发现选择 k 值为 10 能够提供较低的偏差和适中的方差。

Kuhn & Johnson 在他们的书籍 [应用预测建模](https://link.springer.com/book/10.1007/978-1-4614-6849-3) 中讨论了他们选择 k 值的方法。

*“k 的选择通常是 5 或 10，但没有正式的规则。随着 k 值的增大，训练集和重采样子集之间的大小差异会变小。随着这种差异的减少，该技术的偏差也会变小（即 k=10 时的偏差比 k=5 时小）。在这种情况下，偏差是估计值与实际性能值之间的差异”*

让我们用一个例子来说明这个背景：

假设我们有一个数据集，其中 N = 100

+   如果我们选择 k 值 = 2，我们的子集大小 = 50，差异 = 50

+   如果我们选择 k 值 = 4，我们的子集大小 = 75，差异 = 25

+   如果我们选择 k 值 = 10，我们的子集大小 = 90，差异 = 10

因此，随着 k 值的增加，原始数据集与交叉验证子集之间的差异变得更小。

还指出，选择 k=10 在计算上更为高效，因为 k 值越大，计算上的可行性越差。小值也被认为在计算上高效，但它们可能会导致较高的偏差。

# 结论

交叉验证是每个数据科学家都应该使用或至少非常熟练的一个重要工具。它可以让你更好地利用所有数据，同时为数据科学家、机器学习工程师和研究人员提供对算法性能的更好理解。

对模型有信心对于未来的部署和信任模型的有效性和表现至关重要。

**[Nisha Arya](https://www.linkedin.com/in/nisha-arya-ahmed/)** 是一名数据科学家和自由技术作家。她特别关注提供数据科学职业建议或教程以及围绕数据科学的理论知识。她还希望探索人工智能如何/可以促进人类寿命的延续。她是一个热衷学习的人，寻求拓宽她的技术知识和写作技能，同时帮助指导他人。

### 更多相关主题

+   [使用 Pandera 进行 PySpark 应用程序的数据验证](https://www.kdnuggets.com/2023/08/data-validation-pyspark-applications-pandera.html)

+   [Pydantic 教程：简化 Python 中的数据验证](https://www.kdnuggets.com/pydantic-tutorial-data-validation-in-python-made-simple)

+   [MarshMallow：最甜蜜的 Python 数据序列化库](https://www.kdnuggets.com/marshmallow-the-sweetest-python-library-for-data-serialization-and-validation)

+   [为什么最新的 LLMs 使用 MoE（专家混合）架构](https://www.kdnuggets.com/why-the-newest-llms-use-a-moe-mixture-of-experts-architecture)

+   [你应该使用线性回归模型而不是…的 3 个原因](https://www.kdnuggets.com/2021/08/3-reasons-linear-regression-instead-neural-networks.html)

+   [你不应该使用机器学习的 4 个理由](https://www.kdnuggets.com/2021/12/4-reasons-shouldnt-machine-learning.html)
