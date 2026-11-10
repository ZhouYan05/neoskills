# neoskills 快速上手指南（中文）

> 面向第一次接触 neoskills 的中文用户。官方英文文档见仓库根目录 [README.md](../README.md)。

## neoskills 是什么？

neoskills 是一个面向 AI 编码智能体（Claude Code、OpenCode、OpenClaw）的「技能包管理器」，
定位类似编程界的 Homebrew：

- 把技能（Skill）当作**可移植的目录**管理，每个技能是一个含 `SKILL.md` 的文件夹；
- 通过**符号链接（symlink）**把技能选择性部署到不同智能体的技能目录，一处修改、多处生效；
- 内置**本体层（Ontology）**：技能之间的依赖、组合、生命周期都有结构化描述，可生成 ASCII 树 / DOT / Mermaid 图谱。

## 环境要求

- Python ≥ 3.13
- [uv](https://github.com/astral-sh/uv)（官方要求用 uv，不要直接 pip install）

## 三步上手

```bash
# 1. 安装
pip install neoskills          # 或 uv tool install neoskills

# 2. 初始化技能库（skill bank）
neoskills init                 # 创建 ~/.neoskills 目录结构

# 3. 创建一个新技能
neoskills create my-skill      # 生成带 SKILL.md 与 ontology.yaml 的脚手架
```

## 常用命令速查

| 命令 | 作用 |
|---|---|
| `neoskills list` | 列出技能库中的技能 |
| `neoskills create <name>` | 脚手架式创建新技能 |
| `neoskills link <name>` | 把技能链接（部署）到智能体目标 |
| `neoskills doctor` | 检查技能库健康状态 |
| `neoskills ontology load` | 加载并构建技能本体图谱 |
| `neoskills ontology stats` | 查看图谱统计（节点/边/类型） |
| `neoskills ontology graph --mermaid` | 导出 Mermaid 图谱 |
| `neoskills tap <repo>` | 添加外部技能源（类似 Homebrew tap） |

## 与 Homebrew 的对应关系

| Homebrew | neoskills |
|---|---|
| `brew install <formula>` | `neoskills link <skill>` |
| `/usr/local/Cellar` | `~/.neoskills/`（技能库） |
| `brew tap <repo>` | `neoskills tap <repo>` |
| formula 版本管理 | `ontology versioning`（技能版本） |

## 常见问题

- **Q：link 之后改技能源文件不生效？** A：link 用的是 symlink，修改源目录立即生效；如果发现目标处是拷贝而不是链接，运行 `neoskills doctor` 检查。
- **Q：本体层（ontology）是必须的吗？** A：不是。普通使用只靠 SKILL.md 即可；本体层为技能依赖/组合/生命周期提供结构化描述，适合技能数量变多后做治理。

---

*本文档为社区贡献（中文版快速上手），如与英文 README 冲突以 README 为准。*
