# workbuddy-prompt-optimizer-skill

一个 **WorkBuddy 用户级技能**：无需 Docker、无需 API Key、不连外部服务，直接用 WorkBuddy 当前模型把粗糙 / 口语化 / 需求模糊的提示词，优化成结构化、可直接用的高质量提示词。

## 它做什么

内置三类优化模板：

- **用户提示词（任务指令）**：角色 + 任务 + 上下文 + 要求 + 输出格式 + 示例
- **系统提示词（角色 / 规则）**：角色 + 目标 + 能力边界 + 工作流程 + 约束 + 输出规范
- **文生图提示词（T2I）**：主体 + 构图 + 风格 + 氛围 + 光线 + 画幅 + 负向词

优化流程：判断类型 → 找缺口 → 重写 → 优化前 / 后对照 → 多轮迭代。会明确告诉你**补了哪些缺口、为什么补**，方便对照学习。

## 调用方式

- 斜杠命令：`/prompt-optimizer 帮我优化这条提示词：……`
- 自然语言：说「帮我优化这条提示词 / 改进这个 prompt / 帮我写个系统提示词」会自动加载。

## 跨设备安装

任意设备装上后，放到用户级技能目录即可（`/prompt-optimizer` 立即可用）：

```bash
# 方式一：git 克隆（推荐，便于后续更新）
git clone https://github.com/whf1111/workbuddy-prompt-optimizer-skill.git
mkdir -p ~/.workbuddy/skills/prompt-optimizer
cp workbuddy-prompt-optimizer-skill/SKILL.md ~/.workbuddy/skills/prompt-optimizer/SKILL.md
```

Windows（PowerShell）等效路径：

```powershell
$src = "工作空间\workbuddy-prompt-optimizer-skill\SKILL.md"
$dst = "$env:USERPROFILE\.workbuddy\skills\prompt-optimizer\SKILL.md"
New-Item -ItemType Directory -Force -Path (Split-Path $dst) | Out-Null
Copy-Item $src $dst -Force
```

> 提示：技能目录在会话启动时扫描，复制后**重启一下会话 / 开个新对话**就会出现在 `/` 菜单里。

## 许可与署名

- 本仓库中由作者原创撰写的文本（含 `SKILL.md` 的提示词结构）以 **MIT 许可证**发布，见 `LICENSE`。
- 优化方法论的结构化改写思路**参考**了开源项目 [linshenkx/prompt-optimizer](https://github.com/linshenkx/prompt-optimizer)（原项目 AGPL-3.0）。本仓库未复制其源代码，仅借鉴其提示词优化理念，特此署名，详见 `NOTICE`。
