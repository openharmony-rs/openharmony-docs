# TypeConstructorWithArgs

含有任意入参的类构造器。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
new(...args: any): T
```

创建并返回一个指定类型T的实例。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| args | any | 是 | 函数入参。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | T类型的实例。 |

