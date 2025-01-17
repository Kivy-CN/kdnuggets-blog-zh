# NExT-GPT 介绍：任何到任何的多模态大语言模型

> 原文：[`www.kdnuggets.com/introduction-to-nextgpt-anytoany-multimodal-large-language-model`](https://www.kdnuggets.com/introduction-to-nextgpt-anytoany-multimodal-large-language-model)

![NExT-GPT 介绍：任何到任何的多模态大语言模型](img/759e062253b4a9e3c294ac44bcd62830.png)

图片由编辑提供

近年来，生成式 AI 研究的发展改变了我们的工作方式。从内容开发、工作规划、寻找答案，到创建艺术作品，现在都可以通过生成式 AI 实现。然而，每个模型通常适用于某些特定的用例，例如，GPT 用于文本到文本，Stable Diffusion 用于文本到图像，以及许多其他模型。

* * *

## 我们的前三个课程推荐

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 1\. [Google 网络安全证书](https://www.kdnuggets.com/google-cybersecurity) - 快速进入网络安全职业生涯。

![](img/e225c49c3c91745821c8c0368bf04711.png) 2\. [Google 数据分析专业证书](https://www.kdnuggets.com/google-data-analytics) - 提升你的数据分析能力

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 3\. [Google IT 支持专业证书](https://www.kdnuggets.com/google-itsupport) - 支持你组织的 IT 需求

* * *

能够执行多种任务的模型称为多模态模型。许多前沿研究正在向多模态方向发展，因为它在许多条件下已被证明是有用的。这也是为什么多模态研究中令人兴奋的一个方向是 [NExT-GPT](https://arxiv.org/pdf/2309.05519.pdf)。

NExT-GPT 是一个可以将任何东西转换为任何东西的多模态模型。那么，它是如何工作的呢？让我们进一步探索。

# NExT-GPT 介绍

NExT-GPT 是一个任何到任何的多模态 LLM，能够处理四种不同类型的输入和输出：文本、图像、视频和音频。该研究由 [新加坡国立大学的 NExT++研究小组](https://www.nextcenter.org/) 发起。

NExT-GPT 模型的整体表示如下面的图像所示。

![NExT-GPT 介绍：任何到任何的多模态大语言模型](img/5f3b1d0fe21edbaefa094c994bb7be0e.png)

NExT-GPT LLM 模型 ([Wu *et al*. (2023)](https://arxiv.org/pdf/2309.05519.pdf))

NExT-GPT 模型由三个部分组成：

1.  为来自各种模态的输入建立编码器，并将其表示为 LLM 可以接受的类语言输入，

1.  利用开源 LLM 作为核心，处理输入以进行语义理解和推理，并添加独特的模态信号，

1.  将多模态信号提供给不同的编码器，并将结果生成到适当的模态。

NExT-GPT 推理过程的一个示例可以在下面的图像中看到。

![NExT-GPT 介绍：任何到任何的多模态大语言模型](img/36bfc2d94328d91f1f314f6955d82673.png)

NExT-GPT 推理过程 ([Wu *et al*. (2023)](https://arxiv.org/pdf/2309.05519.pdf))

从上面的图像中我们可以看到，根据我们需要的任务，编码器和解码器会切换到适当的模态。这个过程之所以能发生，是因为 NExT-GPT 利用了一个叫做模态切换指令调优的概念，使得模型能够符合用户的意图。

研究人员尝试了多种模态组合的实验。总体而言，NExT-GPT 的性能可以在下图中总结。

![NExT-GPT 简介：任意到任意的多模态大型语言模型](img/ddbf67c258e36190111962e38b0edf0c.png)

NExT-GPT 总体性能结果 ([Wu *et al*. (2023)](https://arxiv.org/pdf/2309.05519.pdf))

NExT-GPT 的最佳表现是文本和音频输入生成图像，其次是文本、音频和图像输入生成图像结果。表现最差的是文本和视频输入生成视频输出。

下图展示了 NExT-GPT 能力的一个示例。

![NExT-GPT 推理过程](img/635190c69b67ec01e1b628ac9c1d7d4b.png)

NExT-GPT 的文本到文本+图像+音频（来源：[NExT-GPT 官网](https://next-gpt.github.io/)）

上述结果显示，与 NExT-GPT 互动可以生成符合用户意图的音频、文本和图像。数据显示 NExT-GPT 的表现相当出色，且非常可靠。

下图展示了 NExT-GPT 的另一个示例。

![NExT-GPT 简介：任意到任意的多模态大型语言模型](img/4b238e3be3fc5a3039d9c824af04e7a2.png)

文本+图像到文本+音频的 NExT-GPT（来源：[NExT-GPT 官网](https://next-gpt.github.io/)）

上图显示了 NExT-GPT 可以处理两种模态以生成文本和音频输出。这显示了模型的多功能性。

如果你想尝试这个模型，你可以从他们的[GitHub 页面](https://github.com/NExT-GPT/NExT-GPT)设置模型和环境。此外，你可以在以下[页面](https://4c5b3bd137f4eec297.gradio.live/)试用演示。

# 结论

NExT-GPT 是一个多模态模型，接受文本、图像、音频和视频的数据输入，并生成相应的输出。该模型通过利用特定的编码器处理模态，并根据用户的意图切换到适当的模态。性能实验结果显示良好，且具有很大的应用潜力。

**[](https://www.linkedin.com/in/cornellius-yudha-wijaya/)**[Cornellius Yudha Wijaya](https://www.linkedin.com/in/cornellius-yudha-wijaya/)** 是一位数据科学助理经理和数据撰稿人。在全职工作于 Allianz Indonesia 期间，他喜欢通过社交媒体和写作媒体分享 Python 和数据技巧。Cornellius 在各种 AI 和机器学习话题上撰写文章。

### 更多相关内容

+   [带有视觉和语言的多模态基础学习](https://www.kdnuggets.com/2022/11/multimodal-grounded-learning-vision-language.html)

+   [多模态模型解析](https://www.kdnuggets.com/2023/03/multimodal-models-explained.html)

+   [终极开源大型语言模型生态系统](https://www.kdnuggets.com/2023/05/ultimate-opensource-large-language-model-ecosystem.html)

+   [探索 Zephyr 7B：最新大型语言模型的全面指南](https://www.kdnuggets.com/exploring-the-zephyr-7b-a-comprehensive-guide-to-the-latest-large-language-model)

+   [免费精通课程：成为大型语言模型专家](https://www.kdnuggets.com/ree-mastery-course-become-a-large-language-model-expert)

+   [掌握大型语言模型微调的 7 个步骤](https://www.kdnuggets.com/7-steps-to-mastering-large-language-model-fine-tuning)
