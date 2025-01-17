# 如何为您的数据科学问题选择初始模型

> 原文：[`www.kdnuggets.com/2021/08/select-initial-model-data-science-problem.html`](https://www.kdnuggets.com/2021/08/select-initial-model-data-science-problem.html)

评论

**由 [Zachary Warnes](https://www.linkedin.com/in/zjwarnes/)，数据科学家**

![](img/b93028ea511d655cf16593e39f61e150.png)

照片由 [Cesar Carlevarino Aragon](https://unsplash.com/@carlevarino?utm_source=medium&utm_medium=referral) 提供，来源于 [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

* * *

## 我们的三大课程推荐

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 1\. [Google 网络安全证书](https://www.kdnuggets.com/google-cybersecurity) - 快速进入网络安全职业轨道。

![](img/e225c49c3c91745821c8c0368bf04711.png) 2\. [Google 数据分析专业证书](https://www.kdnuggets.com/google-data-analytics) - 提升您的数据分析技能

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 3\. [Google IT 支持专业证书](https://www.kdnuggets.com/google-itsupport) - 支持您的组织进行 IT 工作

* * *

本文旨在帮助新手或有志的数据科学家决定在问题中使用哪个模型。

本文不会涉及数据处理。希望您知道这是数据科学家工作的主要部分。我假设您已有一些数据，并希望了解如何进行预测。

## 简单模型

**有很多模型可供选择，并且似乎有无尽的变体。**

通常只需进行轻微的调整即可将回归模型更改为分类模型，反之亦然。幸运的是，这项工作已经通过标准的 Python 监督学习包为您完成。因此，您只需选择您想要的选项即可。

有很多模型可以选择：

+   决策树

+   支持向量机（SVM）

+   朴素贝叶斯

+   K-最近邻

+   神经网络

+   梯度提升

+   随机森林

列表还在继续，但考虑从两个模型之一开始。

## **线性回归 & 逻辑回归**

![](img/3c72d683de98ff51e0f7058e6b385854.png)

照片由 [iMattSmart](https://unsplash.com/@imattsmart?utm_source=medium&utm_medium=referral) 提供，来源于 [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

是的，像 xgboost、BERT 和 GPT-3 这样的高级模型确实存在，但从这两个开始吧。

***注意***：逻辑回归有一个不幸的名称。该模型用于分类，但由于历史原因，名称得以保留。*

我建议将名称更改为像线性分类这样的直接命名，以消除这种混淆。但是，我在行业中还没有那样的影响力。

## 线性回归

```py
**from** **sklearn.linear_model** **import** LinearRegression
**import** **numpy** **as** **np**X = np.array([[2, 3], [5, 6], [8,9], [10, 11]])
y = np.dot(X, np.array([1, 2])) + 1
reg = LinearRegression().fit(X, y)
reg.score(X, y)
```

## 逻辑回归

```py
**from** **sklearn.linear_model** **import** LogisticRegression
**from** **sklearn.datasets** **import** load_breast_cancer
X, y = load_breast_cancer(return_X_y=**True**)
clf = LogisticRegression(solver='liblinear', random_state=10).fit(X, y)
clf.score(X,y)
```

## 为什么选择这些模型？

为什么要从这些简单模型开始？ **因为可能您的问题不需要任何复杂的模型。**

如果只是为了获得稍微提高的准确率而投入大量精力和花费在 AWS 上的费用，那么这是不值得的。

这两种模型已经研究了几十年，是一些**在机器学习中最为理解透彻的模型**。

**它们易于解释。** 两种模型都是线性的，因此它们的输入以一种可以手动计算的方式转化为输出。

## 给自己减轻一些头疼的麻烦。

即使你是一名经验丰富的数据科学家，你也应该了解这些模型在你的问题上的表现，主要是因为它们非常容易实现和测试。

我曾经犯过这种错误。我曾经直接深入并构建复杂的模型。**以为我使用的 xgboost 模型在总体上是更优的**，因此它应该是我的起始模型。结果发现，线性回归模型的表现只差几个百分点。线性回归被使用是因为它更简单且更易解释。

这里涉及到一定的自我认知。

![](img/e8e37dac1e1b9805ce5f6e3dfeee479b.png)

图片由[Sebastian Herrmann](https://unsplash.com/@officestock?utm_source=medium&utm_medium=referral)提供，来源于[Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

你可能想要展示你对这些复杂模型的理解及其使用方法。但有时它们设置、训练和维护起来并不实际。**仅仅因为一个模型可以使用并不意味着它应该被使用。**

不要浪费时间。**某个足够好且被使用的模型总是比复杂但没人使用或理解的模型更好**。

希望现在你能从简单开始，使用这些模型中的一个。

## 第一个问题

我的问题是分类问题还是回归问题？

### 你的问题是回归问题吗？

你是否试图预测一个连续的输出？

![](img/936a86401dfe37adea518d52e2161070.png)

线性回归（作者拍摄）

某物的价格，比如房子、产品或股票？回归。

某事物将持续多长时间，比如飞行时长、制造时间或用户在你的博客上花费的时间？回归。

从线性回归开始。绘制你的线性回归并评估这个模型。

保持目前的表现。如果它已经足够好，符合你的问题需求，那么就继续使用它。否则，你可以开始尝试其他模型。

### 你的问题是分类问题吗？

你是否试图预测一个二元输出或多个唯一且离散的输出？

![](img/45f28ad68cffad0af0d559a60ac9cc99.png)

逻辑回归（作者拍摄）

你是否试图确定某人是否会从你的商店购买东西或赢得比赛？分类。

你是否需要一个简单的“是”或“否”来回答你面临的问题？分类。

从逻辑回归开始，绘制你的数据或其子集的散点图并标记不同的类别。也许已经存在明显的模式。

再次评估模型，如果你仍然需要提高性能，则以此为基准。但从这里开始。

## 结论

可能，那些阅读过这些内容的人会发现自己处于类似的情况中，选择使用什么模型。然后决定你的问题非常适合你读过的论文中的新模型。结果是，花费数小时调整这个复杂模型，最终却是一个更简单的模型胜出。

不一定是因为性能，**而是因为它们简单且易于解释**。

节省时间和精力。只需从线性回归和逻辑回归开始。

**简介：[扎卡里·沃恩斯](https://www.linkedin.com/in/zjwarnes/)** 是 Pacmed 的数据科学家，他不断寻求新的挑战。多年前，扎卡里认识到解决新问题和克服障碍是学习和发展新技能的最快方式，因此他不断地将自己置于新的环境中，以便从每一个新挑战中受益。

[原始内容](https://towardsdatascience.com/how-to-select-an-initial-model-for-your-data-science-problem-77f7b811bd0)。经许可转载。

**相关：**

+   数据科学和机器学习中的基础线性代数

+   你应该使用线性回归模型而非神经网络的 3 个理由

+   10 个机器学习模型训练错误

### 主题更多

+   [解决下一个数据科学问题的 5 步蓝图](https://www.kdnuggets.com/5-step-blueprint-to-your-next-data-science-problem)

+   [如何正确从机器学习中的巨大数据集中选择样本](https://www.kdnuggets.com/2019/05/sample-huge-dataset-machine-learning.html)

+   [如何使用[ ]、.loc、iloc、.at 等在 Pandas 中选择行和列](https://www.kdnuggets.com/2019/06/select-rows-columns-pandas.html)

+   [现实世界中 NLP 应用的范围：不同的…](https://www.kdnuggets.com/2022/03/different-solution-problem-range-nlp-applications-real-world.html)

+   [Python 中的遗传编程：背包问题](https://www.kdnuggets.com/2023/01/knapsack-problem-genetic-programming-python.html)

+   [梯度消失问题：原因、后果及解决方案](https://www.kdnuggets.com/2022/02/vanishing-gradient-problem.html)
