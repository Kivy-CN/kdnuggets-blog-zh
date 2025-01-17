# 决策树直觉：从概念到应用

> 原文：[`www.kdnuggets.com/2020/02/decision-tree-intuition.html`](https://www.kdnuggets.com/2020/02/decision-tree-intuition.html)

评论

![](img/2fbcc0528a1f4b47e01961814dfb1c2e.png)

决策树是我学习过的流行且强大的机器学习算法之一。它是一种非参数的监督学习方法，可用于分类和回归任务。其目标是通过学习从数据特征中推断出的简单决策规则来创建一个预测目标变量值的模型。对于分类模型，目标值是离散的，而对于回归模型，目标值是连续的。与神经网络等黑箱算法不同，**决策树**相对更容易理解，因为它共享内部决策逻辑（你将在以下章节中找到详细信息）。

* * *

## 我们的前三个课程推荐

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 1\. [Google 网络安全证书](https://www.kdnuggets.com/google-cybersecurity) - 快速进入网络安全职业生涯。

![](img/e225c49c3c91745821c8c0368bf04711.png) 2\. [Google 数据分析专业证书](https://www.kdnuggets.com/google-data-analytics) - 提升您的数据分析技能

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 3\. [Google IT 支持专业证书](https://www.kdnuggets.com/google-itsupport) - 支持您的组织进行 IT 工作

* * *

尽管许多数据科学家认为这是一种旧方法，并且由于过拟合问题可能对其准确性有所怀疑，但更近期的树模型，例如随机森林（袋装方法）、梯度提升（提升方法）和 XGBoost（提升方法），都是建立在决策树算法之上的。因此，**决策树**背后的概念和算法非常值得理解！

![](img/43782b4091a23968fac7a66a5190701f.png)

有 4 种流行的决策树算法：**ID3**、**CART（分类与回归树）**、**卡方检验**和**方差减少**。

*在这篇博客中，我将只关注分类树以及 ID3 和 CART 的解释。*

![](img/0d9817fea6ecd8c71e50a13cd69f391a.png)

想象一下，你每个星期天打网球，并且每次都邀请你最好的朋友 Clare 一起去。Clare 有时会来，有时不会。对于她来说，这取决于很多因素，例如天气、温度、湿度和风。我想利用下面的数据集来预测 Clare 是否会和我一起打网球。一种直观的方法是通过决策树。

![](img/87d51f688db1932e95e90fcebcc9b8ba.png)

![](img/891149077bc9ab94fff3f171781152ce.png)

在这个**决策树**图中，我们有：

1.  **根节点**：第一次划分决定整个数据集是否应该进一步分为两个或多个同质集合。在我们的例子中是“天气”节点。

1.  **划分**：将一个节点分成两个或多个子节点的过程。

1.  **决策节点**：决定是否/何时将子节点进一步划分为更多子节点的节点。在这里，我们有“天气”节点、“湿度”节点和“风”节点。

1.  **叶节点**：预测结果的终端节点（分类值或连续值）。上色的节点，即“是”和“否”节点，是叶节点。

> *问题：基于哪个属性（特征）进行划分？什么是最佳划分？*
> 
> *回答：使用具有最高**信息增益**或**基尼增益**的属性*

### ID3（迭代二分法）

ID3 决策树算法使用信息增益来决定划分点。为了测量我们获得了多少信息，我们可以使用***熵***来计算样本的同质性。

> *问题：“熵”是什么？它的功能是什么？*

回答：它是数据集中不确定性量的度量。*熵控制决策树如何划分数据。它实际上影响了**决策树**如何绘制边界。*

**熵的公式：**

![](img/4b834c414864cbedc2eb53f2e081cac1.png)

*概率分布的对数作为熵的度量是有用的。*

![](img/ba5a1a41aff720c6a6ad6af99478fa30.png)

*熵与概率。*

定义：决策树中的熵表示同质性。

如果样本完全同质，熵为 0（概率=0 或 1）；如果样本在各个类别之间均匀分布，熵为 1（概率=0.5）。

下一步是进行最小化熵的划分。我们使用*信息增益*来确定最佳划分。

让我一步步向你展示在打网球的情况下如何计算信息增益。在这里，我将仅展示如何计算“天气”的信息增益和熵。

**步骤 1**：计算一个属性的熵——预测：克莱尔会打网球/克莱尔不会打网球

在这个示例中，我将使用这个列联表来计算目标变量的熵：是否玩？（是/否）。共有 14 个观察值（10 个“是”和 4 个“否”）。‘是’的概率（p）为 0.71428（10/14），‘否’的概率为 0.28571（4/14）。然后，你可以使用上述公式计算目标变量的熵。

![](img/efc3f408ef6a106271d0c31beb37241b.png)

**步骤 2**：使用列联表计算每个特征的熵

为了说明，我使用“天气”作为例子来解释如何计算它的熵。共有 14 个观察值。我们可以看到，有 5 个属于“晴天”，4 个属于“阴天”，5 个属于“雨天”。因此，我们可以找到“晴天”、“阴天”和“雨天”的概率，然后分别使用上述公式计算它们的熵。计算步骤如下。

![](img/2fb40a421db809a2042308f87f5da082.png)

*计算特征 2（Outlook）熵值的示例。*

定义：**信息增益**是节点分裂时熵值的减少或增加。

**信息增益的公式：**

![](img/e36bf0e62f86308085e0a38a54ee98eb.png)

*X 对 Y 的增益。*

![](img/c5045d95b030d831e2ba8e733b7f66d3.png)

*Outlook 的信息增益为 0.147。*

![](img/b10c92744ac10621b92dbadd39d50e5c.png)

*sklearn.tree.**DecisionTreeClassifier:** “entropy”代表信息增益。*

为了可视化如何使用**信息增益**构建决策树，我简单地应用了 sklearn.tree.**DecisionTreeClassifier**来生成图示。

***步骤 3***：选择**信息增益最大**的属性作为根节点

‘湿度’的信息增益最高，为 0.918。湿度是根节点。

***步骤 4***：一个*熵为 0 的分支是叶子节点，而熵大于 0 的分支需要进一步分裂。

***步骤 5***：在 ID3 算法中，节点会递归地增长，直到所有数据都被分类。

你可能听说过**C4.5 算法**，它是 ID3 算法的改进版，使用**增益比**作为信息增益的扩展。使用增益比的优点是通过使用分裂信息（Split Info）来规范化信息增益，以解决偏差问题。我不会在这里详细讨论 C4.5。如需更多信息，请查看[这里](https://www.datacamp.com/community/tutorials/decision-tree-classification-python)（DataCamp）。

### CART（分类与回归树）

另一种决策树算法 CART 使用*基尼方法*来创建分裂点，包括*基尼指数（基尼不纯度）和基尼增益*。

基尼指数的定义：随机挑选标签并为样本分配错误标签的概率，也用于测量树中特征的重要性。

![](img/00887d6088d38cb1d3729ed790915cdc.png)

*基尼指数的公式。*

让我来展示一下如何计算基尼指数和基尼增益 :)

![](img/fb84c8dacf63d3025eb36e55330c1ee9.png)

计算每个属性的基尼增益后，sklearn.tree.**DecisionTreeClassifier**会选择**基尼增益最大**的属性作为根节点。*一个*基尼值为 0 的分支是叶子节点，而基尼值大于 0 的分支需要进一步分裂。节点会递归地增长，直到所有数据都被分类（见下文详细说明）。

如前所述，CART 还可以使用不同的分裂标准处理回归问题：均方误差（MSE）来确定分裂点。回归树的输出变量是数值型的，输入变量可以是连续变量和分类变量的混合。您可以通过[DataCamp](https://www.datacamp.com/courses/machine-learning-with-tree-based-models-in-python)获取更多关于回归树的信息。

太好了！现在你应该理解如何计算熵、信息增益、基尼指数和基尼增益！

> *问题：那么，我应该使用哪个？基尼指数还是熵？*
> 
> *回答：一般来说，结果应该是相同的……我个人更倾向于使用基尼指数，因为它的计算不涉及更复杂的*log*。但为什么不同时尝试这两者呢。*

让我以表格形式总结一下！

![](img/3315c10ab0a6e178568a71af31dcbe1f.png)

### 使用 Scikit Learn 构建决策树

[Scikit Learn](https://en.wikipedia.org/wiki/Scikit-learn)是一个用于 Python 编程语言的免费机器学习库。

**第 1 步**：导入数据

```py
import numpy as np
import pandas as pd
df = pd.read_csv('weather.csv')

```

**第 2 步**：将分类变量转换为虚拟/指示变量

```py
df_getdummy=pd.get_dummies(data=df, columns=['Temperature', 'Outlook', 'Windy'])

```

![](img/947b8248bd1ba382a2f2555152a100b4.png)

*“温度”、“天气”和“风力”的分类变量都转换为虚拟变量。*

**第 3 步**：分离训练集和测试集

```py
from sklearn.model_selection import train_test_split
X = df_getdummy.drop('Played?',axis=1)
y = df_getdummy['Played?']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.30, random_state=101)

```

**第 4 步**：通过 sklearn 导入决策树分类器

```py
from sklearn.tree import DecisionTreeClassifier
dtree = DecisionTreeClassifier(max_depth=3)
dtree.fit(X_train,y_train)
predictions = dtree.predict(X_test)

```

**第 5 步**：可视化决策树图

```py
from sklearn.tree import DecisionTreeClassifier
dtree = DecisionTreeClassifier(max_depth=3)
dtree.fit(X_train,y_train)
predictions = dtree.predict(X_test)
from sklearn.tree import plot_tree
import matplotlib.pyplot as plt
fig = plt.figure(figsize=(16,12))
a = plot_tree(dtree, feature_names=df_getdummy.columns, fontsize=12, filled=True,
class_names=['Not Play', 'Play'])

```

![](img/cc72ce5e277e6deceff8a808e12a74b9.png)

*树的深度：3。*

**有关编码和数据集，请查看[这里](https://github.com/clareyan/Decision-Tree-Intuition-From-Concept-to-Application)。**

![](img/4018a9a410d788a450707a01e439ad58.png)

*如果“湿度”的条件低于或等于 73.5，Clare 很可能会打网球！*

![](img/8c9976be945714d5da3a03469c4f3534.png)

为了提高模型性能（超参数优化），你需要调整超参数。有关详细信息，请查看[这里](https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html)。

决策树的主要缺点是过拟合，尤其是当树特别深的时候。幸运的是，近年来的树模型，包括随机森林和 XGBoost，都是建立在决策树算法基础上的，它们通常在建模技术上表现更强，且比单一决策树更加动态。因此，深入理解**决策树**背后的概念和算法对于构建良好的数据科学和机器学习基础非常有帮助。

### 总结：现在你应该知道

+   如何构建决策树

+   如何计算“熵”和“信息增益”

+   如何计算“基尼指数”和“基尼增益”

+   什么是最佳分裂？

+   如何在 Python 中绘制决策树图

[原文](https://towardsdatascience.com/decision-tree-intuition-from-concept-to-application-530744294bb6)。转载经许可。

**相关：**

+   [决策树算法解析](https://www.kdnuggets.com/2020/01/decision-tree-algorithm-explained.html)

+   [理解 Python 中的分类决策树](https://www.kdnuggets.com/2019/08/understanding-decision-trees-classification-python.html)

+   [决策树——直观介绍](https://www.kdnuggets.com/2019/02/decision-trees-introduction.html)

### 更多相关话题

+   [使用 Python 和 Scikit-learn 简化决策树解释](https://www.kdnuggets.com/2017/05/simplifying-decision-tree-interpretation-decision-rules-python.html)

+   [决策树算法解析](https://www.kdnuggets.com/2020/01/decision-tree-algorithm-explained.html)

+   [通过实现理解：决策树](https://www.kdnuggets.com/2023/02/understanding-implementing-decision-tree.html)

+   [讲述精彩数据故事：可视化决策树](https://www.kdnuggets.com/2021/02/telling-great-data-story-visualization-decision-tree.html)

+   [随机森林与决策树：关键区别](https://www.kdnuggets.com/2022/02/random-forest-decision-tree-key-differences.html)

+   [KDnuggets™ 新闻 22:n09, 3 月 2 日：讲述精彩数据故事：…](https://www.kdnuggets.com/2022/n09.html)
