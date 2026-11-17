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

**命令示例：**

```bash
# 恢复指定主窗口到前台
ohos-window restore-window --windowId 100

# 查看restore-window命令帮助
ohos-window restore-window --help
```

**输出示例：**

```json
{
    "type": "result",
    "status": "success",
    "data": {
        "message": "restore main window to foreground successfully."
    }
}
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

| 参数名 | 说明 |
|------|------|
| `--help` | 查看帮助信息，可选，指定本参数时会忽略其他参数。|
| `--windowId <id>` | 指定查询的窗口ID，可选，默认查询所有窗口。|
| `--displayId <id>` | 指定查询的屏幕ID，可选，默认查询所有屏幕。|
| `--filter <visible\|excludeSystem\|foreground>` | 指定窗口过滤条件，可组合使用，可选，默认不过滤任何窗口。其中：visible表示返回可见窗口，excludeSystem表示不返回桌面、壁纸等系统窗口，foreground表示返回前台窗口。|
| `--type <ui\|display\|layout\|meta>` | 指定返回的[窗口信息类别](#窗口信息类别)，可组合使用，可选，默认返回所有类别信息。其中：ui表示返回uiInfo信息，display表示返回displayInfo信息，layout表示返回layoutInfo信息，meta表示返回metaInfo信息。|

### 窗口信息类别

每种类别代表不同的窗口信息，可根据`--type`参数指定。

- **uiInfo**

    | 字段名 | 说明 |
    |--------|------|
    |visibilityState| 窗口可见性，0表示完全可见，1表示部分可见，2表示完全不可见。|

- **displayInfo**

    | 字段名 | 说明 |
    |--------|------|
    | displayId | 屏幕ID。|

- **layoutInfo**

    | 字段名 | 说明 |
    |--------|------|
    | rect | 窗口尺寸大小。|
    | zOrder | 窗口层级，值越大代表层级越高。|

- **metaInfo**

    | 字段名 | 说明 |
    |--------|------|
    | windowId | 窗口ID。|
    | windowName | 窗口名。|
    | bundleName | 应用包名。|
    | abilityName | 应用Ability名。|
    | appIndex | 多实例应用的索引，用于区分相同应用的不同实例。|
    | pid | 应用的进程号。|
    | windowType | 窗口类型，各数值含义见[WindowType](#windowtype)。|
    | windowMode | 窗口模式，各数值含义见[WindowMode](#windowmode)。|
    | isFocused | 窗口是否是获焦状态。true表示获焦，false表示未获焦。|
    | isTouchable | 窗口是否可触摸。true表示可触摸，false表示不可触摸。|

### WindowType

| 值 | 说明 |
|--------|------|
| 1 | 应用主窗口。|
| 1001 | 应用子窗口。|
| 2000 | 壁纸。|
| 2001 | 桌面。|
| 2101 | Dock栏。|
| 2102 | 来电通知。|
| 2103 | 搜索栏。|
| 2104 | 系统告警弹框。|
| 2105 | 输入法。|
| 2106 | 应用悬浮窗。|
| 2108 | 状态栏。|
| 2109 | 面板。|
| 2110 | 键盘锁。|
| 2111 | 音量条。|
| 2112 | 导航条。|
| 2122 | 对话框。|
| 2123 | 截屏。|
| 2124 | 输入法状态栏。|
| 2125 | 全局搜索框。|
| 2128 | 系统悬浮窗。|
| 2129 | 画中画。|

### WindowMode

| 值 | 说明 |
|--------|------|
| 1 | 全屏。|
| 102 | 悬浮窗。|
| 103 | 画中画。|
| 105 | 分屏。|

### 错误码

| 错误码 | 说明 | 处理建议 |
|--------|------|------|
| ERR_INVALID_INPUT | 无效的输入参数。 | 检查参数是否符合参数说明。 |
| ERR_NO_PERMISSION | 权限校验失败。 | 检查是否配置[ohos.permission.CONTROL_DEVICE](../security/AccessToken/restricted-permissions.md#ohospermissioncontrol_device)权限。 |
| ERR_IPC_FAILED | IPC通信或服务连接失败。 | 请重试。 |

### 示例代码

**命令示例：**

```bash
# 查询所有可见窗口，但不包括桌面等系统窗口
ohos-window list-windows --filter visible --filter excludeSystem

