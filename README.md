# agent-common-skills

工作日常使用的 Agent 能力集合（Agent Common Skills）：一套开箱即用的 Agent 技能库。每个技能以独立的 `SKILL.md` 定义，遵循统一 front-matter 规范（`name` / `display_name` / `description` / `version` / `author` / `category` / `allowed-tools`），可与 OpenAI Codex、Claude Code 等支持 Agent Skills 标准的工具直接互通，无需额外依赖。

## 技能列表

| 技能目录 | 技能名称 | 分类 | 版本 | 简介 |
| --- | --- | --- | --- | --- |
| [algorithm-notes-generator](algorithm-notes-generator/) | 算法笔记生成助手 | coding | 1.0.4 | 输入算法名称，按固定 8 段式结构输出标准化、可直接背诵的中文算法 Markdown 笔记（含复杂度三态、数据结构、简洁 Python 代码、工程案例、面试问答、背诵要点），覆盖后端、大数据、搜索工程、AI Agent 岗位面试复习。 |

> 新技能请按字母/分类命名目录，并在下方表格补充一行。

## 目录结构

```
agent-common-skills/
├── algorithm-notes-generator/   # 算法笔记生成助手
│   └── SKILL.md                 # 技能定义（front-matter + 规则正文）
├── LICENSE                      # Apache-2.0
└── README.md
```

## 安装与使用（以 Codex CLI 为例）

每个技能本质上就是一个 `SKILL.md` 文件，安装 = 把对应目录放到 Codex 的技能目录中。

### 步骤一：整体克隆

```bash
git clone https://github.com/hzjkaka/agent-common-skills.git
```

### 步骤二：安装到Agent全局技能目录

```bash
# Codex
mkdir -p ~/.codex/skills
cp -r algorithm-notes-generator ~/.codex/skills/
# 验证：codex 启动后输入 @algorithm-notes-generator 应能命中该技能
```

```bash
# Claude Code
mkdir -p ~/.claude/skills
cp -r algorithm-notes-generator ~/.claude/skills/
```


### 步骤三：其他场景：Cursor / 其他 IDE Agent

将需要的技能目录（或其中的 `SKILL.md`）复制到项目级或全局的 skills 目录，之后在对话中按技能说明的触发词使用即可，例如输入 `生成快排笔记` 或 `帮我整理二分查找的算法笔记`。

### 使用方式

在 Codex 对话中通过 `@技能名` 显式引用技能，再给出具体指令即可：

```text
用 @algorithm-notes-generator 生成一份快排笔记
帮我整理二分查找的算法笔记
```

> 说明：Codex 可读取技能目录中的 `SKILL.md` 来自动理解技能用途；也可不显式引用，直接描述需求让 Agent 根据技能描述自动匹配。

## 编写规范

- 每个技能一个目录，目录名即 `name` 字段。
- `SKILL.md` 顶部使用 YAML front-matter 声明元数据，正文明确「何时使用」「核心交付」「输出契约」与「红线」。
- 新增技能请遵循现有 `SKILL.md` 的写法与粒度，保持输出可验证、可背诵。

## License

[Apache License 2.0](LICENSE)