# OnHomeShowOnTopCallback

```TypeScript
declare type OnHomeShowOnTopCallback = (name: string) => void
```

当主页在栈顶显示时触发的回调函数。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 显示在栈顶的页面的标识符。 |

