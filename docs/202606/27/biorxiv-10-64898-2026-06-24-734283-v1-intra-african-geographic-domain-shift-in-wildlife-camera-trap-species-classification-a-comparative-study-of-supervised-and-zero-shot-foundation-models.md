---
title: "Intra-African Geographic Domain Shift in Wildlife Camera Trap Species Classification: A Comparative Study of Supervised and Zero-Shot Foundation Models"
title_zh: 非洲内部野生动物相机陷阱物种分类的地理域偏移：监督模型与零样本基础模型的比较研究
authors: "Nanduri, N., Ogundare, J., Anderson, G."
date: 2026-06-25
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.24.734283v1.full.pdf"
tags: ["query:cv"]
score: 8.0
evidence: 评估开源视觉基础模型在域迁移下的表现
tldr: 非洲不同区域相机陷阱数据存在地理域迁移，影响物种分类泛化。本研究首次系统评估内非域迁移，比较BEiTV2监督微调、DINOv2+FAISS检索和BioCLIP零样本三种模型，在Snapshot Kgalagadi、Kruger及博茨瓦纳照片三个测试集进行八项实验，涵盖域内基线、跨集迁移、数据规模、MegaDetector预处理、灰度彩色及逐物种分析。结果：零样本模型在跨域任务中表现竞争力，监督模型随训练数据增加显著提升；不同物种鲁棒性差异大，部分物种性能严重下降。本研究为缺乏新标注数据时部署模型提供实证指导，填补内非域迁移研究空白。
source: biorxiv
selection_source: fresh_fetch
motivation: 探究非洲内部不同区域间相机陷阱物种分类模型的跨区域泛化能力，首次系统评估地理域迁移的影响。
method: 采用BEiTV2监督微调、DINOv2+FAISS检索和BioCLIP零样本三种模型，在三个南方非洲测试集上进行八项对比实验。
result: 零样本模型在跨域任务中表现竞争力，但监督模型随数据量增加表现提升；不同物种对域迁移鲁棒性差异显著，部分物种性能严重下降。
conclusion: 首次实证内非域迁移特征，建议根据数据可用性选择模型，零样本方法适合无标签新区域，监督方法在数据充足时更优。
---

## 摘要
诸如Snapshot Safari等相机陷阱网络已生成非洲数百万张标记野生动物图像，使得能够训练深度学习模型进行自动物种分类。然而，将在一个非洲区域训练的模型部署到另一个区域的效果仍知之甚少。据我们所知，本研究首次使用人工智能的机器学习子领域，系统评估了非洲大陆内野生动物相机陷阱物种分类中的地理域偏移。我们使用三种模型架构，每种以不同方式与Snapshot Serengeti交互：BEiTV2在Serengeti图像上微调作为监督基线；DINOv2与FAISS结合使用Serengeti图像作为检索索引，无需任何权重更新；BioCLIP是真正的零样本基础模型，未接收任何Serengeti训练数据。然后，所有三个模型在两个南部非洲测试集（Snapshot Kgalagadi和Snapshot Kruger）以及博茨瓦纳本地收集的野生动物照片上进行评估。我们进行了八项实验，涵盖域内基线、跨数据集迁移、数据缩放、MegaDetector预处理、灰度与彩色图像条件以及逐物种迁移分析。这项工作首次对监督和零样本架构下非洲内部域偏移进行了实证刻画，并为需要在南部非洲多样化生态系统中部署模型而无需收集新标记数据的保护AI实践者提供了实用指导。

## Abstract
Camera trap networks such as Snapshot Safari have generated millions of labelled wildlife images across Africa, enabling the training of deep learning models for automated species classification. However, deploying models trained in one African region to another remains poorly understood. To the best of our knowledge, this study presents the first systematic evaluation of geographic domain shift within the African continent for wildlife camera trap species classification, using the Machine Learning sub-field of Artificial Intelligence. We use three model architectures, each interacting with Snapshot Serengeti in a different way: BEiTV2is fine-tuned on Serengeti images as a supervised baseline; DINOv2 with FAISS uses Serengeti images as a retrieval index without any weight updates; and BioCLIP is a true zero-shot foundation model that receives no Serengeti training data at all. All three are then evaluated on two Southern African test sets, Snapshot Kgalagadi and Snapshot Kruger, as well as on locally collected wildlife photographs from Botswana. We conduct eight experiments covering in-domain baselines, cross-dataset transfer, data scaling, MegaDetector preprocessing, grayscale vs. colour image conditions, and per-species transfer analysis. This work provides the first empirical characterisation of intra-African domain shift across both supervised and zero-shot architectures, and offers practical guidance for conservation AI practitioners who need to deploy models across the diverse ecosystems of Southern Africa without collecting new labelled data.

---

## 论文详细总结（自动生成）

好的，作为资深学术论文分析助手，我将基于您提供的论文内容，对这篇关于非洲内部地理域偏移的研究进行结构化、深入的总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

