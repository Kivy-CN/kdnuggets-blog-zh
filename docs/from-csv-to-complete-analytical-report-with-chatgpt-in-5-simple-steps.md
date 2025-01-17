# 从 CSV 到完整分析报告，只需 5 个简单步骤

> 原文：[`www.kdnuggets.com/from-csv-to-complete-analytical-report-with-chatgpt-in-5-simple-steps`](https://www.kdnuggets.com/from-csv-to-complete-analytical-report-with-chatgpt-in-5-simple-steps)

![从 CSV 到完整分析报告，只需 5 个简单步骤](img/e4fefdb73466a6000a5e3db7cb973993.png)

图片由 [rawpixel.com](https://www.freepik.com/free-vector/business-performance-analysis-with-graphs_3585415.htm#query=analytical%20report&position=9&from_view=search&track=ais&uuid=89531592-371d-4c87-913c-d56751a40245%22) 提供，来源于 [Freepik](https://www.freepik.com/)

无论你从事什么业务，在数据驱动的时代，了解如何分析数据比以往任何时候都更为重要。数据分析使企业能够保持竞争力，并提供做出更好决策的能力。

* * *

## 我们的前 3 个课程推荐

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 1\. [谷歌网络安全证书](https://www.kdnuggets.com/google-cybersecurity) - 快速开启网络安全职业生涯。

![](img/e225c49c3c91745821c8c0368bf04711.png) 2\. [谷歌数据分析专业证书](https://www.kdnuggets.com/google-data-analytics) - 提升你的数据分析技能

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 3\. [谷歌 IT 支持专业证书](https://www.kdnuggets.com/google-itsupport) - 支持你的组织在 IT 方面

* * *

数据分析的重要性驱使每个人都知道如何进行数据分析。然而，有时进行数据分析会花费过多时间。这就是为什么我们可以依赖 ChatGPT 来从数据文件中创建完整报告。

本文将探讨五个简单步骤，使用你的 CSV 文件创建完整的分析报告。这五个步骤包括：

第一步：导入 CSV 文件

第二步：数据摘要和预处理

第三步：数据分析

第四步：数据可视化

第五步：报告生成

作为前提条件，本文假设读者已经订阅了 ChatGPT Plus。考虑到这一点，让我们开始吧。

# 导入 CSV 文件

第一步是准备你要分析的 CSV 文件并创建报告。这个文件可以来自任何可信的来源，但本文将使用来自[Kaggle](https://www.kaggle.com/datasets/barun2104/telecom-churn)的电信流失数据集。

确保数据结构化、组织良好，并且有明确的标题。如果你有特定的目标需要分析，别忘了在文件中包含这些数据。在我们的示例中，我们将尝试对流失列进行分析。

数据准备好后，将其附加到 ChatGPT 上，让模型进行处理。

# 数据摘要和预处理

下一步是从我们的 CSV 文件中获取数据摘要并进行预处理。在上传数据时输入以下提示。

```py
Provide the data summary to this file and perform appropriate data processing for the dataset.
```

上述提示提供了以下结果：

这是你数据集的摘要：

**行数：** 3333

**列数：** 11

**列名称：**

流失

账户周数

合同续签

数据计划

数据使用

客服通话次数

日通话分钟

日通话次数

月度收费

超额费用

漫游分钟

**数据类型**：

整数：流失、账户周数、合同续签、数据计划、客服通话次数、日通话次数

浮点数：数据使用、日通话分钟、月度收费、超额费用、漫游分钟

**缺失值：** 所有列中没有缺失值。

ChatGPT 能够很好地读取数据，并提供了给定的数据集。接下来的结果是 ChatGPT 的数据预处理。

由于数据集中没有缺失值，数据清理和预处理的主要关注点将是：

+   检查数据中是否存在任何异常值或异常情况。

+   如果需要，可以对数据进行归一化或标准化，特别是对于具有连续数值的列。

+   将类别数据转换为适合分析的格式，如有必要。

让我们继续这些步骤。

![从 CSV 到完整的分析报告，ChatGPT 5 个简单步骤](img/239fe36f4be7c43d6f9686a3f1c2580c.png)

箱型图提供了数据集中每个数值列潜在异常值的视觉概览。以下是一些观察结果：

+   账户周数、客服通话次数、日通话次数：这些列显示了相当正常的分布，但有一些异常值。

+   数据使用、日通话分钟、月度收费、超额费用、漫游分钟：这些列也显示了一些异常值，但考虑到数据的性质，它们似乎在合理范围内。

+   流失、合同续签、数据计划：由于这些列是类别/二进制数据，它们没有显示传统的异常值。

根据这些信息，数据清理和预处理的下一步可能包括：

+   处理异常值：我们可以根据你的具体分析需求和领域知识决定是删除、限制还是以其他方式处理异常值。

+   数据转换：如果需要，我们可以对像日通话分钟、月度收费等列进行归一化或标准化，特别是如果你计划使用对数据规模敏感的算法。

+   类别数据编码：将类别数据转换为适合分析的格式，如有必要进行此类转换。

你可以让 ChatGPT 执行额外的数据清理和预处理步骤，也可以保持现状。对于这个示例，我们将继续下一步。

# 数据分析

接下来，我们将使用 ChatGPT 进行数据分析。数据分析取决于你想要实现的目标。在我们的案例中，我们希望从流失的角度进行数据分析。

我们使用以下提示来执行上述情况的 ChatGPT 数据分析。

```py
Please perform the data analysis based on the data above with respect to the churn data.
```

数据分析可以在以下结果中查看。

为了对流失数据进行数据分析，我们将重点了解不同因素如何与客户流失相关。流失作为一个二进制变量（0 表示无流失，1 表示有流失），通常通过分类方法分析，并通过检查与其他变量的关系。计划如下：

1.  相关性分析：首先，我们将查看每个数值特征与流失的相关性。这可以帮助我们初步了解哪些因素可能与流失更为相关。

1.  统计测试：对于像 ContractRenewal 和 DataPlan 这样的分类变量，我们可以使用统计测试来查看不同类别之间的流失率是否存在显著差异。

1.  视觉分析：我们将创建一些可视化图表来进一步探讨这些关系。这包括比较不同组的流失率以及将关键变量与流失进行绘图。

1.  汇总统计：我们将为不同组提供汇总统计，以查看是否存在明显的均值或分布差异。

我们从相关性分析开始，然后进行下一步。

**与流失的相关性分析**

不同变量与流失的相关性如下（从最强的负相关到最强的正相关）：

负相关：

+   ContractRenewal：最强的负相关。表明未续签合同的客户更可能流失。

+   DataPlan：没有数据计划的客户稍微更可能流失。

+   DataUsage：更高的数据使用略微减少了流失的可能性。

正相关：

+   AccountWeeks，DayCalls：非常弱的正相关，表明对流失的影响很小。

+   RoamMins：漫游分钟数增加与流失可能性略有增加。

+   MonthlyCharge：月费增加略微提高流失率。

+   OverageFee：更高的超额费用与增加的流失有中等的相关性。

+   DayMins：更高的每日分钟数与增加的流失率有中等的相关性。

+   CustServCalls：强正相关。更多的客服电话与更高的流失率相关。

根据这些相关性，似乎合同续签、客服电话、每日分钟数和超额费用等因素与流失关系更为密切。我们可以通过视觉分析和统计测试进一步探讨这些因素，特别是像 ContractRenewal 和 DataPlan 这样的分类变量。

**视觉分析**

![从 CSV 到完整分析报告，ChatGPT 简化五步法](img/bbb1d01c0aaaca87c63ce4de5c317832.png)

可视化图表提供了有关不同变量与流失之间关系的宝贵见解：

根据合同续签和 DataPlan 进行流失分析：

+   ContractRenewal：流失率存在显著差异。未续签合同的客户显示出更高的流失率。

+   DataPlan：根据客户是否拥有数据计划，流失率有明显差异，没有数据计划的客户流失率更高。

数值变量（CustServCalls，DayMins，MonthlyCharge，OverageFee）与流失：

+   CustServCalls：客户服务电话数量较多的客户更倾向于流失。

+   DayMins：更高的每日分钟数与更大的流失可能性相关。

+   每月费用：较高的每月费用与更高的流失率相关。

+   超额费用：较高的超额费用也与更高的流失率相关。

**分析结论**

+   合同续签状态和数据计划的存在是客户流失的重要因素。

+   高使用量（以每日分钟数计算）和高费用（每月费用和超额费用）与更高的流失率相关。

+   客户服务电话数量较多是潜在流失的强指标。

**下一步**

基于这些见解，可以制定针对性的策略来减少流失，例如改善客户服务、修订定价策略或提供合同续签和数据计划订阅的激励。

通过一个提示，我们可以查看 ChatGPT 如何完整地进行数据分析并得出数据洞察。你可以调整分析目标，并从中开始。

# 数据可视化

数据可视化是一项支持活动，有助于提升数据分析和整体报告质量。通过可视化，我们可以拥有更全面的报告来理解数据。

使用以下提示，我们可以利用 ChatGPT 进行数据可视化。

```py
Please perform data visualization **from** the data analysis to explain the data better.
```

为了增强对数据分析结果的理解，我将创建一系列可视化图表，清晰地展示与客户流失相关的关键发现。这些可视化图表包括：

1.  类别变量的条形图：

+   比较有无合同续签的客户流失率。

+   比较有无数据计划的客户流失率。

+   关键数值变量的箱形图：

1.  客户服务电话与流失率。

+   每日通话时间与流失率。

+   每月费用与流失率。

+   超额费用与流失率。

1.  相关性热图：

可视化所有变量与流失的相关性。

![从 CSV 到完整分析报告的 5 个简单步骤](img/12455d91b618c949e1b12ec8479659d7.png)

可视化将展示所有重要图表，概括整个数据集。我们可以要求每个图表提供更详细的描述，你可以尝试自行完成。

# 报告生成

最后一步是基于之前的步骤生成报告。不幸的是，ChatGPT 可能无法捕捉到所有数据分析中的描述和见解，但我们仍可以得到简化版的报告。

使用以下提示生成基于之前分析的 PDF 报告。

```py
Please provide me with the pdf report from the first step to the last step.
```

你将获得包含之前分析的 PDF 链接结果。如果结果不满意或有想更改的地方，请尝试迭代步骤。

# 结论

数据分析是每个人都应掌握的技能，它是当前时代最需要的技能之一。然而，学习如何进行数据分析可能需要很长时间。使用 ChatGPT，我们可以减少这一活动时间。

在这篇文章中，我们讨论了如何通过 5 个步骤从 CSV 文件生成完整的分析报告。ChatGPT 为用户提供了从导入文件到生成报告的端到端数据分析活动。

**[](https://www.linkedin.com/in/cornellius-yudha-wijaya/)**[Cornellius Yudha Wijaya](https://www.linkedin.com/in/cornellius-yudha-wijaya/)**** 是一位数据科学助理经理和数据写作者。在全职工作于 Allianz Indonesia 的同时，他喜欢通过社交媒体和写作媒体分享 Python 和数据技巧。Cornellius 撰写了多种 AI 和机器学习主题。

### 更多相关话题

+   [在 Python 中处理 CSV 文件的 3 种方法](https://www.kdnuggets.com/2022/10/3-ways-process-csv-files-python.html)

+   [5 个简单步骤系列：掌握 Python、SQL、Scikit-learn、PyTorch 等](https://www.kdnuggets.com/5-simple-steps-series-master-python-sql-scikit-learn-pytorch-google-cloud)

+   [用 llamafile 分发和运行 LLMs 的 5 个简单步骤](https://www.kdnuggets.com/distribute-and-run-llms-with-llamafile-in-5-simple-steps)

+   [用 Python 自动化数据清洗的 5 个简单步骤](https://www.kdnuggets.com/5-simple-steps-to-automate-data-cleaning-with-python)

+   [Llama, Llama, Llama: 用你的内容进行本地 RAG 的 3 个简单步骤](https://www.kdnuggets.com/3-simple-steps-to-local-rag-with-your-content)

+   [Python 中的地理编码：完整指南](https://www.kdnuggets.com/2022/11/geocoding-python-complete-guide.html)
