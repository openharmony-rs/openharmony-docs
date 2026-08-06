# OnDestroyAISession

```TypeScript
export type OnDestroyAISession = (id: string) => void
```

Triggered when an AI session is destroyed. Used for cleaning up resources associated with custom AI models.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnDestroyAISession = (id: string) => void--><!--Device-unnamed-export type OnDestroyAISession = (id: string) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | The session task ID.  |

