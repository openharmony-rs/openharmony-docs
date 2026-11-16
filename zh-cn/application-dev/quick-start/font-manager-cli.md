# ohos-fontManager CLI工具

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @OningO-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

## 简介

ohos-fontManager是OpenHarmony提供的字体管理CLI（Command Line Interface，命令行界面）工具，用于在当前登录用户下安装和卸载系统字体。该工具执行结果以JSON格式输出，并提供错误码、错误原因和解决建议。ohos-fontManager的安装路径为`/system/bin/cli_tool/executable/ohos-fontManager`。

> **说明：**
>
> 该工具仅支持用户级系统字体的安装和卸载，不支持应用级或会话级作用域字体管理、数据迁移和字体观察者注册。

## 环境要求

- 设备限制：仅支持在PC/2in1设备上使用。
- 权限要求：调用方需具备[ohos.permission.UPDATE_FONT](../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_font)权限。该权限的权限级别为system_basic，授权方式为system_grant。
- 系统服务：需要font_manager_server服务（SA ID：66262）正常运行。该服务按需启动，首次调用时可能需要等待服务加载完成。

## 输出格式

除help命令外，命令执行结果以JSON格式输出。执行成功时返回`data`字段，执行失败时返回`errCode`、`errMsg`和`suggestion`字段。

| 字段 | 类型 | 说明 |
|------|------|------|
| `type` | string | 结果类型，固定为`result`。 |
| `status` | string | 执行状态。`success`表示成功，`failed`表示失败。 |
| `data` | object | 执行成功时的结果数据。 |
| `errCode` | string | 执行失败时的错误码。 |
| `errMsg` | string | 执行失败时的错误原因。 |
| `suggestion` | string | 执行失败时的处理建议。 |

命令执行成功时返回0，执行失败时返回非0。

## help

查看全局帮助信息或指定子命令的帮助信息。

```bash
# 查看全局帮助
ohos-fontManager --help
ohos-fontManager help

# 查看指定子命令帮助
ohos-fontManager help install
ohos-fontManager install --help
ohos-fontManager help uninstall
ohos-fontManager uninstall --help
```

> **说明：**
>
> help命令的输出为文本格式，不是JSON格式。

## install

从本地字体文件安装字体到当前登录用户的系统字体目录。

### 约束限制

- 需要权限：[ohos.permission.UPDATE_FONT](../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_font)。
- 设备限制：仅支持在PC/2in1设备上使用。
- 字体文件必须存在且可读，支持`.ttf`、`.otf`等字体格式。
- 字体文件路径长度不能超过4096个字符。
- 每个用户可安装的字体数量存在上限，默认最多200个。
- 字体全名不能与已安装字体重复。

### 命令格式

```bash
ohos-fontManager install --font-path <path>
```

### 参数说明

| 参数名 | 说明 |
|------|------|
| `--font-path <path>` | 必选，待安装字体文件的绝对路径或相对路径。 |
| `--help` | 可选，查看install命令的帮助信息。 |

### 错误码

| 错误码 | 说明 | 处理建议 |
|--------|------|------|
| ERR_ARG_MISSING | 缺少`--font-path`参数，或参数值为空。 | 按命令格式传入字体文件路径。 |
| ERR_ARG_INVALID | 参数值非法，例如路径长度超过4096个字符。 | 检查参数格式和长度。 |
| ERR_PERMISSION_DENIED | 调用方缺少`ohos.permission.UPDATE_FONT`权限。 | 为调用方申请并授予该权限。 |
| ERR_RESOURCE_NOT_FOUND | 字体文件不存在或不可读。 | 检查字体文件路径是否正确，以及文件是否可读。 |
| ERR_FM_FILE_VERIFY_FAIL | 字体文件格式不支持或字体校验失败。 | 使用有效的字体文件。 |
| ERR_FM_COPY_FAIL | 字体文件拷贝失败。 | 检查存储空间和字体目录的写权限。 |
| ERR_RESOURCE_EXISTS | 字体已安装。 | 先使用uninstall命令卸载字体，或更换字体文件。 |
| ERR_FM_MAX_COUNT | 已安装字体数量达到上限。 | 卸载不用的字体后重试。 |
| ERR_FM_INSTALL_FAIL | 字体服务异常，安装失败。 | 检查font_manager_server服务状态后重试。 |
| ERR_INTERNAL_ERROR | IPC通信失败或发生未知错误。 | 检查服务状态后重试。 |

### 示例代码

**命令示例：**

```bash
# 安装指定路径的字体文件
ohos-fontManager install --font-path /data/local/tmp/custom.ttf

# 查看install命令帮助
ohos-fontManager install --help
```

