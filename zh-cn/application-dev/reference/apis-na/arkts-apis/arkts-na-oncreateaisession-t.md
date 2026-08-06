# OnCreateAISession

```TypeScript
export type OnCreateAISession = (id: string, params: string, result: OnAISessionCallback) => boolean
```

Triggered when an AI session is created. Allows custom model initialization and result handling. Return \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_ to bypass the default system behavior; return \_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_ to proceed with the default logic.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnCreateAISession = (id: string, params: string, result: OnAISessionCallback) => boolean--><!--Device-unnamed-export type OnCreateAISession = (id: string, params: string, result: OnAISessionCallback) => boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | The session task ID.  |
| params | string | 是 | Contextual data passed during creation.  |
| result | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback function to notify the system of the creation result.  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - Whether to use custom logic. \_\_\_INLINE\_CODE\_USD\_0\_\_\_ = use custom, \_\_\_INLINE\_CODE\_USD\_1\_\_\_ = proceed with default. |

