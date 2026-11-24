# 剪贴板工具（ohos-pasteboard）

<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @zhusiyuan2-->
<!--Tester: @maxiaorong-->
<!--Adviser: @fang-jinxu-->

剪贴板命令行工具，支持对剪贴板数据的读取、写入和查询操作，适用于设置或获取HTML、URI或纯文本数据，不适用于非文本数据类型的设置或获取。

## 设置剪贴板数据命令（set-data）

### 场景介绍

set-data命令用于设置剪贴板数据，支持写入HTML、URI或纯文本内容，可同时设置多种数据类型，创建多样式数据。不适用于非文本数据类型的设置。

### 命令格式

```bash
ohos-pasteboard set-data [--text <text>] [--html <html>] [--uri <uri>]
```

命令执行成功后，数据会写入系统剪贴板。

### 约束限制

- **设备与权限要求**：设备要求详见[面向Agent的CLI命令概述](cli-for-agent-overview.md#约束与限制)；本命令无权限要求。
- **数据类型约束**：仅支持HTML、URI或纯文本数据，不适用于设置非文本类型（如PixelMap）的数据。
- **参数约束**：`--text`、`--html`、`--uri`至少提供一个。

### 参数说明

| 参数 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| --text | string | 三选一 | 写入剪贴板的纯文本内容。 |
| --html | string | 三选一 | 写入剪贴板的HTML内容。 |
| --uri | string | 三选一 | 写入剪贴板的URI内容。 |
| --help | flag | 否 | 显示set-data子命令的帮助信息。 |

### 错误码

命令执行失败时，JSON输出中的`errCode`字段返回以下错误码：

| 错误码 | 说明 | 处理建议 |
| ------- | -------- | -------- |
| ERR_ARG_INVALID | 参数值无效。 | 检查参数有效性，至少提供一种数据类型和内容，如`--text content`。 |
| ERR_NO_DATA | 无数据可设置。 | 至少提供一种数据类型（text/html/uri）。 |
| ERR_DATA_SIZE | 数据大小超限。 | 减小数据大小后重试。 |
| ERR_DATA_INVALID | 数据格式无效。 | 检查数据格式是否受支持。 |
| ERR_SERIALIZATION | 数据序列化失败。 | 减小数据大小后重试。 |
| ERR_DESERIALIZATION | 数据反序列化失败。 | 减小数据大小后重试。 |
| ERR_SERVICE_UNAVAILABLE | 剪贴板服务不可用。 | 检查剪贴板服务是否正常运行。 |
| ERR_SET_DATA_FAILED | 设置剪贴板数据失败。 | 检查剪贴板服务是否可用。 |
| ERR_INTERNAL_ERROR | 内部错误。 | 检查剪贴板进程是否正常启动。 |

### 示例代码

- 设置纯文本数据：

    ```bash
    ohos-pasteboard set-data --text "Hello World"
    ```

- 设置HTML数据：

    ```bash
    ohos-pasteboard set-data --html "<html><p>Hello</p></html>"
    ```

- 设置URI数据：

    ```bash
    ohos-pasteboard set-data --uri "file:///path/to/file"
    ```

- 同时设置多种数据类型（创建多样式数据）：

    ```bash
    ohos-pasteboard set-data --text "Hello" --html "<p>Hello</p>"
    ```

## 读取剪贴板数据命令（get-data）

### 场景介绍

get-data命令用于读取剪贴板数据，可获取剪贴板中的HTML、URI或纯文本内容。不适用于获取非文本类型数据。

### 命令格式

```bash
ohos-pasteboard get-data
```

命令执行成功后，会返回系统剪贴板的数据内容。

### 约束限制

- **设备与权限要求**：设备要求详见[面向Agent的CLI命令概述](cli-for-agent-overview.md#约束与限制)；执行本命令需申请[ohos.permission.READ_PASTEBOARD](../security/AccessToken/restricted-permissions.md#ohospermissionread_pasteboard)权限，申请方式参见[申请访问剪贴板权限](../basic-services/pasteboard/get-pastedata-permission-guidelines.md)。
- **数据类型约束**：仅支持获取HTML、URI或纯文本数据，不适用于非文本数据类型的获取。

### 参数说明

| 参数 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| --help | flag | 否 | 显示get-data子命令的帮助信息。 |

### 错误码

命令执行失败时，JSON输出中的`errCode`字段返回以下错误码：

| 错误码 | 说明 | 处理建议 |
| ------- | -------- | -------- |
| ERR_PERMISSION_DENIED | 权限不足。 | 申请ohos.permission.READ_PASTEBOARD权限。 |
| ERR_NO_DATA | 剪贴板为空。 | 先执行set-data设置数据。 |
| ERR_NO_USER_DATA | 当前用户无剪贴板数据。 | 先执行set-data设置数据。 |
| ERR_DATA_EXPIRED | 剪贴板数据已过期。 | 数据已因过期被自动清除，重新执行set-data设置数据。 |
| ERR_CROSS_BORDER | 屏幕状态不匹配。 | 数据设置时的屏幕锁定状态与当前不一致，请调整屏幕状态后重试。 |
| ERR_TIMEOUT | 操作超时。 | 稍后重试。 |
| ERR_TASK_PROCESSING | 任务正在处理中。 | 另一项粘贴操作正在进行，等待完成后重试。 |
| ERR_REMOTE_EXCEPTION | 远端设备异常。 | 从远端设备获取数据失败，稍后重试。 |
| ERR_REMOTE_TASK | 远端任务失败。 | 远端数据任务创建失败，稍后重试。 |
| ERR_GET_REMOTE | 获取远端数据失败。 | 确认远端设备状态正常或网络连接可用。 |
| ERR_INVALID_USER | 用户ID无效。 | 确认当前用户账号状态正常。 |
| ERR_SERIALIZATION | 数据序列化失败。 | 稍后重试。 |
| ERR_DESERIALIZATION | 数据反序列化失败。 | 稍后重试。 |
| ERR_SERVICE_UNAVAILABLE | 剪贴板服务不可用。 | 检查剪贴板服务是否正常运行。 |
| ERR_GET_DATA_FAILED | 获取剪贴板数据失败。 | 检查剪贴板是否有数据。 |
| ERR_INTERNAL_ERROR | 内部错误。 | 检查剪贴板进程是否正常启动。 |

### 示例代码

- 读取剪贴板数据：

    ```bash
    ohos-pasteboard get-data
    ```

## 清空剪贴板数据命令（clear-data）

### 场景介绍

clear-data命令用于清空剪贴板数据，可用于重置剪贴板状态。

### 命令格式

```bash
ohos-pasteboard clear-data
```

命令执行成功后，会清空系统剪贴板的数据。不支持选择性删除部分记录。

### 约束限制

- **设备与权限要求**：设备要求详见[面向Agent的CLI命令概述](cli-for-agent-overview.md#约束与限制)；本命令无权限要求。
- **操作范围约束**：清空操作将删除系统剪贴板中的全部数据。

### 参数说明

| 参数 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| --help | flag | 否 | 显示clear-data子命令的帮助信息。 |

### 错误码

命令执行失败时，JSON输出中的`errCode`字段返回以下错误码：

| 错误码 | 说明 | 处理建议 |
| ------- | -------- | -------- |
| ERR_INTERNAL_ERROR | 内部错误。 | 检查剪贴板进程是否正常启动。 |

### 示例代码

- 清空剪贴板数据：

    ```bash
    ohos-pasteboard clear-data
    ```

## 检查剪贴板是否有数据命令（has-data）

### 场景介绍

has-data命令用于检查系统剪贴板是否有数据，可在读取数据前确认剪贴板状态，避免无效读取。不支持内容级别的数据校验。

### 命令格式

```bash
ohos-pasteboard has-data
```

命令执行成功后，返回系统剪贴板中是否有数据。

### 约束限制

- **设备与权限要求**：设备要求详见[面向Agent的CLI命令概述](cli-for-agent-overview.md#约束与限制)；本命令无权限要求。

### 参数说明

| 参数 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| --help | flag | 否 | 显示has-data子命令的帮助信息。 |

### 错误码

命令执行失败时，JSON输出中的`errCode`字段返回以下错误码：

| 错误码 | 说明 | 处理建议 |
| ------- | -------- | -------- |
| ERR_INTERNAL_ERROR | 内部错误。 | 检查剪贴板进程是否正常启动。 |

### 示例代码

- 检查剪贴板是否有数据：

    ```bash
    ohos-pasteboard has-data
    ```

## 检查剪贴板数据类型命令（has-data-type）

### 场景介绍

has-data-type命令用于检查系统剪贴板是否有指定类型的数据，可在读取数据前确认目标数据类型。不支持内容级别的数据校验。

### 命令格式

```bash
ohos-pasteboard has-data-type --type <type>
```

命令执行成功后，返回系统剪贴板中是否有指定类型的数据。

### 约束限制

- **设备与权限要求**：设备要求详见[面向Agent的CLI命令概述](cli-for-agent-overview.md#约束与限制)；本命令无权限要求。
- **参数约束**：`--type`是必选参数。

### 参数说明

| 参数 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| --type | string | 是 | 检查的数据类型，如text/plain、text/html或text/uri。 |
| --help | flag | 否 | 显示has-data-type子命令的帮助信息。 |

### 错误码

命令执行失败时，JSON输出中的`errCode`字段返回以下错误码：

| 错误码 | 说明 | 处理建议 |
| ------- | -------- | -------- |
| ERR_ARG_MISSING | 缺少必需参数。 | 输入有效的数据类型，如`--type text/plain`。 |
| ERR_INTERNAL_ERROR | 内部错误。 | 检查剪贴板进程是否正常启动。 |

### 示例代码

- 检查剪贴板是否包含纯文本数据：

    ```bash
    ohos-pasteboard has-data-type --type text/plain
    ```

- 检查剪贴板是否包含HTML数据：

    ```bash
    ohos-pasteboard has-data-type --type text/html
    ```

- 检查剪贴板是否包含URI数据：

    ```bash
    ohos-pasteboard has-data-type --type text/uri
    ```

## 检查剪贴板远端数据命令（has-remote-data）

### 场景介绍

has-remote-data命令用于检查系统剪贴板是否包含远端设备的数据，可用于确认待粘贴的数据是否来自其他设备。不支持查询远端设备详细信息。

### 命令格式

```bash
ohos-pasteboard has-remote-data
```

命令执行成功后，返回系统剪贴板中是否包含远端设备的数据。

### 约束限制

- **设备与权限要求**：设备要求详见[面向Agent的CLI命令概述](cli-for-agent-overview.md#约束与限制)；本命令无权限要求。

### 参数说明

| 参数 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| --help | flag | 否 | 显示has-remote-data子命令的帮助信息。 |

### 错误码

命令执行失败时，JSON输出中的`errCode`字段返回以下错误码：

| 错误码 | 说明 | 处理建议 |
| ------- | -------- | -------- |
| ERR_INTERNAL_ERROR | 内部错误。 | 检查剪贴板进程是否正常启动。 |

### 示例代码

- 检查剪贴板是否有远端设备数据：

    ```bash
    ohos-pasteboard has-remote-data
    ```
