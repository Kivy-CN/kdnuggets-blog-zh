# 使用 SHAP 值进行机器学习模型可解释性

> 原文：[`www.kdnuggets.com/2023/08/shap-values-model-interpretability-machine-learning.html`](https://www.kdnuggets.com/2023/08/shap-values-model-interpretability-machine-learning.html)

![使用 SHAP 值进行机器学习模型可解释性](img/969360458439bb37b2f15a58cf70887a.png)

图片来源：作者

# 机器学习可解释性

* * *

## 我们的三大课程推荐

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 1\. [谷歌网络安全证书](https://www.kdnuggets.com/google-cybersecurity) - 快速进入网络安全职业道路。

![](img/e225c49c3c91745821c8c0368bf04711.png) 2\. [谷歌数据分析专业证书](https://www.kdnuggets.com/google-data-analytics) - 提升你的数据分析技能

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 3\. [谷歌 IT 支持专业证书](https://www.kdnuggets.com/google-itsupport) - 支持你的组织的 IT 工作

* * *

机器学习可解释性是指解释和理解机器学习模型如何进行预测的技术。随着模型变得越来越复杂，解释其内部逻辑和获得对其行为的洞察变得越来越重要。

这很重要，因为机器学习模型通常用于做出具有现实世界影响的决策，如医疗、金融和刑事司法领域。没有可解释性，很难知道机器学习模型是否在做出良好的决策，或者是否存在偏见。

在机器学习可解释性方面，有各种技术可供考虑。一种流行的方法是确定特征重要性分数，这揭示了对模型预测影响最大的特征。SKlearn 模型默认提供特征重要性分数，但你还可以利用 [SHAP](https://shap.readthedocs.io/en/latest/index.html)、[Lime](https://github.com/marcotcr/lime) 和 [Yellowbrick](https://www.scikit-yb.org/en/latest/index.html) 等工具，以更好地可视化和理解机器学习结果。

本教程将介绍 SHAP 值以及如何使用 SHAP Python 包解释机器学习结果。

# 什么是 SHAP 值？

[SHAP](https://shap.readthedocs.io/en/latest/index.html) 值基于博弈论中的 Shapley 值。在博弈论中，Shapley 值帮助确定在协作游戏中每个玩家对总回报的贡献。

对于机器学习模型，每个特征被视为一个“玩家”。特征的 Shapley 值代表该特征在所有可能的特征组合中的平均贡献量。

具体来说，SHAP 值是通过比较模型在某一特征存在与不存在时的预测来计算的。这是针对数据集中的每个特征和每个样本进行迭代完成的。

通过为每个预测分配每个特征的重要性值，SHAP 值提供了一个局部、一致的解释，说明模型如何运作。它们揭示了哪些特征对特定预测有最大的影响，无论是正面还是负面。这对于理解复杂的机器学习模型，如深度神经网络，具有重要价值。

# 开始使用 SHAP 值

在本节中，我们将使用来自 Kaggle 的 [手机价格分类](https://www.kaggle.com/datasets/iabhishekofficial/mobile-price-classification?select=train.csv) 数据集来构建和分析多分类模型。我们将根据特征（如 ram、大小等）对手机价格进行分类。目标变量是 <code>price_range</code>，其值为 0（低成本）、1（中等成本）、2（高成本）和 3（非常高成本）。

**注意：** 带有输出的代码源可以在 [Deepnote 工作区](https://deepnote.com/@abid/Getting-Started-with-SHAP-Values-3e9de750-8212-4ff3-979c-e14a916ac919) 获得。

## 安装 SHAP

使用 <code>pip</code> 或 <code>conda</code> 命令在系统上安装 <code>shap</code> 非常简单。

```py
pip install shap
```

或

```py
conda install -c conda-forge shap
```

## 加载数据

数据集干净且组织良好，类别已使用标签编码器转换为数字。

```py
import pandas as pd

mobile = pd.read_csv("train.csv")
mobile.head()
```

![使用 SHAP 值进行机器学习模型解释性分析](img/49fad221b0b4f1f112defd1c31efc06a.png)

## 准备数据

首先，我们将识别依赖变量和独立变量，然后将它们拆分为单独的训练集和测试集。

```py
from sklearn.model_selection import train_test_split

X = mobile.drop('price_range', axis=1)
y = mobile.pop('price_range')

# Train and test split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=1)
```

## 训练和评估模型

之后，我们将使用训练集训练我们的随机森林分类器模型，并在测试集上评估其性能。我们得到了 87%的准确率，这相当不错，并且我们的模型总体上非常平衡。

```py
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report

# Model fitting
rf = RandomForestClassifier()
rf.fit(X_train, y_train)

# Prediction
y_pred = rf.predict(X_test)

# Model evaluation
print(classification_report(y_pred, y_test))
```

```py
 precision    recall  f1-score   support

           0       0.95      0.91      0.93       141
           1       0.83      0.81      0.82       153
           2       0.80      0.85      0.83       158
           3       0.93      0.93      0.93       148

    accuracy                           0.87       600
   macro avg       0.88      0.87      0.88       600
weighted avg       0.87      0.87      0.87       600
```

## 计算 SHAP 值

在这部分，我们将创建一个 SHAP 树解释器，并使用它计算测试集的 SHAP 值。

```py
import shap
shap.initjs()

# Calculate SHAP values
explainer = shap.TreeExplainer(rf)
shap_values = explainer.shap_values(X_test)
```

## 总结图

总结图是模型中每个特征重要性的图形表示。它是理解模型如何做出预测以及识别最重要特征的有用工具。

在我们的案例中，它显示了每个目标类别的特征重要性。结果表明，“ram”、“电池电量”和手机大小在确定价格范围方面起着重要作用。

```py
# Summarize the effects of features
shap.summary_plot(shap_values, X_test)
```

![使用 SHAP 值进行机器学习模型解释性分析](img/18b7e1943dbb6982df53fe96e02cff9e.png)

我们现在将可视化类别“0”的未来重要性。我们可以清楚地看到，ram、电池和手机大小对预测低成本手机有负面影响。

```py
shap.summary_plot(shap_values[0], X_test)
```

![使用 SHAP 值进行机器学习模型解释性分析](img/bfe7ebf53acef36e8be6cae7ae40c858.png)

## 依赖性图

依赖性图是一种散点图，显示了模型预测如何受到特定特征的影响。在这个例子中，特征是“电池电量”。

图的 x 轴显示了“电池电量”的值，y 轴显示了 SHAP 值。当电池电量超过 1200 时，它开始对低端手机型号的分类产生负面影响。

```py
shap.dependence_plot("battery_power", shap_values[0], X_test,interaction_index="ram")
```

![使用 SHAP 值进行机器学习模型可解释性](img/8ddc41c1521e375458100f103c12722f.png)

## 力量图

让我们将焦点缩小到一个样本上。具体来说，我们将更仔细地查看第 12 个样本，以了解哪些特征导致了“0”的结果。为此，我们将使用力量图，并输入预期值、SHAP 值和测试样本。

事实证明，内存、手机尺寸和时钟速度对模型的影响更大。我们还注意到，由于 f(x)值较低，模型不会预测“0”类别。

```py
shap.plots.force(explainer.expected_value[0], shap_values[0][12,:], X_test.iloc[12, :], matplotlib = True)
```

![使用 SHAP 值进行机器学习模型可解释性](img/2f189a2fd381ccef299ce8a9d5de8a8e.png)

我们现在将可视化类别“1”的力量图，我们可以看到这是正确的类别。

```py
shap.plots.force(explainer.expected_value[1], shap_values[1][12, :], X_test.iloc[12, :],matplotlib = True)
```

![使用 SHAP 值进行机器学习模型可解释性](img/5b054b62d4145293be7daf78992a2b31.png)

我们可以通过检查测试集的第 12 条记录来确认我们的预测。

```py
y_test.iloc[12]
>>> 1 
```

## 决策图

决策图可以是理解机器学习模型决策过程的有用工具。它们可以帮助我们识别对模型预测最重要的特征，并识别潜在的偏差。

为了更好地理解影响模型对类别“1”预测的因素，我们将检查决策图。根据该图，手机高度对模型有负面影响，而内存对模型有正面影响。

```py
shap.decision_plot(explainer.expected_value[1], shap_values[1][12,:], X_test.columns)
```

![使用 SHAP 值进行机器学习模型可解释性](img/79405cb5163a11dca4365a497e8192b6.png)

# 结论

在这篇博客文章中，我们介绍了 SHAP 值，这是一种解释机器学习模型输出的方法。我们展示了如何使用 SHAP 值解释单个预测和模型的整体表现。我们还提供了 SHAP 值在实际应用中的示例。

随着机器学习扩展到敏感领域如医疗、金融和自动驾驶，解释性和可解释性将变得更加重要。SHAP 值提供了一种灵活且一致的方法来解释预测和模型行为。它可以用来深入了解模型如何进行预测，识别潜在的偏差，并改善模型的性能。

**[Abid Ali Awan](https://www.polywork.com/kingabzpro)** ([@1abidaliawan](https://www.linkedin.com/in/1abidaliawan/)) 是一名认证数据科学专业人士，热衷于构建机器学习模型。目前，他专注于内容创作和撰写有关机器学习和数据科学技术的技术博客。Abid 拥有技术管理硕士学位和电信工程学士学位。他的愿景是利用图神经网络构建一个 AI 产品，帮助那些在心理健康方面挣扎的学生。

### 更多相关话题

+   [SHAP：用 Python 解释任何机器学习模型](https://www.kdnuggets.com/2022/11/shap-explain-machine-learning-model-python.html)

+   [机器学习不像你的大脑 第四部分：神经元的…](https://www.kdnuggets.com/2022/06/machine-learning-like-brain-part-4-neuron-limited-ability-represent-precise-values.html)

+   [用 Python 和 Scikit-learn 简化决策树解释](https://www.kdnuggets.com/2017/05/simplifying-decision-tree-interpretation-decision-rules-python.html)

+   [用 SQL 处理时间序列中的缺失值](https://www.kdnuggets.com/2022/09/handling-missing-values-timeseries-sql.html)

+   [Segment Anything Model：图像分割的基础模型](https://www.kdnuggets.com/2023/07/segment-anything-model-foundation-model-image-segmentation.html)

+   [利用迁移学习提升模型性能](https://www.kdnuggets.com/using-transfer-learning-to-boost-model-performance)
