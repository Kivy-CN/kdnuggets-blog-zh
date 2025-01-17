# 7 个使用生成性 AI 构建的项目

> 原文：[`www.kdnuggets.com/2023/08/7-projects-built-generative-ai.html`](https://www.kdnuggets.com/2023/08/7-projects-built-generative-ai.html)

![v](img/c68cb4ab73503ae4fcb15895e171f94a.png)

作者插图 | 来源: Flaticon

要进入数据科学职业市场，认为学位足够获得工作是一个错误。主要建议之一是构建一个强大的个人项目作品集，这可以在从人群中脱颖而出并给招聘人员留下深刻印象方面发挥重要作用。

* * *

## 我们的前三大课程推荐

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 1\. [Google 网络安全证书](https://www.kdnuggets.com/google-cybersecurity) - 快速进入网络安全职业生涯。

![](img/e225c49c3c91745821c8c0368bf04711.png) 2\. [Google 数据分析专业证书](https://www.kdnuggets.com/google-data-analytics) - 提升你的数据分析技能

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 3\. [Google IT 支持专业证书](https://www.kdnuggets.com/google-itsupport) - 支持你的组织的 IT

* * *

随着生成性 AI 工具的出现，如 ChatGPT，标准项目（如物体检测和推荐系统）已经不足以吸引公司的注意。最近几个月，公司正在为能够构建生成性 AI 解决方案的人开设职位。

因此，我们将探索 7 个使用大型语言模型解决任务的项目想法：

1.  创建一个个人作品集网站

1.  个性化语音助手

1.  构建你自己的 AI 翻译器

1.  分析研究论文

1.  创建代码文档

1.  自动化 Powerpoint 演示文稿

1.  评论情感分析

# 1\. 创建一个个人作品集网站

有很多教程解释如何构建数据科学作品集网站，但从零开始没有 HTML 和 CSS 知识可能会让人感到很有压力。我亲自尝试过，当你达成目标时，会感到很大的满足，但找到合适的资源并将所学应用到实践中花了一周时间。

现在，随着大型语言模型的兴起，你不再需要费力气了。你只需有一个好的想法，向 ChatGPT 提问，它将返回你网站的代码。你可以从这样的提示开始：

```py
I decided to build a static website. Can you generate HTML code for building the website? Moreover, I need to have three pages: a page with my name and a short presentation, a page with my data science projects and a page with my work experience. In addition to these pages, I want a vertical navigation menu at the left to move from a page to the other.
```

与其他应用程序一样，你需要明确你想要生成的作品集网站。

项目链接: [使用 ChatGPT 构建数据科学作品集网站](https://medium.com/towards-data-science/how-to-build-a-data-science-portfolio-website-with-chatgpt-e57d29badf7f)

# 2\. 个性化语音助手

在我的个人生活中，我使用 Google Assistant 请求播放不同类型的音乐。例如，“Google，我想听摇滚音乐”，它会立即从 YouTube 音乐中播放一首随机歌曲。比起手动输入歌曲标题，这确实更快捷，而且它收集你的数据越多，就越能学习你的偏好。将这作为个人项目岂不更酷？这个项目可以通过使用 GPT-3 来回答问题和 Whisper API 来转录音频来轻松完成。

项目链接：[使用 GPT 和 Whisper 的个性化语音助手](https://github.com/reese3222/nanoassistant)

# 3\. 构建你自己的 AI 翻译器

你是否厌倦了将文本复制并粘贴到 Google 翻译中？我个人也尝试过使用 Google Chrome 扩展程序来翻译网页上的文本，但当我必须阅读英文 PDF 文件时，仍然会遇到困难。一个可能的替代方案是构建你自己的 AI 应用程序。每天都有新的强大大型语言模型以其令人惊叹的结果让我们惊讶。我们为什么不利用这些模型呢？

这个应用程序可以使用 Hugging Face 创建，该平台提供了许多专门用于语言翻译的模型。例如，你可以选择[这个模型](https://huggingface.co/Helsinki-NLP/opus-mt-en-it/tree/main)，它专注于从英语到意大利语的翻译。在选择了翻译模型后，你可以通过使用 Streamlit 构建一个应用程序来实现这个想法。

项目链接：[构建你自己的 AI 翻译器](https://artificialcorner.com/stop-using-google-translator-build-your-own-ai-application-ea8d3a896ff2)

# 4\. 分析研究论文

在我的研究奖学金期间，我学会了如何快速高效地阅读论文。但仅仅阅读一篇至少 30 页的论文是非常耗时的，而且在每天发布大量论文的情况下，很难跟上研究的进展。为了提高研究生产力，提取学术论文中的相关信息不是更好吗？以下是三种可能对你数据科学领域职业有帮助的用例。

## 论文问答

从文档中生成问题和答案是非常有价值的应用之一。大多数教程使用 Chat-GPT 来创建自动问答会话，但这并不是唯一的解决方案。你也可以使用 LangChain 和 HuggingFace 的 Sentence Transformers 创建你个人化的机器人。步骤如下：

1.  使用 PyPDFLoader 加载 PDF 文档

1.  从文本中提取块

1.  使用 Sentence Transformer 库提取嵌入

1.  构建回答问题的机器人

项目链接：

+   [关于 Chat-GPT API 的问答](https://betterprogramming.pub/building-a-question-answer-bot-with-langchain-vicuna-and-sentence-transformers-b7f80428eadc)

+   [使用 LangChain 和 Sentence Transformers 的问答](https://betterprogramming.pub/building-a-question-answer-bot-with-langchain-vicuna-and-sentence-transformers-b7f80428eadc)

## 总结论文

另一个常见的用例是总结论文。像之前一样，这个任务可以通过生成 AI 工具自动化。可以使用 GPT-3、LangChain 和 Streamlit 构建一个可爱的 web 应用程序。

项目链接: [总结论文](https://medium.com/mlearning-ai/building-a-custom-summarization-app-with-streamlit-and-langchain-11ab19099822)

## 查询多篇论文

如果我们同时总结多篇论文，能够根据问题过滤查询这些摘要会很好。不是很酷吗？利用 LangChain 和 OpenAPI-API 可以非常简单地实现这一点。

项目链接: [查询多篇论文](https://medium.com/mlearning-ai/summarizing-and-querying-multiple-research-papers-with-langchain-fe0bf310926)

# 5\. 创建代码文档

在我最后一次作为数据科学家的工作中，我注意到每天记录代码的重要性。如果你单独工作，你可能不在意。但当你和团队合作时，没有代码文档就很难管理任务。特别是当一个团队成员离开公司，而他/她是唯一理解自己代码的人时，这种情况可能会发生。即使文档非常有用，它也是一项非常无聊且耗时的任务。感谢大型语言模型的兴起，我们可以再次通过 Chat-GPT 创建 Python Docstring 避免这项艰巨的工作。

项目链接: [创建代码文档](https://medium.com/@madhok.simran8/how-to-generate-python-docstring-with-chatgpt-openapi-ed055f302d31)

# 6\. 自动化 PowerPoint 演示文稿

如果你是数据科学家，你肯定遇到过需要为客户准备 PowerPoint 幻灯片的情况。这是另一项耗时的工作，可以借助生成 AI 实现自动化。你可以让 Bing Chat 生成 VBA 代码来创建 PowerPoint 幻灯片，通过明确说明每张幻灯片的背景和信息来实现。

项目链接: [自动化 PowerPoint 演示文稿](https://www.youtube.com/watch?v=zogvDn5Kd8E&ab_channel=MatrixInception)

# 7\. 评论情感分析

在工业界，产品评论的情感分析可以帮助公司了解客户是否喜欢产品，从而改进服务并保持市场竞争力。这是一个经典的数据科学项目，涉及多个步骤：文本预处理、词嵌入和机器学习模型应用。

第一步是最费力的任务，需要对你分析的语言有很好的理解。这个问题可以通过使用 Chat-GPT 快速处理。除了这种分析外，还可以从每条评论中生成优缺点列表、创建改进产品的建议列表等。

项目链接：[评论情感分析](https://medium.com/data-and-beyond/sentiment-analysis-with-chatgpt-openai-and-python-use-chatgpt-to-build-a-sentiment-analysis-ai-2b89158a37f6)

# 最后的想法

就这样！这些是七个生成式 AI 项目，它们可以帮助你提升简历并提高工作效率。我建议你在做这些项目时尽量享受乐趣。受到灵感的驱动，一切皆有可能。如果你有一个想法，尝试将其付诸实践，瞧，你会对最终成果感到满意。感谢阅读。祝你有美好的一天！

**[尤金尼亚·安内洛](https://www.linkedin.com/in/eugenia-anello/)** 目前是意大利帕多瓦大学信息工程系的研究员。她的研究项目专注于将持续学习与异常检测相结合。

### 更多相关话题

+   [8 个内置 Python 装饰器，写出优雅代码](https://www.kdnuggets.com/8-built-in-python-decorators-to-write-elegant-code)

+   [ChatGPT、GPT-4 及更多生成式 AI 新闻](https://www.kdnuggets.com/2023/02/chatgpt-gpt4-generative-ai-news.html)

+   [在生成式 AI 时代，数据科学家仍然需要吗？](https://www.kdnuggets.com/2023/06/data-scientists-still-needed-age-generative-ai.html)

+   [合成数据平台：释放生成式 AI 对结构化数据的力量](https://www.kdnuggets.com/2023/07/synthetic-data-platforms-unlocking-power-generative-ai-structured-data.html)

+   [告别谷歌：生成式 AI 学习路径](https://www.kdnuggets.com/2023/07/free-google-generative-ai-learning-path.html)

+   [谁负责确保生成式 AI 的正确性？](https://www.kdnuggets.com/2023/08/whose-responsibility-get-generative-ai-right.html)
