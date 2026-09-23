# 窗口管理命令行工具
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @JUGaaab-->
<!--Designer: @ki_ja-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 概述

ohos-window 是 OpenHarmony 提供的窗口管理命令行工具，用于操控窗口或查询窗口信息。该工具遵循 Claw 规范，以 JSON 格式输出执行结果，并提供详细的错误码、错误原因和解决建议，ohos-window 的安装路径为 `/system/bin/cli_tool/executable/ohos-window`。

## CLI 子命令表

| 子命令 | 作用 | 可选参数 | 所需权限 |
|--------|------|----------|----------|
| `restore-window` | 将指定主窗口恢复到前台 | `--windowId`、`--help` | `ohos.permission.CONTROL_DEVICE` |
| `--help` / `help` | 显示帮助信息 | 无 | 无 |

### restore-window 子命令参数说明

| 参数 | 类型 | 说明 |
|------|------|------|
| `--windowId <id>` | integer | 待恢复到前台的主窗口的 windowId |
| `--help` | flag | 显示 restore-window 子命令帮助信息 |

> **注意**：`--windowId` 为必填参数，且必须是非负整数。

## Claw 规范遵循情况

### 输出格式规范

所有命令执行结果均以 JSON 格式输出到标准输出，符合 `ohos-window.json` 中 `outputSchema` 的定义。

**成功响应：**

```json
{
  "type": "result",
  "status": "success",
  "data": {
    "message": "restore main window to foreground successfully."
  }
}
```

**失败响应：**

```json
{
  "type": "result",
  "status": "failed",
  "errCode": "ERR_INVALID_INPUT",
  "errMsg": "Invalid input parameters. The passed parameters are invalid.",
  "suggestion": "Check the passed parameters and ensure they are valid."
}
```

### 错误码

ohos-window 定义了以下错误码，在命令执行失败时通过 JSON 输出返回：

| 错误码 | 说明 |
|--------|------|
| `ERR_INVALID_COMMAND` | 无效命令 |
| `ERR_INVALID_INPUT` | 无效的输入参数 |
| `ERR_NO_PERMISSION` | 权限校验失败 |
| `ERR_DEVICE_NOT_SUPPORT` | 设备不支持 |
| `ERR_IPC_FAILED` | IPC 通信或服务连接失败 |
| `ERR_INVALID_OPERATION` | 当前状态不允许该操作 |

## 使用示例

### 查看帮助信息

```bash
# 查看 ohos-window 总体帮助
ohos-window --help

# 查看 restore-window 子命令帮助
ohos-window restore-window --help
```

### 恢复主窗口到前台

```bash
# 恢复指定主窗口到前台
ohos-window restore-window --windowId 100
```