**研究动机**：
- **实际应用瓶颈**：非洲的 Snapshot Safari 等相机陷阱网络已积累了数百万张标记图像，自动化物种分类变得至关重要。然而，将在一个区域（如东非的塞伦盖蒂）训练的深度学习模型直接部署到另一个区域（如南部非洲的克鲁格或卡拉哈迪）时，性能会大幅下降，这一现象被称为**地理域偏移**。这严重阻碍了AI工具在非洲不同生态系统间的实际部署和应用。
- **研究空白**：现有的域偏移研究主要集中在北美洲内部或洲际间（如非洲到美洲）。对于**非洲内部**，即生态系统虽有差异但仍共享部分物种的自然保护区之间的域偏移，缺乏系统性的评估。尤其对于南部非洲的保护工作者，他们需要可靠的工具，但现有的模型大多基于东非数据进行训练。

**整体含义**：
该论文是**首次系统性地评估非洲内部地理域偏移**对野生动物物种分类的影响。它对比了三种完全不同的AI模型范式在跨区域部署时的表现，旨在为保护实践者提供关于如何在缺少新区域标记数据的情况下，选择最稳健模型的实证指导和实践建议。

### 2. 论文提出的方法论

**核心思想**：
通过对比三种代表不同“交互方式”的模型，来分离和量化域偏移对不同范式的影响：
1.  **监督微调模型**：依赖特定域（塞伦盖蒂）的标记数据进行训练。
2.  **基于检索的零样本模型**：使用源域（塞伦盖蒂）的图像作为“检索库”，无需更新模型权重。
3.  **纯零样本基础模型**：完全不接触任何训练数据，仅基于视觉与文本的通用知识进行推理。

**关键技术细节**：
- **BEiTV2（监督基线）**：
    - **过程**：使用在ImageNet-22k上预训练的BEiTV2模型，针对Snapshot Serengeti的17个物种类别进行全参数端到端微调。
    - **核心**：模型学习区分特定于Serengeti环境的物种判别特征。

- **DINOv2 + FAISS（检索式零样本）**：
    - **过程**：
        1.  **建库**：使用DINOv2 ViT-Large模型提取所有Serengeti训练图像的1024维特征向量，并存储在FAISS索引中（IndexFlatIP，用于余弦相似度搜索）。
        2.  **查询**：在测试时，对被测图像提取相同维度特征，与索引中所有特征进行最近邻（k=1）搜索。预测标签即为最相似Serengeti图像的物种标签。
    - **核心**：模型无需任何训练，仅通过视觉特征相似性进行推理，避免了域特定的权重更新。

- **BioCLIP（纯零样本）**：
    - **过程**：使用在生物图像上预训练的BioCLIP模型。对于目标测试集中的每个物种，生成文本提示“a photo of a [species name]”，并通过模型编码。测试图像的嵌入与所有物种的文本嵌入进行余弦相似度比较，相似度最高的物种即为预测结果。
    - **核心**：完全零样本，不依赖任何源域或目标域的训练图像，仅依赖其生物预训练知识和文本语义。

### 3. 实验设计

**数据集**：
- **源域（训练集）**: **Snapshot Serengeti** (东非坦桑尼亚)，约7.1M张图像。用于BEiTV2训练、DINOv2的检索库。
- **目标域（测试集）**:
    - **Snapshot Kgalagadi** (博茨瓦纳/南非)：干旱稀树草原，5个共享物种，146张测试图像。
    - **Snapshot Kruger** (南非)：混合林地稀树草原，14个共享物种，1468张测试图像。
    - **Local Botswana Images** (博茨瓦纳)：手持相机拍摄的照片，6个物种，316张测试图像。代表图像格式的域偏移。

**基准测试（Benchmark）**：
- 自身设计的“域内基线”（Experiment 1），即所有模型在同一数据集（Serengeti）上测试，作为性能上限的参照点。

**对比方法**：
- 直接对比了三种不同范式的模型：
    - **BEiTV2** (监督式)
    - **DINOv2 + FAISS** (检索式零样本)
    - **BioCLIP** (纯零样本)

**评估指标**：
- **主要指标**：宏平均F1（Macro F1），为平衡稀有物种和常见物种的影响。
- **其他指标**：准确率（Accuracy）、精确率（Precision）、召回率（Recall）、逐F1分数、McNemar检验（统计显著性）、最大均值差异（MMD，量化域距离）。

### 4. 资源与算力

论文中明确提到：
> “All measurements are taken on the same hardware (NVIDIA GeForce RTX 3070 Laptop GPU with 8 GB VRAM, 16 GB system RAM).”

因此，所有实验均在一块**NVIDIA GeForce RTX 3070笔记本电脑GPU（8GB显存）** 上完成。但论文未明确说明模型训练（如BEiTV2微调）或推理的总时长。

### 5. 实验数量与充分性

