# 一些建议

## 1. exlucde掉不必要的文件

在.vscode/settings.json里添加

```json
  "files.exclude": {
    "**/.*.asm": true,
    "**/_*": true,
    "**/*.o": true,
    "**/*.d": true,
    "**/*.sym": true,
    "**/*.asm": true
    "**/*.pyc": true
  }
```