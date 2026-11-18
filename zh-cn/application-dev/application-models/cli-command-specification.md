# CLI命令规范

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

以下规范适用于所有预置CLI命令。

## 命令格式

CLI命令的基本格式如下：

```bash
<cli-name> <subcommand> [options]
```

- **cli-name**：CLI工具的可执行程序名称或完整路径。预置CLI工具的安装路径为`/system/bin/cli_tool/executable/`，例如ohos-aa的完整路径为`/system/bin/cli_tool/executable/ohos-aa`。
- **subcommand**：子命令名称，表示要执行的具体操作，例如`start`（启动应用）、`force-stop`（强制停止应用）。
- **options**：命令参数，采用长选项格式（如`--bundlename`、`--abilityname`），多个参数以空格分隔。参数分为必选参数和可选参数。

## 命名规范

- **子命令**：使用小写字母和连字符（`-`）组合，例如`force-stop`、`start`。
- **参数选项**：使用双连字符（`--`）加小写字母或驼峰命名，例如`--bundlename`、`--sandboxCloneIndex`。
- **参数值**：字符串值不能以连字符（`-`）开头，否则会被误识别为参数选项。

## 公共字段说明

以下字段适用于所有预置CLI命令：

| 字段 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| --help | flag | 否 | 显示当前命令的帮助信息。可单独使用，也可附加在子命令后查看该子命令的帮助信息。 |
| --bundlename | string | 否 | 目标应用的Bundle名称。部分命令中为必填参数，详见各命令参数说明。 |

## 数据返回规范

CLI命令执行结果统一以JSON格式输出。

执行成功时的返回示例：

```json
{
  "data": {
    "message": "start ability successfully."
  },
  "status": "success",
  "type": "result"
}
```

执行失败时的返回示例：

```json
{
  "errCode": "ERR_ABILITY_NOT_FOUND",
  "errMsg": "The specified ability does not exist. The specified Ability is not installed.",
  "status": "failed",
  "suggestion": "Check if the parameter abilityName and bundleName are correct. Check if the application corresponding to the specified bundleName is installed.",
  "type": "result"
}
```

JSON输出字段说明如下：

| 字段 | 类型 | 说明 |
| -------- | -------- | -------- |
| data | object | 仅执行成功时存在。包含`message`字段，描述执行结果信息。 |
| errCode | string | 仅执行失败时存在。错误码，如`"ERR_ABILITY_NOT_FOUND"`。 |
| errMsg | string | 仅执行失败时存在。错误原因描述。 |
| suggestion | string | 仅执行失败时存在。处理建议。 |
| status | string | 执行状态。`"success"`表示成功，`"failed"`表示失败。 |
| type | string | 结果类型。`"result"`表示命令执行结果。 |
