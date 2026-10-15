# 和纸拼贴风格穿搭抽象

[English](README.md)

一套不依赖特定 Agent 的穿搭图像工作流：从时尚照或旅行照中识别主要人物的衣服，保留轮廓、比例、颜色、结构、层次和材质特征，转化为由少量大纸片组成的平面和纸拼贴，输出真正透明背景的 PNG 图片。

## 方法一：把仓库链接交给 Agent

如果 Agent 能读取 GitHub 文件，无需安装。上传穿搭照片，并直接告诉它：

```text
请完整读取这个仓库的 SKILL.md 和 references/exact-prompt.md，按照工作流把照片中主要人物的穿搭转化为透明背景的平面和纸拼贴：
https://github.com/AnniiiinnA/washi-paper-collage-style-outfit-abstraction
如果无法读取文件或生成图片，请说明缺少什么能力。
```

如果 Agent 支持从 GitHub 安装 Skill，可以让它按照自身支持的安装方式安装仓库，并保留原有目录结构。

也可以克隆仓库，再让 Agent 读取本地 `SKILL.md`：

```sh
git clone https://github.com/AnniiiinnA/washi-paper-collage-style-outfit-abstraction.git
```

克隆只负责下载文件；是否自动识别为 Skill，取决于 Agent 的安装机制。

## 方法二：上传给对话式 AI

在 GitHub 点击 **Code → Download ZIP**，下载并解压，然后上传：

- `SKILL.md`
- `references` 文件夹中的全部 Markdown 文件（原始提示词必须上传；非 Codex 环境可忽略 Codex 适配文件）
- 需要处理的穿搭照片

然后告诉它：

```text
请完整阅读上传的 SKILL.md 和 references/exact-prompt.md，按照工作流分析照片中的主要穿搭，并生成极简、平面的和纸拼贴图片，输出带真实透明通道的 PNG。只有在 Codex 中运行时才使用 Codex 适配说明。如果你不能生成图片，请提供完整组装后的生图提示词，并明确说明这只是提示词交接，尚未生成图片。
```

如果 AI 不支持上传文档，可以粘贴 `SKILL.md` 和 `references/exact-prompt.md` 的完整内容。不要省略或概括原始提示词。

## 方法三：安装到本地 Skill 目录

使用你的 Agent 官方支持的 Skill 目录或 GitHub 安装方式。保持 `SKILL.md` 与 `references/` 的相对位置不变。`agents/openai.yaml` 是可选的 Codex 界面信息，其他 Agent 可以忽略。

Codex 用户可将仓库文件夹放到：

- Windows：`%USERPROFILE%\.codex\skills\washi-paper-collage-style-outfit-abstraction`
- macOS/Linux：`~/.codex/skills/washi-paper-collage-style-outfit-abstraction`
- 自定义 `CODEX_HOME`：该目录下的 `skills` 文件夹

开启新会话，上传照片后输入：

```text
请使用 $washi-paper-collage-style-outfit-abstraction 处理这张照片里的主要穿搭。
```

不支持 `$skill-name` 语法的 Agent，可以直接用自然语言要求它遵循 `SKILL.md`。

## 能力要求与限制

| Agent 具备的能力 | 可以完成的结果 |
| --- | --- |
| 读取说明、识别照片、参考图生图、输出 PNG 透明通道 | 完整图片工作流 |
| 读取说明、识别照片，但不能生图 | 穿搭分析和完整生图提示词；尚无成品图片 |
| 不能识别照片 | 加载工作流后，需要转到支持视觉的环境处理 |

工作流可以跨 Agent 使用，但无法为平台增加它本身没有的视觉、联网、生图或透明输出能力。其他 Agent 不需要 Codex 或 `imagegen` Skill；Codex 专用工具说明单独放在 `references/codex-adapter.md`。核心流程不需要 Python；服务配置和费用由所用平台决定。

目标图片仅包含衣服，不包含人物或人体模型；穿搭居中，占画布高度约 45–55%，周围为真正透明的像素。默认去掉包、首饰、帽子、鞋等独立配饰，保留衣服自带的腰带、系带等必要结构。

人物选择、分析顺序、纸片规划和提示词组装具有固定规则，但生图结果并非像素级确定。发现明显问题时最多修正一次，仍存在的边缘瑕疵或构图偏差会明确说明。目前尚未在所有 Agent 平台上逐一实测。

原始生图提示词完整保存在 `references/exact-prompt.md`（原扩展名为 `.txt`），内容保持不变。仓库不包含用户原始照片或生成图片。