**成功输出示例：**

```json
{
  "type": "result",
  "status": "success",
  "data": {
    "message": "Font installed successfully",
    "fontPath": "/data/local/tmp/custom.ttf"
  }
}
```

**失败输出示例：**

```json
{
  "type": "result",
  "status": "failed",
  "errCode": "ERR_RESOURCE_NOT_FOUND",
  "errMsg": "The font does not exist.",
  "suggestion": "Verify the font file path is correct and the file is readable"
}
```

## uninstall

按字体名称从当前登录用户的系统字体目录卸载已安装的字体。

### 约束限制

- 需要权限：[ohos.permission.UPDATE_FONT](../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_font)。
- 设备限制：仅支持在PC/2in1设备上使用。
- 字体名称必须与安装时注册的字体全名一致，不能传入文件路径。
- 字体名称长度不能超过256个字符。

### 命令格式

```bash
ohos-fontManager uninstall --font-name <name>
```

### 参数说明

| 参数名 | 说明 |
|------|------|
| `--font-name <name>` | 必选，待卸载字体的名称，必须与安装时的字体全名一致。 |
| `--help` | 可选，查看uninstall命令的帮助信息。 |

### 错误码

| 错误码 | 说明 | 处理建议 |
|--------|------|------|
| ERR_ARG_MISSING | 缺少`--font-name`参数，或参数值为空。 | 按命令格式传入字体名称。 |
| ERR_ARG_INVALID | 参数值非法，例如字体名称长度超过256个字符。 | 检查参数格式和长度。 |
| ERR_PERMISSION_DENIED | 调用方缺少`ohos.permission.UPDATE_FONT`权限。 | 为调用方申请并授予该权限。 |
| ERR_RESOURCE_NOT_FOUND | 指定名称的字体未安装。 | 检查字体名称是否正确，以及字体是否已安装。 |
| ERR_FM_REMOVE_FAIL | 字体文件删除失败。 | 检查字体目录的文件权限后重试。 |
| ERR_FM_UNINSTALL_FAIL | 字体服务异常，卸载失败。 | 检查font_manager_server服务状态后重试。 |
| ERR_INTERNAL_ERROR | IPC通信失败或发生未知错误。 | 检查服务状态后重试。 |

### 示例代码

**命令示例：**

```bash
# 卸载指定名称的字体
ohos-fontManager uninstall --font-name CustomFont

# 查看uninstall命令帮助
ohos-fontManager uninstall --help
```

**成功输出示例：**

```json
{
  "type": "result",
  "status": "success",
  "data": {
    "message": "Font uninstalled successfully",
    "fontName": "CustomFont"
  }
}
```

**失败输出示例：**

```json
{
  "type": "result",
  "status": "failed",
  "errCode": "ERR_RESOURCE_NOT_FOUND",
  "errMsg": "The font file does not exist.",
  "suggestion": "Verify the font name is correct and the font is installed"
}
```

## 错误码说明

ohos-fontManager的命令行错误码与字体管理业务错误码的对应关系如下。字体管理业务错误码的详细说明请参见[字体管理错误码](../reference/apis-localization-kit/errorcode-font-manager.md)。

| 命令行错误码 | 业务错误码 | 说明 |
|------|------|------|
| ERR_ARG_MISSING | - | 缺少必选参数或未指定命令。 |
| ERR_ARG_INVALID | - | 参数值非法或命令无法识别。 |
| ERR_UNKNOWN_COMMAND | - | 未知命令。 |
| ERR_PERMISSION_DENIED | 201 | 调用方缺少`ohos.permission.UPDATE_FONT`权限。 |
| ERR_RESOURCE_NOT_FOUND | 31100101、31100107 | 字体文件不存在，或指定名称的字体未安装。 |
| ERR_FM_FILE_VERIFY_FAIL | 31100102 | 字体文件格式不支持或字体校验失败。 |
| ERR_FM_COPY_FAIL | 31100103 | 字体文件拷贝失败。 |
| ERR_RESOURCE_EXISTS | 31100104 | 字体已安装。 |
| ERR_FM_MAX_COUNT | 31100105 | 已安装字体数量达到上限。 |
| ERR_FM_INSTALL_FAIL | 31100106 | 字体服务异常，安装失败。 |
| ERR_FM_REMOVE_FAIL | 31100108 | 字体文件删除失败。 |
| ERR_FM_UNINSTALL_FAIL | 31100109 | 字体服务异常，卸载失败。 |
| ERR_INTERNAL_ERROR | - | IPC通信失败或发生未知错误。 |