# ohos-window CLI工具
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @JUGaaab-->
<!--Designer: @ki_ja-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->

## 简介

ohos-window是OpenHarmony提供的窗口管理CLI（Command Line Interface，命令行界面）工具，用于操作窗口或查询窗口信息。该工具执行结果输出为JSON格式，并提供详细的错误码、错误原因和解决建议。ohos-window的安装路径为`/system/bin/cli_tool/executable/ohos-window`。

## help

查看帮助信息和所有子命令。

支持以下两种命令格式：

```bash
ohos-window help
ohos-window --help
```

## restore-window

将指定主窗口恢复到前台。

### 约束限制

- 需要权限：[ohos.permission.CONTROL_DEVICE](../security/AccessToken/restricted-permissions.md#ohospermissioncontrol_device)。
- 设备限制：仅支持在PC/2in1设备上使用restore-window命令。

### 命令格式

```bash
ohos-window restore-window [options]
```

> **说明：**
>
> options不填时，调用此命令会报ERR_INVALID_INPUT错误码。

### 参数说明

| 参数名 | 说明 |
|------|------|
| `--windowId <id>` | 可选，其中id为待恢复到前台的主窗口的windowId，必须是非负整数。<br>不可与`--help`同时使用。 |
| `--help` | 可选，查看帮助信息。<br>不可与`--windowId <id>`同时使用。 |

### 错误码

| 错误码 | 说明 | 处理建议 |
|--------|------|------|
| ERR_INVALID_INPUT | 无效的输入参数。 | 检查参数是否符合参数说明。 |
| ERR_NO_PERMISSION | 权限校验失败。 | 检查是否配置[ohos.permission.CONTROL_DEVICE](../security/AccessToken/restricted-permissions.md#ohospermissioncontrol_device)权限。 |
| ERR_DEVICE_NOT_SUPPORT | 设备不支持。 | 检查当前设备类型。 |
| ERR_IPC_FAILED | IPC通信或服务连接失败。 | 请重试。 |
| ERR_INVALID_OPERATION | 当前状态不允许该操作。 | 请在设备解锁后使用该命令。 |

### 示例代码

```bash
# 恢复指定主窗口到前台
ohos-window restore-window --windowId 100

# 查看restore-window命令帮助
ohos-window restore-window --help
```