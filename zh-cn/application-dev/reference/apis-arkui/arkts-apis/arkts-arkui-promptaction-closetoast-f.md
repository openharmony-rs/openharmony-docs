# closeToast

## closeToast

```TypeScript
function closeToast(toastId: number): void
```

关闭即时反馈。

> **说明：**
>
> 直接使用closeToast可能导致[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用
UIContext中的getPromptAction方法获取
> 到PromptAction对象，再通过该对象调用
> [closeToast](../../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#closetoast18)实现。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| toastId | number | 是 | openToast返回的id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |
| [103401](../../errorcode-universal.md#103401-Cannot) | Cannot find the toast. |