# 查询指定窗口的元数据信息
ohos-window list-windows --type meta --windowId 100

# 查询指定屏幕上的窗口的布局信息与元数据信息
ohos-window list-windows --displayId 0 --type layout --type meta
```

**输出示例：**

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

## screenshot

对指定的窗口或屏幕进行截图。屏幕截图支持全屏截图、矩形区域截图、全屏截图时排除指定窗口。

### 约束限制

- 需要权限：[ohos.permission.CUSTOM_SCREEN_CAPTURE](../security/AccessToken/permissions-for-all-user.md#ohospermissioncustom_screen_capture)。

### 命令格式

```bash
ohos-window screenshot [options]
```

> **说明：**
>
> options不填时，默认截主屏幕。

### 参数说明

| 参数名 | 说明 |
|------|------|
| `--help` | 查看帮助信息，可选，指定本参数时会忽略其他参数。|
| `--windowId <id>` | 指定待截图窗口的ID，可选，默认是屏幕截图。当传入值小于0，或指定的窗口不存在，或者是后台窗口、隐私窗口时，均返回ERR_INVALID_INPUT错误。只有指定本选项时才是窗口截图，不可与`--displayId`/`--rect`/`--excludeWindowIds`同时使用。|
| `--displayId <id>` | 指定待截图的屏幕ID，可选，默认值为0。当传入值小于0，或指定的屏幕不存在时，均返回ERR_INVALID_INPUT错误。不可与`--windowId`同时使用。|
| `--outputPath <path>` | 指定截图保存目录的路径，可选，默认保存在`/data/storage/el2/base/temp`目录下，参考[应用沙箱目录](../file-management/app-sandbox-directory.md#应用沙箱目录)。|
| `--rect <x,y,width,height>` | 指定屏幕截取矩形区域，可选，其中x和y表示矩形的左上角相对屏幕左上角顶点的坐标，width和height表示矩形的宽和高，单位均为px；当矩形超出屏幕范围时，会返回ERR_INVALID_INPUT错误。不可与`--excludeWindowIds`/`--windowId`同时使用。|
| `--excludeWindowIds <id1,id2,...>` | 指定屏幕截图时需要排除的窗口的ID，可选，多个ID以英文逗号分隔。当传入值中有小于0或不存在的窗口时，均返回ERR_INVALID_INPUT错误。不可与`--rect`/`--windowId`同时使用。|
| `--format <jpeg\|png>` | 指定截图的图片格式，可选，支持jpeg和png格式，默认jpeg格式。|

### 错误码

| 错误码 | 说明 | 处理建议 |
|--------|------|------|
| ERR_INVALID_INPUT | 无效的输入参数。 | 检查参数是否符合参数说明。 |
| ERR_NO_PERMISSION | 权限校验失败。 | 检查是否配置[ohos.permission.CUSTOM_SCREEN_CAPTURE](../security/AccessToken/permissions-for-all-user.md#ohospermissioncustom_screen_capture)权限。 |
| ERR_DEVICE_NOT_SUPPORT | 设备不支持。 | 检查当前设备类型。 |
| ERR_IPC_FAILED | IPC通信或服务连接失败。 | 请重试。 |
| ERR_INTERNAL_ERROR | 内部错误。 | 请重试。 |

### 示例代码

**命令示例：**

```bash
# 全屏截图
ohos-window screenshot

# 对指定窗口截图，图片格式为jpeg，保存到自定义路径
ohos-window screenshot --windowId 100 --format jpeg --outputPath /app/data/

# 截取指定矩形区域（x=100,y=200,width=300,height=400）
ohos-window screenshot --rect 100,200,300,400

# 全屏截图，排除窗口100和200
ohos-window screenshot --displayId 0 --excludeWindowIds 100,200
```

**输出示例：**

```json
{
    "type": "result",
    "status": "success",
    "data": {
        "message": "capture screenshot successfully.",
        "outputPath": "/data/storage/el2/base/temp/screenshot_2026-11-13_10-20-30.jpeg",
        "width": 2091,
        "height": 1527
    }
}
```