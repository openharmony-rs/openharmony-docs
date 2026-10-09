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
# 方式一
ohos-window help

# 方式二
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

## list-windows

查询窗口信息。

### 约束限制

- 需要权限：[ohos.permission.CONTROL_DEVICE](../security/AccessToken/restricted-permissions.md#ohospermissioncontrol_device)。

### 命令格式

```bash
ohos-window list-windows [options]
```

> **说明：**
>
> options不填时，表示不过滤，会返回所有窗口信息。

### 参数说明

| 参数 | 是否必填 | 说明 |
|------|------|------|
| `--windowId <id>` | 否 | 仅查询指定窗口的信息，默认查询所有窗口。|
| `--displayId <id>` | 否 | 仅查询指定屏幕上的窗口的信息，默认查询所有屏幕。|
| `--filter <visible\|excludeSystem\|foreground>` | 否 | 窗口过滤条件，可组合使用，默认不过滤任何窗口。其中：visible表示返回可见窗口，excludeSystem表示不返回桌面壁纸等零层控件窗口，foreground表示返回前台窗口。|
| `--type <ui\|display\|layout\|meta>` | 否 | 返回的[窗口信息类别](#窗口信息类别说明)，可组合使用，默认返回所有类别信息。其中：ui表示返回[uiInfo](#uiInfo)信息，display表示返回[displayInfo](#displayInfo)信息，layout表示返回[layoutInfo](#layoutInfo)信息，meta表示返回[metaInfo](#metaInfo)信息 |
| `--help` | 否 | 查看帮助信息。|

### 窗口信息类别说明

每种类别代表不同的窗口信息，可根据“--type”参数指定。

#### uiInfo

| 字段名 | 说明 |
|--------|------|
|visibilityState| 窗口可见性值，0表示完全可见，1表示部分可见，2表示不可见。|

#### displayInfo

| 字段名 | 说明 |
|--------|------|
| displayId | 屏幕ID。|

#### layoutInfo

| 字段名 | 说明 |
|--------|------|
| rect | 窗口尺寸大小。|
| zOrder | 窗口层级。|

#### metaInfo

| 字段名 | 说明 |
|--------|------|
| windowId | 窗口ID |
| windowName | 窗口名 |
| bundleName | 应用包名 |
| abilityName | 应用Ability名 |
| appIndex | 应用索引号 |
| pid | 应用的进程号 |
| windowType | 窗口类型 |
| windowMode | 窗口模式 |
| isFocused | 是否是获焦状态 |
| isTouchable | 是否可触摸 |

### 错误码

| 错误码 | 说明 | 处理建议 |
|--------|------|------|
| ERR_INVALID_INPUT | 无效的输入参数。 | 检查参数是否符合参数说明。 |
| ERR_NO_PERMISSION | 权限校验失败。 | 检查是否配置[ohos.permission.CONTROL_DEVICE](../security/AccessToken/restricted-permissions.md#ohospermissioncontrol_device)权限。 |
| ERR_IPC_FAILED | IPC通信或服务连接失败。 | 请重试。 |

### 示例代码

```bash
# 查询所有可见窗口，但不包括零层控件窗口
ohos-window list-windows --filter visible --filter excludeSystem

# 查询指定窗口的元数据信息
ohos-window list-windows --type meta --windowId 100

# 查询指定屏幕上的窗口的布局信息与元数据信息
ohos-window list-windows --displayId 0 --type layout --type meta
```

### 输出示例

```json
{
    "status": "success", 
    "type": "result",
    "data": {
        "windows": [
            {
                "displayInfo": {
                    "displayId": 0
                }, 
                "layoutInfo": {
                    "rect": {
                        "height": 1527, 
                        "posX": 766, 
                        "posY": 178, 
                        "width": 2091
                    }, 
                    "zOrder": 112
                }, 
                "metaInfo": {
                    "abilityName": "EntryAbility", 
                    "appIndex": 0, 
                    "bundleName": "com.ohostoolbox.app", 
                    "isFocused": true, 
                    "isTouchable": true, 
                    "pid": 13989, 
                    "windowId": 70, 
                    "windowMode": 102, 
                    "windowName": "app0", 
                    "windowType": 1
                }, 
                "uiInfo": {
                    "visibilityState": 0
                }
            }
        ]
    } 
}
```