# MediaQuery

class MediaQuery

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## matchMediaSync

```TypeScript
matchMediaSync(condition: string): mediaQuery.MediaQueryListener
```

Sets the media query criteria and returns the corresponding listening handle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | string | 是 | media conditions |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| mediaQuery.MediaQueryListener | the corresponding listening handle |

