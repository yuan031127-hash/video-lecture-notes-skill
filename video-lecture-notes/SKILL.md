---
name: video-lecture-notes
description: Use when a user asks to turn technical course videos, recordings, subtitles, slides, PDFs, board work, or lecture images into complete Chinese lecture notes, especially when formulas, diagrams, experiments, timestamps, or Obsidian output must be preserved and a transcript-only summary would be inadequate.
---

# 理工科课程视频讲义

## 核心原则

把课程视频重建为能够脱离原视频独立学习的中文讲义。把语音、字幕、PPT、板书、
公式、图表、实验画面和时间戳视为一组相互校验的证据，绝不只总结转录文本。

始终区分：

- 视频或配套材料明确给出的内容；
- 为改善结构而做的忠实整理；
- 理解当前内容所必需的外部补充；
- 无法可靠确认的信息。

## 开始前

1. 清点视频、音频、字幕、PPT、PDF、讲义、图片、教材章节和术语表。
2. 检查视频时长、音轨质量、字幕可用性、画面类型和多视频顺序。
3. 识别学习者水平、课程章节和用户指定的交付格式；非关键参数缺失时采用默认值，
   不要停下来反复询问。
4. 对超过 90 分钟或包含多个文件的课程，按知识章节分段处理，但保证全部内容都被
   纳入最终讲义。
5. 在建立清单和开始写作前，阅读 [references/content-rules.md](references/content-rules.md)。

## 默认交付

默认创建：

```text
video-lecture-notes-output/
├── lecture-notes.md
├── transcript/
│   ├── transcript-raw.txt
│   ├── transcript-cleaned.md
│   ├── transcript.srt
│   └── terminology-corrections.md
├── frames/
│   ├── keyframes/
│   ├── formulas/
│   ├── diagrams/
│   └── boards/
├── analysis/
│   ├── chapter-map.md
│   ├── concept-inventory.md
│   ├── formula-inventory.md
│   ├── visual-inventory.md
│   └── uncertainty-log.md
└── assets/
```

主要交付物始终是 `lecture-notes.md`。只有用户明确要求时才生成 PDF、DOCX、
Typst、HTML、复习提纲或习题。

需要新建讲义时，复制并填写
[assets/lecture-notes-template.md](assets/lecture-notes-template.md)，不要直接修改模板。

## 执行流程

### 1. 检查并提取媒体信息

- 使用可用的媒体工具读取时长、编码、分辨率、帧率、音轨和字幕轨。
- 对视频提取适合转录的单声道音频；若降噪或归一化，保留原始音频并记录处理。
- 优先使用已有字幕；缺少字幕时生成带分段起止时间的转录。
- 保存原始转录和清理后文本，不覆盖原始证据。

### 2. 清理转录并校正术语

- 删除无意义口头语和机械重复，但保留影响论证或推导的中间说明。
- 结合 PPT、板书、教材和上下文校正专业术语、数字、单位、希腊字母和上下标。
- 无法确认的词不要强行改写；写入 `uncertainty-log.md` 并在讲义中标记“待核对”。

### 3. 分析画面与关键帧

- 结合场景变化、固定间隔、字幕提示词、PPT 换页和板书增量提取关键帧。
- 至少区分章节、公式、板书和图像四类关键帧。
- 对逐行形成的板书保留形成过程，不要只截最后一帧。
- 优先直接核对原图；OCR 只用于辅助读取，并须回到原图复核公式、数字和单位。
- 仅当输入确实只有音频时才跳过画面分析，并在交付说明中声明限制。

### 4. 建立内容清单

在写讲义前完成：

- 章节清单：范围、问题、结论、前后关系；
- 概念清单：中英文名、首次出现位置、前置关系；
- 公式清单：来源画面、推导起点、变量、单位、假设和适用条件；
- 图像清单：坐标、曲线、符号、装置和教师解释；
- 不确定信息清单：音画冲突、模糊符号、疑似口误和材料分歧。

### 5. 重建知识结构

- 章节内尽量保持视频顺序；教师讲解明显跳跃时，只做必要的局部重排并保留时间戳。
- 首次使用概念前先解释概念，并说明它为什么是后续推导所必需的。
- 公式从适用的定律或定义开始，逐行展示代入、变形、近似和边界条件。
- 解释所有变量、上下标、单位、量纲、数量级、极限情况和适用边界。
- 把微观机制、宏观结果和参数变化连接起来；图像说明必须解释坐标、曲线和特征点。
- 对实验测量按“测量信号 → 物理/热学模型 → 拟合参数 → 假设与适用范围”组织。

### 6. 标记来源与不确定性

视频主体内容无需额外标签。使用以下固定标记：

```markdown
> [!note] 补充说明
> 下面内容不是视频中的直接表述，但属于理解当前内容所必需的前置知识。
```

```markdown
> [!note] 补充推导
> 视频直接给出了最终结果。下面根据本节采用的模型和假设补充完整推导。
```

```markdown
> [!warning] 视频内容核对
> 视频中此处表述为……，结合前后推导判断可能应为……。
```

```markdown
> [!warning] 待核对
> 原视频语音、画面或配套材料不足以可靠确认该内容。
```

不得把模型补充伪装成教师原话，也不得无标记地修正疑似口误。

### 7. 写作并交付

- 使用中文写作；核心术语首次出现时附英文。
- 使用 Obsidian 兼容 Markdown 和 LaTeX，正文公式用 `$...$`，独立公式用 `$$...$$`。
- 在主要知识点处写准确时间范围，在重要公式或画面处写单点时间戳和相对图片路径。
- 讲义正文使用连续解释，列表只用于清单、步骤、变量和对比。
- 完成后阅读 [references/quality-checks.md](references/quality-checks.md) 并逐项核验。

## 完成标准

只有在以下条件均满足时才报告完成：

- 覆盖全部输入视频或明确列出无法处理的文件及原因；
- 讲义脱离视频也能连续阅读；
- 重要公式、变量、单位、假设和适用范围完整；
- 关键图像和板书已解释而不只是插图；
- 时间戳、来源标记和待核对项可追溯；
- `lecture-notes.md` 及其引用的本地文件均存在；
- 最终回复简要列出处理范围、使用的材料、生成文件和仍待确认的内容。

