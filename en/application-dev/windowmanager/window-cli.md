# ohos-window CLI Tool
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @JUGaaab-->
<!--Designer: @ki_ja-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=4a86ee8a7845914c8ac3cdbd3fa60e0b4e8681e0 translatedAt=2026-11-03T02:51:17.673Z pushedAt=2026-11-03T02:58:19.562Z nl=1 -->

## Overview

ohos-window is a window management CLI (Command Line Interface) tool provided by OpenHarmony, used to operate windows or query window information. The tool outputs execution results in JSON format and provides detailed error codes, error causes, and resolution suggestions. The installation path of ohos-window is `/system/bin/cli_tool/executable/ohos-window`.

## help

View help information and all subcommands.

The following two command formats are supported:

```bash
# Method 1
ohos-window help

# Method 2
ohos-window --help
```

## restore-window

Restores the specified main window to the foreground.

### Constraints

- Required permission: [ohos.permission.CONTROL_DEVICE](../security/AccessToken/restricted-permissions.md#ohospermissioncontrol_device).
- Device restriction: The restore-window command is supported only on PC/2-in-1 devices.

### Command Format

```bash
ohos-window restore-window [options]
```

> **Note:**
>
> If options is not specified, calling this command returns the ERR_INVALID_INPUT error code.

### Description

| Name | Description |
|------|------|
| `--windowId <id>` | Optional. Here, id is the windowId of the main window to be restored to the foreground, and it must be a non-negative integer.<br>Cannot be used together with `--help`. |
| `--help` | Optional. View help information.<br>Cannot be used together with `--windowId <id>`. |

### Error Code

| Error Code | Description | Handling Suggestion |
|--------|------|------|
| ERR_INVALID_INPUT | Invalid input parameter. | Check whether the parameter complies with the parameter description. |
| ERR_NO_PERMISSION | Permission verification failed. | Check whether the [ohos.permission.CONTROL_DEVICE](../security/AccessToken/restricted-permissions.md#ohospermissioncontrol_device) permission is configured. |
| ERR_DEVICE_NOT_SUPPORT | The device does not support it. | Check the current device type. |
| ERR_IPC_FAILED | IPC communication or service connection failed. | Please retry. |
| ERR_INVALID_OPERATION | The operation is not allowed in the current state. | Use this command after the device is unlocked. |

### Sample Code

**Command example:**

```bash
# Restore the specified main window to the foreground.
ohos-window restore-window --windowId 100

# View help for the restore-window command.
ohos-window restore-window --help
```

**Output example:**

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

Queries window information.

### Constraints

- Required permission: [ohos.permission.CONTROL_DEVICE](../security/AccessToken/restricted-permissions.md#ohospermissioncontrol_device).

### Command Format

```bash
ohos-window list-windows [options]
```

> **Note:**
>
> If options is not specified, no filtering is performed and all window information is returned.

### Description

| Name | Description |
|------|------|
| `--help` | Views help information. Optional. If this parameter is specified, other parameters are ignored.|
| `--windowId <id>` | Specifies the ID of the window to query. Optional. By default, all windows are queried.|
| `--displayId <id>` | Specifies the ID of the display to query. Optional. By default, all displays are queried.|
| `--filter <visible\|excludeSystem\|foreground>` | Specifies the window filtering conditions, which can be combined. Optional. By default, no window is filtered. Among them, visible indicates returning visible windows, excludeSystem indicates not returning system windows such as the home screen and wallpaper, and foreground indicates returning foreground windows.|
| `--type <ui\|display\|layout\|meta>` | Specifies the [Window Information Category](#window-information-category) to return, which can be combined. Optional. By default, information of all categories is returned. Among them, ui indicates returning uiInfo information, display indicates returning displayInfo information, layout indicates returning layoutInfo information, and meta indicates returning metaInfo information.|

### Window Information Category

Each category represents different window information and can be specified by the `--type` parameter.

- **uiInfo**

    | Name | Description |
    |--------|------|
    |visibilityState| Window visibility. 0 indicates fully visible, 1 indicates partially visible, and 2 indicates fully invisible.|

- **displayInfo**

    | Name | Description |
    |--------|------|
    | displayId | Display ID.|

- **layoutInfo**

    | Name | Description |
    |--------|------|
    | rect | Window size.|
    | zOrder | Window layer. A larger value indicates a higher layer.|

- **metaInfo**

    | Name | Description |
    |--------|------|
    | windowId | Window ID.|
    | windowName | Window name.|
    | bundleName | Application bundle name.|
    | abilityName | Application ability name.|
    | appIndex | Index of a multi-instance application, used to distinguish different instances of the same application.|
    | pid | Process ID of the application.|
    | windowType | Window type. For the meaning of each value, see [WindowType](#windowtype).|
    | windowMode | Window mode. For the meaning of each value, see [WindowMode](#windowmode).|
    | isFocused | Whether the window is focused. true indicates focused, and false indicates not focused.|
    | isTouchable | Whether the window is touchable. true indicates touchable, and false indicates not touchable.|

### WindowType

| Value | Description |
|--------|------|
| 1 | Application main window. |
| 1001 | Application subwindow. |
| 2000 | Wallpaper. |
| 2001 | Desktop. |
| 2101 | Dock bar. |
| 2102 | Incoming call notification. |
| 2103 | Search bar. |
| 2104 | System alarm dialog box. |
| 2105 | Input method. |
| 2106 | Application floating window. |
| 2108 | Status bar. |
| 2109 | Panel. |
| 2110 | Keyguard. |
| 2111 | Volume bar. |
| 2112 | Navigation bar. |
| 2122 | Dialog box. |
| 2123 | Screenshot. |
| 2124 | Input method status bar. |
| 2125 | Global search box. |
| 2128 | System floating window. |
| 2129 | Picture-in-picture. |

### WindowMode

| Value | Description |
|--------|------|
| 1 | Full screen. |
| 102 | Floating window. |
| 103 | Picture-in-picture. |
| 105 | Split screen. |

### Error Code

| Error Code | Description | Handling Suggestion |
|--------|------|------|
| ERR_INVALID_INPUT | Invalid input parameter. | Check whether the parameter complies with the parameter description. |
| ERR_NO_PERMISSION | Permission verification failed. | Check whether the [ohos.permission.CONTROL_DEVICE](../security/AccessToken/restricted-permissions.md#ohospermissioncontrol_device) permission is configured. |
| ERR_IPC_FAILED | IPC communication or service connection failed. | Please retry. |

### Sample Code

**Command Example:**

```bash
# Query all visible windows, excluding system windows such as the desktop.
ohos-window list-windows --filter visible --filter excludeSystem

# Query the metadata information of the specified window.
ohos-window list-windows --type meta --windowId 100

# Query the layout information and metadata information of windows on the specified display.
ohos-window list-windows --displayId 0 --type layout --type meta
```

**Output Example:**

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