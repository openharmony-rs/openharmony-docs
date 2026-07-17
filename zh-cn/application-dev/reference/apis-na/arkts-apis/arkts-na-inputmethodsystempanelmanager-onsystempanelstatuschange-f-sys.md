# onSystemPanelStatusChange（系统接口）

## onSystemPanelStatusChange

```TypeScript
function onSystemPanelStatusChange(callback: Callback<SystemPanelStatus>): void
```

订阅系统面板状态改变事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputMethodSystemPanelManager-function onSystemPanelStatusChange(callback: Callback<SystemPanelStatus>): void--><!--Device-inputMethodSystemPanelManager-function onSystemPanelStatusChange(callback: Callback<SystemPanelStatus>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<SystemPanelStatus> | 是 | 当系统面板状态改变时触发的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |

