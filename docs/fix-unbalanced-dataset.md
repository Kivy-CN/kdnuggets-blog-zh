# 如何修复不平衡的数据集

> 原文：[`www.kdnuggets.com/2019/05/fix-unbalanced-dataset.html`](https://www.kdnuggets.com/2019/05/fix-unbalanced-dataset.html)

![c](img/3d9c022da2d331bb56691a9617b91b90.png) 评论

**由 [Will Badr](https://www.linkedin.com/in/willbadr/), 亚马逊网络服务**。

![](img/a0c36dc828d91a7fd4dd14345fe94e03.png)

* * *

## 我们的前三大课程推荐

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 1\. [Google 网络安全证书](https://www.kdnuggets.com/google-cybersecurity) - 快速进入网络安全职业生涯。

![](img/e225c49c3c91745821c8c0368bf04711.png) 2\. [Google 数据分析专业证书](https://www.kdnuggets.com/google-data-analytics) - 提升你的数据分析技能

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 3\. [Google IT 支持专业证书](https://www.kdnuggets.com/google-itsupport) - 支持你组织的 IT

* * *

**分类** 是最常见的机器学习问题之一。处理任何分类问题的最佳方法是从分析和探索数据集开始，我们称之为 **探索性数据分析（EDA）**。这个过程的唯一目的是尽可能多地生成关于数据的见解和信息。它也用于发现数据集中可能存在的任何问题。分类数据集中常见的问题之一是 **类别不平衡** 问题。

**什么是数据不平衡？**

数据不平衡通常反映数据集中类别的分布不均。例如，在信用卡欺诈检测数据集中，大多数信用卡交易不是欺诈交易，只有少数交易是欺诈交易。这导致欺诈与非欺诈类别之间的比例接近 50:1。本文中，我将使用 Kaggle 上的信用卡欺诈交易数据集，可以从 [这里](https://www.kaggle.com/mlg-ulb/creditcardfraud) 下载。

首先，让我们绘制类别分布图以查看不平衡情况。

![](img/659df8fb4da2a00a010ded4d8f603c34.png)

正如你所见，非欺诈交易远远超过了欺诈交易。如果我们训练一个二元分类模型而不解决这个问题，模型将完全偏向非欺诈交易。这也影响特征之间的相关性，稍后我会展示如何以及为何如此。

现在，让我们介绍一些解决类别不平衡问题的技术。完整代码的笔记本可以在 [这里](https://github.com/wmlba/innovate2019/blob/master/Credit_Card_Fraud_Detection.ipynb) 找到

### 1- 重新采样（过采样和欠采样）：

![](img/c68fc22efb83763dd54238e2a32d66d6.png)

这听起来直观易懂。**欠采样** 是一种从多数类别中随机删除一些观测值以匹配少数类别数量的过程。下面的代码展示了一种简单的方法：

**对多数类进行欠采样**

在对数据集进行欠采样后，我再次绘制它，显示了相等数量的类：

![](img/fa89234764b677e1021c4aaec75f637e.png)

**平衡数据集（欠采样）**

第二种重新采样技术称为**过采样**。这个过程比欠采样稍微复杂一些。它是生成合成数据的过程，试图随机生成来自少数类观察的属性样本。用于过采样数据集的方法有很多。最常见的技术称为**SMOTE（合成少数类过采样技术）**。简单来说，它查看少数类数据点的特征空间，并考虑其*k*最近邻。

![](img/372e64a5fa87707d51b2a10ff9132f70.png)

**来源: [`imbalanced-learn.readthedocs.io/en/stable/over_sampling.html`](https://imbalanced-learn.readthedocs.io/en/stable/over_sampling.html)**

要在 Python 中实现这一点，我使用了一个名为 [**imbalanced-learn**](https://imbalanced-learn.readthedocs.io/en/stable/index.html)** 或 imblearn 的库。**下面的代码展示了如何实现 SMOTE。

记住我之前提到过不平衡数据如何影响特征相关性吗？让我展示一下处理不平衡类前后的相关性。

### 在重新采样之前：

下面的代码绘制了所有特征之间的相关性矩阵。

```py

# Sample figsize in inches
fig, ax = plt.subplots(figsize=(20,10))         
# Imbalanced DataFrame Correlation
corr = credit_df.corr()
sns.heatmap(corr, cmap='YlGnBu', annot_kws={'size':30}, ax=ax)
ax.set_title("Imbalanced Correlation Matrix", fontsize=14)
plt.show()

```

![](img/786ad581fe38578951627b15e790440d.png)

### 重新采样之后：

![](img/3b8ff6dfe744fd5a687bb3ba725eb2a1.png)

注意，现在特征相关性更为明显。在解决不平衡问题之前，大多数特征没有显示出任何相关性，这肯定会影响模型的性能。由于[**特征相关性确实很重要**](https://towardsdatascience.com/why-feature-correlation-matters-a-lot-847e8ba439c4)对整体模型的表现，因此修正不平衡问题很重要，因为这也会影响机器学习模型的性能。

### 2- 集成方法（采样器集成）：

在机器学习中，集成方法使用多个学习算法和技术，以获得比任何单一学习算法所能实现的更好的性能。（是的，就像民主投票系统一样）。使用集成分类器时，袋装方法变得非常流行，它通过在不同的随机选择的数据子集上构建多个估计器来工作。在 scikit-learn 库中，有一个名为 BaggingClassifier 的集成分类器。然而，这个分类器不允许平衡每个数据子集。因此，当在不平衡数据集上训练时，这个分类器会偏向于多数类，从而创建一个有偏的模型。

为了解决这个问题，我们可以使用 [**BalancedBaggingClassifier**](https://imbalanced-learn.readthedocs.io/en/stable/generated/imblearn.ensemble.BalancedBaggingClassifier.html#imblearn.ensemble.BalancedBaggingClassifier) 来自 **imblearn** 库。它允许在训练每个集成估算器之前对数据集的每个子集进行重采样。因此，[**BalancedBaggingClassifier**](https://imbalanced-learn.readthedocs.io/en/stable/generated/imblearn.ensemble.BalancedBaggingClassifier.html#imblearn.ensemble.BalancedBaggingClassifier) 除了与 scikit-learn 的 BaggingClassifier 相同的参数外，还具有两个其他参数，sampling_strategy 和 replacement，这些参数控制随机采样器的行为。以下是一些代码示例：

**使用集成采样器训练不平衡数据集**

这样，您可以训练一个分类器，该分类器将处理不平衡问题，而无需在训练之前手动欠采样或过采样。

总结一下，每个人都应该知道，基于不平衡数据集构建的机器学习模型的整体性能将受到其预测稀有和少数点能力的限制。识别和解决这些点的不平衡问题对于生成模型的质量和性能至关重要。

[原文](https://towardsdatascience.com/having-an-imbalanced-dataset-here-is-how-you-can-solve-it-1640568947eb)。经许可转载。

**个人简介**: [Will Badr](https://www.linkedin.com/in/willbadr/) 是一位经验丰富的高级技术账户经理，在信息技术和服务行业有着丰富的工作经验。他专注于人工智能和机器学习领域，并推动创新文化。

**资源:**

+   [在线和基于网络的：分析、数据挖掘、数据科学、机器学习教育](https://www.kdnuggets.com/education/online.html)

+   [用于分析、数据科学、数据挖掘和机器学习的软件](https://www.kdnuggets.com/software/index.html)

**相关内容:**

+   [数据清理的顶级 R 包](https://www.kdnuggets.com/2019/03/top-r-packages-data-cleaning.html)

+   [为意外情况做好准备](https://www.kdnuggets.com/2019/02/preparing-unexpected.html)

+   [以低成本获取标记数据以训练您的模型](https://www.kdnuggets.com/2019/02/labeled-data-train-models.html)

### 更多相关话题

+   [10 个最常见的数据质量问题及其解决方案](https://www.kdnuggets.com/2022/11/10-common-data-quality-issues-fix.html)

+   [如何在机器学习中从庞大的数据集中正确选择样本](https://www.kdnuggets.com/2019/05/sample-huge-dataset-machine-learning.html)

+   [为您的数据集选择正确的聚类算法](https://www.kdnuggets.com/2019/10/right-clustering-algorithm.html)

+   [如何为机器学习创建数据集](https://www.kdnuggets.com/2022/02/create-dataset-machine-learning.html)

+   [如何生成合成表格数据集](https://www.kdnuggets.com/2022/03/generate-tabular-synthetic-dataset.html)

+   [无监督解缠代表学习在类别不平衡数据集中的应用…](https://www.kdnuggets.com/2023/01/unsupervised-disentangled-representation-learning-class-imbalanced-dataset-elastic-infogan.html)