**实验数量**：
论文设计了**8项**实验，覆盖了多个维度：
1.  域内基线（Serengeti）
2.  跨域迁移（Serengeti → Kgalagadi）
3.  跨域迁移（Serengeti → Kruger）
4.  跨域迁移（Serengeti → 博茨瓦纳照片）
5.  数据缩放分析（BEiTV2训练数据量对性能的影响）
6.  MegaDetector预处理效果
7.  灰度vs彩色图像鲁棒性
8.  逐物种性能分析

**充分性与公平性**：
- **充分性**：实验覆盖全面，从最基本的域内性能到复杂的域迁移、数据规模影响、图像预处理、颜色鲁棒性等，设计较为全面。特别是对三种不同范式的对比，很好地回答了他们提出的问题。
- **公平性**：比较相对公平。BEiTV2和DINOv2都能访问Serengeti数据（一个用于训练，一个用于构建检索库），而BioCLIP作为纯零样本模型，这本身就构成了一个有意义的比较。超参数设置（如表2-4）均有明确说明，基准参照清晰。统计分析（McNemar’s test）的使用也增强了结论的可靠性。
- **局限性**：测试集（尤其是Kgalagadi和博茨瓦纳照片）样本量较小，可能导致置信区间较宽。博茨瓦纳数据集可能存在相同个体重复出现的问题，对结果解读有影响。

### 6. 论文的主要结论与发现

1.  **DINOv2 + FAISS 表现最优、最稳健**：作为零样本模型，它在所有测试集（包括跨域场景）中获得了最高或接近最高的宏F1分数，且对灰度图像最鲁棒，证明了其强大的域外泛化能力。
2.  **监督模型（BEiTV2）域偏移损失最大**：在跨域场景中，其准确率出现断崖式下跌（如Serengeti→ Kgalagadi下降55.54个百分点）。这表明监督微调学习到的特征高度依赖于源域背景。
3.  **监督训练优势不总是存在**：在Kruger测试集上，监督模型BEiTV2与纯零样本模型BioCLIP的准确率在统计上无显著差异（~45%）。这表明，当域偏移明显时，投入大量标记数据进行监督训练的收益可能甚微。
4.  **数据缩放效果跨域后减**：增加更多源域（Serengeti）的数据能显著提升域内性能，但对跨域性能提升有限，呈现更早的饱和趋势。往一个地方加更多数据，无助于解决另一个地方的问题。
5.  **图像格式域偏移存在天花板**：从相机陷阱照片到手持照片的域偏移，无法通过增加相机陷阱训练数据来解决，表明模型过度拟合了特定采集设备导致的图像格式。
6.  **MegaDetector预处理（裁剪）效果巨大**：去除背景的MegaDetector裁剪可以显著提升跨域性能（尤其是BEiTV2），这表明很大一部分域偏移源于场景背景，而非动物本身。
7.  **物种差异性大**：一些物种（如鸵鸟、大象）对各种模型的域迁移鲁棒性高，而另一些（如弯角羚的混淆物种）则极易被误判。

### 7. 优点

1.  **首次系统性研究内非域偏移**：填补了该领域的一个关键空白，具有重要的实际应用价值。
2.  **模型范式对比精妙**：巧妙设计了三种与源域数据交互方式完全不同的模型，能够精准分离出监督、检索和纯零样本这三种策略在面对域偏移时的优劣势。
3.  **实验设计全面且严谨**：8个实验从多个角度解析问题，使用了严格的统计检验（McNemar’s test）来验证性能差异的显著性。
4.  **实践导向性强**：得出的结论，如“监督泛化有限”、“零样本模型更稳健”、“数据缩放效果不理想”，对于指导现实世界中的AI部署具有重要意义。

### 8. 不足与局限

1.  **测试集规模较小**：Kgalagadi（146张）和博茨瓦纳照片（316张）的测试集规模较小，导致置信区间较宽，可能会影响某些结论的精度和泛化能力。
2.  **博茨瓦纳数据集的局限性**：该数据集存在同一动物可能出现在多张图片中的问题，使测试样本非独立，从而可能高估模型性能。
3.  **未探索多区域联合训练**：论文只探索了在单一源域（Serengeti）上进行监督训练，未考虑将多个区域的数据集合起来进行训练的潜在效果，这可能是解决域偏移的有效方法。
4.  **MMD预测能力有限**：论文发现，常用的域距离度量MMD并不能预测跨域分类性能。这指出，寻找更好的域偏移代理指标仍是未来需要解决的问题。
5.  **未提及模型幻觉或安全风险**：论文主要关注分类准确率，未讨论模型在未知物种或错误场景下可能产生的错误输出（类似于AI幻觉）以及对野生动物保护决策可能带来的风险。
6.  **资源开销问题**：虽提及了推理时间，但未讨论DINOv2 + FAISS构建和维护大规模向量索引所需的内存和存储成本，这在实际部署中也是需要考虑的因素。

（完）
