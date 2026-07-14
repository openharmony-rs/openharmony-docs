# Callback

定义基础的回调函数。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
(data: T): V
```

定义回调函数的信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | T | 是 | 将会在回调函数中被使用的数据 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | - 返回回调函数的结果。 |

