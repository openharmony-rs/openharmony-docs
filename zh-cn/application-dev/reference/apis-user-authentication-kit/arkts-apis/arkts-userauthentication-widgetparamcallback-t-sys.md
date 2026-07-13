# WidgetParamCallback（系统接口）

```TypeScript
type WidgetParamCallback = (challenge: Uint8Array) => WidgetParam
```

调用以获取远程身份验证的用户身份验证页面上显示的信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| challenge | Uint8Array | 是 | 挑战值，可以以Uint8Array([])格式传递。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WidgetParam | widgetParam -用户认证页面参数。 |

