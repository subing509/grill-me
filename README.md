# Grill me

一个帮助你把问题问准的中文 AI skill：先审视假设，再提出一个最关键的问题，让后续建议贴合真实目标。

A lightweight, instruction-only skill that surfaces assumptions, identifies missing context, and asks one decisive question before offering advice. It responds in the user's language.

## 工作方式

首轮收到具体问题后，助手会：

1. 指出可能的隐含假设，明确区分推测与已知事实。
2. 说明会实质影响建议的关键信息缺口，不逐项追问。
3. 指出一个具体的常见错误。
4. 只提出一个最关键的问题，然后等待回答。

后续结合你的回答修正前提。信息足够时给出针对性的建议；仍需澄清时每轮只问一个问题。你也可以随时要求直接回答或结束追问。未提供具体问题时，助手只会先请你说明想讨论什么。

适合个人决策、学习计划、职业规划、产品方向等需要结合目标和情境的问题。它不要求所有普通任务都先进入追问流程。

## 安装到 Codex

需要已能正常使用、支持本地 skills 的 Codex。这个 skill 没有脚本、MCP、额外 API Key 或第三方运行依赖。

### 方式一：下载 ZIP 并复制

1. 在 GitHub 点击 **Code → Download ZIP**，解压。
2. 将解压后的仓库文件夹重命名为 `grill-me`。
3. 将整个文件夹放入当前用户的 skills 目录：
   - Windows：`%USERPROFILE%\.agents\skills\grill-me`
   - macOS / Linux：`~/.agents/skills/grill-me`
4. 确认 `SKILL.md` 位于 `grill-me` 内的第一层。若未识别，请重启 Codex。

### 方式二：用 Git 安装

Windows PowerShell：

```powershell
$skillsDir = Join-Path $env:USERPROFILE '.agents\skills'
New-Item -ItemType Directory -Path $skillsDir -Force | Out-Null
git clone https://github.com/subing509/grill-me.git (Join-Path $skillsDir 'grill-me')
```

macOS / Linux：

```sh
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/subing509/grill-me.git "$HOME/.agents/skills/grill-me"
```

已有同名目录时，先将旧目录移到 skills 目录之外备份，或者更新已有 Git 安装，不要叠加复制。

仅在某个项目使用时，也可以安装到该项目的 `.agents/skills/grill-me`。用户级和项目级选择一种，避免同名重复。

## 使用示例

在 Codex 中发送：

```text
请用 $grill-me 帮我审视这个问题：我想在三个月内转行做产品经理，应该先学什么？
```

或者：

```text
请用 $grill-me 帮我想清楚：我该先做产品原型，还是先找用户访谈？
```

预期首轮先做简短分析，最后仅问一个关键问题，而不是立即给出整套方案。回答后继续讨论即可。

不想继续追问时可以说：

```text
请基于目前的信息直接回答，并简要说明剩余假设。
```

## 文件结构

```text
grill-me/
├── SKILL.md             # 技能指令与触发说明
├── agents/
│   └── openai.yaml      # 界面显示元数据
├── README.md
└── LICENSE
```

其他支持 Agent Skills 的工具可参考 SKILL.md，但各工具安装路径和调用方式需要按其文档调整；本仓库的安装说明以 Codex 为目标。

## 更新和卸载

Git 安装可在安装目录运行 `git pull --ff-only`；若有本地修改，先保留修改并自行处理冲突。ZIP 安装时先移走旧目录，再复制新版。必要时重启 Codex。

卸载时将 `grill-me` 文件夹移出 skills 目录即可。

## 贡献

欢迎通过 Issues 提交真实使用中遇到的问题，或通过 Pull Requests 改进指令。描述具体输入、实际行为和期望行为，注意移除个人隐私信息。

## 许可证

[MIT](LICENSE) © 2026 subing509。

Codex 的本地发现目录与调用方式参考 [OpenAI 官方 skills 文档](https://learn.chatgpt.com/docs/build-skills)（核对日期：2026-10-25）。
