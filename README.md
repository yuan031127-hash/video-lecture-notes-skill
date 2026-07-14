# Video Lecture Notes Skill

一个面向理工科课程视频的 Codex Skill，将课程录像、字幕、PPT、PDF 和板书整理成
可脱离视频独立阅读的中文系统讲义与 Obsidian 概念卡片。

它重点适配：

- 固体物理、传热学、微纳米热输运和热测量；
- 数学、物理、材料、工程和计算机课程；
- 含公式推导、板书、曲线、实验装置和专业术语的视频；
- Obsidian/Markdown 讲义工作流。

## 能做什么

- 同时分析语音、字幕和视频画面，不把讲义退化成转录摘要；
- 保留章节与知识点时间戳；
- 逐步恢复公式推导并解释变量、单位、量纲和适用条件；
- 解释板书、图表、物理图像和实验信号；
- 区分视频内容、补充知识、疑似口误和待核对信息；
- 默认每课只输出完整的 `lecture-notes.md` 和可复用的概念卡片；
- 每篇讲义标题下方直接链接对应课程视频；
- 字幕、关键帧和分析清单只用于内部核对，不默认放进 Obsidian，也不嵌入图片。

## 安装

### Windows PowerShell

```powershell
git clone https://github.com/yuan031127-hash/video-lecture-notes-skill.git
Copy-Item -Recurse -Force ".\video-lecture-notes-skill\video-lecture-notes" "$HOME\.codex\skills\video-lecture-notes"
```

安装后重启 Codex，或开启一个新任务，让 Skill 列表重新载入。

## 使用示例

```text
用 $video-lecture-notes 把这套固体物理课程视频做成完整中文 Obsidian 讲义和概念卡片。每课标题下面链接原视频，不要图片。
```

```text
请整理这节 TDTR 课程录像和配套 PPT，按“测量信号 → 热学模型 → 拟合参数 → 假设与适用范围”解释。
```

未显式写出 `$video-lecture-notes` 时，只要请求明显属于技术课程视频讲义整理，Codex
也可以自动触发该 Skill。

## 仓库结构

```text
video-lecture-notes/
├── SKILL.md
├── agents/openai.yaml
├── references/
│   ├── content-rules.md
│   └── quality-checks.md
└── assets/lecture-notes-template.md
```

首版有意不包含未经验证的转录或抽帧脚本。Skill 会调用当前环境中可用的媒体、文档
和转录工具，在临时工作区进行证据核对。除非用户明确要求，最终课程目录只保留课程
入口、讲义和概念卡片 Markdown 文件。

## License

[MIT](LICENSE)
