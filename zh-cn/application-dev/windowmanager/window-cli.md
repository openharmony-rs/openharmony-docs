# ohos-window CLI
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @JUGaaab-->
<!--Designer: @ki_ja-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## help

查看帮助信息和所有子命令。

### 命令格式：

```bash
ohos-window help
ohos-window --help
```

## restore-window

将指定主窗口恢复到前台。

### 命令格式：

```bash
ohos-window restore-window --windowId <id>
```

### 参数：

| 参数名 | 类型 | 说明 |
|------|------|------|
| `--windowId` | integer | 必选，待恢复到前台的主窗口的windowId。必须是非负整数。 |

### 示例：

```bash
# 恢复指定主窗口到前台
ohos-window restore-window --windowId 100
```