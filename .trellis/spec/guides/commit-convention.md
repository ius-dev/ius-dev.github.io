# Commit Convention

Applies to every commit in this repository.

## Message format

```
[类型]: 提交信息
```

- 类型放在半角方括号内，使用小写英文类型名（如 `[feat]`、`[fix]`、`[docs]`、`[chore]`），右方括号后紧跟半角冒号和空格。
- 冒号后是用中文写的简短提交信息，说明这次改动做了什么。
- 示例：`[chore]: 初始化 mini-trellis 记忆层`、`[fix]: 修复 XML 还原对空输入的处理`。

## Human confirmation gate

提交信息必须由人工确认之后才能执行 `git commit`。

- 代理（Claude Code / Codex 等）在提交前先给出拟好的提交信息，等用户确认。
- 未获确认前不得提交；用户改写的措辞以用户版本为准。
