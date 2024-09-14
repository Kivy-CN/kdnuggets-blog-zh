# 大众的深度学习（……以及语义层）

> 原文：[https://www.kdnuggets.com/2018/11/deep-learning-masses-semantic-layer.html](https://www.kdnuggets.com/2018/11/deep-learning-masses-semantic-layer.html)

![c](../Images/3d9c022da2d331bb56691a9617b91b90.png) [评论](/2018/12/deep-learning-masses-semantic-layer.html?page=2#comments)

![](../Images/0d600e54f6ccfa72cd4a1406c5da605f.png)

### 深度学习介绍

本文的范围并不是介绍深度学习，我在其他文章中已经做过了，你可以在这里找到：

[**一个“奇怪”的深度学习介绍**

*有许多令人惊叹的深度学习介绍、课程和博客文章。但这是一种不同类型的介绍……*towardsdatascience.com](https://towardsdatascience.com/a-weird-introduction-to-deep-learning-7828803693b0)

[**我进入深度学习的旅程**

*在这篇文章中，我将分享我如何学习深度学习以及如何用它解决数据科学问题。这是一个……*towardsdatascience.com](https://towardsdatascience.com/my-journey-into-deep-learning-c66e6ef2a317)

[**关于深度学习的对话**

*有人偷听到两个人谈论深度学习，并把每个细节都告诉了我。其中一个人完全是……*towardsdatascience.com](https://towardsdatascience.com/a-conversation-about-deep-learning-9a915983107)

但如果你想从这里尝试一下，我可以这样告诉你：

> …深度学习是利用不同种类的神经网络[深度神经网络]进行表示学习，并优化网络的超参数，以获得（学习）最佳的数据表示。

如果你想知道这从哪里来，阅读上述文章。

### 深度学习并不那么难

![](../Images/15ba9c0960bacdc3345efdd23cea7772.png)

这更难

目前，对于组织而言，深度学习并不是那么难。我不是说深度学习整体上很简单，研究这个领域需要大量的数学、微积分、统计学、机器学习、计算等知识。你可以从我之前制作的时间线上看到深度学习的来源。

![](../Images/3593b60a976d378e248af1e7a4b9e0fd.png)

从那里我可以说，反向传播、网络参数的更好初始化、更好的激活函数、Dropout 概念以及卷积神经网络、残差网络、区域基础 CNN、递归神经网络和生成对抗网络等一些网络类型，是我们在深度学习领域取得的最重要进展之一。

但你现在怎么使用深度学习呢？

![](../Images/5d736887d25f6d03f15ec82a92fbbc64.png)

hehe

### 数据优先

![](../Images/6c1bc4b80d0f94164780f85eba135d51.png)

哦，你可能会想成为他们。对吧？或者可能不是，我不知道。

你想知道秘密吗？那些大科技公司使用的秘密武器？这不仅仅是深度学习（也许根本不是深度学习）

我不会在这里做完整的演讲，但一切都从数据开始。正如你可以想象的那样，数据现在是公司最重要的资产（也许是最重要的）。所以，在你能应用机器学习或深度学习之前，你需要拥有数据，知道你拥有的是什么，理解它，管理它，清理它，分析它，标准化它（也许还要更多），然后你才能考虑如何使用它。

从 [Brian Godsey](https://medium.com/@briangodsey) 的精彩 [文章](https://towardsdatascience.com/is-data-science-really-a-science-9c2249ee2ce4) 中可以看出：

> *无论何种形式，数据现在无处不在，与其说它只是分析师用来得出结论的工具，不如说它已经成为自身的目的。公司现在似乎将数据视为最终目标，而非手段，尽管许多公司声称计划在未来使用这些数据。独立于信息时代的其他定义特征，数据获得了自己的角色、自己的组织和自己的价值。*

所以你可以看到，这不仅仅是将最新的算法应用于你的数据，而是能够将数据以良好的格式呈现出来，并理解它，然后再使用它。

### 语义层

![](../Images/c3f7e57b92039b01d8e6db7f526a4b3a.png)

这些层次是有意义的。不过，这不是语义层。继续阅读。

这对我来说是很不寻常的，但我做了很多调查，并与几家公司合作，它们似乎都有相同的问题：它们的数据。

数据的可用性、数据质量、数据摄取、数据集成等常见问题，不仅会影响数据科学实践，还会影响整个组织。

清理数据并为机器学习做好准备的方法有很多，也有很棒的工具和方法论，你可以在这里阅读更多信息：

[**宣布 Optimus v2——敏捷数据科学工作流简化版**]

*寻找一个可以显著提高你作为数据科学家生产力的库？快来看看这个！* [towardsdatascience.com](https://towardsdatascience.com/announcing-optimus-v2-agile-data-science-workflows-made-easy-c127a12d9e13)

但这假设你已经有了摄取和集成数据的流程。现在有很棒的工具用于 AutoML，我之前已经讨论过这个问题：

[**Auto-Keras，或如何在 4 行代码中创建深度学习模型**]

*自动化机器学习是新来的，它将长期存在。它帮助我们不断创造更好的…* [www.kdnuggets.com](/2018/08/auto-keras-create-deep-learning-model-4-lines-code.html)

以及像 DataRobot 这样的其他商业工具：

[**用于预测建模的自动化机器学习 | DataRobot**]

*DataRobot 的自动化机器学习平台使构建和部署准确的预测模型变得快速而简单…* [www.datarobot.com](https://www.datarobot.com/)

### 那么自动化摄取和集成呢？

这就是语义层的惊人好处之一。但到底什么是语义层呢？

语义一词本身意味着意义或理解。因此，语义层与数据相关的是其含义，而不是数据的结构。

理解是一个非常重要的过程，我之前已经提到过：

[**利用数据科学创建智能**](https://towardsdatascience.com/creating-intelligence-with-data-science-2fb9f697fc79)

*在这篇文章中，我将展示数据科学如何通过 AI 实现智能。* [towardsdatascience.com](https://towardsdatascience.com/creating-intelligence-with-data-science-2fb9f697fc79)

在这里我提到（来自 [Lex Fridman](https://medium.com/@lexfridman)）：

> *理解是将****复杂****信息转化为****简单****、有用**信息的能力。*

当我们理解时，我们是在解码构成这一复杂事物的部分，并将最初获得的原始数据转化为有用且易于理解的东西。我们通过**建模**来实现这一点。正如你可以想象的那样，我们需要这样的模型来理解数据的意义。

### 链接数据和知识图谱

![](../Images/26ff708ca270ef263f52b488adf8fef9.png)

我们需要做的第一件事是链接数据。链接数据的目标是以一种结构化的方式发布数据，使其能够被轻松地消耗并与其他链接数据结合。

链接数据是 Web 上数据发布和互操作性的新的事实标准，也正在进入企业。像 Google、Facebook、Amazon 和 Microsoft 这样的巨头，已经采用了其中的一些原则。

数据链接的过程是一个称为知识图谱的开端。知识图谱是一种高级的方式，用于映射某一特定主题的所有知识，以填补数据如何关联的空白，或数据库中的虫洞。

> 知识图谱由集成的数据和信息集合组成，这些集合还包含了大量不同数据之间的链接。

关键在于，在这种新模型下，我们不是寻找可能的答案，而是在寻求一个答案。我们需要的是事实——这些事实的来源并不那么重要。

这里的数据可以代表概念、对象、事物、人，实际上你脑海中的任何东西。图谱填补了这些概念之间的关系和连接。

这里是 Google 在 6 年前（对，就是 6 年）对知识图谱的一个惊人介绍：

### 知识图谱对你和你的公司意味着什么？

以旧式方式，数据仓库中的数据模型虽然是一个了不起的成就，但无法吸收涌向我们的庞大数据量。创建关系数据模型的过程实在跟不上。此外，用于推动数据发现的数据提取也过于有限。

基于 Hadoop 或云存储的数据湖因此已经变成了数据沼泽——缺乏必要的管理和治理能力。

![](../Images/b308a5f4ccac1ae11975f8c7a9f557a0.png)

[https://timoelliott.com/blog/2014/12/from-data-lakes-to-data-swamps.html](https://timoelliott.com/blog/2014/12/from-data-lakes-to-data-swamps.html)

你是否问过你的数据工程师和科学家，他们是否理解你们组织拥有的所有数据？请这么做。

分析你拥有的所有数据是极其困难的。并理解背后的关系是什么。

因为它们是图形，知识图谱更为直观。人们不会以表格的形式思考，但他们可以立刻理解图形。当你在白板上画出知识图谱的结构时，大多数人能立即明白它的意义。

知识图谱还允许你为图谱中的关系创建结构。你可以告诉图谱父母有孩子，父母可以是孩子，孩子可以是兄弟或姐妹，这些都是人。提供这样的描述信息允许从图谱中推断出新的信息，比如如果两个人有相同的父母，他们必须是兄弟姐妹。

* * *

## 我们的前三大课程推荐

![](../Images/0244c01ba9267c002ef39d4907e0b8fb.png) 1\. [谷歌网络安全证书](https://www.kdnuggets.com/google-cybersecurity) - 快速进入网络安全职业生涯。

![](../Images/e225c49c3c91745821c8c0368bf04711.png) 2\. [谷歌数据分析专业证书](https://www.kdnuggets.com/google-data-analytics) - 提升你的数据分析技能

![](../Images/0244c01ba9267c002ef39d4907e0b8fb.png) 3\. [谷歌IT支持专业证书](https://www.kdnuggets.com/google-itsupport) - 支持你的组织IT需求

* * *

### 更多相关话题

+   [语义层的力量：数据工程师指南](https://www.kdnuggets.com/2023/10/cube-power-of-a-semantic-layer-a-data-engineers-guide)

+   [语义层：AI驱动的数据体验的支柱](https://www.kdnuggets.com/2023/10/cube-semantic-layer-backbone-aipowered-data-experiences)

+   [通用语义层对你的数据栈的6个好处](https://www.kdnuggets.com/2024/01/cube-6-reasons-why-a-universal-semantic-layer-is-beneficial)

+   [语义向量搜索如何改变客户支持互动](https://www.kdnuggets.com/how-semantic-vector-search-transforms-customer-support-interactions)

+   [基于向量数据库的语义搜索](https://www.kdnuggets.com/semantic-search-with-vector-databases)

+   [关于语义分割注释的误解](https://www.kdnuggets.com/2022/01/misconceptions-semantic-segmentation-annotation.html)
��持你的组织进行 IT 工作

* * *

### 更多相关话题

+   [语义层的力量：数据工程师指南](https://www.kdnuggets.com/2023/10/cube-power-of-a-semantic-layer-a-data-engineers-guide)

+   [语义层：AI 驱动的数据体验的基石](https://www.kdnuggets.com/2023/10/cube-semantic-layer-backbone-aipowered-data-experiences)

+   [通用语义层对你的数据堆栈有益的 6 个理由](https://www.kdnuggets.com/2024/01/cube-6-reasons-why-a-universal-semantic-layer-is-beneficial)

+   [语义向量搜索如何变革客户支持互动](https://www.kdnuggets.com/how-semantic-vector-search-transforms-customer-support-interactions)

+   [使用向量数据库的语义搜索](https://www.kdnuggets.com/semantic-search-with-vector-databases)

+   [关于语义分割注释的误解](https://www.kdnuggets.com/2022/01/misconceptions-semantic-segmentation-annotation.html)
