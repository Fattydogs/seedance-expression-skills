# Seedance / Seedence Skills

面向 **即梦 Seedance 2.0** 的 Cursor Agent Skills 集合。将大白话表情描述转为 **肌肉分区 + 三层情绪 + 非对称瑕疵 + 帧级口型时序** 的精准提示词，减少模板化「假脸」。

## 技能列表

| 技能               | 路径                                         | 用途                                                                                  |
| ------------------ | -------------------------------------------- | ------------------------------------------------------------------------------------- |
| 人物表情精准提示词 | `.cursor/skills/seedance-expression-prompt/` | 将大白话表情需求转为肌肉分区 + 三层情绪 + 非对称瑕疵 + 帧级口型时序的 Seedance 提示词 |

## 安装

将下面命令里的 `YOUR_USERNAME` 和 `REPO_NAME` 换成你的 GitHub 用户名与仓库名（发布到 GitHub 后使用）。

### 方式一：克隆仓库（推荐，便于更新）

**Windows（PowerShell）**

```powershell
git clone https://github.com/Fattydogs/seedance-expression-skills.git
cd REPO_NAME
```

**macOS / Linux**

```bash
git clone https://github.com/Fattydogs/seedance-expression-skills.git
cd REPO_NAME
```

然后用 **Cursor 打开该文件夹** 作为工作区，项目内的 `.cursor/skills/` 会自动生效。

### 方式二：安装到 Cursor 个人技能目录（所有项目可用）

只复制技能文件夹，不打开整个仓库也行。

**Windows（PowerShell）**

```powershell
git clone https://github.com/Fattydogs/seedance-expression-skills.git
$dest = "$env:USERPROFILE\.cursor\skills\seedance-expression-prompt"
New-Item -ItemType Directory -Force -Path (Split-Path $dest) | Out-Null
Copy-Item -Recurse -Force ".\REPO_NAME\.cursor\skills\seedance-expression-prompt" $dest
```

**macOS / Linux**

```bash
git clone https://github.com/Fattydogs/seedance-expression-skills.git
mkdir -p ~/.cursor/skills
cp -r REPO_NAME/.cursor/skills/seedance-expression-prompt ~/.cursor/skills/
```

安装后 **重启 Cursor** 或新开一个 Agent 对话，技能即可被识别。

### 方式三：手动下载 ZIP

1. 在 GitHub 仓库页点击 **Code → Download ZIP**
2. 解压后，将 `.cursor/skills/seedance-expression-prompt` 复制到：
   - **个人技能（全局）**：`%USERPROFILE%\.cursor\skills\`（Windows）或 `~/.cursor/skills/`（macOS/Linux）
   - **仅当前项目**：你的项目根目录下的 `.cursor/skills/`

### 验证是否安装成功

在 Cursor 中新建 Agent 对话，输入例如：

> 请用 seedance-expression-prompt 技能，帮我写一段 5 秒特写：强颜欢笑但眼里有泪。

若 Agent 按肌肉分区、三层情绪、帧级时序输出结构化提示词（而非仅「很开心」），说明技能已加载。

### 更新技能

若通过 git 克隆安装：

```bash
cd REPO_NAME
git pull
```

若复制到 `~/.cursor/skills/`，重新执行方式二中的 `cp` / `Copy-Item` 即可覆盖更新。

## 使用方式

在 Cursor 对话中描述你想要的表情（可以说大白话），并提及 **Seedance 2.0** / **表情提示词**，Agent 会生成可复制到即梦的完整提示词。

也可显式调用：

```text
请使用 seedance-expression-prompt 技能
```

**触发关键词示例**：`Seedance`、`Seedence 2.0`、`人物表情`、`微表情`、`唇形`、`表情太假`、`模板化`。

生成结果包含：`@图片` / `@音频` 引用说明、肌肉指令表、非对称瑕疵、分秒时序、负面约束等，见技能内 `SKILL.md` 模板。

## 文件结构

```
.cursor/skills/seedance-expression-prompt/
├── SKILL.md          # 主流程与输出模板
├── muscle-atlas.md   # 肌肉分区与组合参考
└── examples.md       # 前后对照示例
```

## 要求

- [Cursor](https://cursor.com/) 编辑器（支持 Agent Skills 的版本）
- 使用即梦 **Seedance 2.0** 进行视频生成（技能产出为提示词，不替代即梦账号或 API）

## 许可

发布到 GitHub 后，可在本仓库添加 `LICENSE` 文件（例如 MIT）。当前仓库未附带许可证时，默认保留所有权利；使用前请与仓库作者确认。

## 贡献

欢迎通过 Issue / Pull Request 补充表情示例、肌肉映射或 Seedance 平台变更说明。修改 `SKILL.md` 时请保持主文件简洁（详细参考放在 `muscle-atlas.md` / `examples.md`）。
