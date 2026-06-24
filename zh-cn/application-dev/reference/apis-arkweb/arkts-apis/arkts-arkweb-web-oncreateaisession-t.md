# OnCreateAISession

```TypeScript
type OnCreateAISession = (id: string, params: string, result: OnAISessionCallback) => boolean
```

AI会话创建回调函数类型。允许自定义模型初始化和结果处理。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | The session task ID. |
| params | string | 是 | Contextual data passed during creation. |
| result | OnAISessionCallback | 是 | Callback function to notify the system of the creation result. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - `true`表示使用自定义逻辑，跳过系统默认行为；`false`表示继续执行系统默认逻辑。 |

