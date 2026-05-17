<div align="center">

# Steven SuperPPT Skill

**一个公开可分享的 PPT 设计技能：把粗糙想法变成有审美、有结构、可编辑的高质量演示稿。**

<p>
  <img alt="公开技能" src="https://img.shields.io/badge/%E5%85%AC%E5%BC%80%E6%8A%80%E8%83%BD-%E5%8F%AF%E5%88%86%E4%BA%AB-111111?style=for-the-badge">
  <img alt="PPTX 可编辑" src="https://img.shields.io/badge/PPTX-%E5%8F%AF%E7%BC%96%E8%BE%91-2563eb?style=for-the-badge">
  <img alt="生图可交接" src="https://img.shields.io/badge/%E7%94%9F%E5%9B%BE-%E5%8F%AF%E4%BA%A4%E6%8E%A5-f97316?style=for-the-badge">
  <img alt="混合画布" src="https://img.shields.io/badge/%E6%B7%B7%E5%90%88%E7%94%BB%E5%B8%83-HTML%2BCanvas%2BPPTX-10b981?style=for-the-badge">
</p>

**先策划内容，再提炼风格；让图片负责氛围，让代码和 PPT 对齐每一个精确元素。**

</div>

---

## 它解决什么问题

很多 AI 做 PPT 的流程会卡在两个极端：要么内容还行但视觉很普通，要么画面看起来很炫，但关键文字、数字和图表都被烙进了不可编辑的图片里。

Steven SuperPPT 用的是 **双层制作模型**：

| 层级 | 负责什么 | 为什么这样做 |
|---|---|---|
| 图像底板 | 氛围、隐喻、材质、背景结构、物体情绪 | 让生图模型做它最擅长的视觉表达 |
| 精确层 | 文字、数字、图表、标签、流程图、表格、页码 | 让 PPT 保持可编辑、可审计、可复用 |

目标是：**视觉能像发布会，文件仍然像一份真正可交付的 PowerPoint。**

## 工作流

```mermaid
flowchart LR
  A["主题 / 需求简报"] --> B["逐页内容策划"]
  B --> C["选择视觉资产密度"]
  C --> D["风格参考分析"]
  D --> E["审美预检"]
  E --> F["生图提示词包"]
  F --> G["精确层排版"]
  G --> H["PPTX / HTML / PDF"]
  H --> I["视觉质检"]
```

## 核心能力

| 能力 | 这个技能会做什么 |
|---|---|
| 逐页内容策划 | 生成完整 `outline.md`，包括页面 ID、页面任务、精炼标题、讲述意图、证据状态、视觉任务和资产需求 |
| 风格参考提炼 | 从截图、PPT、PDF、网页、标志、产品图、情绪板中抽取可复用的视觉系统 |
| 视觉资产密度选择 | 在制作前选择 `lean`、`standard`、`image-rich` 或 `auto`，决定生图数量和视觉强度 |
| 多图资产规划 | 先写 `imagegen-prompt-pack.md`，不再默认“一张图解决整套 PPT” |
| 生图交接模式 | 如果当前环境不能直接生图，就输出可复制的提示词、文件名、比例、安全区和放置路径 |
| 混合制作路线 | 用图像底板承载氛围，用 HTML/SVG/Canvas/PPTX 承载精确文字、图表和布局 |
| 交付前验证 | 要求检查缩略图、资产清单、PPTX/HTML 可打开性、文字是否可编辑、图片是否嵌入正确 |

## 视觉资产密度

启动技能后，先决定这套 PPT 到底要“多有画面”：

| 模式 | 适合场景 | 生图策略 |
|---|---|---|
| `lean` | 信息密集型汇报、分析报告、法务、合规、董事会材料 | 只给封面、章节页和必要隐喻页规划图像 |
| `standard` | 大多数需要精致感的商务 PPT | 封面多变体、每个章节一张底板、关键页补视觉图 |
| `image-rich` | 发布会、产品演示、品牌故事、营销战役、视频感演示 | 每页都规划视觉资产，封面、产品页、转场页、主视觉页生成多变体 |
| `auto` | 用户不想选，希望技能自己判断 | 根据需求自动选择，并记录判断理由 |

如果用户提到“发布会”“产品演示”“苹果风”“视觉冲击”“电影感”等，技能会自动上调到 `image-rich`。

## 生图提示词的 PPT 专用约束

每个生图提示词都按 PPT 场景优化，而不是泛泛地生成一张壁纸：

- 16:9 演示比例
- 明确标题、正文、图表的安全区
- 图片里不生成可读文字
- 不生成假 Logo、假 UI、假标签、假图表、假仪表盘、水印
- 内容区保持低密度，方便叠加文字
- 每个资产都写 `overlay_plan`，说明哪些元素后续由 HTML/Canvas/PPTX 绘制
- 每个图像资产都有验收标准，避免只看“好看”不看“能不能用于 PPT”

## 无法生图怎么办

如果当前智能体环境不能直接调用生图工具，技能会进入 **提示词交接模式**，照样完成视觉规划，并输出：

```text
references/imagegen-prompt-pack.md
references/imagegen-handoff.md
references/asset-manifest.json
```

用户可以把这些提示词复制到任意外部生图工具里，按指定文件名保存，再继续完成 PPT 制作。

## 安装

把技能文件夹复制到你的智能体技能目录：

```text
~/.codex/skills/steven-superppt-skill/
```

目录结构：

```text
steven-superppt-skill/
  SKILL.md
  agents/openai.yaml
  assets/samples/uffizi-main-works.pptx
  references/
```

## 快速调用示例

默认精致商务版：

```text
请使用 $steven-superppt-skill，把这个主题策划并制作成一套 12 页的高质量 PPT。
```

发布会 / 产品演示版：

```text
请使用 $steven-superppt-skill，并选择 image-rich 视觉资产密度，做一套产品发布会演示稿。
```

带风格参考：

```text
请使用 $steven-superppt-skill。参考我提供的截图风格，先逐页策划内容，再输出 PPTX 和 HTML 预览。
```

不能直接生图的环境：

```text
请使用 $steven-superppt-skill 的提示词交接模式，输出外部生图提示词、资产清单和 PPT 草稿。
```

## 示例文件

仓库里包含一份可编辑 PPTX 示例：

```text
steven-superppt-skill/assets/samples/uffizi-main-works.pptx
```

它展示了一套 12 页的博物馆主题演示稿：图像已嵌入，文字仍然可在 Office 中编辑。

## 公开分享说明

这个仓库面向公开分享，不包含私有公司信息、本机路径或特定品牌规则。如果你需要严格遵守某个品牌规范，可以单独再配一个品牌 / 模板技能。
