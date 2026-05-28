# Seedance / Seedence Skills

面向 **即梦 Seedance 2.0** 的 Cursor Agent Skills 集合。将大白话表情描述转为 **肌肉分区 + 三层情绪 + 非对称瑕疵 + 帧级口型时序** 的精准提示词，减少模板化「假脸」。

## 技能列表

| 技能               | 路径                                         | 用途                                                                                  |
| ------------------ | -------------------------------------------- | ------------------------------------------------------------------------------------- |
| 人物表情精准提示词 | `.cursor/skills/seedance-expression-prompt/` | 将大白话表情需求转为肌肉分区 + 三层情绪 + 非对称瑕疵 + 帧级口型时序的 Seedance 提示词 |

## 安装

仓库地址：<https://github.com/Fattydogs/seedance-expression-skills>

### 方式一：克隆仓库（推荐，便于更新）

**Windows（PowerShell）**

```powershell
git clone https://github.com/Fattydogs/seedance-expression-skills.git
cd seedance-expression-skills
```

**macOS / Linux**

```bash
git clone https://github.com/Fattydogs/seedance-expression-skills.git
cd seedance-expression-skills
```

然后用 **Cursor 打开该文件夹** 作为工作区，项目内的 `.cursor/skills/` 会自动生效。

### 方式二：安装到 Cursor 个人技能目录（所有项目可用）

只复制技能文件夹，不打开整个仓库也行。

**Windows（PowerShell）**

```powershell
git clone https://github.com/Fattydogs/seedance-expression-skills.git
$dest = "$env:USERPROFILE\.cursor\skills\seedance-expression-prompt"
New-Item -ItemType Directory -Force -Path (Split-Path $dest) | Out-Null
Copy-Item -Recurse -Force ".\seedance-expression-skills\.cursor\skills\seedance-expression-prompt" $dest
```

**macOS / Linux**

```bash
git clone https://github.com/Fattydogs/seedance-expression-skills.git
mkdir -p ~/.cursor/skills
cp -r seedance-expression-skills/.cursor/skills/seedance-expression-prompt ~/.cursor/skills/
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
cd seedance-expression-skills
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

## 克隆失败排查（Connection reset / Could not connect）

若出现 `Recv failure: Connection was reset` 或 `Failed to connect to github.com port 443`，说明本机 **访问不到 GitHub**，与仓库名无关。可依次尝试：

### A. 浏览器能打开 GitHub 时 — 用 ZIP 安装（最简单）

1. 打开 <https://github.com/Fattydogs/seedance-expression-skills>
2. **Code → Download ZIP**，解压
3. 将 `.cursor/skills/seedance-expression-prompt` 复制到 `%USERPROFILE%\.cursor\skills\`（见上文方式三）

### B. 为 Git 配置代理（你已有 VPN/代理时）

在 PowerShell 中把地址和端口改成你的代理（示例为本地 HTTP 代理）：

```powershell
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy http://127.0.0.1:7890
```

取消代理：

```powershell
git config --global --unset http.proxy
git config --global --unset https.proxy
```

### C. 改用 SSH（443 端口，部分网络环境更稳）

```powershell
git clone git@github.com:Fattydogs/seedance-expression-skills.git
```

需先在 GitHub 添加 [SSH Key](https://github.com/settings/keys)。若 22 端口被封，可在 `~/.ssh/config` 中设置 `Host github.com` → `Hostname ssh.github.com`、`Port 443`。

### D. 你已在本地开发本仓库时

若在 `e:\Openroad_claude\seedence_skills` 已有完整代码，**不必再 clone**；复制 `.cursor\skills\seedance-expression-prompt` 到个人技能目录即可使用。

### 验证网络

```powershell
git ls-remote https://github.com/Fattydogs/seedance-expression-skills.git HEAD
```

能显示一串 commit hash 即表示 Git 已能访问 GitHub。

## 要求

- [Cursor](https://cursor.com/) 编辑器（支持 Agent Skills 的版本）
- 使用即梦 **Seedance 2.0** 进行视频生成（技能产出为提示词，不替代即梦账号或 API）

## 许可

发布到 GitHub 后，可在本仓库添加 `LICENSE` 文件（例如 MIT）。当前仓库未附带许可证时，默认保留所有权利；使用前请与仓库作者确认。

## 贡献

欢迎通过 Issue / Pull Request 补充表情示例、肌肉映射或 Seedance 平台变更说明。修改 `SKILL.md` 时请保持主文件简洁（详细参考放在 `muscle-atlas.md` / `examples.md`）。
