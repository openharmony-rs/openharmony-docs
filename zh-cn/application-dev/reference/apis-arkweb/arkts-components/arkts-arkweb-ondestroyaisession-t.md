# OnDestroyAISession

```TypeScript
type OnDestroyAISession = (id: string) => void
```

AI会话销毁回调函数类型。用于清理与自定义AI模型关联的资源。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type OnDestroyAISession = (id: string) => void--><!--Device-unnamed-type OnDestroyAISession = (id: string) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 会话任务ID。 |

