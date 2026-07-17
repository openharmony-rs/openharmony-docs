# onSystemPrivateCommand（系统接口）

## onSystemPrivateCommand

```TypeScript
function onSystemPrivateCommand(callback: Callback<Record<string, CommandDataType>>): void
```

订阅输入法应用发送私有数据命令的事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputMethodSystemPanelManager-function onSystemPrivateCommand(callback: Callback<Record<string, CommandDataType>>): void--><!--Device-inputMethodSystemPanelManager-function onSystemPrivateCommand(callback: Callback<Record<string, CommandDataType>>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<Record<string, CommandDataType>> | 是 | 当输入法应用发送私有数据命令时触发的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |

