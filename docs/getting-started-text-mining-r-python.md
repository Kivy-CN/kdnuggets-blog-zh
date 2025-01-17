# 开始使用 R 和 Python 进行文本挖掘的提示

> 原文：[`www.kdnuggets.com/2017/11/getting-started-text-mining-r-python.html`](https://www.kdnuggets.com/2017/11/getting-started-text-mining-r-python.html)

**作者：Chaitanya Sagar，[Perceptive Analytics](http://www.perceptive-analytics.com/)。**

**一切从文本开始**

你我以及所有人关于当今热门话题的文本帖子中蕴藏着大量信息。无论我们在大公司还是小公司工作，我们都收集与各自业务相关的数据，并将其存储以便用于各种项目。同时，我们都需要这些‘非结构化数据’来了解和理解更多关于我们的客户、顾客以及公司在当今世界的状态。然而，处理这些数据并不容易。数据是非结构化的，每一部分都不包含全部信息，每部分都是独特的。这就是文本数据的特点。它需要首先处理并转换为适合分析的形式。这与我们创建的数据库非常相似，只是这些数据库不能直接使用，而且数据量非常大。本文以简单直观的方式打开了文本挖掘的世界，并提供了开始文本挖掘的绝佳提示。

![](img/4a09fc15ca3b602f36a8a527949e76c8.png)

**提示 #1：先思考**

如果你有计划地进行文本挖掘，它可以变得很简单。在全面投入之前，先想想你需要对文本做什么。你进行文本挖掘的目标是什么？你想使用哪些数据来源？你需要多少数据才足够？你计划如何展示数据结果？这一切都在于对问题保持好奇，并将其分解成小部分。思考问题还会让你对可能遇到的各种情况及应对方式有更多了解。然后，你可以制定工作流程并开始执行任务。

**提示 #2：R 还是 Python？还是其他？**

没有一种金标准程序用于文本挖掘。你必须选择最方便的文本挖掘方法。在这里，效率、效果、问题类型等因素发挥作用，帮助你决定最适合你问题的方案。在决定了你的选择路径之后，你需要在该语言中建立知识和技能。我发现 Python 中的文本挖掘技术比 R 更直观，但 R 具有一些便利的功能，例如词频统计，并且在文本挖掘的包方面更丰富。

**提示 #3：早点开始并收集数据**

+   文本挖掘的常规过程包括以下步骤：

+   收集数据；无论是来自社交媒体如 Twitter 还是其他网站。编写可以适应你收集的特定类型文本的代码并存储它

+   将数据转换为可读文本

+   从文本中删除特殊字符（例如井号）。如果需要，可以添加一个井号计数功能。

+   从文本数据中删除数字（除非问题需要数字）。

+   决定是否保留所有数据或删除其中的一部分，例如所有非英语文本。

+   将所有文本转换为大写或小写以简化分析。

+   删除停用词。这些词在你的分析中没有用处，包括冠词、连词等。

+   使用词干提取和将类似词汇（如‘keep’和‘keeping’）分组，这些词在不同的时态形式中使用的是相同的词。

+   对处理后的词干词进行最终分析并可视化结果。

步骤简短而简单，但都依赖于第一步的顺利执行。你需要收集数据以便进行文本挖掘。有许多方式可以收集数据，其中最受欢迎的来源之一是 Twitter。Twitter 提供了一些 API，可以使用 R 和 Python 挖掘推文。除了 Twitter，现在你还可以从任何网站捕获数据，包括电子商务网站、电影网站、歌曲网站等。一些网站还包含预格式化的文本数据库，如 Project Gutenberg、语料库等。Google 趋势和 Yahoo 也提供一些在线分析。

**提示 #4: 找到并使用最佳的文本到数据转换方法**

根据工具和项目目标，你可能会使用不同的方法将收集的文本转换为数据。如果你使用 R，可能会用到如 twitteR、tm 和 stringr 等包进行大部分预处理。在 Python 中，相应的包是 nltk 库和 Tweepy 包。无论使用哪种语言和包，都要确保你有足够的资源和内存来处理数据。文本挖掘可能会很麻烦，因为即使在去除停用词后，数据中仍然可能存在无关文本。使用良好的数据准备方法会在应用建模技术时提供很多有用的信息。

**提示 #5: 探索和尝试**

在对数据进行预处理之前，你需要了解你的数据。不了解数据的具体情况，你可能会不小心删除掉那些在分析中可能有用的文本。有许多标准方法和词典用于去除停用词和给单词分配重要性，但这些方法可能适用于你的数据，也可能不适用。例如，关于政府的数据可能包含许多像“rule”（规则）、“govern”（治理）和“politics”（政治）这样的词汇，这些词汇你可能会认为是不必要的而想要删除。评论中可能在开头包含很多“hi”，但对于评论数据集来说可能没有用处。查看数据源并阅读一些文本，了解你为分析定义的过程是否能够正确地将数据转化为有用的信息，是一个很好的步骤。探索文本数据的另一种方式是创建文档词项矩阵。文档词项矩阵是一个 m*n 矩阵，其中列的数量表示整个数据集中唯一单词的总数，行的数量表示数据点的总数。因此，每个单元格表示该数据点中某个特定单词的计数。这是一个非常大的矩阵，随后会被压缩成词频矩阵。从这个文档词项矩阵中，可以计算数据集中每个单词的总出现次数，这正是词频矩阵所储存的内容。文档词项矩阵的其他用途包括了解单词之间的关联、使用词频绘制词云，或通过建模技术预测模式。这种探索将进一步增强你对如何进行文本数据分析的信心。

**提示 #6：深入挖掘并亲自实践**

每个机器学习和数据科学项目的主要目标是发现数据中那些难以发现的模式。你需要寻找这些有趣的模式，如果你害怕这一步，那你就不是真正的数据科学家。这个过程可以简单到只需将一个简单的分类器应用于数据点，并查看其性能。这将设定一个基准，同时给你一个数据预测能力的概念。有时，数据可能存在偏差或预测能力差，数据质量检查可以帮助定义这一点。例如，如果我基于标签收集 Twitter 数据，我可以将收集的数据分为训练集和测试集，将标签作为依赖特征。如果我的预测性能不理想，我需要回到几步前，找出低性能的原因，然后检查我如何收集数据或清理数据，具体情况而定。获得模式的其他方法包括关联。例如，某些数据点可能彼此相关，而其他数据点可能具有相似或相反的模式。如果用于文本挖掘的推文中可能会有重复推文，因为转发或对评论的辩论。处理数据也会暴露出诸如处理讽刺或传达混合表达的评论等问题。如果不仔细检查数据，很难知道你的数据有多少受到这些问题的影响，以及是否应该删除这些数据或使用某种技术来处理这种情况。

**提示 #7: 重新工作和重复**

你尝试解决的问题可能不是你公司中的第一个文本挖掘问题，但肯定不是今天世界上第一个文本挖掘问题。很多数据科学家曾处理过与您正在处理的相同或类似的问题，了解他们采用的方法以及他们所做的不同之处，将有助于你将问题解决提升到新的水平。虽然不像其他领域那样频繁，但在文本挖掘领域也有很多分析和项目，包括发现趋势话题、对趋势话题的情感分析、识别对公司或产品的评论、识别抱怨和赞赏等。相同的数据可以解决多个问题。可以探索的复杂问题还包括自然语言处理（NLP）和主题建模。我读到一个相对较新的项目，其中一些学生根据当前对话预测了一组人将讨论的下一个话题。在文本挖掘领域，可能会有许多这样的新项目可以构思和追求，但由于这是一个新兴且热门的领域，请始终参考其他类似的数据和资源，以进一步补充你的分析并得出有力的见解。

**提示 #8: 以视觉方式呈现文本**

如前所述，文本挖掘可以解决许多问题，并且可以从同一数据中解决多个问题。面对如此多的内容，提出以吸引人的方式展示结果是一种良好的实践。这也是为什么大多数文本挖掘结果已被可视化为词云、情感研究和图形的原因。每项任务都有相应的包和库，包括 R 中的 wordcloud、ggplot2、igraph、text2vec、networkD3 和 plotly，以及 Python 中的 Networkx、matplotlib、plotly。你还可以使用其他先进的可视化工具，如 Tableau 或 Power BI，以更多的方式展示数据。

**结论：路线图**

结果可视化并不是文本挖掘项目的最终步骤。由于文本来自在线来源，因此它不断变化，捕获的数据也在变化。随着数据的变化，见解也在变化，因此，当项目完成并被接受时，应不断更新新的数据和见解。这些见解可以随着变化的速度进一步丰富。随着时间的推移，变化也可以作为进展的度量来捕捉。这成为另一个需要解决的纵向问题。除了可以用文本数据解决的问题，文本挖掘并非易事。当你创建一个数据收集、清洗和分析的路线图时，可能会遇到一些障碍。这些障碍可能包括决定是处理单个词频还是使用词组（即 n-grams），或创建自己的可视化方法来展示结果，或管理内存。同时，文本挖掘领域也在不断出现新的项目。最好的学习方式是亲自面对问题，从解决问题的经验中学习。希望这篇文章能激励你进入文本世界，开始挖掘有价值的信息。

**简介：[Chaitanya Sagar](https://www.linkedin.com/in/chaitanyasagar/)** 是[Perceptive Analytics](http://www.perceptive-analytics.com/)的创始人兼首席执行官。Perceptive Analytics 被 Analytics India Magazine 评选为值得关注的十大分析公司之一。该公司致力于电子商务、零售和制药公司的市场分析。

**相关：**

+   前 10 名 R 语言机器学习视频

+   使用 R 学习广义线性模型（GLM）

+   缺失数据解决方案：使用 R 进行插补

* * *

## 我们的前三大课程推荐

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 1\. [谷歌网络安全证书](https://www.kdnuggets.com/google-cybersecurity) - 快速进入网络安全职业生涯。

![](img/e225c49c3c91745821c8c0368bf04711.png) 2\. [谷歌数据分析专业证书](https://www.kdnuggets.com/google-data-analytics) - 提升你的数据分析能力

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 3\. [谷歌 IT 支持专业证书](https://www.kdnuggets.com/google-itsupport) - 支持你的组织的 IT 工作

* * *

### 更多相关主题

+   [用自动化文本总结入门](https://www.kdnuggets.com/2019/11/getting-started-automated-text-summarization.html)

+   [开始使用语言模型的 5 个技巧](https://www.kdnuggets.com/5-tips-for-getting-started-with-language-models)

+   [用 PyTest 入门：轻松编写和运行 Python 测试](https://www.kdnuggets.com/getting-started-with-pytest-effortlessly-write-and-run-tests-in-python)

+   [用 Python 生成器入门](https://www.kdnuggets.com/2023/02/getting-started-python-generators.html)

+   [用 5 个步骤开始学习 Python 数据结构](https://www.kdnuggets.com/5-steps-getting-started-python-data-structures)

+   [用 Python 进行数据科学入门](https://www.kdnuggets.com/getting-started-with-python-for-data-science)
