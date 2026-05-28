# Seedance / Seedence Skills

面向 **即梦 Seedance 2.0** 的 Cursor Agent Skills 集合。

## 技能列表

| 技能 | 路径 | 用途 |
|------|------|------|
| 人物表情精准提示词 | `.cursor/skills/seedance-expression-prompt/` | 将大白话表情需求转为肌肉分区 + 三层情绪 + 非对称瑕疵 + 帧级口型时序的 Seedance 提示词 |

## 使用方式

在 Cursor 对话中描述你想要的表情（可以说大白话），并提及 Seedance 2.0 / 表情提示词，Agent 会按技能生成可复制到即梦的完整提示词。

也可在对话中明确：`请使用 seedance-expression-prompt 技能`。

## 文件结构

```
.cursor/skills/seedance-expression-prompt/
├── SKILL.md          # 主流程与输出模板
├── muscle-atlas.md   # 肌肉分区与组合参考
└── examples.md       # 前后对照示例
```
