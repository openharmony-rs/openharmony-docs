# ohos-window CLI命令工具
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @JUGaaab-->
<!--Designer: @ki_ja-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 概述

ohos-window是OpenHarmony提供的窗口管理CLI（Command Line Interface，命令行界面）工具，用于操控窗口或查询窗口信息。该工具遵循Claw规范，以JSON格式输出执行结果，并提供详细的错误码、错误原因和解决建议，ohos-window的安装路径为`/system/bin/cli_tool/executable/ohos-window`。

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

### 约束限制：

需要配置ohos.permission.CONTROL_DEVICE权限。

### 参数：

| 参数名 | 类型 | 说明 |
|------|------|------|
| `--windowId` | integer | 必选，待恢复到前台的主窗口的windowId。必须是非负整数。 |

### 错误码：

| 错误码 | 说明 |
|--------|------|
| `ERR_INVALID_INPUT` | 无效的输入参数 |
| `ERR_NO_PERMISSION` | 权限校验失败 |
| `ERR_DEVICE_NOT_SUPPORT` | 设备不支持 |
| `ERR_IPC_FAILED` | IPC 通信或服务连接失败 |
| `ERR_INVALID_OPERATION` | 当前状态不允许该操作 |

### 示例：

```bash
# 恢复指定主窗口到前台
ohos-window restore-window --windowId 100
```