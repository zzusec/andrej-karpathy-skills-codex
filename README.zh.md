# andrej-karpathy-skills-codex

[English README](README.md)

这是一个面向 OpenAI Codex/Codex CLI 的 `AGENTS.md` 规则文件适配版，用来降低 LLM 编码时常见的问题，例如：

- 改代码前不先思考；
- 实现过度复杂；
- 顺手改无关代码；
- 没有明确验证目标。

这不是 Claude Code 插件，不能通过 Claude Code 的 `/plugin install` 安装。它的使用方式是：把 `AGENTS.md` 放到你运行 Codex 的项目目录或父目录中。

## 中文安装方式

### 方式 1：只让某一个项目使用

如果目标项目还没有 `AGENTS.md`，可以直接下载到项目根目录：

```bash
cd /path/to/your/project
curl -L -o AGENTS.md https://raw.githubusercontent.com/zzusec/andrej-karpathy-skills-codex/main/AGENTS.md
codex
```

目录结构示例：

```text
your-project/AGENTS.md
your-project/src/
your-project/package.json
```

### 方式 2：合并到已有的 `AGENTS.md`

如果项目里已经有自己的 Codex 规则，不要直接覆盖，建议追加后手动检查是否冲突：

```bash
cd /path/to/your/project
printf '\n\n# andrej-karpathy-skills-codex\n\n' >> AGENTS.md
curl -L https://raw.githubusercontent.com/zzusec/andrej-karpathy-skills-codex/main/AGENTS.md >> AGENTS.md
```

### 方式 3：clone 仓库后复制

如果你想先查看或修改规则内容，再放进项目：

```bash
git clone https://github.com/zzusec/andrej-karpathy-skills-codex.git
cd andrej-karpathy-skills-codex
cp AGENTS.md /path/to/your/project/AGENTS.md
```

### 方式 4：让父目录下的所有项目都使用

如果你的所有项目都放在同一个父目录下面，例如 `~/work`、`~/projects` 或用户目录，可以把一个共享的 `AGENTS.md` 放在父目录：

```bash
cd /path/to/parent-directory
curl -L -o AGENTS.md https://raw.githubusercontent.com/zzusec/andrej-karpathy-skills-codex/main/AGENTS.md
```

目录结构示例：

```text
work/AGENTS.md
work/project-a/
work/project-b/
work/project-c/
```

之后进入任意子项目启动 Codex：

```bash
cd /path/to/parent-directory/project-a
codex
```

如果你的 Codex 会读取父目录的 `AGENTS.md`，这些子项目都会共用同一套规则。

如果你的项目都在用户目录下，也可以放到 `~`：

```bash
cd ~
curl -L -o AGENTS.md https://raw.githubusercontent.com/zzusec/andrej-karpathy-skills-codex/main/AGENTS.md
```

目录结构示例：

```text
~/AGENTS.md
~/project-a/
~/project-b/
~/project-c/
```

### 方式 5：复制到每个项目根目录

如果你的 Codex 环境不会读取父目录规则，最兼容的方式是给每个项目都放一份：

```text
project-a/AGENTS.md
project-b/AGENTS.md
project-c/AGENTS.md
```

也可以在确认目标目录无误后用脚本批量复制：

```bash
for project in /path/to/projects/*; do
  if [ -d "$project" ] && [ ! -f "$project/AGENTS.md" ]; then
    cp AGENTS.md "$project/AGENTS.md"
  fi
done
```

如果某个项目已经有 `AGENTS.md`，请手动合并，不要覆盖。

## 验证安装

进入你要运行 Codex 的项目，确认 `AGENTS.md` 存在：

```bash
cd /path/to/your/project
ls AGENTS.md
codex
```

Codex 启动后，可以问它：

```text
请总结当前项目的 AGENTS.md 指令。
```

如果它能总结这些规则，就说明已经生效。

## 后续更新

如果是单独安装，可以用最新版本覆盖：

```bash
cd /path/to/your/project
curl -L -o AGENTS.md https://raw.githubusercontent.com/zzusec/andrej-karpathy-skills-codex/main/AGENTS.md
```

如果你之前是合并到已有 `AGENTS.md`，建议手动更新，避免覆盖自己的项目规则。

## 文件

- `AGENTS.md` — Codex 可读取的项目规则文件。
- `README.md` — 英文首页文档。
- `NOTICE.md` — 来源和归属说明。

## 来源说明

这是 `forrestchang/andrej-karpathy-skills` 的 Codex 适配版本。原仓库 README 标注为 MIT，并说明其内容来自 Andrej Karpathy 对常见 LLM 编码问题的公开观察。

## 许可证

MIT。见 `LICENSE`。
