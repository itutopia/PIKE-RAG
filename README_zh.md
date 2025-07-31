<p align="center">
    <img src="./docs/source/images/logo/PIKE-RAG_horizontal_black-font.svg" alt="PIKE-RAG" style="width: 80%; max-width: 100%; height: auto;">
</p>

<p align="center">
    <a href="https://pike-rag.azurewebsites.net/">🌐在线演示</a>
    <a href="https://arxiv.org/abs/2501.11551">📊技术报告</a>
</p>

[![License](https://img.shields.io/github/license/microsoft/PIKE-RAG)](https://github.com/microsoft/PIKE-RAG/blob/main/LICENSE)
[![CodeQL](https://github.com/microsoft/PIKE-RAG/actions/workflows/github-code-scanning/codeql/badge.svg)](https://github.com/microsoft/PIKE-RAG/actions/workflows/github-code-scanning/codeql)
[![Release](https://img.shields.io/github/v/release/microsoft/PIKE-RAG)](https://github.com/microsoft/PIKE-RAG/releases)
[![ReleaseDate](https://img.shields.io/github/release-date-pre/microsoft/PIKE-RAG)](https://github.com/microsoft/PIKE-RAG/releases)
[![Commits](https://img.shields.io/github/commits-since/microsoft/PIKE-RAG/latest/main)](https://github.com/microsoft/PIKE-RAG/commits/main)
[![Pull Requests](https://img.shields.io/github/issues-pr/microsoft/PIKE-RAG)](https://github.com/microsoft/PIKE-RAG/pulls)
[![Issues](https://img.shields.io/github/issues/microsoft/PIKE-RAG)](https://github.com/microsoft/PIKE-RAG/issues)

# PIKE-RAG：专用知识和基本原理增强生成

## 为什么选择PIKE-RAG？

近年来，检索增强生成（RAG）系统在通过外部检索扩展大型语言模型（LLM）的能力方面取得了重大进展。然而，这些系统在满足现实世界工业应用的复杂和多样化需求方面仍然面临挑战。仅依靠直接检索不足以从专业语料库中提取深层领域特定的知识并进行逻辑推理。为了解决这个问题，我们提出了PIKE-RAG（sPecIalized KnowledgE and Rationale Augmented Generation）方法，该方法侧重于提取、理解和应用特定领域的知识，同时构建连贯的推理逻辑，逐步引导LLM做出准确的反应。

<p align="center">
    <img src="docs/source/images/readme/pipeline.png" alt="PIKE-RAG框架概述" style="width: 80%; max-width: 100%; height: auto;">
</p>

PIKE-RAG框架主要由几个基本模块组成，包括文档解析、知识提取、知识存储、知识检索、知识组织、知识中心推理和任务分解与协调。通过调整主模块内的子模块，可以实现专注于不同功能的RAG系统，以满足现实世界场景的不同需求。
例如，在搜索患者的历史病历时，它侧重于事实信息检索能力。主要挑战是：（1）知识的理解和提取往往受到不恰当的知识分割的阻碍，破坏了语义连贯性，导致检索过程复杂而低效；（2）常用的基于嵌入的知识检索受到嵌入模型对齐专业术语和别名的能力的限制，降低了系统的准确性。通过PIKE-RAG，我们可以在知识提取过程中使用上下文感知分割技术、自动术语标签对齐技术和多粒度知识提取方法来提高知识提取和检索的准确性，从而增强事实信息检索能力，如下图所示。

<p align="center">
    <img src="docs/source/images/readme/L1_pipeline.png" alt="一条专注于事实信息检索的管道" style="width: 80%; max-width: 100%; height: auto;">
</p>

对于合理的治疗计划和患者应对措施建议等复杂任务，需要更高级的能力：需要强大的领域特定知识来准确理解任务，有时还需要合理地分解任务；潜在趋势预测还需要先进的数据检索、处理和组织技术；而多代理规划也有助于考虑创造力和依赖性。在这种情况下，可以初始化下面更丰富的管道来实现这一点。

<p align="center">
    <img src="docs/source/images/readme/L4_pipeline.png" alt="注重基于事实的创新和生成的管道" style="width: 80%; max-width: 100%; height: auto;">
</p>

在公共基准测试中，PIKE-RAG在几个多跳问答数据集上表现出了出色的性能，如HotpotQA、2VikiMultiHopQA和MuSiQue。与现有的基准方法相比，PIKE-RAG在准确性和F1分数等指标上表现出色。在HotpotQA数据集上，PIKE-RAG的准确率为87.6%，在2WikiMultiHopQA上达到82.0%，在更具挑战性的MuSiQue数据集上达到59.6%。这些结果表明，PIKE-RAG在处理复杂的推理任务方面具有显著优势，特别是在需要集成多源信息和执行多步推理的场景中。
PIKE-RAG已经过测试，并在工业制造、采矿和制药等领域显著提高了问答准确性。未来，我们将继续探索其在更多领域的应用。此外，我们将继续探索其他形式的知识和逻辑，以及它们对特定场景的最佳适应。
## 更多详细信息

- 📊 [技术报告](https://arxiv.org/abs/2501.11551) 将说明工业RAG问题的分类，介绍PIKE-RAG中的主要组件，并在公共基准中展示一些实验结果。
- 🌐 [在线演示](https://pike-rag.azurewebsites.net/) 是我们用于L2 RAG任务的知识感知分解管道的一个演示案例。

## 快速入门

1. 克隆此仓库并设置Python环境，请参阅本文档[this document](docs/guides/environment.md);
2. 创建一个.env文件来保存您的端点信息（以及一些其他环境变量，如果需要），请参阅本文档 [this document](docs/guides/env_file.md);
3. 修改yaml配置文件并尝试examples/下的脚本，请参阅本文档 [this document](docs/guides/examples.md);
4. 建立自己的管道和/或添加自己的组件!

🚀 此处已准备好文件 [here](docs/guides/musique_example.md)以便在MuSiQue上快速重新制作实验，如技术报告所示！

## 捐助

该项目欢迎各方提供意见和建议。大多数贡献都要求您同意《贡献者许可协议》（CLA），声明您有权并实际授予我们使用您的贡献的权利。有关详细信息，请访问https://cla.opensource.microsoft.com.
当您提交拉取请求时，CLA机器人将自动确定您是否需要提供CLA并适当地装饰PR（例如，状态检查、评论）。只需按照机器人提供的说明进行操作。您只需使用我们的CLA在所有存储库中执行一次即可。
该项目采用了[微软开源行为准则](https://opensource.microsoft.com/codeofconduct/)。 有关更多信息，请参阅行为准则 [常见问题解答](https://opensource.microsoft.com/codeofconduct/faq/) 或联系 [opencode@microsoft.com](mailto:opencode@microsoft.com)如有任何其他问题或意见。


## 商标
此项目可能包含项目、产品或服务的商标或徽标。授权使用微软商标或徽标须遵守[微软的商标和品牌指南](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).。在本项目的修改版本中使用Microsoft商标或徽标不得造成混淆或暗示Microsoft赞助。任何使用第三方商标或徽标的行为均受这些第三方政策的约束。

