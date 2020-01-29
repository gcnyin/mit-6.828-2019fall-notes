---
layout: page
title: Suggestions
permalink: /suggestions/
---

### 1. exclude不必要的文件

如果您使用vscode，向.vscode/settings文件添加以下内容，以便exclude掉不需要关注的内容：

```json
"files.exclude": {
  "**/.*.asm": true,
  "**/_*": true,
  "**/*.o": true,
  "**/*.d": true,
  "**/*.sym": true,
  "**/*.asm": true,
  "**/*.pyc": true
}
```