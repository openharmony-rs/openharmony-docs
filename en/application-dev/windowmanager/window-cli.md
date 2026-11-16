# ohos-window CLI Tool
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @JUGaaab-->
<!--Designer: @ki_ja-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=5d96cb6799688f7b7c422c42ede1b29e718f6550 translatedAt=2026-11-05T10:50:37.131Z pushedAt=2026-11-06T01:42:07.576Z nl=1 -->

## Description

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

> **NOTE**
>
> If options is not specified, calling this command returns the ERR_INVALID_INPUT error code.

### Parameter Description

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

```bash
# Restore the specified main window to the foreground.
ohos-window restore-window --windowId 100

# View the help information of the restore-window command.
ohos-window restore-window --help
```